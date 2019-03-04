---
title: ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c15014-2440-410d-b02d-b7f1a49240a0
caps.latest.revision: 7
ms.openlocfilehash: 80f375c53c205c793600655fa6031d114871618e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861846"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="e1c3c-102">Element „ItemSelectionCondition“ für ExpressionBinding für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-102">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="e1c3c-103">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="e1c3c-104">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e1c3c-105">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format) ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format) ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1c3c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1c3c-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1c3c-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e1c3c-107">Attributes and Elements</span></span>

<span data-ttu-id="e1c3c-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ItemSelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1c3c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e1c3c-109">Attributes</span></span>

<span data-ttu-id="e1c3c-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1c3c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e1c3c-111">Child Elements</span></span>

|<span data-ttu-id="e1c3c-112">Element</span><span class="sxs-lookup"><span data-stu-id="e1c3c-112">Element</span></span>|<span data-ttu-id="e1c3c-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e1c3c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1c3c-114">PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-114">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e1c3c-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e1c3c-116">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e1c3c-117">ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-117">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="e1c3c-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e1c3c-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e1c3c-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e1c3c-120">Parent Elements</span></span>

|<span data-ttu-id="e1c3c-121">Element</span><span class="sxs-lookup"><span data-stu-id="e1c3c-121">Element</span></span>|<span data-ttu-id="e1c3c-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e1c3c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1c3c-123">ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-123">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="e1c3c-124">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e1c3c-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e1c3c-125">Remarks</span></span>

<span data-ttu-id="e1c3c-126">Sie können einen Eigenschaftennamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="e1c3c-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1c3c-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e1c3c-127">See Also</span></span>

[<span data-ttu-id="e1c3c-128">PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-128">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e1c3c-129">ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-129">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e1c3c-130">ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e1c3c-130">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="e1c3c-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="e1c3c-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
