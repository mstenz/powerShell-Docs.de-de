---
title: PropertyName-Element für SelectionCondition für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: f857f5944b9e971215a06d6f5c39f7c22c6cf99f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853296"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="bd517-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bd517-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="bd517-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="bd517-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="bd517-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Listeneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="bd517-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="bd517-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für ListEntry (Format) SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)-PropertyName-Element für SelectionCondition für EmtrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bd517-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EmtrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd517-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bd517-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd517-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="bd517-107">Attributes and Elements</span></span>

<span data-ttu-id="bd517-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="bd517-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd517-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="bd517-109">Attributes</span></span>

<span data-ttu-id="bd517-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="bd517-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bd517-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bd517-111">Child Elements</span></span>

<span data-ttu-id="bd517-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="bd517-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd517-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bd517-113">Parent Elements</span></span>

|<span data-ttu-id="bd517-114">Element</span><span class="sxs-lookup"><span data-stu-id="bd517-114">Element</span></span>|<span data-ttu-id="bd517-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd517-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bd517-116">SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bd517-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="bd517-117">Definiert die Bedingung, die für diesen Eintrag der Liste zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="bd517-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bd517-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="bd517-118">Text Value</span></span>

<span data-ttu-id="bd517-119">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="bd517-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd517-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bd517-120">Remarks</span></span>

<span data-ttu-id="bd517-121">Die auswahlbedingung muss mindestens einen Eigenschaftennamen oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bd517-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="bd517-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bd517-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="bd517-123">Weitere Informationen zu anderen Komponenten einer Listenansicht, finden Sie unter [Listenansicht erstellen](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="bd517-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd517-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bd517-124">See Also</span></span>

[<span data-ttu-id="bd517-125">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="bd517-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="bd517-126">Definieren von Bedingungen für, wenn Daten wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bd517-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bd517-127">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bd517-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="bd517-128">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bd517-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="bd517-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd517-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
