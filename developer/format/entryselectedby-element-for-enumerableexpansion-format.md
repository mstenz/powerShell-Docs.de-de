---
title: EntrySelectedBy-Element für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855586"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="5af0c-102">Element „EntrySelectedBy“ für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-102">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="5af0c-103">Definiert die .NET-Typen, die dieser Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5af0c-103">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="5af0c-104">-Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5af0c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5af0c-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5af0c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5af0c-106">Attributes and Elements</span></span>

<span data-ttu-id="5af0c-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="5af0c-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5af0c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="5af0c-108">Attributes</span></span>

<span data-ttu-id="5af0c-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="5af0c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5af0c-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5af0c-110">Child Elements</span></span>

|<span data-ttu-id="5af0c-111">Element</span><span class="sxs-lookup"><span data-stu-id="5af0c-111">Element</span></span>|<span data-ttu-id="5af0c-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5af0c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5af0c-113">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-113">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5af0c-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="5af0c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5af0c-115">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="5af0c-115">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="5af0c-116">SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-116">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5af0c-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="5af0c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="5af0c-118">Gibt einen Satz von .NET-Typen, mit denen diese Definition, wie die Auflistungsobjekte erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="5af0c-118">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="5af0c-119">TypeName-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-119">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="5af0c-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="5af0c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="5af0c-121">Gibt einen .NET-Typ, der verwendet diese Definition, wie die Auflistungsobjekte erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="5af0c-121">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5af0c-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5af0c-122">Parent Elements</span></span>

|<span data-ttu-id="5af0c-123">Element</span><span class="sxs-lookup"><span data-stu-id="5af0c-123">Element</span></span>|<span data-ttu-id="5af0c-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5af0c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5af0c-125">EnumerableExpansion-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-125">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="5af0c-126">Definiert, wie .NET Datenbanksammlung Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5af0c-126">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5af0c-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5af0c-127">Remarks</span></span>

<span data-ttu-id="5af0c-128">Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung für einen Definitionseintrag angeben.</span><span class="sxs-lookup"><span data-stu-id="5af0c-128">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="5af0c-129">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="5af0c-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="5af0c-130">Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der eine bestimmte Eigenschaft-Wert oder ein Skript ergibt, `true`.</span><span class="sxs-lookup"><span data-stu-id="5af0c-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="5af0c-131">Weitere Informationen zu auswahlbedingungen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5af0c-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5af0c-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5af0c-132">See Also</span></span>

[<span data-ttu-id="5af0c-133">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="5af0c-133">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5af0c-134">EnumerableExpansion-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-134">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="5af0c-135">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-135">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5af0c-136">SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-136">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5af0c-137">TypeName-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="5af0c-137">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="5af0c-138">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5af0c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
