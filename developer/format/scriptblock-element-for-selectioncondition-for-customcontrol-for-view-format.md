---
title: ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857416"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="d83d8-102">Element „ScriptBlock“ für SelectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="d83d8-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="d83d8-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="d83d8-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d83d8-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="d83d8-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d83d8-105">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d83d8-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d83d8-106">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)-ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="d83d8-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d83d8-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d83d8-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d83d8-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d83d8-108">Attributes and Elements</span></span>

<span data-ttu-id="d83d8-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="d83d8-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d83d8-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d83d8-110">Attributes</span></span>

<span data-ttu-id="d83d8-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="d83d8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d83d8-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d83d8-112">Child Elements</span></span>

<span data-ttu-id="d83d8-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="d83d8-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d83d8-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d83d8-114">Parent Elements</span></span>

|<span data-ttu-id="d83d8-115">Element</span><span class="sxs-lookup"><span data-stu-id="d83d8-115">Element</span></span>|<span data-ttu-id="d83d8-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d83d8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d83d8-117">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d83d8-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="d83d8-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d83d8-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d83d8-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="d83d8-119">Text Value</span></span>

<span data-ttu-id="d83d8-120">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="d83d8-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d83d8-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d83d8-121">Remarks</span></span>

<span data-ttu-id="d83d8-122">Die auswahlbedingung muss einen angeben mindestens ein Skript oder eine Eigenschaft zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="d83d8-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d83d8-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d83d8-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d83d8-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d83d8-124">See Also</span></span>

[<span data-ttu-id="d83d8-125">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d83d8-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="d83d8-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d83d8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
