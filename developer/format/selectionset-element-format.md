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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076309"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="7641d-102">Element „SelectionSet“ (Format)</span><span class="sxs-lookup"><span data-stu-id="7641d-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="7641d-103">Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7641d-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="7641d-104">-Element (Format) SelectionSets-Element (Format) SelectionSet Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="7641d-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7641d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7641d-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7641d-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7641d-106">Attributes and Elements</span></span>

<span data-ttu-id="7641d-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSet` Element.</span><span class="sxs-lookup"><span data-stu-id="7641d-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="7641d-108">Jede Auswahl-Gruppe muss einen Namen haben, und es muss die .NET Objekte der Gruppe angeben.</span><span class="sxs-lookup"><span data-stu-id="7641d-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="7641d-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7641d-109">Attributes</span></span>

<span data-ttu-id="7641d-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="7641d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7641d-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7641d-111">Child Elements</span></span>

|<span data-ttu-id="7641d-112">Element</span><span class="sxs-lookup"><span data-stu-id="7641d-112">Element</span></span>|<span data-ttu-id="7641d-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7641d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7641d-114">Name-Element für SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="7641d-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="7641d-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="7641d-115">Required element.</span></span><br /><br /> <span data-ttu-id="7641d-116">Gibt den Namen verwendet, um den Auswahlsatz zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="7641d-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="7641d-117">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7641d-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="7641d-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="7641d-118">Required element.</span></span><br /><br /> <span data-ttu-id="7641d-119">Definiert die .NET Objekte, die in der Auswahl festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="7641d-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7641d-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7641d-120">Parent Elements</span></span>

|<span data-ttu-id="7641d-121">Element</span><span class="sxs-lookup"><span data-stu-id="7641d-121">Element</span></span>|<span data-ttu-id="7641d-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7641d-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7641d-123">Format des SelectionSets</span><span class="sxs-lookup"><span data-stu-id="7641d-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="7641d-124">Definiert die allgemeine Sätze von .NET-Objekten, die von allen Ansichten des die Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="7641d-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7641d-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7641d-125">Remarks</span></span>

<span data-ttu-id="7641d-126">Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten.</span><span class="sxs-lookup"><span data-stu-id="7641d-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="7641d-127">Wenn Sie Ihre Ansichten definieren, können Sie den Satz von Objekten angeben, mit dem Namen der Markierung anstelle Auflisten aller Objekte in jeder Ansicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="7641d-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="7641d-128">Typische Auswahl Sets werden anhand ihres Namens angegeben, bei der Definition der Ansichten die Formatierungsdatei oder die Definitionen der Ansichten.</span><span class="sxs-lookup"><span data-stu-id="7641d-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="7641d-129">In diesen Fällen die `SelectionSetName` untergeordnetes Element von der `ViewSelectedBy` und `EntrySelectedBy` Elemente gibt den Satz verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7641d-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="7641d-130">Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7641d-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="7641d-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7641d-131">Example</span></span>

<span data-ttu-id="7641d-132">Das folgende Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.</span><span class="sxs-lookup"><span data-stu-id="7641d-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7641d-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7641d-133">See Also</span></span>

[<span data-ttu-id="7641d-134">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="7641d-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7641d-135">Name-Element der SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="7641d-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="7641d-136">SelectionSets-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7641d-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="7641d-137">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7641d-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="7641d-138">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="7641d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
