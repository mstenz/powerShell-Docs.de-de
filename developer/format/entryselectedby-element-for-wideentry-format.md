---
title: EntrySelectedBy-Element für WideEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066174"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="7a611-102">Element „EntrySelectedBy“ für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="7a611-103">Definiert die Typen von .NET, mit denen diese Definition von der breiten Ansicht oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7a611-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="7a611-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a611-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a611-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a611-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7a611-106">Attributes and Elements</span></span>

<span data-ttu-id="7a611-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="7a611-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a611-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7a611-108">Attributes</span></span>

<span data-ttu-id="7a611-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="7a611-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a611-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7a611-110">Child Elements</span></span>

|<span data-ttu-id="7a611-111">Element</span><span class="sxs-lookup"><span data-stu-id="7a611-111">Element</span></span>|<span data-ttu-id="7a611-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7a611-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a611-113">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7a611-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7a611-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7a611-115">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition Breite Ansicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7a611-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="7a611-116">SelectionSetName-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="7a611-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7a611-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7a611-118">Gibt einen Satz von .NET-Typen, die dieser Definition Breite Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="7a611-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="7a611-119">TypeName-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="7a611-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7a611-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7a611-121">Gibt einen .NET-Typ, der diese Breite Ansichtsdefinition verwendet.</span><span class="sxs-lookup"><span data-stu-id="7a611-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7a611-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7a611-122">Parent Elements</span></span>

|<span data-ttu-id="7a611-123">Element</span><span class="sxs-lookup"><span data-stu-id="7a611-123">Element</span></span>|<span data-ttu-id="7a611-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7a611-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a611-125">WideEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="7a611-126">Stellt eine Definition der breiten Ansicht.</span><span class="sxs-lookup"><span data-stu-id="7a611-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7a611-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7a611-127">Remarks</span></span>

<span data-ttu-id="7a611-128">Sie müssen mindestens einen Typ, Auswahlsatz oder erfüllt eine Breite Ansicht-Definition angeben.</span><span class="sxs-lookup"><span data-stu-id="7a611-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="7a611-129">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7a611-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="7a611-130">Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der einen bestimmten Eigenschaftswert oder das Skriptwert ergibt, `true`.</span><span class="sxs-lookup"><span data-stu-id="7a611-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="7a611-131">Weitere Informationen zu auswahlbedingungen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7a611-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7a611-132">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7a611-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a611-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7a611-133">See Also</span></span>

[<span data-ttu-id="7a611-134">WideEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="7a611-135">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7a611-136">SelectionSetName-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7a611-137">TypeName-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7a611-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="7a611-138">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="7a611-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7a611-139">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="7a611-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7a611-140">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a611-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
