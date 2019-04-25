---
title: SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064134"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="07ca8-102">Element „SelectionCondition“ für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="07ca8-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="07ca8-103">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="07ca8-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="07ca8-104">Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format) SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="07ca8-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07ca8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="07ca8-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07ca8-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="07ca8-106">Attributes and Elements</span></span>

<span data-ttu-id="07ca8-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="07ca8-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="07ca8-108">Sie müssen angeben, dass eine einzelne `PropertyName` oder `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="07ca8-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="07ca8-109">Die `SelectionSetName` und `TypeName` Elemente sind optional.</span><span class="sxs-lookup"><span data-stu-id="07ca8-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="07ca8-110">Sie können eine der beiden Element angeben.</span><span class="sxs-lookup"><span data-stu-id="07ca8-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07ca8-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="07ca8-111">Attributes</span></span>

<span data-ttu-id="07ca8-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="07ca8-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07ca8-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="07ca8-113">Child Elements</span></span>

|<span data-ttu-id="07ca8-114">Element</span><span class="sxs-lookup"><span data-stu-id="07ca8-114">Element</span></span>|<span data-ttu-id="07ca8-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="07ca8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07ca8-116">PropertyName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="07ca8-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="07ca8-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="07ca8-117">Optional element.</span></span><br /><br /> <span data-ttu-id="07ca8-118">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="07ca8-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="07ca8-119">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="07ca8-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="07ca8-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="07ca8-120">Optional element.</span></span><br /><br /> <span data-ttu-id="07ca8-121">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="07ca8-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="07ca8-122">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="07ca8-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="07ca8-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="07ca8-123">Optional element.</span></span><br /><br /> <span data-ttu-id="07ca8-124">Gibt den Satz von .NET-Typen, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="07ca8-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="07ca8-125">TypeName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="07ca8-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="07ca8-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="07ca8-126">Optional element.</span></span><br /><br /> <span data-ttu-id="07ca8-127">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="07ca8-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07ca8-128">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="07ca8-128">Parent Elements</span></span>

|<span data-ttu-id="07ca8-129">Element</span><span class="sxs-lookup"><span data-stu-id="07ca8-129">Element</span></span>|<span data-ttu-id="07ca8-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="07ca8-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07ca8-131">EntrySelectedBy-Element für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="07ca8-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="07ca8-132">Definiert, welche .NET Sammlung Objekte nach dieser Definition erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="07ca8-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07ca8-133">Hinweise</span><span class="sxs-lookup"><span data-stu-id="07ca8-133">Remarks</span></span>

<span data-ttu-id="07ca8-134">Jede Definition muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="07ca8-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="07ca8-135">Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="07ca8-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="07ca8-136">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="07ca8-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="07ca8-137">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="07ca8-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="07ca8-138">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für Diplaying Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="07ca8-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="07ca8-139">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="07ca8-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07ca8-140">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="07ca8-140">See Also</span></span>

[<span data-ttu-id="07ca8-141">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="07ca8-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="07ca8-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="07ca8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
