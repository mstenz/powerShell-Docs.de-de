---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „WindowsOptionalFeature“
ms.openlocfilehash: 4cb59151d69adb2a01b7c4bdcaf0e961c24b29a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="eb084-103">DSC-Ressource „WindowsOptionalFeature“</span><span class="sxs-lookup"><span data-stu-id="eb084-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="eb084-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eb084-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="eb084-105">Die Ressource **WindowsOptionalFeature** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass optionale Features auf einem Zielknoten aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="eb084-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb084-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="eb084-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="eb084-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="eb084-107">Properties</span></span>

|  <span data-ttu-id="eb084-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="eb084-108">Property</span></span>  |  <span data-ttu-id="eb084-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eb084-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="eb084-110">Name</span><span class="sxs-lookup"><span data-stu-id="eb084-110">Name</span></span>| <span data-ttu-id="eb084-111">Gibt den Namen des Features an, das aktiviert oder deaktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="eb084-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="eb084-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="eb084-112">Ensure</span></span>| <span data-ttu-id="eb084-113">Gibt an, ob das Feature aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="eb084-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="eb084-114">Um sicherzustellen, dass das Feature aktiviert ist, legen Sie diese Eigenschaft auf „Enable“ fest. Um sicherzustellen, dass das Feature deaktiviert ist, legen Sie diese Eigenschaft auf „Disable“ fest.</span><span class="sxs-lookup"><span data-stu-id="eb084-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="eb084-115">Source</span><span class="sxs-lookup"><span data-stu-id="eb084-115">Source</span></span>| <span data-ttu-id="eb084-116">Nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="eb084-116">Not implemented.</span></span>|
| <span data-ttu-id="eb084-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="eb084-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="eb084-118">Gibt an, ob Windows Update (WU) von DISM kontaktiert wird, wenn die Quelldateien zum Aktivieren eines Features gesucht werden.</span><span class="sxs-lookup"><span data-stu-id="eb084-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="eb084-119">Falls „$true“, wird WU nicht von DISM kontaktiert.</span><span class="sxs-lookup"><span data-stu-id="eb084-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="eb084-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="eb084-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="eb084-121">Legen Sie diese Einstellung auf **$true** fest, um alle zum Feature gehörigen Dateien zu entfernen, wenn es deaktiviert wird (d. h. wenn **Ensure** auf „Absent“ festgelegt wird).</span><span class="sxs-lookup"><span data-stu-id="eb084-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="eb084-122">LogLevel</span><span class="sxs-lookup"><span data-stu-id="eb084-122">LogLevel</span></span>| <span data-ttu-id="eb084-123">Die maximale Ausgabeebene, die in den Protokollen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="eb084-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="eb084-124">Die zulässigen Werte lauten: „ErrorsOnly“ (nur Fehler werden protokolliert), „ErrorsAndWarning“ (Fehler und Warnungen werden protokolliert) und „ErrorsAndWarningAndInformation“ (Fehler, Warnungen und Debuginformationen werden protokolliert).</span><span class="sxs-lookup"><span data-stu-id="eb084-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="eb084-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="eb084-125">LogPath</span></span>| <span data-ttu-id="eb084-126">Der Pfad zu einer Protokolldatei, in der der Ressourcenanbieter den Vorgang protokollieren soll.</span><span class="sxs-lookup"><span data-stu-id="eb084-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="eb084-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="eb084-127">DependsOn</span></span>| <span data-ttu-id="eb084-128">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="eb084-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="eb084-129">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="eb084-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|