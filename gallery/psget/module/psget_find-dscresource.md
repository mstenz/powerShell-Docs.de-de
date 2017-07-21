---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="find-dscresource"></a><span data-ttu-id="eb404-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="eb404-103">Find-DscResource</span></span>

<span data-ttu-id="eb404-104">Sucht DSC-Ressourcen in Modulen.</span><span class="sxs-lookup"><span data-stu-id="eb404-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="eb404-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eb404-105">Description</span></span>

<span data-ttu-id="eb404-106">Das Cmdlet „Find-DscResource“ sucht Ressourcen von [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview), die in Modulen enthalten sind, die mit bestimmten Kriterien von registrierten Repositorys übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="eb404-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="eb404-107">Find-DscResource gibt für jedes Modul, das von diesem Cmdlet gefunden wird, ein PSGetDscResourceInfo-Objekt zurück, das Sie an Install-Module übergeben können, um die Module zu installieren, die die von diesem Cmdlet zurückgegebenen Ressourcen enthalten.</span><span class="sxs-lookup"><span data-stu-id="eb404-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="eb404-108">DSC ist eine neue Verwaltungsplattform in Windows PowerShell, die es ermöglicht, Konfigurationsdaten für Softwaredienste bereitzustellen und zu verwalten und die Umgebung zu verwalten, in der diese Dienste ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="eb404-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="eb404-109">DSC-Ressourcen sind die Bausteine einer DSC-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="eb404-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="eb404-110">Eine Ressource macht Eigenschaften verfügbar, die konfiguriert werden können (Schema), und enthält die PowerShell-Skriptfunktionen, die der lokale Konfigurations-Manager wie gewünscht ausführt.</span><span class="sxs-lookup"><span data-stu-id="eb404-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="eb404-111">Mit einer Ressource kann etwas Allgemeines wie eine Datei oder Spezifisches wie eine IIS-Servereinstellung modelliert werden.</span><span class="sxs-lookup"><span data-stu-id="eb404-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="eb404-112">Gruppen ähnlicher Ressourcen werden in einem DSC-Modul kombiniert, das alle erforderlichen Dateien in einer Struktur organisiert, die portierbar ist und Metadaten zum Bestimmen des Zwecks der Ressourcen enthält.</span><span class="sxs-lookup"><span data-stu-id="eb404-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="eb404-113">Find-DscResource kann mit Versionsparametern filtern: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="eb404-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="eb404-114">Die Parameter schließen sich gegenseitig aus.</span><span class="sxs-lookup"><span data-stu-id="eb404-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="eb404-115">Diese Versionsparameter sind nur mit dem einzigen Modulnamen ohne Platzhalter erlaubt.</span><span class="sxs-lookup"><span data-stu-id="eb404-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="eb404-116">Wenn der RequiredVersion-Parameter nicht angegeben wird, gibt Find-DscResource die neueste Version des Moduls zurück, das gleich oder größer als die angegebene minimale Version oder die neueste Version des Moduls ist, wenn keine Mindestversion angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="eb404-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="eb404-117">Wenn der RequiredVersion-Parameter angegeben ist, gibt Find-DscResource nur die Version des Moduls zurück, die genau mit der angegebenen Version übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="eb404-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="eb404-118">Find-DscResource kann Modulmetadaten anhand des „-Tag“-Parameters filtern.</span><span class="sxs-lookup"><span data-stu-id="eb404-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="eb404-119">Find-DscResource kann mit dem „-Filter“-Parameter nach einer repositoryspezifischen Suchsprache filtern.</span><span class="sxs-lookup"><span data-stu-id="eb404-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="eb404-120">Find-DscResource kann Module von allen oder einigen registrierten Repositorys filtern.</span><span class="sxs-lookup"><span data-stu-id="eb404-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="eb404-121">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="eb404-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="eb404-122">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="eb404-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="eb404-123">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="eb404-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="eb404-124">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="eb404-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

