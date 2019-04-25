---
title: SelectionCondition-Element für EntrySelectedBy für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075714"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="78db8-102">Element „SelectionCondition“ für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="78db8-103">Definiert eine Bedingung, die für die Steuerelementdefinition eines zu verwendenden vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="78db8-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="78db8-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="78db8-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="78db8-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="78db8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="78db8-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78db8-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="78db8-107">Attributes and Elements</span></span>

<span data-ttu-id="78db8-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="78db8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="78db8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="78db8-109">Attributes</span></span>

<span data-ttu-id="78db8-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="78db8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78db8-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="78db8-111">Child Elements</span></span>

|<span data-ttu-id="78db8-112">Element</span><span class="sxs-lookup"><span data-stu-id="78db8-112">Element</span></span>|<span data-ttu-id="78db8-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="78db8-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78db8-114">PropertyName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="78db8-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="78db8-115">Optional element.</span></span><br /><br /> <span data-ttu-id="78db8-116">Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="78db8-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="78db8-117">ScriptBlock-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="78db8-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="78db8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="78db8-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="78db8-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="78db8-120">SelectionSetName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="78db8-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="78db8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="78db8-122">Gibt den Satz von .NET-Typen, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="78db8-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="78db8-123">TypeName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="78db8-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="78db8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="78db8-125">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="78db8-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="78db8-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="78db8-126">Parent Elements</span></span>

|<span data-ttu-id="78db8-127">Element</span><span class="sxs-lookup"><span data-stu-id="78db8-127">Element</span></span>|<span data-ttu-id="78db8-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="78db8-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="78db8-129">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="78db8-130">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="78db8-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="78db8-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="78db8-131">Remarks</span></span>

<span data-ttu-id="78db8-132">Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="78db8-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="78db8-133">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="78db8-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="78db8-134">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="78db8-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="78db8-135">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="78db8-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="78db8-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="78db8-136">See Also</span></span>

[<span data-ttu-id="78db8-137">PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="78db8-138">ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="78db8-139">SelectionSetName-Element für SelectionCondition für benutzerdefiniertes Steuerelement für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="78db8-140">TypeName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="78db8-141">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="78db8-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="78db8-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="78db8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
