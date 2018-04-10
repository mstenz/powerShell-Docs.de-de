---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Register-PSRepository
ms.openlocfilehash: 7a7d1bf56a87161f6ec735399b15b19f317282b6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="register-psrepository"></a><span data-ttu-id="c1d32-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c1d32-103">Register-PSRepository</span></span>

<span data-ttu-id="c1d32-104">Ruft die registrierten Repositorys auf einem Computer ab</span><span class="sxs-lookup"><span data-stu-id="c1d32-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="c1d32-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1d32-105">Description</span></span>

<span data-ttu-id="c1d32-106">Das Cmdlet „Register-PSRepository“ registriert das Online-Repository für PowerShell-Module.</span><span class="sxs-lookup"><span data-stu-id="c1d32-106">The Register-PSRepository cmdlet registers the online repository for PowerShell modules.</span></span> <span data-ttu-id="c1d32-107">Nachdem ein Repository registriert wurde, können Sie von den Cmdlets „Find-Module“, „Install-Module“ und „Publish-Module“ aus darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="c1d32-107">After a repository is registered, you can reference it from the Find-Module, Install-Module, and Publish-Module cmdlets.</span></span> <span data-ttu-id="c1d32-108">Das registrierte Repository wird zum Standard-Repository in „Find-Module“ und „Install-Module“.</span><span class="sxs-lookup"><span data-stu-id="c1d32-108">The registered repository becomes the default repository in Find-Module and Install-Module.</span></span>

<span data-ttu-id="c1d32-109">Registrierte Repositorys sind benutzerspezifisch.</span><span class="sxs-lookup"><span data-stu-id="c1d32-109">Registered repositories are user-specific.</span></span> <span data-ttu-id="c1d32-110">Sie sind nicht in einem systemweiten Kontext registriert.</span><span class="sxs-lookup"><span data-stu-id="c1d32-110">They are not registered in a system-wide context.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="c1d32-111">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="c1d32-111">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Register-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="c1d32-112">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="c1d32-112">Cmdlet online help reference</span></span>

[<span data-ttu-id="c1d32-113">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c1d32-113">Register-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517129)

## <a name="example-commands"></a><span data-ttu-id="c1d32-114">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="c1d32-114">Example commands</span></span>

### <a name="register-a-powershell-repository"></a><span data-ttu-id="c1d32-115">Registrieren eines PowerShell-Repositorys</span><span class="sxs-lookup"><span data-stu-id="c1d32-115">Register a PowerShell Repository</span></span>
<span data-ttu-id="c1d32-116">Sie können PowerShellGet für interne Repositorys konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c1d32-116">You can configure PowerShellGet to work against internal repositories.</span></span>
<span data-ttu-id="c1d32-117">Nachdem ein Repository registriert wurde, können Sie „Find-Module“ und „Install-Module“ dafür verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1d32-117">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
# Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" –InstallationPolicy Trusted

# Get all of the registered repositories
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/
DemoRepo                  Trusted              https://www.myget.org/F/powershellgetdemo/api/v2


# Search only the new repository for modules
Find-Module -Repository DemoRepo

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.12.0.0   xActiveDirectory                    DemoRepo             The xActiveDirectory module is originally part of the Windows PowerShell Desired State Configuration (DSC) Resource Kit. This version has been modified for use in Azure. This module contains the xADD...
1.1.1      SomeModule                          DemoRepo             Module description.

# By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

# Removing a repository
Unregister-PSRepository DemoRepo
```


### <a name="register-psrepository-and-set-psrepository-cmdlets-with-script-sharing-support"></a><span data-ttu-id="c1d32-118">Cmdlets „Register-PSRepository“ und „Set-PSRepository“ mit Unterstützung der Skriptfreigabe</span><span class="sxs-lookup"><span data-stu-id="c1d32-118">Register-PSRepository and Set-PSRepository cmdlets with script sharing support</span></span>

<span data-ttu-id="c1d32-119">Verwenden Sie das Cmdlet „Register-PSRepository“ zum Hinzufügen von **ScriptSourceLocation** und **ScriptPublishLocation** zu „PSRepository“.</span><span class="sxs-lookup"><span data-stu-id="c1d32-119">Use Register-PSRepository cmdlet to add the **ScriptSourceLocation** and **ScriptPublishLocation** to the PSRepository.</span></span>

```powershell

# Register an GalleryINT repository with Scripts and Modules support

Register-PSRepository -Name GalleryINT `
                      -SourceLocation https://customgallery.cloudapp.net `
                      -InstallationPolicy Trusted `
                      -Verbose

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or 'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running
'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes [N] No [S] Suspend [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: The specified assembly 'C:\Program Files\PackageManagement\ProviderAssemblies\nuget-anycpu.exe' is installed at top level directory. However it is recommended that the assemblies
should be installed under its ProviderName\Version folder.
VERBOSE: Installing the package 'https://oneget.org/nuget-2.8.5.201.package.swidtag'.
VERBOSE: Installed the package 'nuget' to 'C:\Program Files\PackageManagement\ProviderAssemblies\nuget\2.8.5.201\Microsoft.PackageManagement.NuGetProvider.dll'.
VERBOSE: The provider 'NuGet' has already been imported. Trying to import it again.
VERBOSE: Importing package provider 'NuGet'.
VERBOSE: Performing the operation "Register Module Repository" on target "Module Repository 'GalleryINT' (https://customgallery.cloudapp.net/) in provider 'PowerShellGet'".
VERBOSE: User did not specify the PackageManagement provider name, trying with the provider name 'NuGet'.
VERBOSE: Successfully registered the repository 'GalleryINT' with source location 'https://customgallery.cloudapp.net/api/v2/'.
VERBOSE: Repository details, Name = 'GalleryINT', Location = 'https://customgallery.cloudapp.net/api/v2/'; IsTrusted = 'True'; IsRegistered = 'True'.

# Get the registered repository details
Get-PSRepository -Name GalleryINT

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
GalleryINT                 Trusted              https://customgallery.cloudapp.net/api/v2/


Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://customgallery.cloudapp.net/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://customgallery.cloudapp.net/api/v2/package/
ScriptSourceLocation : https://customgallery.cloudapp.net/api/v2/items/psscript/
ScriptPublishLocation : https://customgallery.cloudapp.net/api/v2/package/
ProviderOptions : {}

```