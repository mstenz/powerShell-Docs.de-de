---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Ressource,Katalog,Setup
title: Hinzufügen von Parametern zu einer Konfiguration
ms.openlocfilehash: 9dd9f2be58c13840be2b24e7e21a0d4af79b67cc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80263151"
---
# <a name="add-parameters-to-a-configuration"></a>Hinzufügen von Parametern zu einer Konfiguration

Ebenso wie Funktionen können [Konfigurationen](configurations.md) parametrisiert werden können, sodass dynamischere Konfigurationen auf Grundlage der Benutzereingabe möglich sind. Die Schritte ähneln den in [Funktionen mit Parametern](/powershell/module/microsoft.powershell.core/about/about_functions) beschriebenen.

Dieses Beispiel beginnt mit einer einfachen Konfiguration, die den „Spooler“-Dienst als „Wird ausgeführt“ konfiguriert.

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Integrierte Konfigurationsparameter

Im Gegensatz zu einer Funktion fügt das [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute)-Attribut jedoch keine Funktionalität hinzu. Zusätzlich zu [allgemeinen Parametern](/powershell/module/microsoft.powershell.core/about/about_commonparameters) können Konfigurationen auch die folgenden integrierten Parameter verwenden, ohne dass Sie sie definieren müssen.

|        Parameter        |                                         BESCHREIBUNG                                          |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `-InstanceName`         | Zur Definition [zusammengesetzter Konfigurationen](compositeconfigs.md)                             |
| `-DependsOn`            | Zur Definition [zusammengesetzter Konfigurationen](compositeconfigs.md)                             |
| `-PSDSCRunAsCredential` | Zur Definition [zusammengesetzter Konfigurationen](compositeconfigs.md)                             |
| `-ConfigurationData`    | Zur Übergabe strukturierter [Konfigurationsdaten](configData.md) für die Verwendung in der Konfiguration. |
| `-OutputPath`           | Um anzugeben, wo Ihre „\<Computername\>.mof“-Datei kompiliert wird                      |

## <a name="adding-your-own-parameters-to-configurations"></a>Hinzufügen Ihrer eigenen Parameter zu Konfigurationen

Neben den integrierten Parametern können Sie auch Ihre eigenen Parameter Ihren Konfigurationen hinzufügen.
Der Parameterblock wird wie eine Funktion direkt in die Deklaration der Konfiguration eingefügt. Ein Konfigurationsparameterblock muss außerhalb von **Node**-Deklarationen und vor jeglichen *import*-Anweisungen platziert werden. Durch Hinzufügen von Parametern können Sie Ihre Konfigurationen robuster und dynamischer machen.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Hinzufügen eines ComputerName-Parameters

Als ersten Parameter könnten Sie einen `-Computername`-Parameter hinzufügen, sodass Sie dynamisch eine MOF-Datei für einen beliebigen `-Computername` kompilieren können, den Sie Ihrer Konfiguration übergeben. Wie bei Funktionen können Sie auch einen Standardwert definieren für den Fall, dass der Benutzer keinen Wert für `-ComputerName` übergibt.

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Anschließend können Sie in Ihrer Konfiguration Ihren `-ComputerName`-Parameter angeben, wenn Sie Ihren Node-Block definieren.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Aufrufen Ihrer Konfiguration mit Parametern

Nachdem Sie Ihrer Konfiguration Parameter hinzugefügt haben, können Sie sie genau so wie ein Cmdlet verwenden.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Kompilieren mehrerer MOF-Dateien

Der Node-Block kann auch eine durch Trennzeichen getrennte Liste von Computernamen annehmen und generiert für jeden eine MOF-Datei. Sie können das folgende Beispiel ausführen, um MOF-Dateien für alle an den `-ComputerName`-Parameter übergebenen Computer zu generieren.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Erweiterte Parameter in Konfigurationen

Zusätzlich zu einem `-ComputerName`-Parameter können wir Parameter für den Dienstnamen und Zustand hinzufügen.
Im folgenden Beispiel wird ein Parameterblock mit einem `-ServiceName`-Parameter hinzugefügt und verwendet, um den **Service**-Ressourcenblock dynamisch zu definieren. Es wird auch ein `-State`-Parameter hinzugefügt, um den **State** (Zustand) im **Service**-Ressourcenblock dynamisch zu definieren.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> In fortgeschritteneren Szenarien könnte es sinnvoller sein, dynamische Daten in strukturierte [Konfigurationsdaten](configData.md) zu verschieben.

Die Beispielkonfiguration nimmt einen dynamischen `$ServiceName` an, aber wenn er nicht angegeben wird, tritt beim Kompilieren ein Fehler auf. Sie können einen Standardwert wie im folgenden Beispiel hinzufügen.

```powershell
[String]
$ServiceName="Spooler"
```

In diesem Fall ist es allerdings sinnvoller, vom Benutzer einfach die Eingabe eines Werts für den `$ServiceName`-Parameter zu erzwingen. Mit dem `parameter`-Attribut können Sie die Überprüfungs- und Pipelineunterstützung durch die Parameter Ihrer Konfiguration erweitern.

Fügen Sie vor jeder Parameterdeklaration wie im folgenden Beispiel den `parameter`-Attributblock ein.

```powershell
[parameter()]
[String]
$ServiceName
```

Sie können für jedes `parameter`-Attribut Argumente angeben, um die Aspekte der definierten Parameter zu steuern. Im folgenden Beispiel wird `$ServiceName` zu einem **Mandatory**-Parameter.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Wir möchten verhindern, dass der Benutzer für den `$State`-Parameter außerhalb eines vordefinierten Satzes (z.B. „Running“, „Stopped“) liegende Werte angibt, und verwenden hierzu das `ValidationSet*`-Attribut. Im folgenden Beispiel wird das `ValidationSet`-Attribut dem `$State`-Parameter hinzugefügt. Da wir den `$State`-Parameter nicht zu einem **Mandatory**-Parameter machen möchten, müssen wir für ihn einen Standardwert hinzufügen.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Sie müssen kein `parameter`-Attribut angeben, wenn Sie ein `validation`-Attribut verwenden.

Weitere Informationen über `parameter` und Validierungsattribute finden Sie unter [Informationen zu Parametern erweiterter Funktionen](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).

## <a name="fully-parameterized-configuration"></a>Vollständig parametrisierte Konfiguration

Wir verfügen jetzt über eine parametrisierte Konfiguration, die vom Benutzer die Eingabe von `-InstanceName` und `-ServiceName` erzwingt und den `-State`-Parameter überprüft.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to explicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen

- [Schreiben von Hilfe für DSC-Konfigurationen](configHelp.md)
- [Bedingte Anweisungen und Schleifen in Konfigurationen](flow-control-in-configurations.md)
- [Verwenden von Konfigurationsdaten in DSC](configData.md)
- [Trennen von Konfiguration und Umgebungsdaten](separatingEnvData.md)
