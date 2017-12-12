---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Install-Module
ms.openlocfilehash: c066f4b34a03206cc0f31e9d40144fd719d9e305
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2017
---
# <a name="install-module"></a><span data-ttu-id="8196e-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="8196e-103">Install-Module</span></span>

<span data-ttu-id="8196e-104">Installiert die PowerShell-Module aus Onlinerepositorys auf den lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="8196e-104">Installs the PowerShell modules from online repositories to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="8196e-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8196e-105">Description</span></span>

<span data-ttu-id="8196e-106">Das Cmdlet Install-Module lädt ein Modul oder mehrere Module aus einem Onlinekatalog herunter, überprüft diese und installiert sie auf dem lokalen Computer im angegebenen Installationsbereich.</span><span class="sxs-lookup"><span data-stu-id="8196e-106">Install-Module cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="8196e-107">Das Cmdlet Install-Module ruft ein Modul oder mehrere Module ab, das bzw. die mit angegebenen Kriterien aus einem Onlinekatalog übereinstimmen, überprüft, ob die Suchergebnisse gültige Module sind und kopiert die Modulordner in den Installationsbereich.</span><span class="sxs-lookup"><span data-stu-id="8196e-107">The Install-Module cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="8196e-108">Wenn kein Bereich definiert ist oder wenn der Wert des Scope-Parameters AllUsers ist, wird das Modul unter %systemdrive%:\Program Files\WindowsPowerShell\Modules installiert.</span><span class="sxs-lookup"><span data-stu-id="8196e-108">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="8196e-109">Wenn der Wert des Scope-Parameters CurrentUser ist, wird das Modul in $home\Documents\WindowsPowerShell\Modules installiert.</span><span class="sxs-lookup"><span data-stu-id="8196e-109">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="8196e-110">Sie können Ihre Ergebnisse nach den mindestens erforderlichen Versionen oder den exakten Versionen der angegebenen Module filtern.</span><span class="sxs-lookup"><span data-stu-id="8196e-110">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="8196e-111">Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für Windows PowerShell 5.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="8196e-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
- <span data-ttu-id="8196e-112">Unterstützung der Installation von Modulabhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="8196e-112">Module dependency installation support</span></span>
- <span data-ttu-id="8196e-113">**Nicht vertrauenswürdige Aufforderung:** Für die Installation der Module aus einem nicht vertrauenswürdigen Repository ist Benutzerakzeptanz erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8196e-113">**Untrusted prompt:**User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="8196e-114">„-Force“ installiert das bereits installierte Modul neu.</span><span class="sxs-lookup"><span data-stu-id="8196e-114">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="8196e-115">RequiredVersion installiert die angegebene Version in SxS zusammen mit vorhandenen Versionen auf PowerShell-Version 5.0 oder höher.</span><span class="sxs-lookup"><span data-stu-id="8196e-115">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

### <a name="scope"></a><span data-ttu-id="8196e-116">Bereich</span><span class="sxs-lookup"><span data-stu-id="8196e-116">Scope</span></span>
<span data-ttu-id="8196e-117">Gibt den Bereich der Installation des Moduls an.</span><span class="sxs-lookup"><span data-stu-id="8196e-117">Specifies the installation scope of the module.</span></span> <span data-ttu-id="8196e-118">Die folgenden Werte für diesen Parameter sind zulässig: AllUsers und CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="8196e-118">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="8196e-119">Der Standardbereich für die Installation ist AllUsers.</span><span class="sxs-lookup"><span data-stu-id="8196e-119">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="8196e-120">Mit der Einstellung „AllUsers“ können Module an einem Speicherort installiert werden, der Zugriff für alle Benutzer des Computers bietet. Dieser ist: „$env:SystemDrive\Program Files\WindowsPowerShell\Modules“.</span><span class="sxs-lookup"><span data-stu-id="8196e-120">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="8196e-121">Mit dem CurrentUser-Bereich können Module nur unter $home\Documents\WindowsPowerShell\Modules installiert werden. Das Modul ist also nur für den aktuellen Benutzer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8196e-121">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>

## <a name="notes"></a><span data-ttu-id="8196e-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8196e-122">Notes</span></span>

<span data-ttu-id="8196e-123">Dieses Cmdlet wird unter Windows PowerShell 3.0 oder auf höheren Versionen von Windows PowerShell ausgeführt. Ebenso wird es unter Windows 7 oder Windows 2008 R2 und höheren Versionen von Windows ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8196e-123">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="8196e-124">Wenn ein installiertes Modul nicht importiert werden kann (wenn es also nicht über .psm1, .psd1 oder .dll mit dem gleichen Namen im Ordner verfügt), schlägt die Installation fehl, es sei denn, Sie fügen Ihrem Befehl den -Force-Parameter hinzu.</span><span class="sxs-lookup"><span data-stu-id="8196e-124">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="8196e-125">Wenn eine Version des Moduls auf dem Computer mit dem angegebenen Wert für den Name-Parameter übereinstimmt, und Sie die Parameter MinimumVersion oder RequiredVersion nicht hinzugefügt haben, wird das Cmdlet Install-Module im Hintergrund fortgesetzt, ohne das Modul zu installieren.</span><span class="sxs-lookup"><span data-stu-id="8196e-125">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span> <span data-ttu-id="8196e-126">Wenn die Parameter MinimumVersion oder RequiredVersion angegeben sind, und das vorhandene Modul nicht mit den Werten in diesen Parameter übereinstimmen, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="8196e-126">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="8196e-127">Genauer gesagt: Wenn die Version des aktuell installierten Moduls entweder älter als der Wert des MinimumVersion-Parameters ist oder nicht dem Wert des RequiredVersion-Parameters entspricht, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="8196e-127">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="8196e-128">Wenn die Version des installierten Moduls höher als der Wert des MinimumVersion-Parameters ist oder gleich dem Wert des RequiredVersion-Parameters ist, wird das Cmdlet Install-Mode im Hintergrund fortgesetzt, ohne das Modul zu installieren.</span><span class="sxs-lookup"><span data-stu-id="8196e-128">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span>

<span data-ttu-id="8196e-129">Install-Module gibt einen Fehler zurück, wenn kein Modul im Onlinekatalog vorhanden ist, das mit dem angegebenen Namen übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="8196e-129">Install-Module returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="8196e-130">Um mehrere Module zu installieren, geben Sie ein Array von Modulnamen an, die durch Kommas getrennt ist.</span><span class="sxs-lookup"><span data-stu-id="8196e-130">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="8196e-131">Sie können die Parameter MinimumVersion oder RequiredVersion nicht hinzufügen, wenn Sie mehrere Modulnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="8196e-131">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="8196e-132">Standardmäßig werden die Module im Ordner „Programme“ installiert, um Verwechslungen bei der Installation von Ressourcen von Windows PowerShell Desired State Configuration (DSC) zu vermeiden. Sie können mehrere durch Pipezeichen getrennte „PSGetItemInfo“-Objekte an „Install-Module“ übergeben. Dies ist eine weitere Möglichkeit, mehrere Module anzugeben, die mit einem einzigen Befehl installiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="8196e-132">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Module; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="8196e-133">Damit ausgeführte Module, die schädlichen Code enthalten, vermieden werden, werden installierte Module nicht automatisch während der Installation importiert.</span><span class="sxs-lookup"><span data-stu-id="8196e-133">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="8196e-134">Eine bewährte Sicherheitsmethode ist die Bewertung von Modulcode vor der ersten Ausführung von Cmdlets oder Funktionen in einem Modul.</span><span class="sxs-lookup"><span data-stu-id="8196e-134">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="8196e-135">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="8196e-135">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="8196e-136">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="8196e-136">Cmdlet online help reference</span></span>

[<span data-ttu-id="8196e-137">Install-Module</span><span class="sxs-lookup"><span data-stu-id="8196e-137">Install-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a><span data-ttu-id="8196e-138">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="8196e-138">Example commands</span></span>

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a module by name, including prelrelease versions if one exists
Install-Module -Name ContosoServer -AllowPrerelease

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

## <a name="install-module-cmdlet-in-pipeline-operations"></a><span data-ttu-id="8196e-139">Install-Module-Cmdlet in Pipeline-Vorgängen</span><span class="sxs-lookup"><span data-stu-id="8196e-139">Install-Module cmdlet in pipeline operations</span></span>

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

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="8196e-140">Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für PowerShell 5.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="8196e-140">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="8196e-141">Für die in Windows PowerShell 5.0 oder höher ausgeführten Cmdlets „Install-Module“ „Update-Module“ und „Publish-Module“ unterstützt PowerShellGet die gleichzeitige Ausführung unterschiedlicher Modulversionen.</span><span class="sxs-lookup"><span data-stu-id="8196e-141">PowerShellGet supports the side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-module-examples"></a><span data-ttu-id="8196e-142">Beispiele für „Install-Module“</span><span class="sxs-lookup"><span data-stu-id="8196e-142">Install-Module examples</span></span>

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

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="8196e-143">Installieren eines Moduls mit dessen Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="8196e-143">Install module with its dependencies</span></span>

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

## <a name="error-scenarios"></a><span data-ttu-id="8196e-144">Fehlerszenarios</span><span class="sxs-lookup"><span data-stu-id="8196e-144">Error scenarios</span></span>

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

