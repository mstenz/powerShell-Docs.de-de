---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Verwenden von Import-DscResource
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401592"
---
# <a name="using-import-dscresource"></a>Verwenden von Import-DscResource

`Import-DScResource` ist ein Schlüsselwort "dynamic", die nur innerhalb eines Skriptblocks Konfiguration verwendet werden kann. Die `Import-DSCResource` Schlüsselwort, um alle Ressourcen in Ihrer Konfiguration erforderlich sind, zu importieren. Ressourcen, die unter `$phsome` werden automatisch importiert, aber es dennoch als bewährte Methode, die alle verwendete Ressourcen explizit Importieren Ihrer [Konfiguration](Configurations.md).

Die Syntax für `Import-DSCResource` ist unten dargestellt.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|Parameter  |Beschreibung  |
|---------|---------|
|`-Name`|Den Namen der DSC-Ressource, die Sie importieren müssen. Wenn Sie der Namen des Moduls angegeben wird, durchsucht der Befehl, um diese DSC-Ressourcen innerhalb dieses Moduls; Andernfalls sucht der Befehl die DSC-Ressourcen in allen Pfaden der DSC-Ressource. Platzhalter werden unterstützt.|
|`-ModuleName`|Der Container-Module-Namen oder Modul Spezifikation(en).  Bei Angabe von Ressourcen, die von einem Modul zu importieren. versucht der Befehl, nur die Ressourcen zu importieren. Wenn Sie das Modul nur angeben, importiert der Befehl alle DSC-Ressourcen im Modul an.|

Sie können Platzhalterzeichen mit dem `-Name` Parameter bei Verwendung `Import-DSCResource`.

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Beispiel: Verwenden Sie Import-DSCResource in einer Konfiguration

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> Mehrere Werte für Namen von Ressourcen und Module im selben Befehl angeben, werden nicht unterstützt. Sie haben nicht deterministische Verhalten in Bezug auf die Ressource, von welchem Modul geladen wird, für den Fall, dass dieselbe Ressource in mehrere Module vorhanden ist. Folgenden Befehl aus, führt zu Fehler während der Kompilierung.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Folgendes in Betracht, wenn Sie nur den Name-Parameter verwenden:

- Es ist ein ressourcenintensiver Vorgang abhängig von der Anzahl der Module, die auf dem Computer installiert.
- Es lädt die erste Ressource mit dem angegebenen Namen gefunden. Bei mehr als eine Ressource mit demselben Namen, die installiert wird, konnte es falsche Ressource geladen.

Die empfohlene Verwendung ist an `–ModuleName` mit der `-Name` Parameter, wie unten beschrieben.

Diese Verwendung hat die folgenden Vorteile:

- Es verringert die Auswirkungen auf die Leistung begrenzen den Suchbereich für die angegebene Ressource.
- Das Modul definieren die Ressource, um sicherzustellen, dass die richtige Ressource geladen wird definiert explizit.

> [!NOTE]
> In PowerShell 5.0 können DSC-Ressourcen mehrere Versionen haben, und verschiedene Versionen können parallel auf einem Computer installiert sein. Dies wird dadurch implementiert, dass mehrere Versionen eines Ressourcenmoduls vorhanden sind, die sich im selben Modulordner befinden.
> Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense mit Import-DSCResource

Beim Erstellen der DSC-Konfigurations in der ISE bietet PowerShell IntelliSense für Ressourcen und Ressourceneigenschaften. Ressourcendefinitionen unter der `$pshome` Modulpfad automatisch geladen werden. Beim Importieren von Ressourcen mithilfe der `Import-DSCResource` -Schlüsselwort, die Definitionen für die angegebene Ressource hinzugefügt werden und Intellisense wird erweitert, um die importierte Ressource Schema enthalten.

![Intellisense für Ressourcen](/media/resource-intellisense.png)

> [!NOTE]
> PowerShell 5.0 ab, wurde Tab-Vervollständigung der ISE für DSC-Ressourcen und deren Eigenschaften hinzugefügt. Weitere Informationen finden Sie unter [Ressourcen](../resources/resources.md).

Beim Kompilieren der Konfiguration, verwendet PowerShell die Definitionen für importierte Ressource, um alle ressourcenblöcken in der Konfiguration zu überprüfen.
Jedem Ressourcenblock wird überprüft, mit der Schemadefinition der Ressource, für die folgenden Regeln.

- Nur Eigenschaften, die im Schema definiert wird.
- Die Datentypen für jede Eigenschaft sind korrekt.
- Eigenschaften von Schlüsseln werden angegeben.
- Keine nur-Lese Eigenschaft wird verwendet.
- Überprüfung auf dem Wert werden die Datentypen zugeordnet.

Beachten Sie die folgende Konfiguration ein:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Kompilieren diese Konfiguration führt zu einem Fehler.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense und der schemaüberprüfung können Sie weitere Fehler während der Analyse und Kompilierung, Abfangen Komplikationen zur Laufzeit vermieden.

> [!NOTE]
> Jede DSC-Ressource kann einen Namen haben, und ein **FriendlyName** durch die der Ressource Schema definiert wird. Im folgenden sind die ersten beiden Zeilen von "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Wenn Sie diese Ressource in einer Konfiguration verwenden, können Sie angeben **MSFT_ServiceResource** oder **Service**.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell-v4- und v5-Unterschiede

Es gibt mehrere Unterschiede, die Sie sehen, wenn Konfigurationen in PowerShell 4.0 im Vergleich zu erstellen. PowerShell 5.0 und höher. In diesem Abschnitt werden die Unterschiede hervorgehoben, dass für diesen Artikel relevant angezeigt.

### <a name="multiple-resource-versions"></a>Mehrere Versionen der Ressource

Installieren und verwenden mehrere Versionen der Ressourcen-Seite-an-Seite wurde in PowerShell 4.0 nicht unterstützt. Wenn Sie das Importieren von Ressourcen in Ihrer Konfiguration Probleme feststellen, stellen Sie sicher, dass Sie nur eine Version der Ressource installiert haben.

In der Abbildung unten, zwei Versionen der **"xpsdesiredstateconfiguration"** -Modul installiert werden.

![Mehrere Ressourcen Versionen behoben](/media/multiple-resource-versions-broken.md)

Kopieren Sie den Inhalt Ihrer gewünschten Module-Version, auf der obersten Ebene des Modulverzeichnisses.

![Mehrere Ressourcen Versionen behoben](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Ressourcenspeicherort

Beim Erstellen und Kompilieren von Konfigurationen, können Ihre Ressourcen gespeichert werden, in einem Verzeichnis, die gemäß Ihrer [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). In PowerShell 4.0 erfordert der LCM alle DSC-ressourcenmodulen unter "Programm Files\WindowsPowerShell\Modules" gespeichert werden oder `$pshome\Modules`. Ab in PowerShell 5.0 ist diese Anforderung wurde entfernt und Ressourcenmodule können gespeichert werden, in einem Verzeichnis anhand des `PSModulePath`.

## <a name="see-also"></a>Siehe auch

- [Ressourcen](../resources/resources.md)
