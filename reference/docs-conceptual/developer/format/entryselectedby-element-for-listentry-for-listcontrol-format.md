---
title: Entryselectedby-Element für ListEntry für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363829"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="2bdc7-102">Element „EntrySelectedBy“ für ListEntry für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="2bdc7-103">Definiert die .NET-Typen, die diese Listen Ansichts Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="2bdc7-104">In den meisten Fällen ist nur eine Definition für eine Listenansicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="2bdc7-105">Sie können jedoch mehrere Definitionen für die Listenansicht bereitstellen, wenn Sie die gleiche Listenansicht verwenden möchten, um unterschiedliche Daten für unterschiedliche Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="2bdc7-106">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListEntry für ListControl (Format) entryselectedby-Element für ListEntry für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2bdc7-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2bdc7-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2bdc7-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2bdc7-108">Attributes and Elements</span></span>

<span data-ttu-id="2bdc7-109">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2bdc7-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2bdc7-110">Attributes</span></span>

<span data-ttu-id="2bdc7-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2bdc7-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2bdc7-112">Child Elements</span></span>

|<span data-ttu-id="2bdc7-113">Element</span><span class="sxs-lookup"><span data-stu-id="2bdc7-113">Element</span></span>|<span data-ttu-id="2bdc7-114">Description</span><span class="sxs-lookup"><span data-stu-id="2bdc7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bdc7-115">Selectioncondition-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2bdc7-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2bdc7-117">Definiert die Bedingung, die für die Verwendung dieser Listen Ansichts Definition vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="2bdc7-118">Selectionsetname-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2bdc7-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2bdc7-120">Gibt eine Gruppe von .NET-Typen an, die diese Listen Ansichts Definition verwenden.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="2bdc7-121">Tyname-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2bdc7-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2bdc7-123">Gibt einen .NET-Typ an, der diese Listen Ansichts Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2bdc7-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2bdc7-124">Parent Elements</span></span>

|<span data-ttu-id="2bdc7-125">Element</span><span class="sxs-lookup"><span data-stu-id="2bdc7-125">Element</span></span>|<span data-ttu-id="2bdc7-126">Description</span><span class="sxs-lookup"><span data-stu-id="2bdc7-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2bdc7-127">ListEntry-Element für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="2bdc7-128">Definiert, wie die Zeilen der Liste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2bdc7-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2bdc7-129">Remarks</span></span>

<span data-ttu-id="2bdc7-130">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine Listen Ansichts Definition angeben.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="2bdc7-131">Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="2bdc7-132">Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt über eine bestimmte Eigenschaft verfügt oder ein bestimmter Eigenschafts Wert oder Skript als `true`ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="2bdc7-133">Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für den Fall, dass Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2bdc7-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2bdc7-134">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2bdc7-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2bdc7-135">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2bdc7-135">Example</span></span>

<span data-ttu-id="2bdc7-136">Im folgenden Beispiel wird gezeigt, wie die-Objekte für eine Listenansicht mithilfe Ihres .net-Typnamens definiert werden.</span><span class="sxs-lookup"><span data-stu-id="2bdc7-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="2bdc7-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2bdc7-137">See Also</span></span>

[<span data-ttu-id="2bdc7-138">ListEntry-Element für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="2bdc7-139">Selectioncondition-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2bdc7-140">Selectionsetname-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2bdc7-141">Tyname-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="2bdc7-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2bdc7-142">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="2bdc7-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2bdc7-143">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="2bdc7-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2bdc7-144">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="2bdc7-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
