---
title: SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862746"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="d586c-102">Element „SelectionSetName“ für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d586c-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="d586c-103">Gibt den Satz von .NET-Typen, die nach dieser Definition erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="d586c-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="d586c-104">Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format) SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d586c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d586c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d586c-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d586c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d586c-106">Attributes and Elements</span></span>

<span data-ttu-id="d586c-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="d586c-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d586c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="d586c-108">Attributes</span></span>

<span data-ttu-id="d586c-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="d586c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d586c-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d586c-110">Child Elements</span></span>

<span data-ttu-id="d586c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="d586c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d586c-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d586c-112">Parent Elements</span></span>

|<span data-ttu-id="d586c-113">Element</span><span class="sxs-lookup"><span data-stu-id="d586c-113">Element</span></span>|<span data-ttu-id="d586c-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d586c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d586c-115">EntrySelectedBy-Element für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d586c-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="d586c-116">Definiert die .NET Auflistungsobjekte, die nach dieser Definition erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="d586c-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d586c-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="d586c-117">Text Value</span></span>

<span data-ttu-id="d586c-118">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="d586c-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d586c-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d586c-119">Remarks</span></span>

<span data-ttu-id="d586c-120">Jede Definition muss eine oder mehrere Namen, einen Auswahlsatz oder eine auswahlbedingung angeben.</span><span class="sxs-lookup"><span data-stu-id="d586c-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="d586c-121">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="d586c-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d586c-122">Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d586c-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d586c-123">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren legt der Objekte für eine Sicht](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d586c-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d586c-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d586c-124">See Also</span></span>

[<span data-ttu-id="d586c-125">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="d586c-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d586c-126">EntrySelectedBy-Element für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="d586c-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="d586c-127">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d586c-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
