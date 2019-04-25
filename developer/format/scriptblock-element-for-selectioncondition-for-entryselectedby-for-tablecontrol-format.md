---
title: ScriptBlock-Element für SelectionCondition für EntrySelectedBy für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076343"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="c5170-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c5170-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="c5170-103">Gibt den Skriptblock, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="c5170-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="c5170-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und der Tabelleneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="c5170-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="c5170-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy Konfigurationselement für TableRowEntry (Format) SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)-ScriptBlock-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c5170-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5170-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c5170-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5170-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="c5170-107">Attributes and Elements</span></span>

<span data-ttu-id="c5170-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="c5170-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5170-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c5170-109">Attributes</span></span>

<span data-ttu-id="c5170-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="c5170-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5170-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c5170-111">Child Elements</span></span>

<span data-ttu-id="c5170-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="c5170-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c5170-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c5170-113">Parent Elements</span></span>

|<span data-ttu-id="c5170-114">Element</span><span class="sxs-lookup"><span data-stu-id="c5170-114">Element</span></span>|<span data-ttu-id="c5170-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c5170-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5170-116">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c5170-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c5170-117">Definiert die Bedingung, die für diesen Tabelleneintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="c5170-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c5170-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="c5170-118">Text Value</span></span>

<span data-ttu-id="c5170-119">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="c5170-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5170-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c5170-120">Remarks</span></span>

<span data-ttu-id="c5170-121">Die auswahlbedingung muss mindestens einen Namen für die Skript-Block oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="c5170-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="c5170-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c5170-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c5170-123">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c5170-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5170-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c5170-124">See Also</span></span>

[<span data-ttu-id="c5170-125">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="c5170-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c5170-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="c5170-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c5170-127">PropertyName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c5170-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="c5170-128">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="c5170-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c5170-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="c5170-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
