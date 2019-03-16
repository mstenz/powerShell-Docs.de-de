---
title: EntrySelectedBy-Element für TableRowEntry für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058758"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="7c2a1-102">Element „EntrySelectedBy“ für TableRowEntry für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="7c2a1-103">Definiert .NET Typen, die dieser Definition der Tabellenansicht oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="7c2a1-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7c2a1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7c2a1-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7c2a1-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7c2a1-106">Attributes and Elements</span></span>

<span data-ttu-id="7c2a1-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7c2a1-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7c2a1-108">Attributes</span></span>

<span data-ttu-id="7c2a1-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7c2a1-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7c2a1-110">Child Elements</span></span>

|<span data-ttu-id="7c2a1-111">Element</span><span class="sxs-lookup"><span data-stu-id="7c2a1-111">Element</span></span>|<span data-ttu-id="7c2a1-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7c2a1-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c2a1-113">SelectionCondition-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="7c2a1-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7c2a1-115">Definiert die Bedingung, die für diese Tabelle View Definition zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="7c2a1-116">SelectionSetName-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="7c2a1-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7c2a1-118">Gibt einen Satz von .NET-Typen, die diese Tabelle (Definition) Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="7c2a1-119">TypeName-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="7c2a1-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7c2a1-121">Gibt einen .NET-Typ, der dieser Tabelle anzeigen (Definition) verwendet.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c2a1-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7c2a1-122">Parent Elements</span></span>

|<span data-ttu-id="7c2a1-123">Element</span><span class="sxs-lookup"><span data-stu-id="7c2a1-123">Element</span></span>|<span data-ttu-id="7c2a1-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7c2a1-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7c2a1-125">TableRowEntry-Element für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="7c2a1-126">Definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7c2a1-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7c2a1-127">Remarks</span></span>

<span data-ttu-id="7c2a1-128">Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung für eine Tabelle (Definition) Ansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="7c2a1-129">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="7c2a1-130">Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der eine bestimmte Eigenschaft-Wert oder ein Skript ergibt, `true`.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="7c2a1-131">Weitere Informationen zu auswahlbedingungen, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a1-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7c2a1-132">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7c2a1-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7c2a1-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7c2a1-133">Example</span></span>

<span data-ttu-id="7c2a1-134">Das folgende Beispiel zeigt eine `TableRowEntry` -Element, das verwendet wird, zum Anzeigen der Eigenschaften der ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="7c2a1-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7c2a1-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7c2a1-135">See Also</span></span>

[<span data-ttu-id="7c2a1-136">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="7c2a1-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7c2a1-137">SelectionCondition-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7c2a1-138">SelectionSetName-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7c2a1-139">TableRowEntry-Element für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="7c2a1-140">TypeName-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7c2a1-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7c2a1-141">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="7c2a1-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
