---
title: SelectionSetName-Element für SelectionCondition für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075578"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="92fb1-102">Element „SelectionSetName“ für SelectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="92fb1-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="92fb1-103">Gibt den Satz von .NET-Typen, die die Bedingung auslösen.</span><span class="sxs-lookup"><span data-stu-id="92fb1-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="92fb1-104">Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mit diesem Steuerelement angezeigt.</span><span class="sxs-lookup"><span data-stu-id="92fb1-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="92fb1-105">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="92fb1-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="92fb1-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) EntrySelectedBy -Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="92fb1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92fb1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="92fb1-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92fb1-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="92fb1-108">Attributes and Elements</span></span>

<span data-ttu-id="92fb1-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="92fb1-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92fb1-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="92fb1-110">Attributes</span></span>

<span data-ttu-id="92fb1-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="92fb1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92fb1-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="92fb1-112">Child Elements</span></span>

<span data-ttu-id="92fb1-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="92fb1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92fb1-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="92fb1-114">Parent Elements</span></span>

|<span data-ttu-id="92fb1-115">Element</span><span class="sxs-lookup"><span data-stu-id="92fb1-115">Element</span></span>|<span data-ttu-id="92fb1-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="92fb1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92fb1-117">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="92fb1-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="92fb1-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="92fb1-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92fb1-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="92fb1-119">Text Value</span></span>

<span data-ttu-id="92fb1-120">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="92fb1-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="92fb1-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="92fb1-121">Remarks</span></span>

<span data-ttu-id="92fb1-122">Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="92fb1-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="92fb1-123">Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="92fb1-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="92fb1-124">Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="92fb1-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="92fb1-125">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="92fb1-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92fb1-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="92fb1-126">See Also</span></span>

[<span data-ttu-id="92fb1-127">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="92fb1-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="92fb1-128">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="92fb1-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="92fb1-129">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="92fb1-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="92fb1-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="92fb1-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
