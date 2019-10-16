---
title: ScriptBlock-Element für selectioncondition für entryselectedby für enumerableweiterung (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4126b799-c43d-4175-8513-6d761c65437e
caps.latest.revision: 9
ms.openlocfilehash: a51d8d22fa8b0c7f303a5e8f37edcc5e57724063
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368609"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="fdb1c-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb1c-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="fdb1c-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="fdb1c-103">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="fdb1c-104">Configuration-Element (Format) DefaultSettings-Element (Format) enumerableerweiterungen-Element (Format) enumerableweiterung-Element (Format) entryselectedby-Element für enumerableexpansion (Format) selectioncondition-Element für entryselectedby Enumerableexpansion (Format) ScriptBlock-Element für selectioncondition für entryselectedby für enumerableexpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb1c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdb1c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fdb1c-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdb1c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fdb1c-106">Attributes and Elements</span></span>

<span data-ttu-id="fdb1c-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="fdb1c-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdb1c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="fdb1c-108">Attributes</span></span>

<span data-ttu-id="fdb1c-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="fdb1c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdb1c-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fdb1c-110">Child Elements</span></span>

<span data-ttu-id="fdb1c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="fdb1c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fdb1c-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fdb1c-112">Parent Elements</span></span>

|<span data-ttu-id="fdb1c-113">Element</span><span class="sxs-lookup"><span data-stu-id="fdb1c-113">Element</span></span>|<span data-ttu-id="fdb1c-114">Description</span><span class="sxs-lookup"><span data-stu-id="fdb1c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdb1c-115">Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb1c-115">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="fdb1c-116">Definiert die Bedingung, die vorhanden sein muss, um die Auflistungs Objekte dieser Definition zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="fdb1c-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fdb1c-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="fdb1c-117">Text Value</span></span>

<span data-ttu-id="fdb1c-118">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="fdb1c-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fdb1c-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fdb1c-119">Remarks</span></span>

<span data-ttu-id="fdb1c-120">Die Auswahlbedingung muss mindestens ein Skript oder einen Eigenschaftsnamen angeben, der ausgewertet werden soll, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="fdb1c-120">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="fdb1c-121">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="fdb1c-121">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fdb1c-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fdb1c-122">See Also</span></span>

[<span data-ttu-id="fdb1c-123">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="fdb1c-123">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fdb1c-124">PropertyName-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb1c-124">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="fdb1c-125">Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb1c-125">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="fdb1c-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="fdb1c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
