---
title: Selectionsetname-Element für selectioncondition für entryselectedby für enumerableweiterung (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361989"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="0843e-102">Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0843e-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="0843e-103">Gibt den Satz von .NET-Typen an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0843e-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="0843e-104">Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt.</span><span class="sxs-lookup"><span data-stu-id="0843e-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="0843e-105">Configuration-Element DefaultSettings-Element (Format) enumerableerweiterungs-Element (Format) enumerableerweiterungs-Element (Format) entryselectedby-Element für enumerableexpansion (Format) selectioncondition-Element für entryselectedby Enumerableexpansion (Format) selectionsetname-Element für selectioncondition für entryselectedby für enumerableexpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="0843e-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0843e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0843e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0843e-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0843e-107">Attributes and Elements</span></span>

<span data-ttu-id="0843e-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0843e-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0843e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="0843e-109">Attributes</span></span>

<span data-ttu-id="0843e-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="0843e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0843e-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0843e-111">Child Elements</span></span>

<span data-ttu-id="0843e-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="0843e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0843e-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0843e-113">Parent Elements</span></span>

|<span data-ttu-id="0843e-114">Element</span><span class="sxs-lookup"><span data-stu-id="0843e-114">Element</span></span>|<span data-ttu-id="0843e-115">Description</span><span class="sxs-lookup"><span data-stu-id="0843e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0843e-116">Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="0843e-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="0843e-117">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungs Objekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="0843e-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0843e-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="0843e-118">Text Value</span></span>

<span data-ttu-id="0843e-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="0843e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0843e-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0843e-120">Remarks</span></span>

<span data-ttu-id="0843e-121">Die Auswahlbedingung kann einen Auswahl Satz oder einen .NET-Typ angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="0843e-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="0843e-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0843e-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0843e-123">Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird.</span><span class="sxs-lookup"><span data-stu-id="0843e-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="0843e-124">Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0843e-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0843e-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0843e-125">See Also</span></span>

[<span data-ttu-id="0843e-126">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="0843e-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0843e-127">Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="0843e-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="0843e-128">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="0843e-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
