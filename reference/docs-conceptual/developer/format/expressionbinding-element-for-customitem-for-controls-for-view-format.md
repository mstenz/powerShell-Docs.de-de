---
title: ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363779"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="45c18-102">Element „ExpressionBinding“ für CustomItem für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-102">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="45c18-103">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45c18-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="45c18-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="45c18-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="45c18-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für View (Format) ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="45c18-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="45c18-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="45c18-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="45c18-107">Attributes and Elements</span></span>

<span data-ttu-id="45c18-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ExpressionBinding`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="45c18-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="45c18-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="45c18-109">Attributes</span></span>

<span data-ttu-id="45c18-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="45c18-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="45c18-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="45c18-111">Child Elements</span></span>

|<span data-ttu-id="45c18-112">Element</span><span class="sxs-lookup"><span data-stu-id="45c18-112">Element</span></span>|<span data-ttu-id="45c18-113">Description</span><span class="sxs-lookup"><span data-stu-id="45c18-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="45c18-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="45c18-114">Optional element.</span></span><br /><br /> <span data-ttu-id="45c18-115">Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="45c18-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="45c18-116">Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-116">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="45c18-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="45c18-117">Optional element.</span></span><br /><br /> <span data-ttu-id="45c18-118">Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="45c18-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="45c18-119">Enumeratecollection-Element für ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-119">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="45c18-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="45c18-120">Optional element.</span></span><br /><br /> <span data-ttu-id="45c18-121">Gibt an, dass die Elemente der Auflistungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45c18-121">Specifies that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="45c18-122">Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-122">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="45c18-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="45c18-123">Optional element.</span></span><br /><br /> <span data-ttu-id="45c18-124">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="45c18-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="45c18-125">PropertyName-Element für ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-125">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="45c18-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="45c18-126">Optional element.</span></span><br /><br /> <span data-ttu-id="45c18-127">Gibt die .net-Eigenschaft an, deren Wert vom-Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="45c18-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="45c18-128">ScriptBlock-Element für ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-128">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="45c18-129">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="45c18-129">Optional element.</span></span><br /><br /> <span data-ttu-id="45c18-130">Gibt das Skript an, dessen Wert vom-Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="45c18-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="45c18-131">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="45c18-131">Parent Elements</span></span>

|<span data-ttu-id="45c18-132">Element</span><span class="sxs-lookup"><span data-stu-id="45c18-132">Element</span></span>|<span data-ttu-id="45c18-133">Description</span><span class="sxs-lookup"><span data-stu-id="45c18-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="45c18-134">CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-134">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="45c18-135">Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="45c18-135">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="45c18-136">Hinweise</span><span class="sxs-lookup"><span data-stu-id="45c18-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="45c18-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="45c18-137">See Also</span></span>

[<span data-ttu-id="45c18-138">CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-138">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="45c18-139">Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-139">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="45c18-140">Enumeratecollection-Element für ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-140">EnumerateCollection Element for ExpressionBinding for Controls for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="45c18-141">Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-141">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="45c18-142">PropertyName-Element für ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-142">PropertyName Element for ExpressionBinding for Controls for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="45c18-143">ScriptBlock-Element für ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="45c18-143">ScriptBlock Element for ExpressionBinding for Controls for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="45c18-144">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="45c18-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
