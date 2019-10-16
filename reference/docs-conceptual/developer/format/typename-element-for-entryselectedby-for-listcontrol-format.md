---
title: Tyname-Element für entryselectedby für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361659"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="7932b-102">Element „TypeName“ für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7932b-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="7932b-103">Gibt einen .NET-Typ an, der diesen Eintrag in der Listenansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="7932b-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="7932b-104">Es gibt keine Beschränkung für die Anzahl von Typen, die für einen Listeneintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="7932b-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="7932b-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) entryselectedby-Element für ListEntry (Format) Typname-Element für Entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7932b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7932b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7932b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7932b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7932b-107">Attributes and Elements</span></span>

<span data-ttu-id="7932b-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7932b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7932b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7932b-109">Attributes</span></span>

<span data-ttu-id="7932b-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="7932b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7932b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7932b-111">Child Elements</span></span>

<span data-ttu-id="7932b-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="7932b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7932b-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7932b-113">Parent Elements</span></span>

|<span data-ttu-id="7932b-114">Element</span><span class="sxs-lookup"><span data-stu-id="7932b-114">Element</span></span>|<span data-ttu-id="7932b-115">Description</span><span class="sxs-lookup"><span data-stu-id="7932b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7932b-116">Entryselectedby-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7932b-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="7932b-117">Definiert die .NET-Typen, die diesen Listeneintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="7932b-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7932b-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="7932b-118">Text Value</span></span>

<span data-ttu-id="7932b-119">Geben Sie den voll qualifizierten Namen des .net-Typs an, z. b. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="7932b-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7932b-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7932b-120">Remarks</span></span>

<span data-ttu-id="7932b-121">Für jeden Listeneintrag muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="7932b-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="7932b-122">Weitere Informationen zur Verwendung dieses Elements in einer Listenansicht finden Sie in der [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7932b-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7932b-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7932b-123">Example</span></span>

<span data-ttu-id="7932b-124">Im folgenden Beispiel wird gezeigt, wie Sie einen Auswahl Satz für einen Eintrag einer Listenansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="7932b-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="7932b-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7932b-125">See Also</span></span>

[<span data-ttu-id="7932b-126">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="7932b-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7932b-127">Entryselectedby-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7932b-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="7932b-128">Selectionsetname-Element für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="7932b-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="7932b-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="7932b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
