---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Find-Command
ms.openlocfilehash: f867f12b1c6efad30a04581c6f36c5a77a2fb2ae
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="find-command"></a><span data-ttu-id="74528-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="74528-103">Find-Command</span></span>

<span data-ttu-id="74528-104">Sucht PowerShell-Befehle in Modulen.</span><span class="sxs-lookup"><span data-stu-id="74528-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="74528-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74528-105">Description</span></span>
<span data-ttu-id="74528-106">Das Cmdlet Find-Command sucht PowerShell-Befehle wie z.B. Cmdlets, Aliase, Funktionen und Workflows.</span><span class="sxs-lookup"><span data-stu-id="74528-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="74528-107">Find-Command sucht Module in registrierten Repositorys.</span><span class="sxs-lookup"><span data-stu-id="74528-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="74528-108">Für jeden Befehl, den dieses Cmdlet findet, gibt es ein PSGetCommandInfo-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="74528-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="74528-109">Sie können ein PSGetCommandInfo-Objekt an das Install-Module-Cmdlet übergeben, um das Modul zu installieren, das den Befehl enthält.</span><span class="sxs-lookup"><span data-stu-id="74528-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="74528-110">Find-Command kann mit Versionsparametern filtern: MinimumVersion, RequiredVersion, AllVersions.</span><span class="sxs-lookup"><span data-stu-id="74528-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="74528-111">Die Parameter schließen sich gegenseitig aus.</span><span class="sxs-lookup"><span data-stu-id="74528-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="74528-112">Diese Versionsparameter sind nur mit dem einzigen Modulnamen ohne Platzhalter erlaubt.</span><span class="sxs-lookup"><span data-stu-id="74528-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="74528-113">Wenn der RequiredVersion-Parameter nicht angegeben wird, gibt Find-Command die neueste Version des Moduls zurück, das gleich oder größer als die angegebene minimale Version oder die neueste Version des Moduls ist, wenn keine Mindestversion angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="74528-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="74528-114">Wenn der RequiredVersion-Parameter angegeben ist, gibt Find-Command nur die Version des Moduls zurück, die genau mit der angegebenen Version übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="74528-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="74528-115">Find-Command kann Modulmetadaten anhand des „-Tag“-Parameters filtern.</span><span class="sxs-lookup"><span data-stu-id="74528-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="74528-116">Find-Command kann mit dem „-Filter“-Parameter nach einer repositoryspezifischen Suchsprache filtern.</span><span class="sxs-lookup"><span data-stu-id="74528-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="74528-117">Find-Command kann Module von allen oder einigen registrierten Repositorys filtern.</span><span class="sxs-lookup"><span data-stu-id="74528-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="74528-118">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="74528-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="74528-119">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="74528-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="74528-120">Find-Command</span><span class="sxs-lookup"><span data-stu-id="74528-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="74528-121">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="74528-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

