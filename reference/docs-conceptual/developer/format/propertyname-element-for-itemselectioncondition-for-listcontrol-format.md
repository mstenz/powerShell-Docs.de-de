---
title: PropertyName-Element für itemselectioncondition für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362389"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="585c9-102">Element „PropertyName“ für ItemSeclectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="585c9-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="585c9-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="585c9-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="585c9-104">Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und die Ansicht wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="585c9-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="585c9-105">Dieses Element wird beim Definieren einer Listenansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="585c9-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="585c9-106">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element für ListControl (Format) ListItems-Element für ListEntry für ListControl (Format) ListItem Element für ListItems für ListControl (Format) itemselectioncondition-Element für ListItem für ListControls propertyName-Element für itemselectioncondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="585c9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="585c9-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="585c9-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="585c9-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="585c9-108">Attributes and Elements</span></span>

<span data-ttu-id="585c9-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="585c9-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="585c9-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="585c9-110">Attributes</span></span>

<span data-ttu-id="585c9-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="585c9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="585c9-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="585c9-112">Child Elements</span></span>

<span data-ttu-id="585c9-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="585c9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="585c9-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="585c9-114">Parent Elements</span></span>

|<span data-ttu-id="585c9-115">Element</span><span class="sxs-lookup"><span data-stu-id="585c9-115">Element</span></span>|<span data-ttu-id="585c9-116">Description</span><span class="sxs-lookup"><span data-stu-id="585c9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="585c9-117">Itemselectioncondition-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="585c9-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="585c9-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="585c9-118">Text Value</span></span>

<span data-ttu-id="585c9-119">Geben Sie den Namen der Eigenschaft an, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="585c9-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="585c9-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="585c9-120">Remarks</span></span>

<span data-ttu-id="585c9-121">Wenn dieses Element verwendet wird, können Sie das [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -Element nicht angeben, wenn Sie die Auswahlbedingung definieren.</span><span class="sxs-lookup"><span data-stu-id="585c9-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="585c9-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="585c9-122">See Also</span></span>

[<span data-ttu-id="585c9-123">ScriptBlock-Element für itemselectioncondition für listicontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="585c9-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="585c9-124">Itemselectioncondition-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="585c9-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="585c9-125">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="585c9-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
