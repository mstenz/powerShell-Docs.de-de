---
title: ScriptBlock-Element für selectioncondition für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08512496-5682-4539-ab56-0c5394ce1f01
caps.latest.revision: 6
ms.openlocfilehash: 0137886437f01518f396613c564517e7910e657a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364799"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="94c93-102">Element „ScriptBlock“ für SelectionCondition für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="94c93-102">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="94c93-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="94c93-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="94c93-104">Wenn dieses Skript `true` ausgewertet wird, wird die Bedingung erfüllt, und die Definition wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="94c93-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="94c93-105">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="94c93-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="94c93-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für das View (Format) customentry-Element für customentries für Steuerelemente für das View (Format) entryselectedby-Element für customentry für Steuerelemente für das View (Format) selectioncondition-Element für entryselectedby für Steuerelemente für View ( Format) ScriptBlock-Element für selectioncondition für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="94c93-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94c93-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="94c93-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94c93-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="94c93-108">Attributes and Elements</span></span>

<span data-ttu-id="94c93-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="94c93-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94c93-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="94c93-110">Attributes</span></span>

<span data-ttu-id="94c93-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="94c93-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94c93-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="94c93-112">Child Elements</span></span>

<span data-ttu-id="94c93-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="94c93-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94c93-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="94c93-114">Parent Elements</span></span>

|<span data-ttu-id="94c93-115">Element</span><span class="sxs-lookup"><span data-stu-id="94c93-115">Element</span></span>|<span data-ttu-id="94c93-116">Description</span><span class="sxs-lookup"><span data-stu-id="94c93-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94c93-117">Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="94c93-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="94c93-118">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="94c93-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="94c93-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="94c93-119">Text Value</span></span>

<span data-ttu-id="94c93-120">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="94c93-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="94c93-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="94c93-121">Remarks</span></span>

<span data-ttu-id="94c93-122">Die Auswahlbedingung muss mindestens ein Skript oder einen Eigenschaftsnamen angeben, um ausgewertet zu werden, aber nicht beides.</span><span class="sxs-lookup"><span data-stu-id="94c93-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="94c93-123">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="94c93-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94c93-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="94c93-124">See Also</span></span>

[<span data-ttu-id="94c93-125">Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="94c93-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="94c93-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="94c93-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
