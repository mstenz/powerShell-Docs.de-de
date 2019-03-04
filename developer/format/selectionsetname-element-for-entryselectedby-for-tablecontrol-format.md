---
title: SelectionSetName-Element für EntrySelectedBy für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5dd0bd5d-f206-4cc6-a0f8-70700ee2c4b7
caps.latest.revision: 8
ms.openlocfilehash: 819906127e81355c45103ede85ef3608e1c1cfeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856096"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ad4a2-102">Element „SelectionSetName“ für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4a2-102">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ad4a2-103">Gibt an, der ein Satz von .NET die Verwendung von Typen, diesen Eintrag der Tabellenansicht.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-103">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="ad4a2-104">Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-104">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="ad4a2-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy-Element (Format) SelectionSetName Konfigurationselement für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4a2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ad4a2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad4a2-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ad4a2-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ad4a2-107">Attributes and Elements</span></span>

<span data-ttu-id="ad4a2-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ad4a2-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ad4a2-109">Attributes</span></span>

<span data-ttu-id="ad4a2-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ad4a2-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ad4a2-111">Child Elements</span></span>

<span data-ttu-id="ad4a2-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ad4a2-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ad4a2-113">Parent Elements</span></span>

|<span data-ttu-id="ad4a2-114">Element</span><span class="sxs-lookup"><span data-stu-id="ad4a2-114">Element</span></span>|<span data-ttu-id="ad4a2-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ad4a2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ad4a2-116">EntrySelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4a2-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ad4a2-117">Definiert die .NET-Typen, die diesen Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ad4a2-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="ad4a2-118">Text Value</span></span>

<span data-ttu-id="ad4a2-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad4a2-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ad4a2-120">Remarks</span></span>

<span data-ttu-id="ad4a2-121">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ad4a2-122">Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="ad4a2-123">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren Sätze von Objekten, die für eine Sicht](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ad4a2-123">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ad4a2-124">Wenn Sie eine Auswahl, legen Sie für einen Eintrag angeben, können nicht Sie einen Namen angeben.</span><span class="sxs-lookup"><span data-stu-id="ad4a2-124">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="ad4a2-125">Weitere Informationen zur Vorgehensweise beim Angeben eines .NET-Typs angesprochen, finden Sie unter [TypeName-Element für EntrySelectedBy für TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="ad4a2-125">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="ad4a2-126">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ad4a2-126">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad4a2-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ad4a2-127">See Also</span></span>

[<span data-ttu-id="ad4a2-128">EntrySelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="ad4a2-128">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ad4a2-129">Definieren von Gruppen von Objekten für eine Sicht</span><span class="sxs-lookup"><span data-stu-id="ad4a2-129">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ad4a2-130">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="ad4a2-130">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ad4a2-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad4a2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
