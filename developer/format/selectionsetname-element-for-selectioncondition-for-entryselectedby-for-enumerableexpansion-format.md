---
title: SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861216"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="c9f15-102">Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="c9f15-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="c9f15-103">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="c9f15-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c9f15-104">Wenn alle Typen in dieser Gruppe vorhanden sind, wird die Bedingung erfüllt.</span><span class="sxs-lookup"><span data-stu-id="c9f15-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="c9f15-105">Element DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansions-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format) SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format) SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="c9f15-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9f15-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9f15-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9f15-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="c9f15-107">Attributes and Elements</span></span>

<span data-ttu-id="c9f15-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="c9f15-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9f15-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c9f15-109">Attributes</span></span>

<span data-ttu-id="c9f15-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="c9f15-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9f15-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c9f15-111">Child Elements</span></span>

<span data-ttu-id="c9f15-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="c9f15-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9f15-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c9f15-113">Parent Elements</span></span>

|<span data-ttu-id="c9f15-114">Element</span><span class="sxs-lookup"><span data-stu-id="c9f15-114">Element</span></span>|<span data-ttu-id="c9f15-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c9f15-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9f15-116">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="c9f15-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="c9f15-117">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="c9f15-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9f15-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="c9f15-118">Text Value</span></span>

<span data-ttu-id="c9f15-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="c9f15-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9f15-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c9f15-120">Remarks</span></span>

<span data-ttu-id="c9f15-121">Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="c9f15-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c9f15-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c9f15-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c9f15-123">Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="c9f15-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c9f15-124">Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c9f15-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9f15-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c9f15-125">See Also</span></span>

[<span data-ttu-id="c9f15-126">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="c9f15-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c9f15-127">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="c9f15-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="c9f15-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9f15-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
