---
title: SelectionSet-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861156"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="12413-102">Element „SelectionSet“ (Format)</span><span class="sxs-lookup"><span data-stu-id="12413-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="12413-103">Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="12413-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="12413-104">-Element (Format) SelectionSets-Element (Format) SelectionSet Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="12413-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="12413-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="12413-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12413-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="12413-106">Attributes and Elements</span></span>

<span data-ttu-id="12413-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSet` Element.</span><span class="sxs-lookup"><span data-stu-id="12413-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="12413-108">Jede Auswahl-Gruppe muss einen Namen haben, und es muss die .NET Objekte der Gruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="12413-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="12413-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="12413-109">Attributes</span></span>

<span data-ttu-id="12413-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="12413-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="12413-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="12413-111">Child Elements</span></span>

|<span data-ttu-id="12413-112">Element</span><span class="sxs-lookup"><span data-stu-id="12413-112">Element</span></span>|<span data-ttu-id="12413-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="12413-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12413-114">Name-Element für SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="12413-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="12413-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="12413-115">Required element.</span></span><br /><br /> <span data-ttu-id="12413-116">Gibt den Namen verwendet, um den Auswahlsatz zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="12413-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="12413-117">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="12413-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="12413-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="12413-118">Required element.</span></span><br /><br /> <span data-ttu-id="12413-119">Definiert die .NET Objekte, die in der Auswahl festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="12413-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="12413-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="12413-120">Parent Elements</span></span>

|<span data-ttu-id="12413-121">Element</span><span class="sxs-lookup"><span data-stu-id="12413-121">Element</span></span>|<span data-ttu-id="12413-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="12413-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="12413-123">Format des SelectionSets</span><span class="sxs-lookup"><span data-stu-id="12413-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="12413-124">Definiert die allgemeine Sätze von .NET-Objekten, die von allen Ansichten des die Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="12413-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="12413-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="12413-125">Remarks</span></span>

<span data-ttu-id="12413-126">Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten.</span><span class="sxs-lookup"><span data-stu-id="12413-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="12413-127">Wenn Sie Ihre Ansichten definieren, können Sie den Satz von Objekten angeben, mit dem Namen der Markierung anstelle Auflisten aller Objekte in jeder Ansicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="12413-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="12413-128">Typische Auswahl Sets werden anhand ihres Namens angegeben, bei der Definition der Ansichten die Formatierungsdatei oder die Definitionen der Ansichten.</span><span class="sxs-lookup"><span data-stu-id="12413-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="12413-129">In diesen Fällen die `SelectionSetName` untergeordnetes Element von der `ViewSelectedBy` und `EntrySelectedBy` Elemente gibt den Satz verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="12413-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="12413-130">Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="12413-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="12413-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="12413-131">Example</span></span>

<span data-ttu-id="12413-132">Das folgende Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.</span><span class="sxs-lookup"><span data-stu-id="12413-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="12413-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="12413-133">See Also</span></span>

[<span data-ttu-id="12413-134">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="12413-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="12413-135">Name-Element der SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="12413-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="12413-136">SelectionSets-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="12413-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="12413-137">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="12413-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="12413-138">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="12413-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
