---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „WindowsOptionalFeature“
ms.openlocfilehash: bca6294db74c92a2c1940cfbe00305542a1c5d19
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565365"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="e3558-103">DSC-Ressource „WindowsOptionalFeature“</span><span class="sxs-lookup"><span data-stu-id="e3558-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="e3558-104">Gilt für: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="e3558-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="e3558-105">Die Ressource **WindowsOptionalFeature** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass optionale Features auf einem Zielknoten aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="e3558-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3558-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3558-106">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="e3558-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e3558-107">Properties</span></span>

|<span data-ttu-id="e3558-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e3558-108">Property</span></span> |<span data-ttu-id="e3558-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="e3558-109">Description</span></span> |
|---|---|
|<span data-ttu-id="e3558-110">Name</span><span class="sxs-lookup"><span data-stu-id="e3558-110">Name</span></span> |<span data-ttu-id="e3558-111">Gibt den Namen des Features an, das aktiviert oder deaktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e3558-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="e3558-112">`Source`</span><span class="sxs-lookup"><span data-stu-id="e3558-112">Source</span></span> |<span data-ttu-id="e3558-113">Nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="e3558-113">Not implemented.</span></span> |
|<span data-ttu-id="e3558-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="e3558-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="e3558-115">Gibt an, ob Windows Update (WU) von DISM kontaktiert wird, wenn die Quelldateien zum Aktivieren eines Features gesucht werden.</span><span class="sxs-lookup"><span data-stu-id="e3558-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="e3558-116">Falls `$true`, wird WU nicht von DISM kontaktiert.</span><span class="sxs-lookup"><span data-stu-id="e3558-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="e3558-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="e3558-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="e3558-118">Legen Sie diese Einstellung auf `$true` fest, um alle zu dem Feature gehörigen Dateien zu entfernen, wenn **Ensure** auf **Absent** festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="e3558-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="e3558-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="e3558-119">LogLevel</span></span> |<span data-ttu-id="e3558-120">Die maximale Ausgabeebene, die in den Protokollen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3558-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="e3558-121">Zulässige Werte: **ErrorsOnly**, **ErrorsAndWarning** und **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="e3558-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="e3558-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="e3558-122">LogPath</span></span> |<span data-ttu-id="e3558-123">Der Pfad zu einer Protokolldatei, in der der Ressourcenanbieter den Vorgang protokollieren soll.</span><span class="sxs-lookup"><span data-stu-id="e3558-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e3558-124">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e3558-124">Common properties</span></span>

|<span data-ttu-id="e3558-125">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e3558-125">Property</span></span> |<span data-ttu-id="e3558-126">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="e3558-126">Description</span></span> |
|---|---|
|<span data-ttu-id="e3558-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e3558-127">DependsOn</span></span> |<span data-ttu-id="e3558-128">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="e3558-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e3558-129">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e3558-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e3558-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="e3558-130">Ensure</span></span> |<span data-ttu-id="e3558-131">Gibt an, ob die Funktion aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="e3558-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="e3558-132">Um sicherzustellen, dass das Feature aktiviert ist, legen Sie diese Eigenschaft auf _Enable_ fest.</span><span class="sxs-lookup"><span data-stu-id="e3558-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="e3558-133">Um sicherzustellen, dass das Feature deaktiviert ist, legen Sie diese Eigenschaft auf _Disable_ fest.</span><span class="sxs-lookup"><span data-stu-id="e3558-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="e3558-134">Der Standardwert ist _Enable_.</span><span class="sxs-lookup"><span data-stu-id="e3558-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="e3558-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e3558-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="e3558-136">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="e3558-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="e3558-137">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e3558-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="e3558-138">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="e3558-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
