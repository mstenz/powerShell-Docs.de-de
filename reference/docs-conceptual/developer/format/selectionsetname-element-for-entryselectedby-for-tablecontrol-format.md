---
title: Selectionsetname-Element für entryselectedby für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368319"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="cb744-102">Element „SelectionSetName“ für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cb744-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="cb744-103">Gibt einen Satz von .NET-Typen an, der diesen Eintrag der Tabellenansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="cb744-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="cb744-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Sätze, die für einen Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="cb744-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="cb744-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element (Format) selectionsetname-Element für Entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cb744-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb744-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb744-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb744-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="cb744-107">Attributes and Elements</span></span>

<span data-ttu-id="cb744-108">In den folgenden Abschnitten werden die Attribute, untergeordneten und übergeordneten Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="cb744-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb744-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="cb744-109">Attributes</span></span>

<span data-ttu-id="cb744-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="cb744-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb744-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cb744-111">Child Elements</span></span>

<span data-ttu-id="cb744-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="cb744-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cb744-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cb744-113">Parent Elements</span></span>

|<span data-ttu-id="cb744-114">Element</span><span class="sxs-lookup"><span data-stu-id="cb744-114">Element</span></span>|<span data-ttu-id="cb744-115">Description</span><span class="sxs-lookup"><span data-stu-id="cb744-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb744-116">Entryselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cb744-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="cb744-117">Definiert die .NET-Typen, die diesen Eintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="cb744-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cb744-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="cb744-118">Text Value</span></span>

<span data-ttu-id="cb744-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="cb744-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb744-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cb744-120">Remarks</span></span>

<span data-ttu-id="cb744-121">Auswahl Sätze werden in der Regel verwendet, wenn Sie eine Gruppe von Objekten definieren möchten, die in mehreren Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cb744-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="cb744-122">Beispielsweise können Sie eine Tabellenansicht und eine Listenansicht für denselben Satz von Objekten erstellen.</span><span class="sxs-lookup"><span data-stu-id="cb744-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="cb744-123">Weitere Informationen zum Definieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen für eine Sicht](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="cb744-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="cb744-124">Wenn Sie einen Auswahl Satz für einen Eintrag angeben, können Sie keinen Typnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="cb744-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="cb744-125">Weitere Informationen zum Angeben eines .net-Typs finden Sie unter [Typname-Element für entryselectedby für tablerowentry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="cb744-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="cb744-126">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="cb744-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb744-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cb744-127">See Also</span></span>

[<span data-ttu-id="cb744-128">Entryselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cb744-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="cb744-129">Definieren von Objekt Sätzen für eine Sicht</span><span class="sxs-lookup"><span data-stu-id="cb744-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cb744-130">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="cb744-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cb744-131">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="cb744-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
