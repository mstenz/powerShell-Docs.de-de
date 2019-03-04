---
title: PropertyName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859626"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="40d1e-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="40d1e-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="40d1e-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="40d1e-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="40d1e-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="40d1e-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="40d1e-105">Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format) SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)-PropertyName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="40d1e-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="40d1e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="40d1e-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40d1e-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="40d1e-107">Attributes and Elements</span></span>

<span data-ttu-id="40d1e-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="40d1e-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="40d1e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="40d1e-109">Attributes</span></span>

<span data-ttu-id="40d1e-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="40d1e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="40d1e-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="40d1e-111">Child Elements</span></span>

<span data-ttu-id="40d1e-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="40d1e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40d1e-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="40d1e-113">Parent Elements</span></span>

|<span data-ttu-id="40d1e-114">Element</span><span class="sxs-lookup"><span data-stu-id="40d1e-114">Element</span></span>|<span data-ttu-id="40d1e-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="40d1e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40d1e-116">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="40d1e-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="40d1e-117">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="40d1e-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="40d1e-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="40d1e-118">Text Value</span></span>

<span data-ttu-id="40d1e-119">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="40d1e-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="40d1e-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="40d1e-120">Remarks</span></span>

<span data-ttu-id="40d1e-121">Die auswahlbedingung muss angeben, über mindestens einen Eigenschaftennamen oder ein Skript zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="40d1e-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="40d1e-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="40d1e-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40d1e-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="40d1e-123">See Also</span></span>

[<span data-ttu-id="40d1e-124">Definieren von Bedingungen für, wenn Daten wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="40d1e-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="40d1e-125">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="40d1e-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="40d1e-126">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="40d1e-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="40d1e-127">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="40d1e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
