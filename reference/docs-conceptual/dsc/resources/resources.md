---
ms.date: 02/28/2020
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressourcen
ms.openlocfilehash: 863898d910cc3c75c3e5977a5b6b0657ba7ed512
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278244"
---
# <a name="dsc-resources"></a>DSC-Ressourcen

> Gilt für Windows PowerShell 4.0 und höher.

## <a name="overview"></a>Übersicht

DSC-Ressourcen sind die Bausteine einer DSC-Konfiguration. Eine Ressource macht Eigenschaften verfügbar, die konfiguriert werden können (Schema), und enthält die PowerShell-Skriptfunktionen, die der lokale Konfigurations-Manager wie gewünscht ausführt.

Mit einer Ressource kann etwas Allgemeines wie eine Datei oder Spezifisches wie eine IIS-Servereinstellung modelliert werden. Gruppen ähnlicher Ressourcen werden in einem DSC-Modul kombiniert, das alle erforderlichen Dateien in einer Struktur organisiert, die portierbar ist und Metadaten zum Bestimmen des Zwecks der Ressourcen enthält.

Jede Ressource verfügt über ein *schema, das die Syntax bestimmt, die für die Verwendung der Ressource in einer [Konfiguration](../configurations/configurations.md) erforderlich ist.
Das Schema einer Ressource kann auf folgende Weise definiert werden:

- Datei **„Schema.Mof“** : Die meisten Ressourcen definieren ihr _Schema_ in einer Datei „schema.mof“ mithilfe des [Managed Object Format (MOF)](/windows/desktop/wmisdk/managed-object-format--mof-).
- **Datei „\<Ressourcenname\>.schema.psm1“** : [Zusammengesetzte Ressourcen](../configurations/compositeConfigs.md) definieren ihr *Schema* in einer Datei „<ResourceName>.schema.psm1“ unter Verwendung eines [Parameterblocks](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **Datei „\<Ressourcenname\>.psm1“** : Klassenbasierte DSC-Ressourcen definieren ihr _Schema_ in der Klassendefinition. Syntaxelemente werden als Eigenschaften der Klasse angegeben. Weitere Informationen finden Sie unter [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Um die Syntax für eine DSC-Ressource abzurufen, verwenden Sie das Cmdlet [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) mit dem Parameter `-Syntax`. Diese Syntax ist ähnlich wie die Verwendung von [Get-Command](/powershell/module/microsoft.powershell.core/get-command) mit dem Parameter `-Syntax`, um die Cmdlet-Syntax abzurufen. Die Ausgabe, die Sie sehen, zeigt die Vorlage für einen Ressourcenblock für die Ressource an, die Sie angeben.

```powershell
Get-DscResource -Syntax Service
```

Die Ausgabe, die Sie sehen, sollte der folgenden Ausgabe ähneln, obwohl sich die Syntax dieser Ressource in Zukunft ändern kann. Wie bei der Cmdlet-Syntax sind die _Schlüssel_ in eckigen Klammern optional. Die Typen geben den Typ der Daten an, die jeder Schlüssel erwartet.

> [!NOTE]
> Der Schlüssel **Ensure** ist optional, da er standardmäßig auf „Present“ (Vorhanden) festgelegt ist.

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

Innerhalb einer Konfiguration könnte ein **Service**-Ressourcenblock wie folgt aussehen, um sicherzustellen (**Ensure**), dass der Spoolerdienst ausgeführt wird.

> [!NOTE]
> Bevor Sie eine Ressource in einer Konfiguration verwenden, müssen Sie sie mit [Import-DSCResource](../configurations/import-dscresource.md) importieren.

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

Konfigurationen können mehrere Instanzen desselben Ressourcentyps enthalten. Jede Instanz muss eindeutig benannt sein. Im folgenden Beispiel wird ein zweiter **Service**-Ressourcenblock zum Konfigurieren des „DHCP“-Diensts hinzugefügt.

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
> Ab PowerShell 5.0 wurde IntelliSense für DSC hinzugefügt. Dieses neue Feature ermöglicht Ihnen, <kbd>TAB-TASTE</kbd> und <kbd>STRG</kbd>+<kbd>LEERTASTE</kbd> zum automatischen Vervollständigen von Schlüsselnamen zu verwenden.

![Vervollständigung der Ressource mit der TAB-TASTE](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a>Ressourcentypen

Windows bietet integrierte Ressourcen, Linux betriebssystemspezifische Ressourcen. Es gibt Ressourcen für [ knotenübergreifende Abhängigkeiten](../configurations/crossNodeDependencies.md), Ressourcen für die Paketverwaltung sowie [von der Community bereitgestellte und gepflegte Ressourcen](https://github.com/dsccommunity). Mit den oben genannten Schritten können Sie die Syntax dieser Ressourcen und deren Verwendung festlegen. Die Seiten, die diese Ressourcen verarbeiten, wurden unter **Reference** archiviert.

### <a name="windows-built-in-resources"></a>Integrierte Windows-Ressourcen

- [Archive-Ressource](../reference/resources/windows/archiveResource.md)
- [Environment-Ressource](../reference/resources/windows/environmentResource.md)
- [File-Ressource](../reference/resources/windows/fileResource.md)
- [Group-Ressource](../reference/resources/windows/groupResource.md)
- [GroupSet-Ressource](../reference/resources/windows/groupSetResource.md)
- [Log-Ressource](../reference/resources/windows/logResource.md)
- [Package-Ressource](../reference/resources/windows/packageResource.md)
- [ProcessSet-Ressource](../reference/resources/windows/ProcessSetResource.md)
- [Registry-Ressource](../reference/resources/windows/registryResource.md)
- [Script-Ressource](../reference/resources/windows/scriptResource.md)
- [Service-Ressource](../reference/resources/windows/serviceResource.md)
- [ServiceSet-Ressource](../reference/resources/windows/serviceSetResource.md)
- [User-Ressource](../reference/resources/windows/userResource.md)
- [WindowsFeature-Ressource](../reference/resources/windows/windowsFeatureResource.md)
- [WindowsFeatureSet-Ressource](../reference/resources/windows/windowsFeatureSetResource.md)
- [WindowsOptionalFeature-Ressource](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [WindowsOptionalFeatureSet-Ressource](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [WindowsPackageCabResource-Ressource](../reference/resources/windows/windowsPackageCabResource.md)
- [WindowsProcess-Ressource](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a>Ressourcen mit knotenübergreifenden Abhängigkeiten

- [WaitForAll-Ressource](../reference/resources/windows/waitForAllResource.md)
- [WaitForSome-Ressource](../reference/resources/windows/waitForSomeResource.md)
- [WaitForAny-Ressource](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a>Paketverwaltungsressourcen

- [PackageManagement-Ressource](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [PackageManagementSource-Ressource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a>Linux-Ressourcen

- [Linux-Ressource „Archive“](../reference/resources/linux/lnxArchiveResource.md)
- [Linux-Resource „Environment“](../reference/resources/linux/lnxEnvironmentResource.md)
- [Linux-Ressource „FileLine“](../reference/resources/linux/lnxFileLineResource.md)
- [Linux-Ressource „File“](../reference/resources/linux/lnxFileResource.md)
- [Linux-Ressource „Group“](../reference/resources/linux/lnxGroupResource.md)
- [Linux-Ressource „Package“](../reference/resources/linux/lnxPackageResource.md)
- [Linux-Ressource „Script“](../reference/resources/linux/lnxScriptResource.md)
- [Linux-Ressource „Service“](../reference/resources/linux/lnxServiceResource.md)
- [Linux-Ressource „SshAuthorizedKeys“](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [Linux-Ressource „User“](../reference/resources/linux/lnxUserResource.md)
