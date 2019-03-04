---
title: PropertyName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860986"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="19201-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19201-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="19201-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="19201-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="19201-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Tabelleneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="19201-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="19201-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy Konfigurationselement für TableRowEntry (Format) SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)-PropertyName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19201-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19201-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="19201-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19201-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="19201-107">Attributes and Elements</span></span>

<span data-ttu-id="19201-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="19201-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19201-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="19201-109">Attributes</span></span>

<span data-ttu-id="19201-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="19201-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19201-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="19201-111">Child Elements</span></span>

<span data-ttu-id="19201-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="19201-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19201-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="19201-113">Parent Elements</span></span>

|<span data-ttu-id="19201-114">Element</span><span class="sxs-lookup"><span data-stu-id="19201-114">Element</span></span>|<span data-ttu-id="19201-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="19201-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19201-116">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19201-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="19201-117">Definiert die Bedingung, die für diesen Tabelleneintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="19201-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19201-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="19201-118">Text Value</span></span>

<span data-ttu-id="19201-119">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="19201-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="19201-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="19201-120">Remarks</span></span>

<span data-ttu-id="19201-121">Die auswahlbedingung muss mindestens einen Eigenschaftennamen oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="19201-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="19201-122">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="19201-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="19201-123">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="19201-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19201-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="19201-124">See Also</span></span>

[<span data-ttu-id="19201-125">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="19201-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="19201-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="19201-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="19201-127">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19201-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="19201-128">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19201-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="19201-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="19201-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
