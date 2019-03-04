---
title: Element-Typen für SelectionSet (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862376"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="9eee1-102">Element „Types“ für SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="9eee1-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="9eee1-103">Definiert die .NET Objekte, die in der Auswahl festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="9eee1-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="9eee1-104">-Element (Format) SelectionSets-Element (Format) SelectionSet Konfigurationselement (Format)-Typen (Format)-Element</span><span class="sxs-lookup"><span data-stu-id="9eee1-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9eee1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9eee1-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9eee1-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9eee1-106">Attributes and Elements</span></span>

<span data-ttu-id="9eee1-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Types` Element.</span><span class="sxs-lookup"><span data-stu-id="9eee1-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="9eee1-108">Es muss mindestens ein untergeordnetes Element vorhanden sein, aber es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="9eee1-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="9eee1-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9eee1-109">Attributes</span></span>

<span data-ttu-id="9eee1-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9eee1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9eee1-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9eee1-111">Child Elements</span></span>

|<span data-ttu-id="9eee1-112">Element</span><span class="sxs-lookup"><span data-stu-id="9eee1-112">Element</span></span>|<span data-ttu-id="9eee1-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9eee1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9eee1-114">TypeName-Element der Typen (Format)</span><span class="sxs-lookup"><span data-stu-id="9eee1-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="9eee1-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="9eee1-115">Required element.</span></span><br /><br /> <span data-ttu-id="9eee1-116">Gibt das .NET-Objekt, das auf die Auswahl gehört.</span><span class="sxs-lookup"><span data-stu-id="9eee1-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9eee1-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9eee1-117">Parent Elements</span></span>

|<span data-ttu-id="9eee1-118">Element</span><span class="sxs-lookup"><span data-stu-id="9eee1-118">Element</span></span>|<span data-ttu-id="9eee1-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9eee1-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9eee1-120">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9eee1-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="9eee1-121">Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9eee1-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9eee1-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9eee1-122">Remarks</span></span>

<span data-ttu-id="9eee1-123">Die von diesem Element definierten Objekte bilden einen Auswahlsatz, die durch eine Sicht, indem Sie eine Definition einer Sicht verwendet werden kann (Ansichten können hat mehrere Definitionen), oder wenn Sie eine auswahlbedingung angeben.</span><span class="sxs-lookup"><span data-stu-id="9eee1-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="9eee1-124">Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="9eee1-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="9eee1-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9eee1-125">Example</span></span>

<span data-ttu-id="9eee1-126">Dieses Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.</span><span class="sxs-lookup"><span data-stu-id="9eee1-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="9eee1-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9eee1-127">See Also</span></span>

[<span data-ttu-id="9eee1-128">Definieren von Gruppen von Objekten</span><span class="sxs-lookup"><span data-stu-id="9eee1-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="9eee1-129">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9eee1-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="9eee1-130">TypeName-Element der Typen (Format)</span><span class="sxs-lookup"><span data-stu-id="9eee1-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="9eee1-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="9eee1-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
