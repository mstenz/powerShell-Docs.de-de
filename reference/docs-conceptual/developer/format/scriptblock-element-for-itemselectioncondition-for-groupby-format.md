---
title: ScriptBlock-Element für itemselectioncondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364829"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="0b211-102">Element „ScriptBlock“ für ItemSeclectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0b211-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="0b211-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0b211-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="0b211-104">Wenn dieses Skript `true` ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="0b211-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0b211-105">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0b211-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0b211-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) ExpressionBinding-Element für customItem für GroupBy (Format) itemselectioncondition-Element für ExpressionBinding für GroupBy (Format) ScriptBlock-Element für Itemselectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0b211-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b211-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="0b211-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b211-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0b211-108">Attributes and Elements</span></span>

<span data-ttu-id="0b211-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0b211-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b211-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0b211-110">Attributes</span></span>

<span data-ttu-id="0b211-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="0b211-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b211-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0b211-112">Child Elements</span></span>

<span data-ttu-id="0b211-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="0b211-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0b211-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0b211-114">Parent Elements</span></span>

|<span data-ttu-id="0b211-115">Element</span><span class="sxs-lookup"><span data-stu-id="0b211-115">Element</span></span>|<span data-ttu-id="0b211-116">Description</span><span class="sxs-lookup"><span data-stu-id="0b211-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b211-117">Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0b211-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="0b211-118">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="0b211-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0b211-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="0b211-119">Text Value</span></span>

<span data-ttu-id="0b211-120">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="0b211-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="0b211-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0b211-121">Remarks</span></span>

<span data-ttu-id="0b211-122">Wenn dieses Element verwendet wird, können Sie beim Definieren der Auswahlbedingung nicht das [propertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) -Element angeben.</span><span class="sxs-lookup"><span data-stu-id="0b211-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b211-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0b211-123">See Also</span></span>

[<span data-ttu-id="0b211-124">Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0b211-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="0b211-125">PropertyName-Element für itemselectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0b211-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="0b211-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="0b211-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
