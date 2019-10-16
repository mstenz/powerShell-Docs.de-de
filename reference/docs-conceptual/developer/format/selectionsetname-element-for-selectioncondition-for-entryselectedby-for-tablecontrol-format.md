---
title: Selectionsetname-Element für selectioncondition für entryselectedby für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361919"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="6ac99-102">Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6ac99-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="6ac99-103">Gibt den Satz von .NET-Typen an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="6ac99-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="6ac99-104">Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt, und das Objekt wird mit dieser Definition der Tabellenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6ac99-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="6ac99-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element für tablerowentry (Format) Selectioncondition-Element für entryselectedby für tablerowentry (Format) selectionsetname-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ac99-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ac99-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ac99-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ac99-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6ac99-107">Attributes and Elements</span></span>

<span data-ttu-id="6ac99-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6ac99-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ac99-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6ac99-109">Attributes</span></span>

<span data-ttu-id="6ac99-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6ac99-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ac99-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6ac99-111">Child Elements</span></span>

<span data-ttu-id="6ac99-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="6ac99-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ac99-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6ac99-113">Parent Elements</span></span>

|<span data-ttu-id="6ac99-114">Element</span><span class="sxs-lookup"><span data-stu-id="6ac99-114">Element</span></span>|<span data-ttu-id="6ac99-115">Description</span><span class="sxs-lookup"><span data-stu-id="6ac99-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ac99-116">Selectioncondition-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ac99-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="6ac99-117">Definiert die Bedingung, die für die Verwendung in dieser Definition der Tabellenansicht vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="6ac99-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6ac99-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="6ac99-118">Text Value</span></span>

<span data-ttu-id="6ac99-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="6ac99-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ac99-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6ac99-120">Remarks</span></span>

<span data-ttu-id="6ac99-121">Die Auswahlbedingung kann einen Auswahl Satz oder einen .NET-Typ angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="6ac99-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="6ac99-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6ac99-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="6ac99-123">Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird.</span><span class="sxs-lookup"><span data-stu-id="6ac99-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="6ac99-124">Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6ac99-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="6ac99-125">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6ac99-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ac99-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6ac99-126">See Also</span></span>

[<span data-ttu-id="6ac99-127">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="6ac99-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6ac99-128">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="6ac99-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="6ac99-129">Typname-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ac99-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6ac99-130">Selectioncondition-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="6ac99-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="6ac99-131">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="6ac99-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
