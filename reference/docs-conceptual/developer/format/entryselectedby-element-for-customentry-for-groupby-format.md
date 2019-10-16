---
title: Entryselectedby-Element für customentry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363859"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="0250f-102">Element „EntrySelectedBy“ für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-102">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="0250f-103">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="0250f-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0250f-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0250f-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="0250f-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0250f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0250f-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0250f-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0250f-107">Attributes and Elements</span></span>

<span data-ttu-id="0250f-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0250f-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="0250f-109">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine Definition angeben.</span><span class="sxs-lookup"><span data-stu-id="0250f-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="0250f-110">Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="0250f-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="0250f-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="0250f-111">Attributes</span></span>

<span data-ttu-id="0250f-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="0250f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0250f-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0250f-113">Child Elements</span></span>

|<span data-ttu-id="0250f-114">Element</span><span class="sxs-lookup"><span data-stu-id="0250f-114">Element</span></span>|<span data-ttu-id="0250f-115">Description</span><span class="sxs-lookup"><span data-stu-id="0250f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0250f-116">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0250f-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0250f-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0250f-118">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="0250f-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0250f-119">Selectionsetname-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-119">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0250f-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0250f-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0250f-121">Gibt einen Satz von .NET-Typen an, die diese Definition des-Steuer Elements verwenden.</span><span class="sxs-lookup"><span data-stu-id="0250f-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="0250f-122">Tyname-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-122">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="0250f-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0250f-123">Optional element.</span></span><br /><br /> <span data-ttu-id="0250f-124">Gibt einen .NET-Typ an, der diese Definition des-Steuer Elements verwendet.</span><span class="sxs-lookup"><span data-stu-id="0250f-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0250f-125">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0250f-125">Parent Elements</span></span>

|<span data-ttu-id="0250f-126">Element</span><span class="sxs-lookup"><span data-stu-id="0250f-126">Element</span></span>|<span data-ttu-id="0250f-127">Description</span><span class="sxs-lookup"><span data-stu-id="0250f-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0250f-128">Customentry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-128">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="0250f-129">Stellt eine Definition des-Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="0250f-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0250f-130">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0250f-130">Remarks</span></span>

<span data-ttu-id="0250f-131">Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt eine bestimmte Eigenschaft hat oder wenn ein bestimmter Eigenschafts Wert oder ein Skript zu `true` ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="0250f-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0250f-132">Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0250f-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0250f-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0250f-133">See Also</span></span>

[<span data-ttu-id="0250f-134">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0250f-135">Selectionsetname-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-135">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0250f-136">Tyname-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-136">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="0250f-137">Customentry-Element für customentries für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="0250f-137">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="0250f-138">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="0250f-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
