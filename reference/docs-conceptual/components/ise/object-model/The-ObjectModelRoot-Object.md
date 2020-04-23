---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: Das ObjectModelRoot-Objekt
ms.openlocfilehash: 0b04bdb3127edaac7b504556843efb64ee65ed13
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736027"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="e0d58-103">Das ObjectModelRoot-Objekt</span><span class="sxs-lookup"><span data-stu-id="e0d58-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="e0d58-104">Das `$psISE`-Objekt ist das Prinzipalstammobjekt in Windows PowerShell® Integrated Scripting Environment (ISE) und eine Instanz der Microsoft.PowerShell.Host.ISE.ObjectModelRoot-Klasse.</span><span class="sxs-lookup"><span data-stu-id="e0d58-104">The `$psISE` object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span> <span data-ttu-id="e0d58-105">Dieses Thema beschreibt die Eigenschaften des **ObjectModelRoot**-Objekts.</span><span class="sxs-lookup"><span data-stu-id="e0d58-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="e0d58-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e0d58-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="e0d58-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="e0d58-107">CurrentFile</span></span>

> <span data-ttu-id="e0d58-108">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0d58-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e0d58-109">Die schreibgeschützte Eigenschaft, die die diesem Hostobjekt, das gegenwärtig den Fokus besitzt, zugeordnete Datei abruft.</span><span class="sxs-lookup"><span data-stu-id="e0d58-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="e0d58-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="e0d58-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="e0d58-111">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0d58-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e0d58-112">Die schreibgeschützte Eigenschaft, die die PowerShell-Registerkarte abruft, die zurzeit den Fokus besitzt.</span><span class="sxs-lookup"><span data-stu-id="e0d58-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="e0d58-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="e0d58-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="e0d58-114">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0d58-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e0d58-115">Die schreibgeschützte Eigenschaft, die das derzeit sichtbare Windows PowerShell ISE-Add-On-Tool abruft, das sich im horizontalen Toolbereich unten im Editor befindet.</span><span class="sxs-lookup"><span data-stu-id="e0d58-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="e0d58-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="e0d58-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="e0d58-117">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0d58-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e0d58-118">Die schreibgeschützte Eigenschaft, die das derzeit sichtbare Windows PowerShell ISE-Add-On-Tool abruft, das sich im vertikalen Toolbereich rechts im Editor befindet.</span><span class="sxs-lookup"><span data-stu-id="e0d58-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="e0d58-119">Tastatur</span><span class="sxs-lookup"><span data-stu-id="e0d58-119">Options</span></span>

> <span data-ttu-id="e0d58-120">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0d58-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e0d58-121">Die schreibgeschützte Eigenschaft, mit der die verschiedenen Optionen zum Ändern von Eigenschaften in Windows PowerShell ISE abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="e0d58-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="e0d58-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="e0d58-122">PowerShellTabs</span></span>

> <span data-ttu-id="e0d58-123">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e0d58-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="e0d58-124">Die schreibgeschützte Eigenschaft, die die Sammlung von in Windows PowerShell ISE geöffneten PowerShell-Registerkarten abruft.</span><span class="sxs-lookup"><span data-stu-id="e0d58-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="e0d58-125">Standardmäßig enthält dieses Objekt eine PowerShell-Registerkarte. Allerdings können Sie mit Skripts oder Menüs in Windows PowerShell ISE weitere PowerShell-Registerkarten zu diesem Objekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e0d58-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0d58-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e0d58-126">See Also</span></span>

- [<span data-ttu-id="e0d58-127">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="e0d58-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="e0d58-128">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="e0d58-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)