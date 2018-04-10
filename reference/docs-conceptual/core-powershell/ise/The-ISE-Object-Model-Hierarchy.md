---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Die ISE-Objektmodellhierarchie
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="c1286-103">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="c1286-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="c1286-104">In diesem Thema wird die Hierarchie der Objekte beschrieben, die Teil von Windows PowerShell Integrated Scripting Environment (ISE) sind.</span><span class="sxs-lookup"><span data-stu-id="c1286-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
<span data-ttu-id="c1286-105">Windows PowerShell ISE ist in Windows PowerShell 3.0 und in Windows PowerShell 4.0 enthalten.</span><span class="sxs-lookup"><span data-stu-id="c1286-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span>
<span data-ttu-id="c1286-106">Klicken Sie auf ein Objekt, um die Dokumentation für die Klasse aufzurufen, die das Objekt definiert.</span><span class="sxs-lookup"><span data-stu-id="c1286-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="c1286-107">$psISE-Objekt</span><span class="sxs-lookup"><span data-stu-id="c1286-107">$psISE Object</span></span>

<span data-ttu-id="c1286-108">Das **$psISE**-Objekt ist das [Stammobjekt](The-ObjectModelRoot-Object.md) der Windows PowerShell ISE-Objekthierarchie.</span><span class="sxs-lookup"><span data-stu-id="c1286-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="c1286-109">Es befindet sich auf der obersten Ebene und macht die folgenden Objekte für Skripts verfügbar:</span><span class="sxs-lookup"><span data-stu-id="c1286-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="c1286-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="c1286-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="c1286-111">Das **$psISE.CurrentFile**-Objekt ist eine Instanz der [ISEFile](The-ISEFile-Object.md)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="c1286-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="c1286-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="c1286-113">Das **$psISE.CurrentPowerShellTab**-Objekt ist eine Instanz der [PowerShellTab](The-PowerShellTab-Object.md)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="c1286-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="c1286-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="c1286-115">Das **$psISE.CurrentVisibleHorizontalTool**-Objekt ist eine Instanz der [ISEAddOnTool](The-ISEAddOnTool-Object.md)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="c1286-116">Es stellt das installierte Add-On-Tool dar, das derzeit am oberen Rand des Windows PowerShell ISE-Fensters angedockt ist.</span><span class="sxs-lookup"><span data-stu-id="c1286-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="c1286-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="c1286-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="c1286-118">Das **$psISE.CurrentVisibleHorizontalTool**-Objekt ist eine Instanz der [ISEAddOnTool](The-ISEAddOnTool-Object.md)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="c1286-119">Es stellt das installierte Add-On-Tool dar, das derzeit am rechten Rand des Windows PowerShell ISE-Fensters angedockt ist.</span><span class="sxs-lookup"><span data-stu-id="c1286-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="c1286-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="c1286-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="c1286-121">Das **$psISE.Options**-Objekt ist eine Instanz der [ISEOptions](The-ISEOptions-Object.md)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="c1286-122">Das ISEOptions-Objekt stellt verschiedene Einstellungen für Windows PowerShell ISE dar.</span><span class="sxs-lookup"><span data-stu-id="c1286-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="c1286-123">Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEOptions-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="c1286-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="c1286-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="c1286-125">Das **$psISE.PowerShellTabs**-Objekt ist eine Instanz der [PowerShellTabCollection](The-PowerShellTabCollection-Object.md)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="c1286-126">Es ist eine Sammlung aller zurzeit geöffneten PowerShell-Registerkarten, die die verfügbaren Windows PowerShell-Ausführungsumgebungen auf dem lokalen Computer oder auf verbundenen Remotecomputern darstellen.</span><span class="sxs-lookup"><span data-stu-id="c1286-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span>
<span data-ttu-id="c1286-127">Jedes Element in der Sammlung ist eine Instanz der [PowerShellTab](The-PowerShellTab-Object.md)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c1286-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1286-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c1286-128">See Also</span></span>

- [<span data-ttu-id="c1286-129">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="c1286-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c1286-130">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="c1286-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)