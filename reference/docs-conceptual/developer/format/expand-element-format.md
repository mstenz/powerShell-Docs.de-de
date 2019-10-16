---
title: Expand-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368739"
---
# <a name="expand-element-format"></a><span data-ttu-id="fae94-102">Element „Expand“ (Format)</span><span class="sxs-lookup"><span data-stu-id="fae94-102">Expand Element (Format)</span></span>

<span data-ttu-id="fae94-103">Gibt an, wie das Sammlungsobjekt für diese Definition erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="fae94-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="fae94-104">Configuration-Element (Format) DefaultSettings-Element (Format) enumerableexpand-Element (Format) enumerableweiterung-Element (Format) Expand Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fae94-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fae94-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fae94-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fae94-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fae94-106">Attributes and Elements</span></span>

<span data-ttu-id="fae94-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Expand`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="fae94-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fae94-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="fae94-108">Attributes</span></span>

<span data-ttu-id="fae94-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="fae94-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fae94-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fae94-110">Child Elements</span></span>

<span data-ttu-id="fae94-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="fae94-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fae94-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fae94-112">Parent Elements</span></span>

|<span data-ttu-id="fae94-113">Element</span><span class="sxs-lookup"><span data-stu-id="fae94-113">Element</span></span>|<span data-ttu-id="fae94-114">Description</span><span class="sxs-lookup"><span data-stu-id="fae94-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fae94-115">Enumerableweiterung-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fae94-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="fae94-116">Definiert, wie bestimmte .net-Auflistungs Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fae94-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fae94-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="fae94-117">Text Value</span></span>

<span data-ttu-id="fae94-118">Geben Sie einen der folgenden Werte an:</span><span class="sxs-lookup"><span data-stu-id="fae94-118">Specify one of the following values:</span></span>

- <span data-ttu-id="fae94-119">Enumonly: zeigt nur die Eigenschaften der Objekte in der Auflistung an.</span><span class="sxs-lookup"><span data-stu-id="fae94-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="fae94-120">Coreonly: zeigt nur die Eigenschaften des Auflistungs Objekts an.</span><span class="sxs-lookup"><span data-stu-id="fae94-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="fae94-121">Beides: zeigt die Eigenschaften der Objekte in der Auflistung und die Eigenschaften des Auflistungs Objekts an.</span><span class="sxs-lookup"><span data-stu-id="fae94-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="fae94-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fae94-122">Remarks</span></span>

<span data-ttu-id="fae94-123">Dieses Element wird verwendet, um zu definieren, wie Auflistungs Objekte und die Objekte in der Auflistung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fae94-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="fae94-124">In diesem Fall bezieht sich ein Auflistungs Objekt auf jedes Objekt, das die **System. Collections. ICollection** -Schnittstelle unterstützt.</span><span class="sxs-lookup"><span data-stu-id="fae94-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="fae94-125">Standardmäßig werden nur die Eigenschaften der Objekte in der Auflistung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fae94-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="fae94-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fae94-126">See Also</span></span>

[<span data-ttu-id="fae94-127">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="fae94-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
