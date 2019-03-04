---
title: TypeName-Element für SelectionCondition für EntrySelectedBy für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856496"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="3fbb5-102">Element „TypeName“ für SelectionCondition für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3fbb5-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="3fbb5-103">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="3fbb5-104">Wenn dieses Typs vorhanden ist, die Bedingung ist erfüllt, und die Tabellenzeile verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="3fbb5-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy Konfigurationselement für TableRowEntry (Format) SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format) TypeName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3fbb5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3fbb5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3fbb5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3fbb5-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3fbb5-107">Attributes and Elements</span></span>

<span data-ttu-id="3fbb5-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3fbb5-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3fbb5-109">Attributes</span></span>

<span data-ttu-id="3fbb5-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3fbb5-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3fbb5-111">Child Elements</span></span>

<span data-ttu-id="3fbb5-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3fbb5-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3fbb5-113">Parent Elements</span></span>

|<span data-ttu-id="3fbb5-114">Element</span><span class="sxs-lookup"><span data-stu-id="3fbb5-114">Element</span></span>|<span data-ttu-id="3fbb5-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3fbb5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3fbb5-116">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3fbb5-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="3fbb5-117">Definiert die Bedingung, die für diese Tabellenzeile zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3fbb5-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="3fbb5-118">Text Value</span></span>

<span data-ttu-id="3fbb5-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="3fbb5-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3fbb5-120">Remarks</span></span>

<span data-ttu-id="3fbb5-121">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="3fbb5-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="3fbb5-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3fbb5-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="3fbb5-123">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3fbb5-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3fbb5-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3fbb5-124">See Also</span></span>

[<span data-ttu-id="3fbb5-125">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="3fbb5-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3fbb5-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="3fbb5-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="3fbb5-127">SelectionCondition-Element für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3fbb5-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3fbb5-128">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3fbb5-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="3fbb5-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fbb5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
