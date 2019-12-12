---
title: PropertyName-Element für selectioncondition für entryselectedby für tablerowentry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364999"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="318bd-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="318bd-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="318bd-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="318bd-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="318bd-104">Wenn diese Eigenschaft vorhanden ist oder als zu `true`ausgewertet wird, wird die Bedingung erfüllt, und der Tabelleneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="318bd-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="318bd-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element für tablerowentry (Format) Selectioncondition-Element für entryselectedby für tablerowentry (Format) propertyName-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="318bd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="318bd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="318bd-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="318bd-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="318bd-107">Attributes and Elements</span></span>

<span data-ttu-id="318bd-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="318bd-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="318bd-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="318bd-109">Attributes</span></span>

<span data-ttu-id="318bd-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="318bd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="318bd-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="318bd-111">Child Elements</span></span>

<span data-ttu-id="318bd-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="318bd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="318bd-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="318bd-113">Parent Elements</span></span>

|<span data-ttu-id="318bd-114">Element</span><span class="sxs-lookup"><span data-stu-id="318bd-114">Element</span></span>|<span data-ttu-id="318bd-115">Description</span><span class="sxs-lookup"><span data-stu-id="318bd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="318bd-116">Selectioncondition-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="318bd-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="318bd-117">Definiert die Bedingung, die für die Verwendung dieses Tabellen Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="318bd-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="318bd-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="318bd-118">Text Value</span></span>

<span data-ttu-id="318bd-119">Geben Sie den Namen der .net-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="318bd-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="318bd-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="318bd-120">Remarks</span></span>

<span data-ttu-id="318bd-121">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="318bd-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="318bd-122">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="318bd-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="318bd-123">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="318bd-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="318bd-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="318bd-124">See Also</span></span>

[<span data-ttu-id="318bd-125">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="318bd-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="318bd-126">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="318bd-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="318bd-127">ScriptBlock-Element für selectioncondition für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="318bd-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="318bd-128">Selectioncondition-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="318bd-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="318bd-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="318bd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
