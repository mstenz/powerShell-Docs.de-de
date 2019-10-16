---
title: Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a13a429c-a31b-4e29-828c-c0c0917b5415
caps.latest.revision: 11
ms.openlocfilehash: baea89e4b259611dfa45b6bcf94fa0bf2df6b9de
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368409"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="0c464-102">Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c464-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="0c464-103">Gibt den Satz von .NET-Typen an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0c464-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="0c464-104">Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt, und das Objekt wird mit dieser Definition der breiten Ansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0c464-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the wide view.</span></span>

<span data-ttu-id="0c464-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) entryselectedby-Element für wideentry (Format) selectioncondition-Element für Entryselectedby für wideentry (Format) selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c464-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c464-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c464-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c464-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0c464-107">Attributes and Elements</span></span>

<span data-ttu-id="0c464-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0c464-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0c464-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="0c464-109">Attributes</span></span>

<span data-ttu-id="0c464-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="0c464-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0c464-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0c464-111">Child Elements</span></span>

<span data-ttu-id="0c464-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="0c464-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0c464-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0c464-113">Parent Elements</span></span>

|<span data-ttu-id="0c464-114">Element</span><span class="sxs-lookup"><span data-stu-id="0c464-114">Element</span></span>|<span data-ttu-id="0c464-115">Description</span><span class="sxs-lookup"><span data-stu-id="0c464-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0c464-116">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c464-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0c464-117">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="0c464-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0c464-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="0c464-118">Text Value</span></span>

<span data-ttu-id="0c464-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="0c464-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c464-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0c464-120">Remarks</span></span>

<span data-ttu-id="0c464-121">Die Auswahlbedingung kann einen Auswahl Satz oder einen .NET-Typ angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="0c464-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="0c464-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0c464-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0c464-123">Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird.</span><span class="sxs-lookup"><span data-stu-id="0c464-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="0c464-124">Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0c464-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="0c464-125">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0c464-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c464-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0c464-126">See Also</span></span>

[<span data-ttu-id="0c464-127">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="0c464-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0c464-128">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="0c464-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0c464-129">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="0c464-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0c464-130">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c464-130">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0c464-131">Typname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="0c464-131">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0c464-132">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="0c464-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
