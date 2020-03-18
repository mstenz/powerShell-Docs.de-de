---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Verwenden von Import-DscResource
ms.openlocfilehash: a041169ad557becf7ca87641d9ce5222ee8f6beb
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402447"
---
# <a name="using-import-dscresource"></a>Verwenden von Import-DscResource

`Import-DScResource` ist ein dynamisches Schlüsselwort, das nur innerhalb eines Configuration-Skriptblocks verwendet werden kann. Das `Import-DSCResource`-Schlüsselwort dient zum Importieren aller Ressourcen, die in Ihrer Konfiguration erforderlich sind. Ressourcen unter `$pshome` werden automatisch importiert, aber es gilt immer noch als bewährte Methode, alle in Ihrer [Konfiguration](Configurations.md) verwendeten Ressourcen explizit zu importieren.

Die Syntax für `Import-DSCResource` ist unten dargestellt.  Wenn Sie Module mit Namen angeben, müssen Sie jedes in einer neuen Zeile aufführen.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|Parameter  |BESCHREIBUNG  |
|---------|---------|
|`-Name`|Die Namen der DSC-Ressourcen, die Sie importieren müssen. Wenn der Name des Moduls angegeben wird, durchsucht der Befehl dieses Modul nach diesen DSC-Ressourcen; andernfalls durchsucht der Befehl die DSC-Ressourcen in allen DSC-Ressourcenpfaden. Platzhalter werden unterstützt.|
|`-ModuleName`|Modulname oder Modulspezifikation.  Bei Angabe von Ressourcen, die aus einem Modul importiert werden sollen, versucht der Befehl, nur diese Ressourcen zu importieren. Wenn Sie nur das Modul angeben, importiert der Befehl alle DSC-Ressourcen im Modul.|
|`-ModuleVersion`|Ab PowerShell 5.0 können Sie angeben, welche Version eines Moduls von einer Konfiguration verwendet werden soll. Weitere Informationen finden Sie unter [Importieren einer spezifischen Version einer installierten Ressource](sxsresource.md).|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Beispiel: Verwenden von Import-DSCResource in einer Konfiguration

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> Die Angabe mehrerer Werte für Ressourcen- und Modulnamen im selben Befehl wird nicht unterstützt. Falls dieselbe Ressource in mehreren Modulen vorhanden ist, kann dies in Bezug darauf, welche Ressource aus welchem Modul geladen wird, zu einem nicht deterministischen Verhalten führen. Der folgende Befehl führt zu einem Fehler während der Kompilierung.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Wenn Sie nur den Name-Parameter verwenden, müssen Sie Folgendes beachten:

- Abhängig von der Anzahl der auf dem Computer installierten Module ist es ein ressourcenintensiver Vorgang.
- Es wird die zuerst gefundene Ressource des angegebenen Namens geladen. Falls mehrere Ressourcen mit demselben Namen installiert sind, könnte die falsche Ressource geladen werden.

Wie unten beschrieben sollte `–ModuleName` mit dem `-Name`-Parameter angegeben werden.

Dies bietet folgende Vorteile:

- Durch Begrenzen des Suchbereichs für die angegebene Ressource sind die Auswirkungen auf die Leistung geringer.
- Durch Definieren der Ressource wird das Modul explizit definiert und sichergestellt, dass die richtige Ressource geladen wird.

> [!NOTE]
> In PowerShell 5.0 können DSC-Ressourcen mehrere Versionen haben, und verschiedene Versionen können parallel auf einem Computer installiert sein. Dies wird dadurch implementiert, dass mehrere Versionen eines Ressourcenmoduls vorhanden sind, die sich im selben Modulordner befinden.
> Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense mit Import-DSCResource

Beim Erstellen der DSC-Konfiguration in ISE stellt PowerShell IntelliSense für Ressourcen und Ressourceneigenschaften zur Verfügung. Ressourcendefinitionen unter dem `$pshome`-Modulpfad werden automatisch geladen. Beim Importieren von Ressourcen mithilfe des `Import-DSCResource`-Schlüsselworts werden die angegebenen Ressourcendefinitionen hinzugefügt, und IntelliSense wird erweitert, um das Schema der importierten Ressource einzubeziehen.

![IntelliSense für Ressourcen](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> In PowerShell 5.0 wurde der ISE für DSC-Ressourcen und deren Eigenschaften die Vervollständigung mit der TAB-TASTE hinzugefügt. Weitere Informationen finden Sie unter [Ressourcen](../resources/resources.md).

Beim Kompilieren der Konfiguration verwendet PowerShell die importierten Ressourcendefinitionen, um alle Ressourcenblöcke in der Konfiguration zu überprüfen.
Jeder Ressourcenblock wird mit der Schemadefinition der Ressource auf Einhaltung der folgenden Regeln überprüft.

- Nur im Schema definierte Eigenschaften werden verwendet.
- Die Datentypen für jede Eigenschaft sind korrekt.
- Schlüsseleigenschaften werden angegeben.
- Es wird keine schreibgeschützte Eigenschaft verwendet.
- Überprüfung von Wertzuordnungstypen.

Beachten Sie die folgende Konfiguration:

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
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

Die Kompilierung dieser Konfiguration führt zu einem Fehler.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

Mit IntelliSense und Schemaüberprüfung können Sie mehr Fehler während Analyse und Kompilierung abfangen und damit Komplikationen während der Runtime vermieden.

> [!NOTE]
> Jede DSC-Ressource kann einen Namen haben und einen durch das Schema der Ressource definierten **FriendlyName** (Anzeigenamen). Im Folgenden sehen Sie ersten beiden Zeilen von „MSFT_ServiceResource.shema.mof“.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Wenn Sie diese Ressource in einer Konfiguration verwenden, können Sie **MSFT_ServiceResource** oder **Service** angeben.

## <a name="powershell-v4-and-v5-differences"></a>Unterschiede zwischen PowerShell v4 und v5

Wenn Sie Konfigurationen in PowerShell 4.0 und PowerShell 5.0 und höher erstellen, werden Ihnen mehrere Unterschiede auffallen. In diesem Abschnitt werden die Unterschiede hervorgehoben, die für diesen Artikel relevant sind.

### <a name="multiple-resource-versions"></a>Mehrere Versionen der Ressource

Das parallele Installieren und Verwenden mehrerer Versionen von Ressourcen wurde in PowerShell 4.0 nicht unterstützt. Wenn beim Importieren von Ressourcen in Ihre Konfiguration Probleme auftreten, stellen Sie sicher, dass Sie nur eine Version der Ressource installiert haben.

In der folgenden Abbildung sind zwei Versionen des **xPSDesiredStateConfiguration**-Moduls installiert.

![Problembehebung bei mehreren Versionen einer Ressource](media/import-dscresource/multiple-resource-versions-broken.png)

Kopieren Sie den Inhalt Ihrer gewünschten Modulversion in die oberste Ebene des Modulverzeichnisses.

![Problembehebung bei mehreren Versionen einer Ressource](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>Ressourcenspeicherort

Beim Erstellen und Kompilieren von Konfigurationen können Ihre Ressourcen in einem beliebigen, durch Ihren [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path) angegebenen Verzeichnis gespeichert werden. In PowerShell 4.0 erfordert der LCM, dass alle DSC-Ressourcenmodule unter „Programme\WindowsPowerShell\Modules“ oder `$pshome\Modules` gespeichert werden. Seit PowerShell 5.0 besteht diese Anforderung nicht mehr, und Ressourcenmodule können in einem beliebigen durch `PSModulePath` angegebenen Verzeichnis gespeichert werden.

### <a name="moduleversion-added"></a>ModuleVersion hinzugefügt

Ab PowerShell 5.0 können Sie mit dem `-ModuleVersion`-Parameter angeben, welche Version eines Moduls in der Konfiguration verwendet werden soll.

## <a name="see-also"></a>Weitere Informationen

- [Ressourcen](../resources/resources.md)
