---
title: ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065919"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="b3949-102">Element „ExpressionBinding“ für CustomItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="b3949-103">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b3949-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="b3949-104">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b3949-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="b3949-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3949-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3949-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="b3949-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b3949-107">Attributes and Elements</span></span>

<span data-ttu-id="b3949-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ExpressionBinding` Element.</span><span class="sxs-lookup"><span data-stu-id="b3949-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b3949-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b3949-109">Attributes</span></span>

<span data-ttu-id="b3949-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="b3949-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b3949-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b3949-111">Child Elements</span></span>

|<span data-ttu-id="b3949-112">Element</span><span class="sxs-lookup"><span data-stu-id="b3949-112">Element</span></span>|<span data-ttu-id="b3949-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b3949-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="b3949-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b3949-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b3949-115">Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b3949-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="b3949-116">CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3949-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b3949-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b3949-118">Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="b3949-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="b3949-119">EnumerateCollection-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3949-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b3949-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b3949-121">Angegeben, dass die Elemente der Auflistungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b3949-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="b3949-122">ItemSelectionCondition-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="b3949-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b3949-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b3949-124">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="b3949-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="b3949-125">PropertyName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3949-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b3949-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b3949-127">Gibt die .NET-Eigenschaft, deren Wert durch das Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b3949-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="b3949-128">ScriptBlock-Element für die ExpressionBinding für CustomCustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3949-129">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b3949-129">Optional element.</span></span><br /><br /> <span data-ttu-id="b3949-130">Gibt das Skript an, dessen Wert vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b3949-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b3949-131">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b3949-131">Parent Elements</span></span>

|<span data-ttu-id="b3949-132">Element</span><span class="sxs-lookup"><span data-stu-id="b3949-132">Element</span></span>|<span data-ttu-id="b3949-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b3949-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b3949-134">CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="b3949-135">Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b3949-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b3949-136">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b3949-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="b3949-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b3949-137">See Also</span></span>

[<span data-ttu-id="b3949-138">CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3949-139">EnumerateCollection-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3949-140">ItemSelectionCondition-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="b3949-141">PropertyName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3949-142">ScriptBlock-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3949-143">CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="b3949-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="b3949-144">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3949-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
