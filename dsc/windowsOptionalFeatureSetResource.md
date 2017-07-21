---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „WindowsOptionalFeatureSet“"
ms.openlocfilehash: 3bf6a993d0ec9ce71c1e9222ddaa3bb429accb15
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="12a07-103">DSC-Ressource „WindowsOptionalFeatureSet“</span><span class="sxs-lookup"><span data-stu-id="12a07-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="12a07-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="12a07-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="12a07-105">Die Ressource **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass optionale Features auf einem Zielknoten aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="12a07-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="12a07-106">Diese Ressource ist eine [zusammengesetzte Ressource](authoringResourceComposite.md), die die Ressource [WindowsOptionalFeature](windowsOptionalFeatureResource.md) für jedes Feature aufruft, das in der `Name`-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="12a07-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="12a07-107">Verwenden Sie diese Ressource, wenn Sie verschiedene optionale Windows-Features mit demselben Status konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="12a07-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="12a07-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="12a07-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="12a07-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="12a07-109">Properties</span></span>

|  <span data-ttu-id="12a07-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="12a07-110">Property</span></span>  |  <span data-ttu-id="12a07-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="12a07-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="12a07-112">Name</span><span class="sxs-lookup"><span data-stu-id="12a07-112">Name</span></span>| <span data-ttu-id="12a07-113">Gibt den Namen der Features an, die aktiviert oder deaktiviert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="12a07-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>| 
| <span data-ttu-id="12a07-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="12a07-114">Ensure</span></span>| <span data-ttu-id="12a07-115">Gibt an, ob die Features aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="12a07-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="12a07-116">Um sicherzustellen, dass die Feature aktiviert sind, legen Sie diese Eigenschaft auf „Enable“ fest. Um sicherzustellen, dass die Feature deaktiviert sind, legen Sie diese Eigenschaft auf „Disable“ fest.</span><span class="sxs-lookup"><span data-stu-id="12a07-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="12a07-117">Source</span><span class="sxs-lookup"><span data-stu-id="12a07-117">Source</span></span>| <span data-ttu-id="12a07-118">Nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="12a07-118">Not implemented.</span></span>|
| <span data-ttu-id="12a07-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="12a07-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="12a07-120">Gibt an, ob Windows Update (WU) von DISM kontaktiert wird, wenn die Quelldateien zum Aktivieren von Features gesucht werden.</span><span class="sxs-lookup"><span data-stu-id="12a07-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="12a07-121">Falls „$true“, wird WU nicht von DISM kontaktiert.</span><span class="sxs-lookup"><span data-stu-id="12a07-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="12a07-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="12a07-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="12a07-123">Legen Sie diese Einstellung auf **$true** fest, um alle zu den Features gehörigen Dateien zu entfernen, wenn sie deaktiviert werden (d. h. wenn **Ensure** auf „Absent“ festgelegt wird).</span><span class="sxs-lookup"><span data-stu-id="12a07-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="12a07-124">LogLevel</span><span class="sxs-lookup"><span data-stu-id="12a07-124">LogLevel</span></span>| <span data-ttu-id="12a07-125">Die maximale Ausgabeebene, die in den Protokollen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="12a07-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="12a07-126">Die zulässigen Werte lauten: „ErrorsOnly“ (nur Fehler werden protokolliert), „ErrorsAndWarning“ (Fehler und Warnungen werden protokolliert) und „ErrorsAndWarningAndInformation“ (Fehler, Warnungen und Debuginformationen werden protokolliert).</span><span class="sxs-lookup"><span data-stu-id="12a07-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="12a07-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="12a07-127">LogPath</span></span>| <span data-ttu-id="12a07-128">Der Pfad zu einer Protokolldatei, in der der Ressourcenanbieter den Vorgang protokollieren soll.</span><span class="sxs-lookup"><span data-stu-id="12a07-128">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="12a07-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="12a07-129">DependsOn</span></span>| <span data-ttu-id="12a07-130">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="12a07-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="12a07-131">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="12a07-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



