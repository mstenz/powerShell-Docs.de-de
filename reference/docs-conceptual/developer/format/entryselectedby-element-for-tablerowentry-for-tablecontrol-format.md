---
title: Entryselectedby-Element für tablerowentry für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363339"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="d9bcd-102">Element „EntrySelectedBy“ für TableRowEntry für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="d9bcd-103">Definiert die .NET-Typen, die diese Definition der Tabellen Sicht verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="d9bcd-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9bcd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9bcd-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9bcd-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d9bcd-106">Attributes and Elements</span></span>

<span data-ttu-id="d9bcd-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9bcd-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="d9bcd-108">Attributes</span></span>

<span data-ttu-id="d9bcd-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9bcd-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d9bcd-110">Child Elements</span></span>

|<span data-ttu-id="d9bcd-111">Element</span><span class="sxs-lookup"><span data-stu-id="d9bcd-111">Element</span></span>|<span data-ttu-id="d9bcd-112">Description</span><span class="sxs-lookup"><span data-stu-id="d9bcd-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9bcd-113">Selectioncondition-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d9bcd-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-114">Optional element.</span></span><br /><br /> <span data-ttu-id="d9bcd-115">Definiert die Bedingung, die vorhanden sein muss, damit diese Tabellen Sicht Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="d9bcd-116">Selectionsetname-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d9bcd-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="d9bcd-118">Gibt eine Gruppe von .NET-Typen an, die diese Tabellen Sicht Definition verwenden.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="d9bcd-119">Tyname-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d9bcd-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="d9bcd-121">Gibt einen .NET-Typ an, der diese Tabellen Sicht Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d9bcd-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d9bcd-122">Parent Elements</span></span>

|<span data-ttu-id="d9bcd-123">Element</span><span class="sxs-lookup"><span data-stu-id="d9bcd-123">Element</span></span>|<span data-ttu-id="d9bcd-124">Description</span><span class="sxs-lookup"><span data-stu-id="d9bcd-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9bcd-125">Tablerowentry-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="d9bcd-126">Definiert die Daten, die in einer Zeile der Tabelle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9bcd-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d9bcd-127">Remarks</span></span>

<span data-ttu-id="d9bcd-128">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine Tabellen Sicht Definition angeben.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="d9bcd-129">Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="d9bcd-130">Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt über eine bestimmte Eigenschaft verfügt oder ein bestimmter Eigenschafts Wert oder Skript zu `true` ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="d9bcd-131">Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d9bcd-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d9bcd-132">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d9bcd-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d9bcd-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d9bcd-133">Example</span></span>

<span data-ttu-id="d9bcd-134">Das folgende Beispiel zeigt ein `TableRowEntry`-Element, das verwendet wird, um die Eigenschaften des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d9bcd-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="d9bcd-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d9bcd-135">See Also</span></span>

[<span data-ttu-id="d9bcd-136">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="d9bcd-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d9bcd-137">Selectioncondition-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d9bcd-138">Selectionsetname-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d9bcd-139">Tablerowentry-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="d9bcd-140">Tyname-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d9bcd-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d9bcd-141">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="d9bcd-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
