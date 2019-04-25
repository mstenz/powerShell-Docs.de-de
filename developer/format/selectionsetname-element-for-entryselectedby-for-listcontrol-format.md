---
title: SelectionSetName-Element für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075561"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="344c7-102">Element „SelectionSetName“ für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="344c7-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="344c7-103">Gibt einen Satz von .NET-Objekten für den Listeneintrag.</span><span class="sxs-lookup"><span data-stu-id="344c7-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="344c7-104">Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="344c7-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="344c7-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für ListEntry (Format) SelectionSetName-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="344c7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="344c7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="344c7-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="344c7-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="344c7-107">Attributes and Elements</span></span>

<span data-ttu-id="344c7-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="344c7-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="344c7-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="344c7-109">Attributes</span></span>

<span data-ttu-id="344c7-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="344c7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="344c7-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="344c7-111">Child Elements</span></span>

<span data-ttu-id="344c7-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="344c7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="344c7-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="344c7-113">Parent Elements</span></span>

|<span data-ttu-id="344c7-114">Element</span><span class="sxs-lookup"><span data-stu-id="344c7-114">Element</span></span>|<span data-ttu-id="344c7-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="344c7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="344c7-116">EntrySelectedBy-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="344c7-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="344c7-117">Definiert die .NET-Typen, die diesen Eintrag der Liste oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="344c7-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="344c7-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="344c7-118">Text Value</span></span>

<span data-ttu-id="344c7-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="344c7-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="344c7-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="344c7-120">Remarks</span></span>

<span data-ttu-id="344c7-121">Jeder Listeneintrag muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="344c7-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="344c7-122">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="344c7-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="344c7-123">Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="344c7-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="344c7-124">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren Sätze von Objekten, die für eine Sicht](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="344c7-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="344c7-125">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="344c7-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="344c7-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="344c7-126">Example</span></span>

<span data-ttu-id="344c7-127">Das folgende Beispiel zeigt, wie Sie eine Auswahl, legen Sie für einen Eintrag in einer Listenansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="344c7-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="344c7-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="344c7-128">See Also</span></span>

[<span data-ttu-id="344c7-129">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="344c7-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="344c7-130">EntrySelectedBy-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="344c7-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="344c7-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="344c7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
