---
title: Selectionsetname-Element für selectioncondition für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52b05a9-762e-4f1c-ad57-9d1710149722
caps.latest.revision: 10
ms.openlocfilehash: 25d46665ca5df3ddf49af5718d513b84c77988c8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368269"
---
# <a name="selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="8f242-102">Element „SelectionSetName“ für SelectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8f242-102">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="8f242-103">Gibt den Satz von .NET-Typen an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="8f242-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="8f242-104">Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt, und das Objekt wird mithilfe dieses Steuer Elements angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8f242-104">When any of the types in this set are present, the condition is met and the object is displayed using this control.</span></span> <span data-ttu-id="8f242-105">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f242-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="8f242-106">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries for View (Format) entryselectedby Element für customentry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8f242-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f242-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f242-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f242-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8f242-108">Attributes and Elements</span></span>

<span data-ttu-id="8f242-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8f242-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f242-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="8f242-110">Attributes</span></span>

<span data-ttu-id="8f242-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="8f242-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f242-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8f242-112">Child Elements</span></span>

<span data-ttu-id="8f242-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="8f242-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8f242-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8f242-114">Parent Elements</span></span>

|<span data-ttu-id="8f242-115">Element</span><span class="sxs-lookup"><span data-stu-id="8f242-115">Element</span></span>|<span data-ttu-id="8f242-116">Description</span><span class="sxs-lookup"><span data-stu-id="8f242-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f242-117">Selectioncondition-Element für entryselectedby für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8f242-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="8f242-118">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="8f242-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8f242-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="8f242-119">Text Value</span></span>

<span data-ttu-id="8f242-120">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="8f242-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f242-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8f242-121">Remarks</span></span>

<span data-ttu-id="8f242-122">Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird.</span><span class="sxs-lookup"><span data-stu-id="8f242-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="8f242-123">Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="8f242-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="8f242-124">Die Auswahlbedingung kann einen Auswahl Satz oder einen .NET-Typ angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="8f242-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="8f242-125">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8f242-125">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8f242-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8f242-126">See Also</span></span>

[<span data-ttu-id="8f242-127">Selectioncondition-Element für entryselectedby für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8f242-127">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="8f242-128">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="8f242-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8f242-129">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="8f242-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="8f242-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="8f242-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
