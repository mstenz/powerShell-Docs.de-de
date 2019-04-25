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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064559"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="a189a-102">Element „ScriptBlock“ für SelectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a189a-102">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="a189a-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a189a-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a189a-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="a189a-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="a189a-105">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a189a-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a189a-106">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)-ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="a189a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a189a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a189a-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a189a-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a189a-108">Attributes and Elements</span></span>

<span data-ttu-id="a189a-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="a189a-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a189a-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="a189a-110">Attributes</span></span>

<span data-ttu-id="a189a-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a189a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a189a-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a189a-112">Child Elements</span></span>

<span data-ttu-id="a189a-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="a189a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a189a-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a189a-114">Parent Elements</span></span>

|<span data-ttu-id="a189a-115">Element</span><span class="sxs-lookup"><span data-stu-id="a189a-115">Element</span></span>|<span data-ttu-id="a189a-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a189a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a189a-117">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a189a-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="a189a-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a189a-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a189a-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="a189a-119">Text Value</span></span>

<span data-ttu-id="a189a-120">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="a189a-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a189a-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a189a-121">Remarks</span></span>

<span data-ttu-id="a189a-122">Die auswahlbedingung muss einen angeben mindestens ein Skript oder eine Eigenschaft zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="a189a-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="a189a-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a189a-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a189a-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a189a-124">See Also</span></span>

[<span data-ttu-id="a189a-125">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a189a-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="a189a-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="a189a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
