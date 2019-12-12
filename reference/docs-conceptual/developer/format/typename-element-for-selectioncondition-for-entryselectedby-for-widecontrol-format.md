---
title: Typname-Element für selectioncondition für entryselectedby für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368059"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="9c780-102">Element „TypeName“ für SelectionCondition für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9c780-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="9c780-103">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9c780-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9c780-104">Wenn dieser Typ vorhanden ist, wird die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="9c780-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="9c780-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) entryselectedby-Element für wideentry (Format) selectioncondition-Element für Entryselectedby für wideentry (Format) Typname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9c780-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9c780-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c780-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9c780-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9c780-107">Attributes and Elements</span></span>

<span data-ttu-id="9c780-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9c780-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c780-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9c780-109">Attributes</span></span>

<span data-ttu-id="9c780-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9c780-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9c780-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9c780-111">Child Elements</span></span>

<span data-ttu-id="9c780-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="9c780-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c780-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9c780-113">Parent Elements</span></span>

|<span data-ttu-id="9c780-114">Element</span><span class="sxs-lookup"><span data-stu-id="9c780-114">Element</span></span>|<span data-ttu-id="9c780-115">Description</span><span class="sxs-lookup"><span data-stu-id="9c780-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9c780-116">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9c780-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="9c780-117">Definiert die Bedingung, die für die Verwendung dieses breiten Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="9c780-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9c780-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="9c780-118">Text Value</span></span>

<span data-ttu-id="9c780-119">Geben Sie den voll qualifizierten Namen des .net-Typs an, z. b. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="9c780-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9c780-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9c780-120">Remarks</span></span>

<span data-ttu-id="9c780-121">Mit der Auswahlbedingung kann ein .NET-Typ oder ein Auswahl Satz angegeben werden, aber nicht beides.</span><span class="sxs-lookup"><span data-stu-id="9c780-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="9c780-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9c780-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9c780-123">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="9c780-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9c780-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9c780-124">See Also</span></span>

[<span data-ttu-id="9c780-125">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="9c780-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="9c780-126">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="9c780-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9c780-127">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9c780-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="9c780-128">Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="9c780-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="9c780-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="9c780-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
