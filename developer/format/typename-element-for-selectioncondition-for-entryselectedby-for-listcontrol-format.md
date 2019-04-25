---
title: TypeName-Element für SelectionCondition für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083857"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="5b031-102">Element „TypeName“ für SelectionCondition für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b031-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="5b031-103">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="5b031-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="5b031-104">Wenn dieses Typs vorhanden ist, wird der Listeneintrag verwendet.</span><span class="sxs-lookup"><span data-stu-id="5b031-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="5b031-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListEntries für ListControl (Format) EntrySelectedBy-Element für ListEntry für ListControl (Format) SelectionCondition-Element für EntrySelectedBy für ListControl (Format) TypeName-Element für SelectionCondition für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b031-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b031-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b031-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b031-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5b031-107">Attributes and Elements</span></span>

<span data-ttu-id="5b031-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="5b031-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b031-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5b031-109">Attributes</span></span>

<span data-ttu-id="5b031-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="5b031-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b031-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5b031-111">Child Elements</span></span>

<span data-ttu-id="5b031-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="5b031-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b031-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5b031-113">Parent Elements</span></span>

|<span data-ttu-id="5b031-114">Element</span><span class="sxs-lookup"><span data-stu-id="5b031-114">Element</span></span>|<span data-ttu-id="5b031-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5b031-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b031-116">SelectionCondition-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b031-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="5b031-117">Definiert die Bedingung, die für diesen Eintrag der Liste zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="5b031-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b031-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="5b031-118">Text Value</span></span>

<span data-ttu-id="5b031-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="5b031-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b031-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5b031-120">Remarks</span></span>

<span data-ttu-id="5b031-121">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5b031-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="5b031-122">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5b031-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5b031-123">Weitere Informationen zu anderen die Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5b031-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b031-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5b031-124">See Also</span></span>

[<span data-ttu-id="5b031-125">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="5b031-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5b031-126">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="5b031-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5b031-127">SelectionCondition-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b031-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="5b031-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b031-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
