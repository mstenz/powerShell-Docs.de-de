---
title: EnumerableExpansion-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066140"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="176c8-102">Element „EnumerableExpansion“ (Format)</span><span class="sxs-lookup"><span data-stu-id="176c8-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="176c8-103">Definiert, wie .NET Datenbanksammlung Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="176c8-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="176c8-104">-Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="176c8-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="176c8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="176c8-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="176c8-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="176c8-106">Attributes and Elements</span></span>

<span data-ttu-id="176c8-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EnumerableExpansion` Element.</span><span class="sxs-lookup"><span data-stu-id="176c8-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="176c8-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="176c8-108">Attributes</span></span>

<span data-ttu-id="176c8-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="176c8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="176c8-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="176c8-110">Child Elements</span></span>

|<span data-ttu-id="176c8-111">Element</span><span class="sxs-lookup"><span data-stu-id="176c8-111">Element</span></span>|<span data-ttu-id="176c8-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="176c8-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="176c8-113">EntrySelectedBy-Element für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="176c8-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="176c8-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="176c8-114">Optional element.</span></span><br /><br /> <span data-ttu-id="176c8-115">Definiert, welche .NET Sammlung Objekte nach dieser Definition erweitert werden.</span><span class="sxs-lookup"><span data-stu-id="176c8-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="176c8-116">Erweitern Sie (Format)-Element</span><span class="sxs-lookup"><span data-stu-id="176c8-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="176c8-117">Gibt an, wie das Objekt für diese Definition erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="176c8-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="176c8-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="176c8-118">Parent Elements</span></span>

|<span data-ttu-id="176c8-119">Element</span><span class="sxs-lookup"><span data-stu-id="176c8-119">Element</span></span>|<span data-ttu-id="176c8-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="176c8-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="176c8-121">EnumerableExpansions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="176c8-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="176c8-122">Definiert den verschiedenen Möglichkeiten, .NET-Auflistung, die Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="176c8-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="176c8-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="176c8-123">Remarks</span></span>

<span data-ttu-id="176c8-124">Dieses Element wird verwendet, um zu definieren, Auflistungsobjekte und die Objekte in der Auflistung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="176c8-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="176c8-125">In diesem Fall ein Auflistungsobjekt verweist auf ein Objekt, das unterstützt die **System.Collections.ICollection** Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="176c8-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="176c8-126">Standardmäßig werden nur die Eigenschaften der Objekte in der Auflistung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="176c8-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="176c8-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="176c8-127">See Also</span></span>

[<span data-ttu-id="176c8-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="176c8-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
