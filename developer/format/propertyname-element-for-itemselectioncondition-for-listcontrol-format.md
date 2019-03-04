---
title: PropertyName-Element für ItemSelectionCondition für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855536"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="75a79-102">Element „PropertyName“ für ItemSeclectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75a79-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="75a79-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="75a79-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="75a79-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Ansicht wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="75a79-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="75a79-105">Dieses Element wird verwendet, wenn Sie eine Ansicht zu definieren.</span><span class="sxs-lookup"><span data-stu-id="75a79-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="75a79-106">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries-Element (Format) ListEntry Konfigurationselement für ListItems-Element für ListEntry für ListControl (Format) ListItem ListControl (Format) -Element für ListItems für ListControl (Format) ItemSelectionCondition-Element für ListItem für ListControls PropertyName-Element für ItemSelectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75a79-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75a79-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="75a79-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75a79-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="75a79-108">Attributes and Elements</span></span>

<span data-ttu-id="75a79-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="75a79-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75a79-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="75a79-110">Attributes</span></span>

<span data-ttu-id="75a79-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="75a79-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75a79-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="75a79-112">Child Elements</span></span>

<span data-ttu-id="75a79-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="75a79-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75a79-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="75a79-114">Parent Elements</span></span>

|<span data-ttu-id="75a79-115">Element</span><span class="sxs-lookup"><span data-stu-id="75a79-115">Element</span></span>|<span data-ttu-id="75a79-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="75a79-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75a79-117">ItemSelectionCondition-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75a79-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="75a79-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="75a79-118">Text Value</span></span>

<span data-ttu-id="75a79-119">Geben Sie den Namen der Eigenschaft, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="75a79-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="75a79-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="75a79-120">Remarks</span></span>

<span data-ttu-id="75a79-121">Wenn dieses Element verwendet wird, Sie können nicht angeben, die ["scriptblock"](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -Element, wenn die auswahlbedingung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="75a79-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="75a79-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="75a79-122">See Also</span></span>

[<span data-ttu-id="75a79-123">ScriptBlock-Element für ItemSelectionCondition für ListIControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75a79-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="75a79-124">ItemSelectionCondition-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="75a79-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="75a79-125">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="75a79-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
