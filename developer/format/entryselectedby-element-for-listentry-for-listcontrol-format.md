---
title: EntrySelectedBy-Element für ListEntry für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054934"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="96707-102">Element „EntrySelectedBy“ für ListEntry für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="96707-103">Definiert .NET Typen, die diese Liste View Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="96707-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="96707-104">In den meisten Fällen ist nur eine Definition für eine Listenansicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="96707-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="96707-105">Sie können jedoch mehrere Definitionen für die Listenansicht bereitstellen, sollten Sie die gleiche Listenansicht zu verwenden, um unterschiedliche Daten für verschiedene Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="96707-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="96707-106">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListEntry für ListControl (Format) EntrySelectedBy-Element für ListEntry für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96707-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="96707-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96707-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="96707-108">Attributes and Elements</span></span>

<span data-ttu-id="96707-109">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="96707-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96707-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="96707-110">Attributes</span></span>

<span data-ttu-id="96707-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="96707-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96707-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="96707-112">Child Elements</span></span>

|<span data-ttu-id="96707-113">Element</span><span class="sxs-lookup"><span data-stu-id="96707-113">Element</span></span>|<span data-ttu-id="96707-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="96707-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96707-115">SelectionCondition-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="96707-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="96707-116">Optional element.</span></span><br /><br /> <span data-ttu-id="96707-117">Definiert die Bedingung, die für diese Ansicht Listendefinition zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="96707-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="96707-118">SelectionSetName-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="96707-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="96707-119">Optional element.</span></span><br /><br /> <span data-ttu-id="96707-120">Gibt einen Satz von .NET-Typen, die diese Ansicht Listendefinition zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="96707-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="96707-121">TypeName-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="96707-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="96707-122">Optional element.</span></span><br /><br /> <span data-ttu-id="96707-123">Gibt einen .NET-Typ, der diese Liste Sichtdefinition verwendet.</span><span class="sxs-lookup"><span data-stu-id="96707-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="96707-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="96707-124">Parent Elements</span></span>

|<span data-ttu-id="96707-125">Element</span><span class="sxs-lookup"><span data-stu-id="96707-125">Element</span></span>|<span data-ttu-id="96707-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="96707-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96707-127">ListEntry-Element für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="96707-128">Definiert, wie die Zeilen aus der Liste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="96707-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="96707-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="96707-129">Remarks</span></span>

<span data-ttu-id="96707-130">Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung für eine Sichtdefinition Liste angeben.</span><span class="sxs-lookup"><span data-stu-id="96707-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="96707-131">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="96707-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="96707-132">Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der eine bestimmte Eigenschaft-Wert oder ein Skript ergibt, `true`.</span><span class="sxs-lookup"><span data-stu-id="96707-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="96707-133">Weitere Informationen zu auswahlbedingungen, finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="96707-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="96707-134">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="96707-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="96707-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="96707-135">Example</span></span>

<span data-ttu-id="96707-136">Das folgende Beispiel zeigt, wie die Objekte für eine Listenansicht mit ihren Typnamen .NET definiert wird.</span><span class="sxs-lookup"><span data-stu-id="96707-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="96707-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="96707-137">See Also</span></span>

[<span data-ttu-id="96707-138">ListEntry-Element für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="96707-139">SelectionCondition-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="96707-140">SelectionSetName-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="96707-141">TypeName-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="96707-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="96707-142">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="96707-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="96707-143">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="96707-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="96707-144">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="96707-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
