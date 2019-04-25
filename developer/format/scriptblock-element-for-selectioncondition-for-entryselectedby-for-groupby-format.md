---
title: ScriptBlock-Element für SelectionCondition für EntrySelectedBy für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01344bd-ad69-4789-8e9f-2e79880c3a33
caps.latest.revision: 6
ms.openlocfilehash: cb79fb942111cee89c6b2abba75de4c494082b7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064340"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="bad3c-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bad3c-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="bad3c-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="bad3c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="bad3c-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="bad3c-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="bad3c-105">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bad3c-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="bad3c-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)-ScriptBlock-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bad3c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bad3c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="bad3c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bad3c-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="bad3c-108">Attributes and Elements</span></span>

<span data-ttu-id="bad3c-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="bad3c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bad3c-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="bad3c-110">Attributes</span></span>

<span data-ttu-id="bad3c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="bad3c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bad3c-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bad3c-112">Child Elements</span></span>

<span data-ttu-id="bad3c-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="bad3c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bad3c-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bad3c-114">Parent Elements</span></span>

|<span data-ttu-id="bad3c-115">Element</span><span class="sxs-lookup"><span data-stu-id="bad3c-115">Element</span></span>|<span data-ttu-id="bad3c-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bad3c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bad3c-117">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bad3c-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="bad3c-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bad3c-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bad3c-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="bad3c-119">Text Value</span></span>

<span data-ttu-id="bad3c-120">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="bad3c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="bad3c-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bad3c-121">Remarks</span></span>

<span data-ttu-id="bad3c-122">Die auswahlbedingung muss einen angeben mindestens ein Skript oder eine Eigenschaft zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="bad3c-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="bad3c-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bad3c-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bad3c-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bad3c-124">See Also</span></span>

[<span data-ttu-id="bad3c-125">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bad3c-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="bad3c-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="bad3c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
