---
title: Selectionsetname-Element für selectioncondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361859"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="f8001-102">Element „SelectionSetName“ für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f8001-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="f8001-103">Gibt den Satz von .NET-Typen an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="f8001-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="f8001-104">Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt, und das Objekt wird mithilfe dieses Steuer Elements angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f8001-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="f8001-105">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f8001-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="f8001-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format) selectioncondition-Element für entryselectedby für GroupBy (Format) selectionsetname-Element für selectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f8001-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f8001-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8001-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8001-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f8001-108">Attributes and Elements</span></span>

<span data-ttu-id="f8001-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f8001-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8001-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f8001-110">Attributes</span></span>

<span data-ttu-id="f8001-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="f8001-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8001-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f8001-112">Child Elements</span></span>

<span data-ttu-id="f8001-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="f8001-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f8001-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f8001-114">Parent Elements</span></span>

|<span data-ttu-id="f8001-115">Element</span><span class="sxs-lookup"><span data-stu-id="f8001-115">Element</span></span>|<span data-ttu-id="f8001-116">Description</span><span class="sxs-lookup"><span data-stu-id="f8001-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8001-117">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f8001-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="f8001-118">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="f8001-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f8001-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="f8001-119">Text Value</span></span>

<span data-ttu-id="f8001-120">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="f8001-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8001-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f8001-121">Remarks</span></span>

<span data-ttu-id="f8001-122">Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird.</span><span class="sxs-lookup"><span data-stu-id="f8001-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="f8001-123">Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="f8001-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="f8001-124">Wenn dieses Element angegeben ist, können Sie das [tygtame](./typename-element-for-selectioncondition-for-groupby-format.md) -Element nicht angeben.</span><span class="sxs-lookup"><span data-stu-id="f8001-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="f8001-125">Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f8001-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8001-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f8001-126">See Also</span></span>

[<span data-ttu-id="f8001-127">Typname-Element für selectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f8001-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="f8001-128">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f8001-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="f8001-129">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="f8001-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f8001-130">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="f8001-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="f8001-131">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="f8001-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
