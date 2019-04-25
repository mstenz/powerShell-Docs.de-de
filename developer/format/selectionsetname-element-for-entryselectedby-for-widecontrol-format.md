---
title: SelectionSetName-Element für EntrySelectedBy für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064024"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="04f34-102">Element „SelectionSetName“ für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="04f34-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="04f34-103">Gibt einen Satz von .NET-Objekten für die Definition.</span><span class="sxs-lookup"><span data-stu-id="04f34-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="04f34-104">Die Definition wird verwendet, wenn eines dieser Objekte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="04f34-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="04f34-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionSetName-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="04f34-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="04f34-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="04f34-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="04f34-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="04f34-107">Attributes and Elements</span></span>

<span data-ttu-id="04f34-108">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="04f34-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="04f34-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="04f34-109">Attributes</span></span>

<span data-ttu-id="04f34-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="04f34-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04f34-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="04f34-111">Child Elements</span></span>

<span data-ttu-id="04f34-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="04f34-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="04f34-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="04f34-113">Parent Elements</span></span>

|<span data-ttu-id="04f34-114">Element</span><span class="sxs-lookup"><span data-stu-id="04f34-114">Element</span></span>|<span data-ttu-id="04f34-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="04f34-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04f34-116">EntrySelectedBy-Element für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="04f34-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="04f34-117">Definiert die .NET-Typen, die dieser breiten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="04f34-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="04f34-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="04f34-118">Text Value</span></span>

<span data-ttu-id="04f34-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="04f34-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="04f34-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="04f34-120">Remarks</span></span>

<span data-ttu-id="04f34-121">Jede Definition muss ein Typname, Auswahlsatz oder auswahlbedingung angeben.</span><span class="sxs-lookup"><span data-stu-id="04f34-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="04f34-122">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="04f34-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="04f34-123">Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="04f34-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="04f34-124">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren legt der Objekte für eine Sicht](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="04f34-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="04f34-125">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="04f34-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="04f34-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="04f34-126">See Also</span></span>

[<span data-ttu-id="04f34-127">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="04f34-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="04f34-128">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="04f34-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="04f34-129">EntrySelectedBy-Element für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="04f34-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="04f34-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="04f34-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
