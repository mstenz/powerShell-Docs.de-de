---
title: ScriptBlock-Element für selectioncondition für entryselectedby für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368579"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a8486-102">Element „ScriptBlock“ für SelectionCondition für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a8486-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a8486-103">Gibt den Skriptblock an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a8486-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="a8486-104">Wenn dieses Skript zum `true`ausgewertet wird, wird die Bedingung erfüllt, und der Tabelleneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="a8486-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="a8486-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element für tablerowentry (Format) Selectioncondition-Element für entryselectedby für tablerowentry (Format) ScriptBlock-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="a8486-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8486-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8486-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8486-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a8486-107">Attributes and Elements</span></span>

<span data-ttu-id="a8486-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a8486-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8486-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="a8486-109">Attributes</span></span>

<span data-ttu-id="a8486-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="a8486-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8486-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a8486-111">Child Elements</span></span>

<span data-ttu-id="a8486-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="a8486-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8486-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a8486-113">Parent Elements</span></span>

|<span data-ttu-id="a8486-114">Element</span><span class="sxs-lookup"><span data-stu-id="a8486-114">Element</span></span>|<span data-ttu-id="a8486-115">Description</span><span class="sxs-lookup"><span data-stu-id="a8486-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8486-116">Selectioncondition-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="a8486-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a8486-117">Definiert die Bedingung, die für die Verwendung dieses Tabellen Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="a8486-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a8486-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="a8486-118">Text Value</span></span>

<span data-ttu-id="a8486-119">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="a8486-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8486-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a8486-120">Remarks</span></span>

<span data-ttu-id="a8486-121">In der Auswahlbedingung muss mindestens ein Skriptblock oder ein Eigenschaftsname angegeben werden, es können jedoch nicht beide angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a8486-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="a8486-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter Definieren von Bedingungen für den Fall, [dass ein Ansichts Eintrag oder Element verwendet wird](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a8486-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a8486-123">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a8486-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8486-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a8486-124">See Also</span></span>

[<span data-ttu-id="a8486-125">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="a8486-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a8486-126">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="a8486-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a8486-127">PropertyName-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="a8486-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="a8486-128">Selectioncondition-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="a8486-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a8486-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a8486-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
