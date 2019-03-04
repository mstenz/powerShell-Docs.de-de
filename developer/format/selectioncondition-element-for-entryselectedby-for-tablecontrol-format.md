---
title: SelectionCondition-Element für EntrySelectedBy für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912f3e63-e4d5-41ce-8710-6dfd8c885dc2
caps.latest.revision: 12
ms.openlocfilehash: 2faca6021dc26878869bdd2d35bc4ffc64d0fe7b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861236"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="15f5f-102">Element „SelectionCondition“ für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="15f5f-103">Definiert die Bedingung, die vorhanden sein muss, um für diese Definition der Tabellenansicht zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="15f5f-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="15f5f-104">Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine Tabelle (Definition) angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="15f5f-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="15f5f-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy Konfigurationselement für TableRowEntry (Format) SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15f5f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="15f5f-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15f5f-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="15f5f-107">Attributes and Elements</span></span>

<span data-ttu-id="15f5f-108">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des Elements SelectionCondition.</span><span class="sxs-lookup"><span data-stu-id="15f5f-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15f5f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="15f5f-109">Attributes</span></span>

<span data-ttu-id="15f5f-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="15f5f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15f5f-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="15f5f-111">Child Elements</span></span>

|<span data-ttu-id="15f5f-112">Element</span><span class="sxs-lookup"><span data-stu-id="15f5f-112">Element</span></span>|<span data-ttu-id="15f5f-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="15f5f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15f5f-114">PropertyName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="15f5f-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="15f5f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="15f5f-116">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="15f5f-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="15f5f-117">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="15f5f-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="15f5f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="15f5f-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="15f5f-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="15f5f-120">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="15f5f-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="15f5f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="15f5f-122">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="15f5f-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="15f5f-123">TypeName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="15f5f-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="15f5f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="15f5f-125">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="15f5f-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="15f5f-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="15f5f-126">Parent Elements</span></span>

|<span data-ttu-id="15f5f-127">Element</span><span class="sxs-lookup"><span data-stu-id="15f5f-127">Element</span></span>|<span data-ttu-id="15f5f-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="15f5f-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15f5f-129">EntrySelectedBy-Element für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="15f5f-130">Definiert die .NET-Typen, die diesen Tabelleneintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="15f5f-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="15f5f-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="15f5f-131">Remarks</span></span>

<span data-ttu-id="15f5f-132">Jeder Listeneintrag muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="15f5f-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="15f5f-133">Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="15f5f-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="15f5f-134">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="15f5f-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="15f5f-135">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="15f5f-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="15f5f-136">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="15f5f-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="15f5f-137">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="15f5f-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15f5f-138">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="15f5f-138">See Also</span></span>

[<span data-ttu-id="15f5f-139">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="15f5f-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="15f5f-140">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="15f5f-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="15f5f-141">EntrySelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="15f5f-142">PropertyName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="15f5f-143">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="15f5f-144">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="15f5f-145">TypeName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15f5f-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="15f5f-146">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="15f5f-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
