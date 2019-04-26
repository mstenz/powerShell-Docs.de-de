---
title: ScriptBlock-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064372"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f1f90-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f90-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f1f90-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="f1f90-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="f1f90-104">Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format) SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)-ScriptBlock-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f90-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f1f90-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f1f90-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f1f90-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f1f90-106">Attributes and Elements</span></span>

<span data-ttu-id="f1f90-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="f1f90-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f1f90-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f1f90-108">Attributes</span></span>

<span data-ttu-id="f1f90-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="f1f90-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f1f90-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f1f90-110">Child Elements</span></span>

<span data-ttu-id="f1f90-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="f1f90-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f1f90-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f1f90-112">Parent Elements</span></span>

|<span data-ttu-id="f1f90-113">Element</span><span class="sxs-lookup"><span data-stu-id="f1f90-113">Element</span></span>|<span data-ttu-id="f1f90-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f1f90-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f1f90-115">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f90-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f1f90-116">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="f1f90-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f1f90-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="f1f90-117">Text Value</span></span>

<span data-ttu-id="f1f90-118">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="f1f90-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1f90-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f1f90-119">Remarks</span></span>

<span data-ttu-id="f1f90-120">Geben Sie die auswahlbedingung muss mindestens ein Skript oder die Eigenschaft Name zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="f1f90-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="f1f90-121">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f1f90-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1f90-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f1f90-122">See Also</span></span>

[<span data-ttu-id="f1f90-123">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="f1f90-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f1f90-124">PropertyName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f90-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="f1f90-125">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f1f90-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="f1f90-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1f90-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
