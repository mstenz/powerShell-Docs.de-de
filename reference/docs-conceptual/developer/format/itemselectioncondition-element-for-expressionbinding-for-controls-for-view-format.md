---
title: Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362939"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="e5e38-102">Element „ItemSelectionCondition“ für ExpressionBinding für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="e5e38-103">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="e5e38-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e5e38-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="e5e38-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e5e38-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für View (Format) ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format) Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5e38-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5e38-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5e38-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e5e38-107">Attributes and Elements</span></span>

<span data-ttu-id="e5e38-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ItemSelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e5e38-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5e38-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e5e38-109">Attributes</span></span>

<span data-ttu-id="e5e38-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="e5e38-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5e38-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e5e38-111">Child Elements</span></span>

|<span data-ttu-id="e5e38-112">Element</span><span class="sxs-lookup"><span data-stu-id="e5e38-112">Element</span></span>|<span data-ttu-id="e5e38-113">Description</span><span class="sxs-lookup"><span data-stu-id="e5e38-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5e38-114">PropertyName-Element für itemselectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e5e38-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e5e38-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e5e38-116">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="e5e38-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e5e38-117">ScriptBlock-Element für itemselectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e5e38-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e5e38-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e5e38-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="e5e38-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5e38-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e5e38-120">Parent Elements</span></span>

|<span data-ttu-id="e5e38-121">Element</span><span class="sxs-lookup"><span data-stu-id="e5e38-121">Element</span></span>|<span data-ttu-id="e5e38-122">Description</span><span class="sxs-lookup"><span data-stu-id="e5e38-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5e38-123">ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="e5e38-124">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e5e38-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5e38-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e5e38-125">Remarks</span></span>

<span data-ttu-id="e5e38-126">Sie können einen Eigenschaftsnamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="e5e38-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5e38-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5e38-127">See Also</span></span>

[<span data-ttu-id="e5e38-128">PropertyName-Element für itemselectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e5e38-129">ScriptBlock-Element für itemselectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e5e38-130">ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e5e38-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="e5e38-131">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="e5e38-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
