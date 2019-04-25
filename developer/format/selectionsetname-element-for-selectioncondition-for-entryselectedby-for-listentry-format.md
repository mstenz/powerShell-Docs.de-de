---
title: SelectionSetName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae67e47-6c60-4741-8430-78d2cb6067b1
caps.latest.revision: 10
ms.openlocfilehash: ccfc0b772ad3b2d1979c7c832a5153de870035d7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075510"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="b9c96-102">Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b9c96-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="b9c96-103">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="b9c96-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b9c96-104">Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mithilfe dieser Definition der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b9c96-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="b9c96-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für ListEntry (Format) SelectionCondition-Element für EntrySelectedBy für ListEntry (Format) SelectionSetName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b9c96-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9c96-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9c96-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9c96-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b9c96-107">Attributes and Elements</span></span>

<span data-ttu-id="b9c96-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="b9c96-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9c96-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="b9c96-109">Attributes</span></span>

<span data-ttu-id="b9c96-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="b9c96-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9c96-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9c96-111">Child Elements</span></span>

<span data-ttu-id="b9c96-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="b9c96-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9c96-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9c96-113">Parent Elements</span></span>

|<span data-ttu-id="b9c96-114">Element</span><span class="sxs-lookup"><span data-stu-id="b9c96-114">Element</span></span>|<span data-ttu-id="b9c96-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9c96-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9c96-116">SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b9c96-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="b9c96-117">Definiert die Bedingung, die vorhanden sein muss, um diese Definition der Listenansicht zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b9c96-117">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9c96-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="b9c96-118">Text Value</span></span>

<span data-ttu-id="b9c96-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="b9c96-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9c96-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b9c96-120">Remarks</span></span>

<span data-ttu-id="b9c96-121">Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="b9c96-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b9c96-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b9c96-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b9c96-123">Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="b9c96-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b9c96-124">Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b9c96-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b9c96-125">Weitere Informationen zu anderen Komponenten einer Listenansicht, finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b9c96-125">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9c96-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b9c96-126">See Also</span></span>

[<span data-ttu-id="b9c96-127">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="b9c96-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b9c96-128">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="b9c96-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b9c96-129">SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b9c96-129">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="b9c96-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9c96-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
