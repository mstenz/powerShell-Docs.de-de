---
title: Typname-Element für Typen (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368029"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="bcd16-102">Element „TypeName“ für Types (Format)</span><span class="sxs-lookup"><span data-stu-id="bcd16-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="bcd16-103">Gibt den .NET-Typ eines Objekts an, das zum Auswahl Satz gehört.</span><span class="sxs-lookup"><span data-stu-id="bcd16-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="bcd16-104">Configuration-Element (Format) selectionsets-Element (Format) SelectionSet-Element (Format) Types-Element (Format) Typname Element of Types (Format)</span><span class="sxs-lookup"><span data-stu-id="bcd16-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bcd16-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bcd16-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bcd16-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="bcd16-106">Attributes and Elements</span></span>

<span data-ttu-id="bcd16-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="bcd16-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="bcd16-108">Mindestens ein `TypeName` Element muss im Auswahl Satz enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="bcd16-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="bcd16-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="bcd16-109">Attributes</span></span>

<span data-ttu-id="bcd16-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="bcd16-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bcd16-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bcd16-111">Child Elements</span></span>

<span data-ttu-id="bcd16-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="bcd16-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bcd16-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bcd16-113">Parent Elements</span></span>

|<span data-ttu-id="bcd16-114">Element</span><span class="sxs-lookup"><span data-stu-id="bcd16-114">Element</span></span>|<span data-ttu-id="bcd16-115">Description</span><span class="sxs-lookup"><span data-stu-id="bcd16-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bcd16-116">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bcd16-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="bcd16-117">Definiert die .NET-Objekte, die sich im Auswahl Satz befinden.</span><span class="sxs-lookup"><span data-stu-id="bcd16-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bcd16-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="bcd16-118">Text Value</span></span>

<span data-ttu-id="bcd16-119">Geben Sie den voll qualifizierten Namen des .net-Typs an.</span><span class="sxs-lookup"><span data-stu-id="bcd16-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="bcd16-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bcd16-120">Remarks</span></span>

<span data-ttu-id="bcd16-121">Sie können Auswahl Sätze verwenden, wenn Sie über einen Satz verwandter Objekte verfügen, auf die Sie verweisen möchten, indem Sie einen einzelnen Namen verwenden, z. b. eine Gruppe von Objekten, die durch Vererbung verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="bcd16-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="bcd16-122">Wenn Sie die Ansichten definieren, können Sie den Satz von-Objekten angeben, indem Sie den Namen des Auswahl Satzes verwenden, anstatt alle Objekte in jeder Ansicht aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="bcd16-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="bcd16-123">Allgemeine Auswahl Sätze werden durch ihren Namen angegeben, wenn die Ansichten der Formatierungs Datei definiert werden.</span><span class="sxs-lookup"><span data-stu-id="bcd16-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="bcd16-124">In diesen Fällen gibt das `SelectionSetName` untergeordnete Element des `ViewSelectedBy`-Elements für die Sicht den Satz an.</span><span class="sxs-lookup"><span data-stu-id="bcd16-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="bcd16-125">Bei verschiedenen Einträgen einer Sicht kann jedoch auch ein Auswahl Satz angegeben werden, der nur für diesen Eintrag der Sicht gilt.</span><span class="sxs-lookup"><span data-stu-id="bcd16-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="bcd16-126">Weitere Informationen zu Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bcd16-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="bcd16-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bcd16-127">Example</span></span>

<span data-ttu-id="bcd16-128">Das folgende Beispiel zeigt ein `SelectionSet`-Element, das vier .NET-Typen definiert.</span><span class="sxs-lookup"><span data-stu-id="bcd16-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="bcd16-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bcd16-129">See Also</span></span>

[<span data-ttu-id="bcd16-130">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="bcd16-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bcd16-131">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bcd16-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="bcd16-132">Selectionsets-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bcd16-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="bcd16-133">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bcd16-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="bcd16-134">Schreiben einer Windows PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="bcd16-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
