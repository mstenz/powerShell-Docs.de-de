---
title: PropertyName-Element für selectioncondition für entryselectedby für enumerableweiterung (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ae11924-0072-451e-bf70-c5ffb25dccc0
caps.latest.revision: 13
ms.openlocfilehash: 0c20512e660c8d2b61d063dbd7078b55b23efeb8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362319"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="fe1e1-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="fe1e1-102">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="fe1e1-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="fe1e1-104">Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und die Definition wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="fe1e1-105">Configuration-Element (Format) DefaultSettings-Element (Format) enumerableerweiterungen-Element (Format) enumerableweiterung-Element (Format) entryselectedby-Element für enumerableexpansion (Format) selectioncondition-Element für entryselectedby Enumerableexpansion (Format) propertyName-Element für selectioncondition für entryselectedby für enumerableexpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="fe1e1-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe1e1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe1e1-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe1e1-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fe1e1-107">Attributes and Elements</span></span>

<span data-ttu-id="fe1e1-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe1e1-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="fe1e1-109">Attributes</span></span>

<span data-ttu-id="fe1e1-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe1e1-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fe1e1-111">Child Elements</span></span>

<span data-ttu-id="fe1e1-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe1e1-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fe1e1-113">Parent Elements</span></span>

|<span data-ttu-id="fe1e1-114">Element</span><span class="sxs-lookup"><span data-stu-id="fe1e1-114">Element</span></span>|<span data-ttu-id="fe1e1-115">Description</span><span class="sxs-lookup"><span data-stu-id="fe1e1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe1e1-116">Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="fe1e1-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="fe1e1-117">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungs Objekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe1e1-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="fe1e1-118">Text Value</span></span>

<span data-ttu-id="fe1e1-119">Geben Sie den Namen der .net-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe1e1-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fe1e1-120">Remarks</span></span>

<span data-ttu-id="fe1e1-121">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder ein auszuwertende Skript angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="fe1e1-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="fe1e1-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fe1e1-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe1e1-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fe1e1-123">See Also</span></span>

[<span data-ttu-id="fe1e1-124">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="fe1e1-124">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fe1e1-125">ScriptBlock-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="fe1e1-125">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="fe1e1-126">Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="fe1e1-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="fe1e1-127">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="fe1e1-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
