---
title: EntrySelectedBy-Element für CustomEntry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862816"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="34f08-102">Element „EntrySelectedBy“ für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="34f08-103">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="34f08-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="34f08-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="34f08-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="34f08-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="34f08-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="34f08-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34f08-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="34f08-107">Attributes and Elements</span></span>

<span data-ttu-id="34f08-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="34f08-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="34f08-109">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition eines angeben.</span><span class="sxs-lookup"><span data-stu-id="34f08-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="34f08-110">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="34f08-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="34f08-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="34f08-111">Attributes</span></span>

<span data-ttu-id="34f08-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="34f08-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="34f08-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="34f08-113">Child Elements</span></span>

|<span data-ttu-id="34f08-114">Element</span><span class="sxs-lookup"><span data-stu-id="34f08-114">Element</span></span>|<span data-ttu-id="34f08-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="34f08-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34f08-116">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="34f08-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="34f08-117">Optional element.</span></span><br /><br /> <span data-ttu-id="34f08-118">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="34f08-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="34f08-119">SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="34f08-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="34f08-120">Optional element.</span></span><br /><br /> <span data-ttu-id="34f08-121">Gibt einen Satz von .NET-Typen, die dieser Definition des Steuerelements verwenden.</span><span class="sxs-lookup"><span data-stu-id="34f08-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="34f08-122">TypeName-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="34f08-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="34f08-123">Optional element.</span></span><br /><br /> <span data-ttu-id="34f08-124">Gibt einen .NET-Typ, ein, der dieser Definition des Steuerelements verwendet.</span><span class="sxs-lookup"><span data-stu-id="34f08-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="34f08-125">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="34f08-125">Parent Elements</span></span>

|<span data-ttu-id="34f08-126">Element</span><span class="sxs-lookup"><span data-stu-id="34f08-126">Element</span></span>|<span data-ttu-id="34f08-127">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="34f08-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34f08-128">CustomEntry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="34f08-129">Stellt eine Definition des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="34f08-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="34f08-130">Hinweise</span><span class="sxs-lookup"><span data-stu-id="34f08-130">Remarks</span></span>

<span data-ttu-id="34f08-131">Auswahlbedingungen werden verwendet, um eine Bedingung, die vorhanden sein muss, für die Definition verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder einen bestimmten Eigenschaftswert zu definieren oder Skripts ergibt `true`.</span><span class="sxs-lookup"><span data-stu-id="34f08-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="34f08-132">Weitere Informationen zu auswahlbedingungen, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="34f08-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34f08-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="34f08-133">See Also</span></span>

[<span data-ttu-id="34f08-134">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="34f08-135">SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="34f08-136">TypeName-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="34f08-137">CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="34f08-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="34f08-138">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="34f08-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
