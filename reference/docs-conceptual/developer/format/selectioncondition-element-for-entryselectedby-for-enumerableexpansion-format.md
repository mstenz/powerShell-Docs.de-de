---
title: Selectioncondition-Element für entryselectedby für enumerableexpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362009"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b7ec7-102">Element „SelectionCondition“ für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ec7-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b7ec7-103">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungs Objekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="b7ec7-104">Configuration-Element (Format) DefaultSettings-Element (Format) enumerableerweiterungen-Element (Format) enumerableweiterung-Element (Format) entryselectedby-Element für enumerableexpansion (Format) selectioncondition-Element für entryselectedby Enumerableerweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ec7-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7ec7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7ec7-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7ec7-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b7ec7-106">Attributes and Elements</span></span>

<span data-ttu-id="b7ec7-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="b7ec7-108">Sie müssen ein einzelnes `PropertyName`-oder `ScriptBlock`-Element angeben.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="b7ec7-109">Die `SelectionSetName`-und `TypeName`-Elemente sind optional.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="b7ec7-110">Sie können eines der beiden Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7ec7-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="b7ec7-111">Attributes</span></span>

<span data-ttu-id="b7ec7-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7ec7-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b7ec7-113">Child Elements</span></span>

|<span data-ttu-id="b7ec7-114">Element</span><span class="sxs-lookup"><span data-stu-id="b7ec7-114">Element</span></span>|<span data-ttu-id="b7ec7-115">Description</span><span class="sxs-lookup"><span data-stu-id="b7ec7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7ec7-116">PropertyName-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ec7-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ec7-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ec7-118">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b7ec7-119">ScriptBlock-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ec7-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ec7-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ec7-121">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="b7ec7-122">Selectionsetname-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ec7-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ec7-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ec7-124">Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="b7ec7-125">Typname-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ec7-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ec7-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ec7-127">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7ec7-128">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b7ec7-128">Parent Elements</span></span>

|<span data-ttu-id="b7ec7-129">Element</span><span class="sxs-lookup"><span data-stu-id="b7ec7-129">Element</span></span>|<span data-ttu-id="b7ec7-130">Description</span><span class="sxs-lookup"><span data-stu-id="b7ec7-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7ec7-131">Entryselectedby-Element für enumerableexpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ec7-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="b7ec7-132">Definiert, welche .net-Auflistungs Objekte durch diese Definition erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7ec7-133">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b7ec7-133">Remarks</span></span>

<span data-ttu-id="b7ec7-134">Für jede Definition muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b7ec7-135">Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="b7ec7-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="b7ec7-136">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="b7ec7-137">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="b7ec7-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="b7ec7-138">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Wiedergabe von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b7ec7-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b7ec7-139">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b7ec7-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b7ec7-140">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b7ec7-140">See Also</span></span>

[<span data-ttu-id="b7ec7-141">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="b7ec7-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b7ec7-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="b7ec7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
