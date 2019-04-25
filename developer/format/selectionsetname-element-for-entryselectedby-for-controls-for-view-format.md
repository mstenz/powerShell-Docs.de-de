---
title: SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075646"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="e62b8-102">Element „SelectionSetName“ für EntrySelectedBy für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="e62b8-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="e62b8-103">Gibt einen Satz von .NET-Typen, die dieser Definition des Steuerelements verwenden.</span><span class="sxs-lookup"><span data-stu-id="e62b8-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="e62b8-104">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e62b8-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e62b8-105">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für Steuerelemente für Ansicht (Format) SelectionSetName-Element für EntrySelectedBy für Steuerelemente für Ansicht) -Format)</span><span class="sxs-lookup"><span data-stu-id="e62b8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e62b8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e62b8-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e62b8-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e62b8-107">Attributes and Elements</span></span>

<span data-ttu-id="e62b8-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="e62b8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e62b8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e62b8-109">Attributes</span></span>

<span data-ttu-id="e62b8-110">Keine</span><span class="sxs-lookup"><span data-stu-id="e62b8-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e62b8-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e62b8-111">Child Elements</span></span>

<span data-ttu-id="e62b8-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="e62b8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e62b8-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e62b8-113">Parent Elements</span></span>

|<span data-ttu-id="e62b8-114">Element</span><span class="sxs-lookup"><span data-stu-id="e62b8-114">Element</span></span>|<span data-ttu-id="e62b8-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e62b8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e62b8-116">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e62b8-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="e62b8-117">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e62b8-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e62b8-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="e62b8-118">Text Value</span></span>

<span data-ttu-id="e62b8-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="e62b8-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e62b8-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e62b8-120">Remarks</span></span>

<span data-ttu-id="e62b8-121">Jedes Steuerelement muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e62b8-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e62b8-122">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e62b8-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e62b8-123">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e62b8-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e62b8-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e62b8-124">See Also</span></span>

[<span data-ttu-id="e62b8-125">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="e62b8-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="e62b8-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="e62b8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
