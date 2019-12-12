---
title: ExpressionBinding-Element für customItem für CustomControl für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363149"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="2b4c2-102">Element „ExpressionBinding“ für CustomItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="2b4c2-103">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="2b4c2-104">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="2b4c2-105">Konfigurationselement (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element für View (Format) customentries-Element für CustomControl for View (Format) customentry-Element für customentries für CustomControl für Ansicht ( Format) customItem-Element für customentry für CustomControl für View (Format) ExpressionBinding-Element für customItem für CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b4c2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b4c2-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="2b4c2-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2b4c2-107">Attributes and Elements</span></span>

<span data-ttu-id="2b4c2-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ExpressionBinding`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b4c2-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2b4c2-109">Attributes</span></span>

<span data-ttu-id="2b4c2-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b4c2-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b4c2-111">Child Elements</span></span>

|<span data-ttu-id="2b4c2-112">Element</span><span class="sxs-lookup"><span data-stu-id="2b4c2-112">Element</span></span>|<span data-ttu-id="2b4c2-113">Description</span><span class="sxs-lookup"><span data-stu-id="2b4c2-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="2b4c2-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-114">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4c2-115">Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="2b4c2-116">Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b4c2-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4c2-118">Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="2b4c2-119">Enumeratecollection-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b4c2-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4c2-121">Gibt an, dass die Elemente der Auflistungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="2b4c2-122">Itemselectioncondition-Element für ExpressionBinding für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="2b4c2-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-123">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4c2-124">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="2b4c2-125">PropertyName-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b4c2-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-126">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4c2-127">Gibt die .net-Eigenschaft an, deren Wert vom-Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="2b4c2-128">ScriptBlock-Element für ExpressionBinding für customcustomcontrol für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b4c2-129">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-129">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4c2-130">Gibt das Skript an, dessen Wert vom-Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2b4c2-131">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b4c2-131">Parent Elements</span></span>

|<span data-ttu-id="2b4c2-132">Element</span><span class="sxs-lookup"><span data-stu-id="2b4c2-132">Element</span></span>|<span data-ttu-id="2b4c2-133">Description</span><span class="sxs-lookup"><span data-stu-id="2b4c2-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b4c2-134">CustomItem-Element für customentry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="2b4c2-135">Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2b4c2-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b4c2-136">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2b4c2-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2b4c2-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2b4c2-137">See Also</span></span>

[<span data-ttu-id="2b4c2-138">Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b4c2-139">Enumeratecollection-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b4c2-140">Itemselectioncondition-Element für ExpressionBinding für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="2b4c2-141">PropertyName-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b4c2-142">ScriptBlock-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b4c2-143">CustomItem-Element für customentry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4c2-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="2b4c2-144">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="2b4c2-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
