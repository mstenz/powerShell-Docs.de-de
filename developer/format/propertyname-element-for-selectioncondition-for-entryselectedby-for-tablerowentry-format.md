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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064661"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="f25b4-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f25b4-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="f25b4-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="f25b4-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="f25b4-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Tabelleneintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="f25b4-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="f25b4-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy Konfigurationselement für TableRowEntry (Format) SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)-PropertyName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f25b4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f25b4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f25b4-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f25b4-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f25b4-107">Attributes and Elements</span></span>

<span data-ttu-id="f25b4-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="f25b4-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f25b4-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f25b4-109">Attributes</span></span>

<span data-ttu-id="f25b4-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="f25b4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f25b4-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f25b4-111">Child Elements</span></span>

<span data-ttu-id="f25b4-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="f25b4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f25b4-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f25b4-113">Parent Elements</span></span>

|<span data-ttu-id="f25b4-114">Element</span><span class="sxs-lookup"><span data-stu-id="f25b4-114">Element</span></span>|<span data-ttu-id="f25b4-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f25b4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f25b4-116">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f25b4-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f25b4-117">Definiert die Bedingung, die für diesen Tabelleneintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="f25b4-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f25b4-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="f25b4-118">Text Value</span></span>

<span data-ttu-id="f25b4-119">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f25b4-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f25b4-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f25b4-120">Remarks</span></span>

<span data-ttu-id="f25b4-121">Die auswahlbedingung muss mindestens einen Eigenschaftennamen oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="f25b4-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="f25b4-122">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f25b4-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f25b4-123">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f25b4-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f25b4-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f25b4-124">See Also</span></span>

[<span data-ttu-id="f25b4-125">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="f25b4-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f25b4-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="f25b4-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f25b4-127">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f25b4-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f25b4-128">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f25b4-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f25b4-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="f25b4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
