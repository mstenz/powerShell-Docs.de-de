---
title: Erweitern Sie (Format)-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858576"
---
# <a name="expand-element-format"></a><span data-ttu-id="4d87d-102">Element „Expand“ (Format)</span><span class="sxs-lookup"><span data-stu-id="4d87d-102">Expand Element (Format)</span></span>

<span data-ttu-id="4d87d-103">Gibt an, wie das Objekt für diese Definition erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="4d87d-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="4d87d-104">Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion Konfigurationselement (Format) erweitern (Format)-Element</span><span class="sxs-lookup"><span data-stu-id="4d87d-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d87d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4d87d-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d87d-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="4d87d-106">Attributes and Elements</span></span>

<span data-ttu-id="4d87d-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Expand` Element.</span><span class="sxs-lookup"><span data-stu-id="4d87d-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d87d-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="4d87d-108">Attributes</span></span>

<span data-ttu-id="4d87d-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="4d87d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d87d-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4d87d-110">Child Elements</span></span>

<span data-ttu-id="4d87d-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="4d87d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4d87d-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4d87d-112">Parent Elements</span></span>

|<span data-ttu-id="4d87d-113">Element</span><span class="sxs-lookup"><span data-stu-id="4d87d-113">Element</span></span>|<span data-ttu-id="4d87d-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4d87d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d87d-115">EnumerableExpansion-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4d87d-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="4d87d-116">Definiert, wie .NET Datenbanksammlung Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4d87d-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4d87d-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="4d87d-117">Text Value</span></span>

<span data-ttu-id="4d87d-118">Geben Sie eine der folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="4d87d-118">Specify one of the following values:</span></span>

- <span data-ttu-id="4d87d-119">EnumOnly: Zeigt nur die Eigenschaften der Objekte in der Auflistung.</span><span class="sxs-lookup"><span data-stu-id="4d87d-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="4d87d-120">CoreOnly: Zeigt nur die Eigenschaften des Auflistungsobjekts.</span><span class="sxs-lookup"><span data-stu-id="4d87d-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="4d87d-121">Beide: Zeigt die Eigenschaften der Objekte in der Auflistung und die Eigenschaften des Auflistungsobjekts.</span><span class="sxs-lookup"><span data-stu-id="4d87d-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d87d-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4d87d-122">Remarks</span></span>

<span data-ttu-id="4d87d-123">Dieses Element wird verwendet, um zu definieren, Auflistungsobjekte und die Objekte in der Auflistung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4d87d-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="4d87d-124">In diesem Fall ein Auflistungsobjekt verweist auf ein Objekt, das unterstützt die **System.Collections.ICollection** Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="4d87d-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="4d87d-125">Standardmäßig werden nur die Eigenschaften der Objekte in der Auflistung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4d87d-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d87d-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4d87d-126">See Also</span></span>

[<span data-ttu-id="4d87d-127">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d87d-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
