---
title: SelectionCondition-Element für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735090"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d7139-102">Element „SelectionCondition“ für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-102">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d7139-103">Definiert die Bedingung, die vorhanden sein muss, um diese Definition der Listenansicht zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="d7139-103">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="d7139-104">Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine Listendefinition angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="d7139-104">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="d7139-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für ListEntry (Format) SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7139-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7139-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7139-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d7139-107">Attributes and Elements</span></span>

<span data-ttu-id="d7139-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="d7139-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7139-109">Attribute</span><span class="sxs-lookup"><span data-stu-id="d7139-109">Attributes</span></span>

<span data-ttu-id="d7139-110">Keine</span><span class="sxs-lookup"><span data-stu-id="d7139-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7139-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d7139-111">Child Elements</span></span>

|<span data-ttu-id="d7139-112">Element</span><span class="sxs-lookup"><span data-stu-id="d7139-112">Element</span></span>|<span data-ttu-id="d7139-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7139-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7139-114">PropertyName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-114">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d7139-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d7139-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d7139-116">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="d7139-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d7139-117">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d7139-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d7139-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d7139-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="d7139-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="d7139-120">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="d7139-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d7139-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d7139-122">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="d7139-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="d7139-123">TypeName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-123">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d7139-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d7139-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d7139-125">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="d7139-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d7139-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d7139-126">Parent Elements</span></span>

|<span data-ttu-id="d7139-127">Element</span><span class="sxs-lookup"><span data-stu-id="d7139-127">Element</span></span>|<span data-ttu-id="d7139-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7139-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7139-129">EntrySelectedBy-Element für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d7139-130">Definiert die .NET-Typen, die diesen Tabelleneintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="d7139-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d7139-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d7139-131">Remarks</span></span>

<span data-ttu-id="d7139-132">lWhen, die Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="d7139-132">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="d7139-133">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="d7139-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="d7139-134">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="d7139-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="d7139-135">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d7139-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d7139-136">Weitere Informationen zu anderen Komponenten einer Listenansicht, finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d7139-136">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7139-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d7139-137">See Also</span></span>

[<span data-ttu-id="d7139-138">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="d7139-138">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d7139-139">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="d7139-139">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d7139-140">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-140">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="d7139-141">SelectionSetName-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-141">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d7139-142">TypeName-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="d7139-142">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="d7139-143">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7139-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
