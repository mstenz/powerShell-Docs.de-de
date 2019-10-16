---
title: ScriptBlock-Element für selectioncondition für entryselectedby für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368599"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="5b447-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5b447-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="5b447-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="5b447-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="5b447-104">Wenn dieses Skript `true` ausgewertet wird, wird die Bedingung erfüllt, und die Definition wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="5b447-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="5b447-105">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5b447-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5b447-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format) selectioncondition-Element für entryselectedby für GroupBy (Format) ScriptBlock-Element für selectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5b447-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b447-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b447-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b447-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5b447-108">Attributes and Elements</span></span>

<span data-ttu-id="5b447-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5b447-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b447-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="5b447-110">Attributes</span></span>

<span data-ttu-id="5b447-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="5b447-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b447-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5b447-112">Child Elements</span></span>

<span data-ttu-id="5b447-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="5b447-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b447-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5b447-114">Parent Elements</span></span>

|<span data-ttu-id="5b447-115">Element</span><span class="sxs-lookup"><span data-stu-id="5b447-115">Element</span></span>|<span data-ttu-id="5b447-116">Description</span><span class="sxs-lookup"><span data-stu-id="5b447-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b447-117">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5b447-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="5b447-118">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="5b447-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b447-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="5b447-119">Text Value</span></span>

<span data-ttu-id="5b447-120">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="5b447-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b447-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5b447-121">Remarks</span></span>

<span data-ttu-id="5b447-122">Die Auswahlbedingung muss mindestens ein Skript oder einen Eigenschaftsnamen angeben, um ausgewertet zu werden, aber nicht beides.</span><span class="sxs-lookup"><span data-stu-id="5b447-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="5b447-123">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5b447-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b447-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5b447-124">See Also</span></span>

[<span data-ttu-id="5b447-125">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5b447-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="5b447-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="5b447-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
