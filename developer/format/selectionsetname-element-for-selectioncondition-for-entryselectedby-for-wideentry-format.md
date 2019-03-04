---
title: SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854126"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="26c76-102">Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26c76-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="26c76-103">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="26c76-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="26c76-104">Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mithilfe dieser Definition der breiten Ansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="26c76-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="26c76-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format) SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26c76-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26c76-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="26c76-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26c76-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="26c76-107">Attributes and Elements</span></span>

<span data-ttu-id="26c76-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="26c76-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="26c76-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="26c76-109">Attributes</span></span>

<span data-ttu-id="26c76-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="26c76-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26c76-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="26c76-111">Child Elements</span></span>

<span data-ttu-id="26c76-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="26c76-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26c76-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="26c76-113">Parent Elements</span></span>

|<span data-ttu-id="26c76-114">Element</span><span class="sxs-lookup"><span data-stu-id="26c76-114">Element</span></span>|<span data-ttu-id="26c76-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="26c76-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26c76-116">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26c76-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="26c76-117">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="26c76-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26c76-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="26c76-118">Text Value</span></span>

<span data-ttu-id="26c76-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="26c76-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="26c76-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="26c76-120">Remarks</span></span>

<span data-ttu-id="26c76-121">Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="26c76-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="26c76-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="26c76-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="26c76-123">Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="26c76-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="26c76-124">Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="26c76-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="26c76-125">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="26c76-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26c76-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="26c76-126">See Also</span></span>

[<span data-ttu-id="26c76-127">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="26c76-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="26c76-128">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="26c76-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="26c76-129">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="26c76-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="26c76-130">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26c76-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="26c76-131">TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="26c76-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="26c76-132">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="26c76-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
