---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Install-Module
ms.openlocfilehash: 37e07cd32e7b2fd4a7a8e6cab179aecc3251baf3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="install-module"></a>Install-Module

Installiert die PowerShell-Module aus Onlinerepositorys auf den lokalen Computer.

## <a name="description"></a>Beschreibung

Das Cmdlet Install-Module lädt ein Modul oder mehrere Module aus einem Onlinekatalog herunter, überprüft diese und installiert sie auf dem lokalen Computer im angegebenen Installationsbereich.

Das Cmdlet Install-Module ruft ein Modul oder mehrere Module ab, das bzw. die mit angegebenen Kriterien aus einem Onlinekatalog übereinstimmen, überprüft, ob die Suchergebnisse gültige Module sind und kopiert die Modulordner in den Installationsbereich.

Wenn kein Bereich definiert ist oder wenn der Wert des Scope-Parameters AllUsers ist, wird das Modul unter %systemdrive%:\Program Files\WindowsPowerShell\Modules installiert. Wenn der Wert des Scope-Parameters CurrentUser ist, wird das Modul in $home\Documents\WindowsPowerShell\Modules installiert.

Sie können Ihre Ergebnisse nach den mindestens erforderlichen Versionen oder den exakten Versionen der angegebenen Module filtern.

- Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für Windows PowerShell 5.0 oder höher
- Unterstützung der Installation von Modulabhängigkeiten
- **Nicht vertrauenswürdige Aufforderung:** Für die Installation der Module aus einem nicht vertrauenswürdigen Repository ist Benutzerakzeptanz erforderlich.
- „-Force“ installiert das bereits installierte Modul neu.
- RequiredVersion installiert die angegebene Version in SxS zusammen mit vorhandenen Versionen auf PowerShell-Version 5.0 oder höher.

### <a name="scope"></a>Bereich
Gibt den Bereich der Installation des Moduls an. Die folgenden Werte für diesen Parameter sind zulässig: AllUsers und CurrentUser.

Der Standardbereich für die Installation ist AllUsers.

Mit der Einstellung „AllUsers“ können Module an einem Speicherort installiert werden, der Zugriff für alle Benutzer des Computers bietet. Dieser ist: „$env:SystemDrive\Program Files\WindowsPowerShell\Modules“.

Mit dem CurrentUser-Bereich können Module nur unter $home\Documents\WindowsPowerShell\Modules installiert werden. Das Modul ist also nur für den aktuellen Benutzer verfügbar.

## <a name="notes"></a>Hinweise

Dieses Cmdlet wird unter Windows PowerShell 3.0 oder auf höheren Versionen von Windows PowerShell ausgeführt. Ebenso wird es unter Windows 7 oder Windows 2008 R2 und höheren Versionen von Windows ausgeführt.

Wenn ein installiertes Modul nicht importiert werden kann (wenn es also nicht über .psm1, .psd1 oder .dll mit dem gleichen Namen im Ordner verfügt), schlägt die Installation fehl, es sei denn, Sie fügen Ihrem Befehl den -Force-Parameter hinzu.

Wenn eine Version des Moduls auf dem Computer mit dem angegebenen Wert für den Name-Parameter übereinstimmt, und Sie die Parameter MinimumVersion oder RequiredVersion nicht hinzugefügt haben, wird das Cmdlet Install-Module im Hintergrund fortgesetzt, ohne das Modul zu installieren. Wenn die Parameter MinimumVersion oder RequiredVersion angegeben sind, und das vorhandene Modul nicht mit den Werten in diesen Parameter übereinstimmen, tritt ein Fehler auf. Genauer gesagt: Wenn die Version des aktuell installierten Moduls entweder älter als der Wert des MinimumVersion-Parameters ist oder nicht dem Wert des RequiredVersion-Parameters entspricht, tritt ein Fehler auf. Wenn die Version des installierten Moduls höher als der Wert des MinimumVersion-Parameters ist oder gleich dem Wert des RequiredVersion-Parameters ist, wird das Cmdlet Install-Mode im Hintergrund fortgesetzt, ohne das Modul zu installieren.

Install-Module gibt einen Fehler zurück, wenn kein Modul im Onlinekatalog vorhanden ist, das mit dem angegebenen Namen übereinstimmt.

Um mehrere Module zu installieren, geben Sie ein Array von Modulnamen an, die durch Kommas getrennt ist. Sie können die Parameter MinimumVersion oder RequiredVersion nicht hinzufügen, wenn Sie mehrere Modulnamen angeben.

Standardmäßig werden die Module im Ordner „Programme“ installiert, um Verwechslungen bei der Installation von Ressourcen von Windows PowerShell Desired State Configuration (DSC) zu vermeiden. Sie können mehrere durch Pipezeichen getrennte „PSGetItemInfo“-Objekte an „Install-Module“ übergeben. Dies ist eine weitere Möglichkeit, mehrere Module anzugeben, die mit einem einzigen Befehl installiert werden sollen.

Damit ausgeführte Module, die schädlichen Code enthalten, vermieden werden, werden installierte Module nicht automatisch während der Installation importiert. Eine bewährte Sicherheitsmethode ist die Bewertung von Modulcode vor der ersten Ausführung von Cmdlets oder Funktionen in einem Modul.


## <a name="cmdlet-syntax"></a>Cmdlet-Syntax
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-Onlinehilfe

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a>Beispiele für Befehle

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name 
```

## <a name="install-module-cmdlet-in-pipeline-operations"></a>Install-Module-Cmdlet in Pipeline-Vorgängen

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a>Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für PowerShell 5.0 oder höher

Für die in Windows PowerShell 5.0 oder höher ausgeführten Cmdlets „Install-Module“ „Update-Module“ und „Publish-Module“ unterstützt PowerShellGet die gleichzeitige Ausführung unterschiedlicher Modulversionen.

### <a name="install-module-examples"></a>Beispiele für „Install-Module“

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a>Installieren eines Moduls mit dessen Abhängigkeiten

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a>Fehlerszenarios

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```

