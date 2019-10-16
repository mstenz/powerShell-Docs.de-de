---
title: ScriptBlock-Element für selectioncondition für entryselectedby für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368589"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="fbab5-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fbab5-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="fbab5-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="fbab5-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="fbab5-104">Wenn dieses Skript `true` ausgewertet wird, wird die Bedingung erfüllt, und der Listeneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="fbab5-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="fbab5-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) entryselectedby-Element für ListEntry (Format) selectioncondition-Element für Entryselectedby für ListEntry (Format) ScriptBlock-Element für selectioncondition für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="fbab5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fbab5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fbab5-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fbab5-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fbab5-107">Attributes and Elements</span></span>

<span data-ttu-id="fbab5-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="fbab5-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fbab5-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="fbab5-109">Attributes</span></span>

<span data-ttu-id="fbab5-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="fbab5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fbab5-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fbab5-111">Child Elements</span></span>

<span data-ttu-id="fbab5-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="fbab5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fbab5-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fbab5-113">Parent Elements</span></span>

|<span data-ttu-id="fbab5-114">Element</span><span class="sxs-lookup"><span data-stu-id="fbab5-114">Element</span></span>|<span data-ttu-id="fbab5-115">Description</span><span class="sxs-lookup"><span data-stu-id="fbab5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fbab5-116">Selectioncondition-Element für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="fbab5-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="fbab5-117">Definiert die Bedingung, die für die Verwendung dieses Listen Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="fbab5-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fbab5-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="fbab5-118">Text Value</span></span>

<span data-ttu-id="fbab5-119">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="fbab5-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="fbab5-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fbab5-120">Remarks</span></span>

<span data-ttu-id="fbab5-121">Die Auswahlbedingung muss mindestens ein Skript oder einen Eigenschaftsnamen angeben, um ausgewertet zu werden, aber nicht beides.</span><span class="sxs-lookup"><span data-stu-id="fbab5-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="fbab5-122">(Weitere Informationen dazu, wie Auswahl Bedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="fbab5-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="fbab5-123">Weitere Informationen zu den anderen Komponenten einer Listenansicht finden Sie in der [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fbab5-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbab5-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fbab5-124">See Also</span></span>

[<span data-ttu-id="fbab5-125">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fbab5-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="fbab5-126">PropertyName-Element für selectioncondition für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="fbab5-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="fbab5-127">Selectioncondition-Element für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="fbab5-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="fbab5-128">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="fbab5-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fbab5-129">Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder-Elements</span><span class="sxs-lookup"><span data-stu-id="fbab5-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="fbab5-130">Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="fbab5-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
