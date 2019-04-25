---
title: SelectionSetName-Element für SelectionCondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063765"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="9ff71-102">Element „SelectionSetName“ für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ff71-102">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="9ff71-103">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="9ff71-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="9ff71-104">Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt mit diesem Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9ff71-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="9ff71-105">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9ff71-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9ff71-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionCondition-Element für EntrySelectedBy für GroupBy (Format) SelectionSetName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ff71-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ff71-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ff71-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ff71-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9ff71-108">Attributes and Elements</span></span>

<span data-ttu-id="9ff71-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="9ff71-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ff71-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="9ff71-110">Attributes</span></span>

<span data-ttu-id="9ff71-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="9ff71-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ff71-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9ff71-112">Child Elements</span></span>

<span data-ttu-id="9ff71-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="9ff71-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9ff71-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9ff71-114">Parent Elements</span></span>

|<span data-ttu-id="9ff71-115">Element</span><span class="sxs-lookup"><span data-stu-id="9ff71-115">Element</span></span>|<span data-ttu-id="9ff71-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ff71-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ff71-117">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ff71-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="9ff71-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9ff71-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9ff71-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="9ff71-119">Text Value</span></span>

<span data-ttu-id="9ff71-120">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="9ff71-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ff71-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9ff71-121">Remarks</span></span>

<span data-ttu-id="9ff71-122">Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="9ff71-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="9ff71-123">Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9ff71-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="9ff71-124">Wenn dieses Element angegeben ist, können Sie nicht angeben der [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="9ff71-124">When this element is specified, you cannot specify the [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) element.</span></span> <span data-ttu-id="9ff71-125">Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9ff71-125">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ff71-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9ff71-126">See Also</span></span>

[<span data-ttu-id="9ff71-127">TypeName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ff71-127">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="9ff71-128">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ff71-128">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="9ff71-129">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="9ff71-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9ff71-130">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="9ff71-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9ff71-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ff71-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
