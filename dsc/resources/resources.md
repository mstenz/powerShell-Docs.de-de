---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC-Ressourcen
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046690"
---
# <a name="dsc-resources"></a>DSC-Ressourcen

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC-Ressourcen sind die Bausteine einer DSC-Konfiguration. Eine Ressource macht Eigenschaften verfügbar, die konfiguriert werden können (Schema), und enthält die PowerShell-Skriptfunktionen, die der lokale Konfigurations-Manager wie gewünscht ausführt.

Mit einer Ressource kann etwas Allgemeines wie eine Datei oder Spezifisches wie eine IIS-Servereinstellung modelliert werden.  Gruppen ähnlicher Ressourcen werden in einem DSC-Modul kombiniert, das alle erforderlichen Dateien in einer Struktur organisiert, die portierbar ist und Metadaten zum Bestimmen des Zwecks der Ressourcen enthält.

Jede Ressource verfügt über eine * Schema, das bestimmt, die Syntax erforderlich, um die Ressource im Verwenden einer [Konfiguration](../configurations/configurations.md). Schema für eine Ressource kann auf folgende Weise definiert werden:

- **"Schema.Mof"** Datei: Die meisten Ressourcen definieren ihre *Schema* in eine Datei "schema.mof"-Datei mithilfe [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **"\<Ressourcenname\>. psm1"** Datei: [Zusammengesetzte Ressourcen](../configurations/compositeConfigs.md) definieren ihre *Schema* in eine "<ResourceName>. psm1" Datei mithilfe einer [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **"\<Ressourcenname\>. psm1"** Datei: Klasse, die je DSC-Ressourcen definieren, deren *Schema* in der Klassendefinition. Syntaxelemente werden als Eigenschaften der Klasse angegeben. Weitere Informationen finden Sie unter ["about_classes"](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Um die Syntax für eine DSC-Ressource abzurufen, verwenden Sie die [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) Cmdlet mit dem `-Syntax` Parameter. Diese Verwendung ist vergleichbar mit der Verwendung [Get-Command](/powershell/module/microsoft.powershell.core/get-command) mit der `-Syntax` Parameter, um die Cmdlet-Syntax zu erhalten. Die Ausgabe, die Sie sehen, zeigt die Vorlage für einen Ressourcenblock für die Ressource, die Sie angeben.

```powershell
Get-DscResource -Syntax Service
```

Die Ausgabe angezeigten sollte ungefähr wie unten sein, obwohl die Syntax für diese Ressource in der Zukunft ändern kann. Cmdlet-Syntax, wie die *Schlüssel* in eckigen Klammern angezeigt, sind optional. Die Typen angeben, den Typ der Daten, die jedem Schlüssel erwartet wird.

> [!NOTE]
> Die **stellen Sie sicher** Schlüssel ist optional, da modusangabe wird standardmäßig auf "Present".

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

In einer Konfiguration einen **Service** Ressourcenblock sieht wie folgt zu **stellen Sie sicher** , die der Spooler-Dienst ausgeführt wird.

> [!NOTE]
> Bevor Sie eine Ressource in einer Konfiguration verwenden, müssen Sie importieren Sie es mithilfe [Import-DSCResource](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Konfigurationen können mehrere Instanzen desselben Typs der Ressource enthalten. Jede Instanz muss eindeutig benannt sein. Im folgenden Beispiel eine zweite **Service** Ressourcenblock wird zum Konfigurieren des Diensts "DHCP" hinzugefügt.

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> PowerShell 5.0 ab, war Intellisense für DSC hinzugefügt. Dieses neue Feature können Sie mit \<Registerkarte\> und \<STRG + LEERTASTE\> , automatische Vervollständigung von Schlüsselnamen.

![Resource-Befehlszeilenergänzung](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Integrierte Ressourcen

Zusätzlich zu den Communityressourcen sind integrierte Ressourcen für Windows, Ressourcen für Linux und Ressourcen für die knotenübergreifende Abhängigkeit. Sie können die oben genannten Schritte verwenden, um zu bestimmen, die Syntax dieser Ressourcen und deren Verwendung. Die Seiten, die diese Ressourcen dienen unter archiviert haben **Verweis**.

Integrierte Windows-Ressourcen

* [Archive-Ressource](../reference/resources/windows/archiveResource.md)
* [Environment-Ressource](../reference/resources/windows/environmentResource.md)
* [File-Ressource](../reference/resources/windows/fileResource.md)
* [Group-Ressource](../reference/resources/windows/groupResource.md)
* [GroupSet-Ressource](../reference/resources/windows/groupSetResource.md)
* [Log-Ressource](../reference/resources/windows/logResource.md)
* [Package-Ressource](../reference/resources/windows/packageResource.md)
* [ProcessSet-Ressource](../reference/resources/windows/ProcessSetResource.md)
* [Registry-Ressource](../reference/resources/windows/registryResource.md)
* [Script-Ressource](../reference/resources/windows/scriptResource.md)
* [Service-Ressource](../reference/resources/windows/serviceResource.md)
* [ServiceSet-Ressource](../reference/resources/windows/serviceSetResource.md)
* [User-Ressource](../reference/resources/windows/userResource.md)
* [WindowsFeature-Ressource](../reference/resources/windows/windowsFeatureResource.md)
* [WindowsFeatureSet-Ressource](../reference/resources/windows/windowsFeatureSetResource.md)
* [WindowsOptionalFeature-Ressource](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [WindowsOptionalFeatureSet-Ressource](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource-Ressource](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess-Ressource](../reference/resources/windows/windowsProcessResource.md)

[Knotenübergreifender Abhängigkeiten](../configurations/crossNodeDependencies.md) Ressourcen

* [WaitForAll-Ressource](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome-Ressource](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny-Ressource](../reference/resources/windows/waitForAnyResource.md)

Paket-Management-Ressourcen

* [Ressource "PackageManagement"](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [Ressource "packagemanagementsource"](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux-Ressourcen

* [Linux-Archive-Ressource](../reference/resources/linux/lnxArchiveResource.md)
* [Ressourcen für Linux-Umgebung](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux-FileLine-Ressource](../reference/resources/linux/lnxFileLineResource.md)
* [Ressource "File" Linux](../reference/resources/linux/lnxFileResource.md)
* [Ressource "Group" Linux](../reference/resources/linux/lnxGroupResource.md)
* [Ressource "Package" Linux](../reference/resources/linux/lnxPackageResource.md)
* [Ressource "Script" Linux](../reference/resources/linux/lnxScriptResource.md)
* [Linux-Service-Ressource](../reference/resources/linux/lnxServiceResource.md)
* [Linux-SshAuthorizedKeys-Ressource](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Linux-User-Ressource](../reference/resources/linux/lnxUserResource.md)
