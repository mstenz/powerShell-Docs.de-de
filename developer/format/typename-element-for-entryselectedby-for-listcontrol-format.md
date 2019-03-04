---
title: TypeName-Element für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856106"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="6d485-102">Element „TypeName“ für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6d485-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="6d485-103">Gibt einen .NET-Typ, der diesen Eintrag der Listenansicht wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="6d485-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="6d485-104">Es gibt keine Beschränkung der Anzahl von Typen, die für einen Eintrag für eine angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="6d485-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="6d485-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für TypeName-Element für ListEntry (Format) EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6d485-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d485-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d485-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d485-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6d485-107">Attributes and Elements</span></span>

<span data-ttu-id="6d485-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="6d485-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d485-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6d485-109">Attributes</span></span>

<span data-ttu-id="6d485-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6d485-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d485-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6d485-111">Child Elements</span></span>

<span data-ttu-id="6d485-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="6d485-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6d485-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6d485-113">Parent Elements</span></span>

|<span data-ttu-id="6d485-114">Element</span><span class="sxs-lookup"><span data-stu-id="6d485-114">Element</span></span>|<span data-ttu-id="6d485-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6d485-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d485-116">EntrySelectedBy-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d485-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="6d485-117">Definiert die .NET-Typen, die diesen Eintrag der Liste oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="6d485-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6d485-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="6d485-118">Text Value</span></span>

<span data-ttu-id="6d485-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="6d485-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6d485-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6d485-120">Remarks</span></span>

<span data-ttu-id="6d485-121">Jeder Listeneintrag muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="6d485-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="6d485-122">Weitere Informationen zur Verwendung dieses Elements in einer Listenansicht finden Sie unter [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="6d485-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6d485-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6d485-123">Example</span></span>

<span data-ttu-id="6d485-124">Das folgende Beispiel zeigt, wie Sie eine Auswahl, legen Sie für einen Eintrag in einer Listenansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="6d485-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="6d485-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6d485-125">See Also</span></span>

[<span data-ttu-id="6d485-126">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="6d485-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6d485-127">EntrySelectedBy-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d485-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="6d485-128">SelectionSetName-Element für EnrtySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="6d485-128">SelectionSetName Element for EnrtySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="6d485-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d485-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
