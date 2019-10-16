---
title: Entryselectedby-Element für wideentry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363329"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="2b4cf-102">Element „EntrySelectedBy“ für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="2b4cf-103">Definiert die .NET-Typen, die diese Definition der breiten Ansicht verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="2b4cf-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) entryselectedby-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b4cf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b4cf-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b4cf-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2b4cf-106">Attributes and Elements</span></span>

<span data-ttu-id="2b4cf-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b4cf-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="2b4cf-108">Attributes</span></span>

<span data-ttu-id="2b4cf-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b4cf-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b4cf-110">Child Elements</span></span>

|<span data-ttu-id="2b4cf-111">Element</span><span class="sxs-lookup"><span data-stu-id="2b4cf-111">Element</span></span>|<span data-ttu-id="2b4cf-112">Description</span><span class="sxs-lookup"><span data-stu-id="2b4cf-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b4cf-113">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2b4cf-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-114">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4cf-115">Definiert die Bedingung, die vorhanden sein muss, damit diese Breite Sicht Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="2b4cf-116">Selectionsetname-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="2b4cf-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-117">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4cf-118">Gibt einen Satz von .NET-Typen an, die diese Breite Sicht Definition verwenden.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="2b4cf-119">Tyname-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="2b4cf-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2b4cf-121">Gibt einen .NET-Typ an, der diese Breite Sicht Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2b4cf-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b4cf-122">Parent Elements</span></span>

|<span data-ttu-id="2b4cf-123">Element</span><span class="sxs-lookup"><span data-stu-id="2b4cf-123">Element</span></span>|<span data-ttu-id="2b4cf-124">Description</span><span class="sxs-lookup"><span data-stu-id="2b4cf-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b4cf-125">Wideentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="2b4cf-126">Stellt eine Definition der breiten Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b4cf-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2b4cf-127">Remarks</span></span>

<span data-ttu-id="2b4cf-128">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine breite Sicht Definition angeben.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="2b4cf-129">Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="2b4cf-130">Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt über eine bestimmte Eigenschaft verfügt oder ein bestimmter Eigenschafts Wert oder Skript Wert als `true` ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="2b4cf-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="2b4cf-131">Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2b4cf-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2b4cf-132">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="2b4cf-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b4cf-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2b4cf-133">See Also</span></span>

[<span data-ttu-id="2b4cf-134">Wideentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="2b4cf-135">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2b4cf-136">Selectionsetname-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="2b4cf-137">Tyname-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="2b4cf-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="2b4cf-138">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="2b4cf-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2b4cf-139">Definieren von Bedingungen zum Anzeigen von Daten</span><span class="sxs-lookup"><span data-stu-id="2b4cf-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2b4cf-140">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="2b4cf-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
