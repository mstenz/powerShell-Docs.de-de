---
title: SelectionSetName-Element für EntrySelectedBy für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569c623-2277-49e3-933e-c26262b91cd5
caps.latest.revision: 6
ms.openlocfilehash: 69cd113c444b4e3c5dceabcdfddb439cd1376f6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858856"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="4288e-102">Element „SelectionSetName“ für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4288e-102">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="4288e-103">Gibt einen Satz von .NET-Objekten für den Listeneintrag.</span><span class="sxs-lookup"><span data-stu-id="4288e-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="4288e-104">Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="4288e-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="4288e-105">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4288e-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="4288e-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4288e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4288e-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4288e-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4288e-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="4288e-108">Attributes and Elements</span></span>

<span data-ttu-id="4288e-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="4288e-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4288e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="4288e-110">Attributes</span></span>

<span data-ttu-id="4288e-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="4288e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4288e-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4288e-112">Child Elements</span></span>

<span data-ttu-id="4288e-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="4288e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4288e-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4288e-114">Parent Elements</span></span>

|<span data-ttu-id="4288e-115">Element</span><span class="sxs-lookup"><span data-stu-id="4288e-115">Element</span></span>|<span data-ttu-id="4288e-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4288e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4288e-117">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4288e-117">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="4288e-118">Definiert die .NET-Typen, die dieser benutzerdefinierten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="4288e-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4288e-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="4288e-119">Text Value</span></span>

<span data-ttu-id="4288e-120">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="4288e-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4288e-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4288e-121">Remarks</span></span>

<span data-ttu-id="4288e-122">Jede Definition des benutzerdefinierten Steuerelements muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="4288e-122">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4288e-123">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4288e-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4288e-124">Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4288e-124">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="4288e-125">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4288e-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="4288e-126">Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4288e-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4288e-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4288e-127">See Also</span></span>

[<span data-ttu-id="4288e-128">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4288e-128">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="4288e-129">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="4288e-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4288e-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="4288e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
