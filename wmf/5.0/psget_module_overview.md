---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 82b8046d5cbb47300f090ce2ffbf3c279ed19458
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="46779-102">Ermittlung, Installation und Inventur von PowerShell-Modulen mit PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="46779-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="46779-103">PowerShellGet ist in dieser Version von WMF enthalten:</span><span class="sxs-lookup"><span data-stu-id="46779-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="46779-104">„Find-Module“ kann Modulmetadaten anhand des „-Tag“-Parameters filtern.</span><span class="sxs-lookup"><span data-stu-id="46779-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="46779-105">„Find-Module“ kann mit dem „-Filter“-Parameter nach einer repositoryspezifischen Suchsprache filtern.</span><span class="sxs-lookup"><span data-stu-id="46779-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="46779-106">„Find-Module“ kann mit den Parametern „-Command“, „-DscResource“ und „-Includes“ den Modulinhalt filtern.</span><span class="sxs-lookup"><span data-stu-id="46779-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="46779-107">„Find-DscResource“ ermöglicht die Ermittlung einzelner DSC-Ressourcen in Repositorys.</span><span class="sxs-lookup"><span data-stu-id="46779-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="46779-108">Unterstützung für die Installation über und Veröffentlichung in Dateifreigaben mit NuGet</span><span class="sxs-lookup"><span data-stu-id="46779-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="46779-109">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="46779-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="46779-110">Neue Features in Windows PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="46779-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="46779-111">Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für Windows PowerShell 5.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="46779-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="46779-112">Unterstützung der Installation von Modulabhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="46779-112">Module dependency installation support</span></span>
-   <span data-ttu-id="46779-113">Drei neue Cmdlets</span><span class="sxs-lookup"><span data-stu-id="46779-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="46779-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="46779-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="46779-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="46779-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="46779-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="46779-116">Save-Module</span></span>