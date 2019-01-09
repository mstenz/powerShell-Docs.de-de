---
ms.date: 12/12/2018
keywords: DSC, Powershell, Resource, Katalog, setup
title: Hinzufügen von Parametern zu einer Konfiguration
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401430"
---
# <a name="add-parameters-to-a-configuration"></a>Hinzufügen von Parametern zu einer Konfiguration

Ebenso wie Funktionen, [Konfigurationen](configurations.md) parametrisiert werden können, um mehr dynamische Konfigurationen, die auf Grundlage der Benutzereingabe zu ermöglichen. Die Schritte ähneln jenen in [Funktionen mit Parametern](/powershell/module/microsoft.powershell.core/about/about_functions).

Dieses Beispiel beginnt mit einer einfachen Konfiguration, die den "Spooler" Dienst "Ausgeführt wird" konfiguriert.

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a>Integrierte Konfiguration-Parameter

Im Gegensatz zu einer Funktion jedoch die [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) -Attribut fügt keine Funktionalität. Zusätzlich zu [allgemeine Parameter](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Konfigurationen können auch die folgenden integrierten in-Parameter, ohne dass Sie sie definieren.

|Parameter  |Beschreibung  |
|---------|---------|
|`-InstanceName`|Bei der Definition verwendet [zusammengesetzten Konfigurationen](compositeconfigs.md)|
|`-DependsOn`|Bei der Definition verwendet [zusammengesetzten Konfigurationen](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Bei der Definition verwendet [zusammengesetzten Konfigurationen](compositeconfigs.md)|
|`-ConfigurationData`|Zum Übergeben von in strukturierten [Konfigurationsdaten](configData.md) für die Verwendung in der Konfiguration.|
|`-OutputPath`|Zum angeben, wo Ihre "\<Computername\>.mof" Datei kompiliert wird|

## <a name="adding-your-own-parameters-to-configurations"></a>Hinzufügen von Ihren eigenen Parametern an Konfigurationen

Neben den integrierten-Standardparametern können Sie auch Ihren eigenen Parametern an, Ihre Konfigurationen hinzufügen. Der Parameterblock wird direkt in der Deklaration der Konfiguration, wie eine Funktion. Ein Konfigurationsblock-Parameter muss außerhalb einer **Knoten** Deklarationen und über allen *importieren* Anweisungen. Durch Hinzufügen von Parametern, können Sie Ihre Konfigurationen robuster und dynamisches vornehmen.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Fügen Sie einen "Computername"-Parameter hinzu.

Der erste Parameter, die Sie möglicherweise hinzufügen, ist eine `-Computername` an, damit Sie dynamisch eine "MOF"-Datei für eine beliebige kompilieren können, `-Computername` Sie Ihrer Konfiguration übergeben. Wie Functions können Sie auch einen Standardwert definieren für den Fall, dass der Benutzer einen Wert für nicht erfüllt `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

Anschließend können Sie angeben, in Ihrer Konfiguration können Ihre `-ComputerName` Parameter, wenn Sie Ihre "Node"-Block zu definieren.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Rufen Sie Ihre Konfiguration mit Parametern

Nachdem Sie die Konfiguration Parameter hinzugefügt haben, können Sie sie genau so wie Sie mit einem Cmdlet verwenden.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Kompilieren mehrere MOF-Dateien

Der "Node"-Block kann auch eine durch Trennzeichen getrennte Liste von Computernamen annehmen und "MOF"-Dateien für die einzelnen generiert. Sie können das folgende Beispiel zum Generieren von "MOF"-Dateien für alle Computer, die an Ausführen der `-ComputerName` Parameter.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
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

Zusätzlich zu einem `-ComputerName` Parameter, wir können die Parameter für den Dienstnamen und den Zustand hinzufügen. Das folgende Beispiel fügt einen Parameterblock mit einer `-ServiceName` Parameter und verwendet, um dynamisch zu definieren die **Service** Ressourcenblock. Auch eine `-State` Parameter, um dynamisch zu definieren die **Zustand** in die **Service** Ressourcenblock.

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

    # It is best practice to implicitly import any required resources or modules.
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
> In weitere Advacned Szenarien kann es sinnvoller, dynamische Daten in eine strukturierte verschieben, [Konfigurationsdaten](configData.md).

In diesem Beispiel Konfiguration jetzt wird eine dynamische `$ServiceName`, aber wenn nicht angegeben wurde, kompilieren führt zu einem Fehler. Sie können einen Standardwert wie im folgenden Beispiel hinzufügen.

```powershell
[String]
$ServiceName="Spooler"
```

In diesem Fall allerdings es ist sinnvoller, einfach erzwingen, dass die Benutzer geben Sie einen Wert für die `$ServiceName` Parameter. Die `parameter` Attribut können Sie nun Unterstützung für weitere Überprüfung und die Pipeline an die Konfiguration der Parameter.

Fügen Sie vor jeder Parameterdeklaration der `parameter` Attributblock, wie im folgenden Beispiel.

```powershell
[parameter()]
[String]
$ServiceName
```

Sie können angeben, dass Argumente für jede `parameter` -Attribut, um die Kontrolle einiger Aspekte der definierten Parameter. Im folgenden Beispiel wird die `$ServiceName` eine **obligatorisch** Parameter.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Für die `$State` Parameter würden wir gerne, dass Benutzer von der Angabe von Werten außerhalb eines vordefinierten Satzes (z. B. wird ausgeführt, beendet) der `ValidationSet*`Attribut würde verhindern, dass den Benutzer angeben von Werten außerhalb eines vordefinierten Satzes (z. B. wird ausgeführt, Beendet). Im folgenden Beispiel wird die `ValidationSet` -Attribut auf die `$State` Parameter. Da wir nicht, stellen möchten die `$State` Parameter **obligatorisch**, wir müssen einen Standardwert für die sie hinzufügen.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Sie müssen sich nicht an eine `parameter` -Attribut bei Verwendung einer `validation` Attribut.

Erfahren Sie mehr über die `parameter` und bei Validierungsattributen im [About_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Vollständig parametrisierter Konfiguration

Wir verfügen jetzt über eine parametrisierte Konfiguration, die erzwingt, den Benutzer dass an eine `-InstanceName`, `-ServiceName`, und überprüft die `-State` Parameter.

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

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- [Schreiben von Hilfe für DSC-Konfigurationen](configHelp.md)
- [Dynamische Konfigurationen](flow-control-in-configurations.md)
- [Verwenden von Konfigurationsdaten in Ihren Konfigurationen](configData.md)
- [Separate Daten für Konfigurations- und Umgebungsdaten](separatingEnvData.md)
