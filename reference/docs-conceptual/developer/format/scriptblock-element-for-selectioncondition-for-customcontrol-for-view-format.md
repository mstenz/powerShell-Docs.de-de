---
title: ScriptBlock-Element für selectioncondition für CustomControl für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368639"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="0e937-102">Element „ScriptBlock“ für SelectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e937-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="0e937-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0e937-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="0e937-104">Wenn dieses Skript zum `true`ausgewertet wird, wird die Bedingung erfüllt, und die Definition wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="0e937-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="0e937-105">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="0e937-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="0e937-106">Konfigurationselement (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element für View (Format) customentries-Element für CustomControl for View (Format) customentry-Element für customentries für CustomControl für Ansicht ( Format) customItem-Element für customentry für CustomControl für View (Format) selectioncondition-Element für entryselectedby für CustomControl for View (Format) ScriptBlock-Element für selectioncondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e937-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e937-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e937-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e937-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0e937-108">Attributes and Elements</span></span>

<span data-ttu-id="0e937-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0e937-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e937-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="0e937-110">Attributes</span></span>

<span data-ttu-id="0e937-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="0e937-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e937-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0e937-112">Child Elements</span></span>

<span data-ttu-id="0e937-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="0e937-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0e937-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0e937-114">Parent Elements</span></span>

|<span data-ttu-id="0e937-115">Element</span><span class="sxs-lookup"><span data-stu-id="0e937-115">Element</span></span>|<span data-ttu-id="0e937-116">Description</span><span class="sxs-lookup"><span data-stu-id="0e937-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e937-117">Selectioncondition-Element für entryselectedby für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e937-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="0e937-118">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="0e937-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0e937-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="0e937-119">Text Value</span></span>

<span data-ttu-id="0e937-120">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="0e937-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e937-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0e937-121">Remarks</span></span>

<span data-ttu-id="0e937-122">Die Auswahlbedingung muss mindestens ein Skript oder einen Eigenschaftsnamen angeben, um ausgewertet zu werden, aber nicht beides.</span><span class="sxs-lookup"><span data-stu-id="0e937-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="0e937-123">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0e937-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e937-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0e937-124">See Also</span></span>

[<span data-ttu-id="0e937-125">Selectioncondition-Element für entryselectedby für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e937-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="0e937-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="0e937-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
