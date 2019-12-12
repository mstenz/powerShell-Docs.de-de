---
title: Selectionsetname-Element für entryselectedby für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361999"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="6b491-102">Element „SelectionSetName“ für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6b491-102">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="6b491-103">Gibt eine Gruppe von .NET-Objekten für den Listeneintrag an.</span><span class="sxs-lookup"><span data-stu-id="6b491-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="6b491-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Sätze, die für einen Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="6b491-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="6b491-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) entryselectedby-Element für ListEntry (Format) selectionsetname-Element für Entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6b491-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b491-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b491-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b491-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6b491-107">Attributes and Elements</span></span>

<span data-ttu-id="6b491-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6b491-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b491-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6b491-109">Attributes</span></span>

<span data-ttu-id="6b491-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6b491-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b491-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6b491-111">Child Elements</span></span>

<span data-ttu-id="6b491-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="6b491-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6b491-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6b491-113">Parent Elements</span></span>

|<span data-ttu-id="6b491-114">Element</span><span class="sxs-lookup"><span data-stu-id="6b491-114">Element</span></span>|<span data-ttu-id="6b491-115">Description</span><span class="sxs-lookup"><span data-stu-id="6b491-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b491-116">Entryselectedby-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6b491-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="6b491-117">Definiert die .NET-Typen, die diesen Listeneintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="6b491-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6b491-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="6b491-118">Text Value</span></span>

<span data-ttu-id="6b491-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="6b491-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b491-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6b491-120">Remarks</span></span>

<span data-ttu-id="6b491-121">Für jeden Listeneintrag muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="6b491-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="6b491-122">Auswahl Sätze werden in der Regel verwendet, wenn Sie eine Gruppe von Objekten definieren möchten, die in mehreren Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6b491-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="6b491-123">Beispielsweise können Sie eine Tabellenansicht und eine Listenansicht für denselben Satz von Objekten erstellen.</span><span class="sxs-lookup"><span data-stu-id="6b491-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="6b491-124">Weitere Informationen zum Definieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen für eine Sicht](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6b491-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="6b491-125">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6b491-125">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6b491-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6b491-126">Example</span></span>

<span data-ttu-id="6b491-127">Im folgenden Beispiel wird gezeigt, wie Sie einen Auswahl Satz für einen Eintrag einer Listenansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="6b491-127">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="6b491-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6b491-128">See Also</span></span>

[<span data-ttu-id="6b491-129">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="6b491-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6b491-130">Entryselectedby-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6b491-130">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="6b491-131">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="6b491-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
