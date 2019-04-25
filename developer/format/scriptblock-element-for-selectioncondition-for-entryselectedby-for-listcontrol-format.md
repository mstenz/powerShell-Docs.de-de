---
title: ScriptBlock-Element für SelectionCondition für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a1adad7-e864-4892-9d26-a6476a9698d2
caps.latest.revision: 7
ms.openlocfilehash: b65d953169f6daf15fb617ce4d0303cf4cb584ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064355"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="7788d-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7788d-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="7788d-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="7788d-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="7788d-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und der Listeneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="7788d-104">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="7788d-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für ListEntry (Format) SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)-ScriptBlock-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7788d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7788d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7788d-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7788d-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7788d-107">Attributes and Elements</span></span>

<span data-ttu-id="7788d-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="7788d-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7788d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7788d-109">Attributes</span></span>

<span data-ttu-id="7788d-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="7788d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7788d-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7788d-111">Child Elements</span></span>

<span data-ttu-id="7788d-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="7788d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7788d-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7788d-113">Parent Elements</span></span>

|<span data-ttu-id="7788d-114">Element</span><span class="sxs-lookup"><span data-stu-id="7788d-114">Element</span></span>|<span data-ttu-id="7788d-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7788d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7788d-116">SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7788d-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="7788d-117">Definiert die Bedingung, die für diesen Eintrag der Liste zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="7788d-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7788d-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="7788d-118">Text Value</span></span>

<span data-ttu-id="7788d-119">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="7788d-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7788d-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7788d-120">Remarks</span></span>

<span data-ttu-id="7788d-121">Die auswahlbedingung muss einen angeben mindestens ein Skript oder eine Eigenschaft zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="7788d-121">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7788d-122">(Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="7788d-122">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="7788d-123">Weitere Informationen zu den anderen Komponenten einer Listenansicht, finden Sie unter [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7788d-123">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7788d-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7788d-124">See Also</span></span>

[<span data-ttu-id="7788d-125">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7788d-125">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="7788d-126">PropertyName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7788d-126">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="7788d-127">SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7788d-127">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="7788d-128">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="7788d-128">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7788d-129">Definieren Bedingungen für ein, wenn eine Ansicht Eintrag oder ein Element verwendet wird</span><span class="sxs-lookup"><span data-stu-id="7788d-129">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7788d-130">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="7788d-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
