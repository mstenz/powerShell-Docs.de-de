---
title: Enumerableexpansions-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363299"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="90a8b-102">Element „EnumerableExpansions“ (Format)</span><span class="sxs-lookup"><span data-stu-id="90a8b-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="90a8b-103">Definiert, wie .net-Auflistungs Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="90a8b-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="90a8b-104">Configuration-Element (Format) DefaultSettings-Element (Format) enumerableerweiterungen-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="90a8b-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="90a8b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="90a8b-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90a8b-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="90a8b-106">Attributes and Elements</span></span>

<span data-ttu-id="90a8b-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EnumerableExpansions`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="90a8b-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="90a8b-108">Es gibt keine Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="90a8b-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="90a8b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="90a8b-109">Attributes</span></span>

<span data-ttu-id="90a8b-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="90a8b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="90a8b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="90a8b-111">Child Elements</span></span>

|<span data-ttu-id="90a8b-112">Element</span><span class="sxs-lookup"><span data-stu-id="90a8b-112">Element</span></span>|<span data-ttu-id="90a8b-113">Description</span><span class="sxs-lookup"><span data-stu-id="90a8b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90a8b-114">Enumerableweiterung-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="90a8b-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="90a8b-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="90a8b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="90a8b-116">Definiert die spezifischen .net-Auflistungs Objekte, die erweitert werden, wenn Sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="90a8b-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90a8b-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="90a8b-117">Parent Elements</span></span>

|<span data-ttu-id="90a8b-118">Element</span><span class="sxs-lookup"><span data-stu-id="90a8b-118">Element</span></span>|<span data-ttu-id="90a8b-119">Description</span><span class="sxs-lookup"><span data-stu-id="90a8b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="90a8b-120">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="90a8b-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="90a8b-121">Definiert allgemeine Einstellungen, die für alle Sichten der Formatierungs Datei gelten.</span><span class="sxs-lookup"><span data-stu-id="90a8b-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90a8b-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="90a8b-122">Remarks</span></span>

<span data-ttu-id="90a8b-123">Dieses Element wird verwendet, um zu definieren, wie Auflistungs Objekte und die Objekte in der Auflistung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="90a8b-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="90a8b-124">In diesem Fall bezieht sich ein Auflistungs Objekt auf jedes Objekt, das die **System. Collections. ICollection** -Schnittstelle unterstützt.</span><span class="sxs-lookup"><span data-stu-id="90a8b-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="90a8b-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="90a8b-125">See Also</span></span>

[<span data-ttu-id="90a8b-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="90a8b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
