---
title: ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec68309-7826-4643-a521-e29c996663fb
caps.latest.revision: 11
ms.openlocfilehash: 649a978e21e9421a3f3e953261e1d309e23c3f9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862946"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="9866d-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9866d-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="9866d-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9866d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9866d-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Breite Eintrag-Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="9866d-104">When this script is evaluated to `true`, the condition is met, and the wide entry definition is used.</span></span>

<span data-ttu-id="9866d-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)-ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9866d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9866d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9866d-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9866d-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9866d-107">Attributes and Elements</span></span>

<span data-ttu-id="9866d-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="9866d-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9866d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9866d-109">Attributes</span></span>

<span data-ttu-id="9866d-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9866d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9866d-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9866d-111">Child Elements</span></span>

<span data-ttu-id="9866d-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="9866d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9866d-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9866d-113">Parent Elements</span></span>

|<span data-ttu-id="9866d-114">Element</span><span class="sxs-lookup"><span data-stu-id="9866d-114">Element</span></span>|<span data-ttu-id="9866d-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9866d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9866d-116">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9866d-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9866d-117">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9866d-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9866d-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="9866d-118">Text Value</span></span>

<span data-ttu-id="9866d-119">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="9866d-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9866d-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9866d-120">Remarks</span></span>

<span data-ttu-id="9866d-121">Geben Sie die auswahlbedingung muss mindestens ein Skript oder die Eigenschaft Name zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="9866d-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="9866d-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9866d-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9866d-123">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9866d-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9866d-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9866d-124">See Also</span></span>

[<span data-ttu-id="9866d-125">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="9866d-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9866d-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="9866d-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9866d-127">PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9866d-127">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9866d-128">SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="9866d-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9866d-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="9866d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
