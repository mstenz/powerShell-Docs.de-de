---
title: TypeName-Element für Typen (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853576"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="81d62-102">Element „TypeName“ für Types (Format)</span><span class="sxs-lookup"><span data-stu-id="81d62-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="81d62-103">Gibt den Typ .NET eines Objekts, das auf die Auswahl gehört.</span><span class="sxs-lookup"><span data-stu-id="81d62-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="81d62-104">Element (Format) SelectionSets-Element (Format) SelectionSet Konfigurationselement (Format)-Typen (Format)-Element TypeName-Element der Typen (Format)</span><span class="sxs-lookup"><span data-stu-id="81d62-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81d62-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="81d62-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81d62-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="81d62-106">Attributes and Elements</span></span>

<span data-ttu-id="81d62-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="81d62-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="81d62-108">Mindestens ein `TypeName` Element in der Auswahl enthalten sein muss.</span><span class="sxs-lookup"><span data-stu-id="81d62-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="81d62-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="81d62-109">Attributes</span></span>

<span data-ttu-id="81d62-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="81d62-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81d62-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="81d62-111">Child Elements</span></span>

<span data-ttu-id="81d62-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="81d62-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="81d62-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="81d62-113">Parent Elements</span></span>

|<span data-ttu-id="81d62-114">Element</span><span class="sxs-lookup"><span data-stu-id="81d62-114">Element</span></span>|<span data-ttu-id="81d62-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="81d62-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81d62-116">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="81d62-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="81d62-117">Definiert die .NET Objekte, die in der Auswahl festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="81d62-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="81d62-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="81d62-118">Text Value</span></span>

<span data-ttu-id="81d62-119">Geben Sie den vollqualifizierten Namen für den Typ .NET.</span><span class="sxs-lookup"><span data-stu-id="81d62-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="81d62-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="81d62-120">Remarks</span></span>

<span data-ttu-id="81d62-121">Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten.</span><span class="sxs-lookup"><span data-stu-id="81d62-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="81d62-122">Wenn Sie Ihre Ansichten definieren, können Sie den Satz von Objekten angeben, mit dem Namen der Markierung anstelle Auflisten aller Objekte in jeder Ansicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="81d62-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="81d62-123">Typische Auswahl Sets werden anhand ihres Namens angegeben, bei der Definition der Ansichten die Formatierungsdatei.</span><span class="sxs-lookup"><span data-stu-id="81d62-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="81d62-124">In diesen Fällen die `SelectionSetName` untergeordnetes Element von der `ViewSelectedBy` das-Element für die Sicht angibt.</span><span class="sxs-lookup"><span data-stu-id="81d62-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="81d62-125">Verschiedene Einträge einer Sicht können jedoch auch einen Auswahlsatz angeben, der für nur diesen Eintrag der Sicht gilt.</span><span class="sxs-lookup"><span data-stu-id="81d62-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="81d62-126">Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="81d62-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="81d62-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="81d62-127">Example</span></span>

<span data-ttu-id="81d62-128">Das folgende Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.</span><span class="sxs-lookup"><span data-stu-id="81d62-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="81d62-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="81d62-129">See Also</span></span>

[<span data-ttu-id="81d62-130">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="81d62-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="81d62-131">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="81d62-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="81d62-132">SelectionSets-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="81d62-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="81d62-133">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="81d62-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="81d62-134">Schreiben Sie eine Windows PowDefining verschiedene ObjecterShell Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="81d62-134">Writing a Windows PowDefining Sets of ObjecterShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
