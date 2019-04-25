---
title: SelectionSetName-Element für EntrySelectedBy für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063972"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="de099-102">Element „SelectionSetName“ für EntrySelectedBy für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="de099-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="de099-103">Gibt einen Satz von .NET-Objekten für den Listeneintrag.</span><span class="sxs-lookup"><span data-stu-id="de099-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="de099-104">Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="de099-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="de099-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) EntrySelectedBy -Element für CustomEntry für Ansicht (Format) SelectionSetName-Element für EntrySelectedBy für CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="de099-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="de099-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="de099-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="de099-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="de099-107">Attributes and Elements</span></span>

<span data-ttu-id="de099-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="de099-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="de099-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="de099-109">Attributes</span></span>

<span data-ttu-id="de099-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="de099-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="de099-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="de099-111">Child Elements</span></span>

<span data-ttu-id="de099-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="de099-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="de099-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="de099-113">Parent Elements</span></span>

|<span data-ttu-id="de099-114">Element</span><span class="sxs-lookup"><span data-stu-id="de099-114">Element</span></span>|<span data-ttu-id="de099-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de099-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="de099-116">EntrySelectedBy-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="de099-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="de099-117">Definiert die .NET-Typen, die dieser benutzerdefinierten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="de099-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="de099-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="de099-118">Text Value</span></span>

<span data-ttu-id="de099-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="de099-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="de099-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="de099-120">Remarks</span></span>

<span data-ttu-id="de099-121">Jeder Eintrag benutzerdefiniertes Steuerelement muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="de099-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="de099-122">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="de099-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="de099-123">Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="de099-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="de099-124">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="de099-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="de099-125">Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="de099-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="de099-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="de099-126">See Also</span></span>

[<span data-ttu-id="de099-127">EntrySelectedBy-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="de099-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="de099-128">Benutzerdefiniertes Steuerelement anzeigen</span><span class="sxs-lookup"><span data-stu-id="de099-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="de099-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="de099-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
