---
title: Selectioncondition-Element für entryselectedby für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368389"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="9cc91-102">Element „SelectionCondition“ für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="9cc91-103">Definiert die Bedingung, die für die Verwendung in dieser Definition der Tabellenansicht vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="9cc91-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="9cc91-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die für eine Tabellendefinition angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="9cc91-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="9cc91-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element für tablerowentry (Format) Selectioncondition-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9cc91-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9cc91-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9cc91-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9cc91-107">Attributes and Elements</span></span>

<span data-ttu-id="9cc91-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des selectioncondition-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9cc91-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9cc91-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9cc91-109">Attributes</span></span>

<span data-ttu-id="9cc91-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9cc91-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9cc91-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9cc91-111">Child Elements</span></span>

|<span data-ttu-id="9cc91-112">Element</span><span class="sxs-lookup"><span data-stu-id="9cc91-112">Element</span></span>|<span data-ttu-id="9cc91-113">Description</span><span class="sxs-lookup"><span data-stu-id="9cc91-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9cc91-114">PropertyName-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="9cc91-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9cc91-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9cc91-116">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9cc91-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9cc91-117">ScriptBlock-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9cc91-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9cc91-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9cc91-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9cc91-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="9cc91-120">Selectionsetname-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9cc91-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9cc91-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9cc91-122">Gibt den Satz von .NET-Typen an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9cc91-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="9cc91-123">Typname-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="9cc91-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9cc91-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9cc91-125">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9cc91-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9cc91-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9cc91-126">Parent Elements</span></span>

|<span data-ttu-id="9cc91-127">Element</span><span class="sxs-lookup"><span data-stu-id="9cc91-127">Element</span></span>|<span data-ttu-id="9cc91-128">Description</span><span class="sxs-lookup"><span data-stu-id="9cc91-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9cc91-129">Entryselectedby-Element für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="9cc91-130">Definiert die .NET-Typen, die diesen Tabelleneintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="9cc91-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9cc91-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9cc91-131">Remarks</span></span>

<span data-ttu-id="9cc91-132">Für jeden Listeneintrag muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="9cc91-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9cc91-133">Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="9cc91-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="9cc91-134">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="9cc91-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="9cc91-135">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="9cc91-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="9cc91-136">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter Definieren von Bedingungen für den Fall, [dass ein Ansichts Eintrag oder Element verwendet wird](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9cc91-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9cc91-137">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="9cc91-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9cc91-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9cc91-138">See Also</span></span>

[<span data-ttu-id="9cc91-139">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="9cc91-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="9cc91-140">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="9cc91-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9cc91-141">Entryselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="9cc91-142">PropertyName-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="9cc91-143">ScriptBlock-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9cc91-144">Selectionsetname-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9cc91-145">Typname-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9cc91-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="9cc91-146">Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="9cc91-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
