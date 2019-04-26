---
title: ExpressionBinding-Element für CustomItem für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065902"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a><span data-ttu-id="3db1c-102">Element „ExpressionBinding“ für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-102">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="3db1c-103">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3db1c-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="3db1c-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3db1c-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3db1c-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format) ExpressionBinding-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3db1c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3db1c-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="3db1c-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3db1c-107">Attributes and Elements</span></span>

<span data-ttu-id="3db1c-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ExpressionBinding` Element.</span><span class="sxs-lookup"><span data-stu-id="3db1c-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3db1c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3db1c-109">Attributes</span></span>

<span data-ttu-id="3db1c-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="3db1c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3db1c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3db1c-111">Child Elements</span></span>

|<span data-ttu-id="3db1c-112">Element</span><span class="sxs-lookup"><span data-stu-id="3db1c-112">Element</span></span>|<span data-ttu-id="3db1c-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3db1c-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="3db1c-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3db1c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3db1c-115">Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3db1c-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="3db1c-116">CustomControlName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-116">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3db1c-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3db1c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3db1c-118">Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="3db1c-118">Specifies the name of a common control or a view control.</span></span>|
|<span data-ttu-id="3db1c-119">[EnumerateCollection-Element für die ExpressionBinding für GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-119">[EnumerateCollection Element for ExpressionBinding for GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>|<span data-ttu-id="3db1c-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3db1c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3db1c-121">Angegeben, dass die Elemente der Auflistungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="3db1c-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="3db1c-122">ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-122">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3db1c-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3db1c-123">Optional element.</span></span><br /><br /> <span data-ttu-id="3db1c-124">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="3db1c-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="3db1c-125">PropertyName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-125">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3db1c-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3db1c-126">Optional element.</span></span><br /><br /> <span data-ttu-id="3db1c-127">Gibt die .NET-Eigenschaft, deren Wert durch das Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3db1c-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="3db1c-128">ScriptBlock-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-128">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="3db1c-129">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3db1c-129">Optional element.</span></span><br /><br /> <span data-ttu-id="3db1c-130">Gibt das Skript an, dessen Wert vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3db1c-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3db1c-131">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3db1c-131">Parent Elements</span></span>

|<span data-ttu-id="3db1c-132">Element</span><span class="sxs-lookup"><span data-stu-id="3db1c-132">Element</span></span>|<span data-ttu-id="3db1c-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3db1c-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3db1c-134">CustomItem-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-134">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="3db1c-135">Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3db1c-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3db1c-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3db1c-136">See Also</span></span>

[<span data-ttu-id="3db1c-137">CustomControlName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-137">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3db1c-138">EnumerateCollection-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-138">EnumerateCollection Element for ExpressionBinding for GroupBy (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3db1c-139">ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-139">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3db1c-140">PropertyName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-140">PropertyName Element for ExpressionBinding for GroupBy (Format)</span></span>](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3db1c-141">ScriptBlock-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-141">ScriptBlock Element for ExpressionBinding for GroupBy (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="3db1c-142">CustomItem-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3db1c-142">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="3db1c-143">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="3db1c-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
