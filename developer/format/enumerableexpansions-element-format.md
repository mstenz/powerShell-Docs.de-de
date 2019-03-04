---
title: EnumerableExpansions-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860256"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="7dd1c-102">Element „EnumerableExpansions“ (Format)</span><span class="sxs-lookup"><span data-stu-id="7dd1c-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="7dd1c-103">Definiert, wie .NET Auflistungsobjekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="7dd1c-104">-Element (Format) DefaultSettings-Element (Format) EnumerableExpansions Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="7dd1c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7dd1c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7dd1c-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7dd1c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7dd1c-106">Attributes and Elements</span></span>

<span data-ttu-id="7dd1c-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EnumerableExpansions` Element.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="7dd1c-108">Es gibt keine Beschränkung der Anzahl von untergeordneten Elementen, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="7dd1c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7dd1c-109">Attributes</span></span>

<span data-ttu-id="7dd1c-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7dd1c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7dd1c-111">Child Elements</span></span>

|<span data-ttu-id="7dd1c-112">Element</span><span class="sxs-lookup"><span data-stu-id="7dd1c-112">Element</span></span>|<span data-ttu-id="7dd1c-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7dd1c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7dd1c-114">EnumerableExpansion-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7dd1c-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="7dd1c-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7dd1c-116">Definiert die spezifische .NET Auflistungsobjekte, die erweitert werden, wenn sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7dd1c-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7dd1c-117">Parent Elements</span></span>

|<span data-ttu-id="7dd1c-118">Element</span><span class="sxs-lookup"><span data-stu-id="7dd1c-118">Element</span></span>|<span data-ttu-id="7dd1c-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7dd1c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7dd1c-120">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7dd1c-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="7dd1c-121">Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7dd1c-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7dd1c-122">Remarks</span></span>

<span data-ttu-id="7dd1c-123">Dieses Element wird verwendet, um zu definieren, Auflistungsobjekte und die Objekte in der Auflistung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="7dd1c-124">In diesem Fall ein Auflistungsobjekt verweist auf ein Objekt, das unterstützt die **System.Collections.ICollection** Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="7dd1c-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7dd1c-125">See Also</span></span>

[<span data-ttu-id="7dd1c-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="7dd1c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
