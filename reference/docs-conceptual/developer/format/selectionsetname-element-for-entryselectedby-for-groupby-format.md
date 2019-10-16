---
title: Selectionsetname-Element für entryselectedby für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364739"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="076db-102">Element „SelectionSetName“ für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="076db-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="076db-103">Gibt eine Gruppe von .NET-Objekten für den Listeneintrag an.</span><span class="sxs-lookup"><span data-stu-id="076db-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="076db-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Sätze, die für einen Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="076db-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="076db-105">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="076db-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="076db-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format) selectionsetname-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="076db-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="076db-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="076db-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="076db-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="076db-108">Attributes and Elements</span></span>

<span data-ttu-id="076db-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="076db-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="076db-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="076db-110">Attributes</span></span>

<span data-ttu-id="076db-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="076db-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="076db-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="076db-112">Child Elements</span></span>

<span data-ttu-id="076db-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="076db-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="076db-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="076db-114">Parent Elements</span></span>

|<span data-ttu-id="076db-115">Element</span><span class="sxs-lookup"><span data-stu-id="076db-115">Element</span></span>|<span data-ttu-id="076db-116">Description</span><span class="sxs-lookup"><span data-stu-id="076db-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="076db-117">Entryselectedby-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="076db-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="076db-118">Definiert die .NET-Typen, die diesen benutzerdefinierten Eintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="076db-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="076db-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="076db-119">Text Value</span></span>

<span data-ttu-id="076db-120">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="076db-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="076db-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="076db-121">Remarks</span></span>

<span data-ttu-id="076db-122">Für jede benutzerdefinierte Steuerelement Definition muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="076db-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="076db-123">Auswahl Sätze werden in der Regel verwendet, wenn Sie eine Gruppe von Objekten definieren möchten, die in mehreren Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="076db-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="076db-124">Beispielsweise können Sie eine Tabellenansicht und eine Listenansicht für denselben Satz von Objekten erstellen.</span><span class="sxs-lookup"><span data-stu-id="076db-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="076db-125">Weitere Informationen zum Definieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="076db-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="076db-126">Weitere Informationen zu den Komponenten einer benutzerdefinierten Steuerelement Ansicht finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="076db-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="076db-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="076db-127">See Also</span></span>

[<span data-ttu-id="076db-128">Entryselectedby-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="076db-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="076db-129">Erstellen benutzerdefinierter Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="076db-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="076db-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="076db-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
