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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368379"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="6d4bf-102">Element „SelectionSet“ (Format)</span><span class="sxs-lookup"><span data-stu-id="6d4bf-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="6d4bf-103">Definiert einen Satz von .NET-Objekten, auf die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="6d4bf-104">Configuration-Element (Format) selectionsets-Element (Format) SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6d4bf-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d4bf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d4bf-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d4bf-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6d4bf-106">Attributes and Elements</span></span>

<span data-ttu-id="6d4bf-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `SelectionSet`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="6d4bf-108">Jeder Auswahl Satz muss über einen Namen verfügen, und er muss die .NET-Objekte des Satzes angeben.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d4bf-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6d4bf-109">Attributes</span></span>

<span data-ttu-id="6d4bf-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d4bf-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6d4bf-111">Child Elements</span></span>

|<span data-ttu-id="6d4bf-112">Element</span><span class="sxs-lookup"><span data-stu-id="6d4bf-112">Element</span></span>|<span data-ttu-id="6d4bf-113">Description</span><span class="sxs-lookup"><span data-stu-id="6d4bf-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d4bf-114">Name-Element für SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="6d4bf-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="6d4bf-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-115">Required element.</span></span><br /><br /> <span data-ttu-id="6d4bf-116">Gibt den Namen an, mit dem auf den Auswahl Satz verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="6d4bf-117">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6d4bf-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="6d4bf-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-118">Required element.</span></span><br /><br /> <span data-ttu-id="6d4bf-119">Definiert die .NET-Objekte, die sich im Auswahl Satz befinden.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6d4bf-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6d4bf-120">Parent Elements</span></span>

|<span data-ttu-id="6d4bf-121">Element</span><span class="sxs-lookup"><span data-stu-id="6d4bf-121">Element</span></span>|<span data-ttu-id="6d4bf-122">Description</span><span class="sxs-lookup"><span data-stu-id="6d4bf-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d4bf-123">Selectionsets-Element Format</span><span class="sxs-lookup"><span data-stu-id="6d4bf-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="6d4bf-124">Definiert die allgemeinen Sätze von .NET-Objekten, die von allen Sichten der Formatierungs Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6d4bf-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6d4bf-125">Remarks</span></span>

<span data-ttu-id="6d4bf-126">Sie können Auswahl Sätze verwenden, wenn Sie über einen Satz verwandter Objekte verfügen, auf die Sie verweisen möchten, indem Sie einen einzelnen Namen verwenden, z. b. eine Gruppe von Objekten, die durch Vererbung verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="6d4bf-127">Wenn Sie die Ansichten definieren, können Sie den Satz von-Objekten angeben, indem Sie den Namen des Auswahl Satzes verwenden, anstatt alle Objekte in jeder Ansicht aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="6d4bf-128">Beim Definieren der Sichten der Formatierungs Datei oder der Definitionen der Sichten werden allgemeine Auswahl Sätze durch ihren Namen angegeben.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="6d4bf-129">In diesen Fällen gibt das untergeordnete `SelectionSetName`-Element der `ViewSelectedBy`-und `EntrySelectedBy`-Elemente die zu verwendende Gruppe an.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="6d4bf-130">Weitere Informationen zu Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6d4bf-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6d4bf-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6d4bf-131">Example</span></span>

<span data-ttu-id="6d4bf-132">Das folgende Beispiel zeigt ein `SelectionSet`-Element, das vier .NET-Typen definiert.</span><span class="sxs-lookup"><span data-stu-id="6d4bf-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6d4bf-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6d4bf-133">See Also</span></span>

[<span data-ttu-id="6d4bf-134">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="6d4bf-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6d4bf-135">Name-Element von SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="6d4bf-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="6d4bf-136">Selectionsets-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6d4bf-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="6d4bf-137">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6d4bf-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="6d4bf-138">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="6d4bf-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
