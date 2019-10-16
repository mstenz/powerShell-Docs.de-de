---
title: PropertyName-Element für selectioncondition für entryselectedby für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362289"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="8dc06-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8dc06-102">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="8dc06-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="8dc06-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="8dc06-104">Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und der Listeneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="8dc06-104">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="8dc06-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) entryselectedby-Element für ListEntry (Format) selectioncondition-Element für Entryselectedby für ListEntry (Format) propertyName-Element für selectioncondition für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8dc06-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8dc06-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8dc06-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8dc06-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8dc06-107">Attributes and Elements</span></span>

<span data-ttu-id="8dc06-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8dc06-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8dc06-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="8dc06-109">Attributes</span></span>

<span data-ttu-id="8dc06-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="8dc06-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8dc06-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8dc06-111">Child Elements</span></span>

<span data-ttu-id="8dc06-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="8dc06-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8dc06-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8dc06-113">Parent Elements</span></span>

|<span data-ttu-id="8dc06-114">Element</span><span class="sxs-lookup"><span data-stu-id="8dc06-114">Element</span></span>|<span data-ttu-id="8dc06-115">Description</span><span class="sxs-lookup"><span data-stu-id="8dc06-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8dc06-116">Selectioncondition-Element für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8dc06-116">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8dc06-117">Definiert die Bedingung, die für die Verwendung dieses Listen Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="8dc06-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8dc06-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="8dc06-118">Text Value</span></span>

<span data-ttu-id="8dc06-119">Geben Sie den Namen der .net-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="8dc06-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="8dc06-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8dc06-120">Remarks</span></span>

<span data-ttu-id="8dc06-121">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="8dc06-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="8dc06-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter Definieren von Bedingungen für den Fall, [dass ein Ansichts Eintrag oder Element verwendet wird](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8dc06-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8dc06-123">Weitere Informationen zu anderen Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8dc06-123">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8dc06-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8dc06-124">See Also</span></span>

[<span data-ttu-id="8dc06-125">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="8dc06-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8dc06-126">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="8dc06-126">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8dc06-127">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8dc06-127">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="8dc06-128">ScriptBlock-Element für selectioncondition für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="8dc06-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8dc06-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="8dc06-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
