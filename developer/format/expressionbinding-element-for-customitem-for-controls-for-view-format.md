---
title: ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858296"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="806b0-102">Element „ExpressionBinding“ für CustomItem für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="806b0-103">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="806b0-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="806b0-104">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="806b0-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="806b0-105">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format) ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="806b0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="806b0-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="806b0-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="806b0-107">Attributes and Elements</span></span>

<span data-ttu-id="806b0-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ExpressionBinding` Element.</span><span class="sxs-lookup"><span data-stu-id="806b0-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="806b0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="806b0-109">Attributes</span></span>

<span data-ttu-id="806b0-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="806b0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="806b0-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="806b0-111">Child Elements</span></span>

|<span data-ttu-id="806b0-112">Element</span><span class="sxs-lookup"><span data-stu-id="806b0-112">Element</span></span>|<span data-ttu-id="806b0-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="806b0-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="806b0-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="806b0-114">Optional element.</span></span><br /><br /> <span data-ttu-id="806b0-115">Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="806b0-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="806b0-116">CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="806b0-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="806b0-117">Optional element.</span></span><br /><br /> <span data-ttu-id="806b0-118">Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="806b0-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="806b0-119">EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="806b0-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="806b0-120">Optional element.</span></span><br /><br /> <span data-ttu-id="806b0-121">Gibt an, dass die Elemente der Auflistungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="806b0-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="806b0-122">ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="806b0-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="806b0-123">Optional element.</span></span><br /><br /> <span data-ttu-id="806b0-124">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="806b0-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="806b0-125">PropertyName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="806b0-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="806b0-126">Optional element.</span></span><br /><br /> <span data-ttu-id="806b0-127">Gibt die .NET-Eigenschaft, deren Wert durch das Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="806b0-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="806b0-128">ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="806b0-129">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="806b0-129">Optional element.</span></span><br /><br /> <span data-ttu-id="806b0-130">Gibt das Skript an, dessen Wert vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="806b0-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="806b0-131">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="806b0-131">Parent Elements</span></span>

|<span data-ttu-id="806b0-132">Element</span><span class="sxs-lookup"><span data-stu-id="806b0-132">Element</span></span>|<span data-ttu-id="806b0-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="806b0-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="806b0-134">CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="806b0-135">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="806b0-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="806b0-136">Hinweise</span><span class="sxs-lookup"><span data-stu-id="806b0-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="806b0-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="806b0-137">See Also</span></span>

[<span data-ttu-id="806b0-138">CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="806b0-139">CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="806b0-140">EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="806b0-141">ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="806b0-142">PropertyName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="806b0-143">ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="806b0-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="806b0-144">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="806b0-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
