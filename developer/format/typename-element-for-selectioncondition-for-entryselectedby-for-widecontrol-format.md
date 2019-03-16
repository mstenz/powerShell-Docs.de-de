---
title: TypeName-Element für SelectionCondition für EntrySelectedBy für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055978"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="e5fa0-102">Element „TypeName“ für SelectionCondition für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e5fa0-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="e5fa0-103">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="e5fa0-104">Wenn dieses Typs vorhanden ist, wird die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="e5fa0-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format) TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e5fa0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5fa0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5fa0-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5fa0-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e5fa0-107">Attributes and Elements</span></span>

<span data-ttu-id="e5fa0-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5fa0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e5fa0-109">Attributes</span></span>

<span data-ttu-id="e5fa0-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5fa0-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e5fa0-111">Child Elements</span></span>

<span data-ttu-id="e5fa0-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5fa0-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e5fa0-113">Parent Elements</span></span>

|<span data-ttu-id="e5fa0-114">Element</span><span class="sxs-lookup"><span data-stu-id="e5fa0-114">Element</span></span>|<span data-ttu-id="e5fa0-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e5fa0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5fa0-116">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e5fa0-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e5fa0-117">Definiert die Bedingung, die für diesen wide Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5fa0-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="e5fa0-118">Text Value</span></span>

<span data-ttu-id="e5fa0-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5fa0-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e5fa0-120">Remarks</span></span>

<span data-ttu-id="e5fa0-121">Die auswahlbedingung kann einen .NET-Typ, ein angeben, oder eine Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="e5fa0-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="e5fa0-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e5fa0-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e5fa0-123">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e5fa0-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5fa0-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e5fa0-124">See Also</span></span>

[<span data-ttu-id="e5fa0-125">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="e5fa0-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e5fa0-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="e5fa0-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e5fa0-127">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e5fa0-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e5fa0-128">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e5fa0-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="e5fa0-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5fa0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
