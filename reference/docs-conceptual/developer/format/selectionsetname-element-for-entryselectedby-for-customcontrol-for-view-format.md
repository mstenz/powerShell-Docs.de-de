---
title: Selectionsetname-Element für entryselectedby für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364749"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="acb35-102">Element „SelectionSetName“ für EntrySelectedBy für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="acb35-102">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="acb35-103">Gibt eine Gruppe von .NET-Objekten für den Listeneintrag an.</span><span class="sxs-lookup"><span data-stu-id="acb35-103">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="acb35-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Sätze, die für einen Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="acb35-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="acb35-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries for View (Format) entryselectedby Element für customentry für View (Format) selectionsetname-Element für entryselectedby für customentry (Format)</span><span class="sxs-lookup"><span data-stu-id="acb35-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="acb35-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="acb35-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="acb35-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="acb35-107">Attributes and Elements</span></span>

<span data-ttu-id="acb35-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="acb35-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="acb35-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="acb35-109">Attributes</span></span>

<span data-ttu-id="acb35-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="acb35-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="acb35-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="acb35-111">Child Elements</span></span>

<span data-ttu-id="acb35-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="acb35-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="acb35-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="acb35-113">Parent Elements</span></span>

|<span data-ttu-id="acb35-114">Element</span><span class="sxs-lookup"><span data-stu-id="acb35-114">Element</span></span>|<span data-ttu-id="acb35-115">Description</span><span class="sxs-lookup"><span data-stu-id="acb35-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="acb35-116">Entryselectedby-Element für customentry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="acb35-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="acb35-117">Definiert die .NET-Typen, die diesen benutzerdefinierten Eintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="acb35-117">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="acb35-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="acb35-118">Text Value</span></span>

<span data-ttu-id="acb35-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="acb35-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="acb35-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="acb35-120">Remarks</span></span>

<span data-ttu-id="acb35-121">Jeder benutzerdefinierte Steuerelement Eintrag muss mindestens einen Typnamen, einen Auswahl Satz oder eine Auswahlbedingung definieren.</span><span class="sxs-lookup"><span data-stu-id="acb35-121">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="acb35-122">Auswahl Sätze werden in der Regel verwendet, wenn Sie eine Gruppe von Objekten definieren möchten, die in mehreren Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="acb35-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="acb35-123">Beispielsweise können Sie eine Tabellenansicht und eine Listenansicht für denselben Satz von Objekten erstellen.</span><span class="sxs-lookup"><span data-stu-id="acb35-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="acb35-124">Weitere Informationen zum Definieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="acb35-124">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="acb35-125">Weitere Informationen zu den Komponenten einer benutzerdefinierten Steuerelement Ansicht finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="acb35-125">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="acb35-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="acb35-126">See Also</span></span>

[<span data-ttu-id="acb35-127">Entryselectedby-Element für customentry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="acb35-127">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="acb35-128">Benutzerdefinierte Steuerelement Ansicht</span><span class="sxs-lookup"><span data-stu-id="acb35-128">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="acb35-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="acb35-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
