---
title: SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063886"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="d516d-102">Element „SelectionSetName“ für SelectionCondition für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="d516d-102">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="d516d-103">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="d516d-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="d516d-104">Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mit diesem Steuerelement angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d516d-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="d516d-105">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d516d-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="d516d-106">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für Steuerelemente für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für Steuerelemente für Ansicht) SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="d516d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d516d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d516d-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d516d-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d516d-108">Attributes and Elements</span></span>

<span data-ttu-id="d516d-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="d516d-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d516d-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d516d-110">Attributes</span></span>

<span data-ttu-id="d516d-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="d516d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d516d-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d516d-112">Child Elements</span></span>

<span data-ttu-id="d516d-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="d516d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d516d-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d516d-114">Parent Elements</span></span>

|<span data-ttu-id="d516d-115">Element</span><span class="sxs-lookup"><span data-stu-id="d516d-115">Element</span></span>|<span data-ttu-id="d516d-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d516d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d516d-117">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d516d-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="d516d-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d516d-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d516d-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="d516d-119">Text Value</span></span>

<span data-ttu-id="d516d-120">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="d516d-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d516d-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d516d-121">Remarks</span></span>

<span data-ttu-id="d516d-122">Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="d516d-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="d516d-123">Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d516d-123">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d516d-124">Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="d516d-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="d516d-125">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d516d-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d516d-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d516d-126">See Also</span></span>

[<span data-ttu-id="d516d-127">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d516d-127">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="d516d-128">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="d516d-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d516d-129">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="d516d-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d516d-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d516d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
