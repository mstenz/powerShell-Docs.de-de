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
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057925"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="26359-102">Element „TypeName“ für Types (Format)</span><span class="sxs-lookup"><span data-stu-id="26359-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="26359-103">Gibt den Typ .NET eines Objekts, das auf die Auswahl gehört.</span><span class="sxs-lookup"><span data-stu-id="26359-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="26359-104">Element (Format) SelectionSets-Element (Format) SelectionSet Konfigurationselement (Format)-Typen (Format)-Element TypeName-Element der Typen (Format)</span><span class="sxs-lookup"><span data-stu-id="26359-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26359-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="26359-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="26359-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="26359-106">Attributes and Elements</span></span>

<span data-ttu-id="26359-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="26359-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="26359-108">Mindestens ein `TypeName` Element in der Auswahl enthalten sein muss.</span><span class="sxs-lookup"><span data-stu-id="26359-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="26359-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="26359-109">Attributes</span></span>

<span data-ttu-id="26359-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="26359-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26359-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="26359-111">Child Elements</span></span>

<span data-ttu-id="26359-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="26359-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="26359-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="26359-113">Parent Elements</span></span>

|<span data-ttu-id="26359-114">Element</span><span class="sxs-lookup"><span data-stu-id="26359-114">Element</span></span>|<span data-ttu-id="26359-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="26359-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26359-116">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="26359-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="26359-117">Definiert die .NET Objekte, die in der Auswahl festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="26359-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="26359-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="26359-118">Text Value</span></span>

<span data-ttu-id="26359-119">Geben Sie den vollqualifizierten Namen für den Typ .NET.</span><span class="sxs-lookup"><span data-stu-id="26359-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="26359-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="26359-120">Remarks</span></span>

<span data-ttu-id="26359-121">Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten.</span><span class="sxs-lookup"><span data-stu-id="26359-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="26359-122">Wenn Sie Ihre Ansichten definieren, können Sie den Satz von Objekten angeben, mit dem Namen der Markierung anstelle Auflisten aller Objekte in jeder Ansicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="26359-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="26359-123">Typische Auswahl Sets werden anhand ihres Namens angegeben, bei der Definition der Ansichten die Formatierungsdatei.</span><span class="sxs-lookup"><span data-stu-id="26359-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="26359-124">In diesen Fällen die `SelectionSetName` untergeordnetes Element von der `ViewSelectedBy` das-Element für die Sicht angibt.</span><span class="sxs-lookup"><span data-stu-id="26359-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="26359-125">Verschiedene Einträge einer Sicht können jedoch auch einen Auswahlsatz angeben, der für nur diesen Eintrag der Sicht gilt.</span><span class="sxs-lookup"><span data-stu-id="26359-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="26359-126">Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="26359-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="26359-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="26359-127">Example</span></span>

<span data-ttu-id="26359-128">Das folgende Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.</span><span class="sxs-lookup"><span data-stu-id="26359-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="26359-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="26359-129">See Also</span></span>

[<span data-ttu-id="26359-130">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="26359-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="26359-131">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="26359-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="26359-132">SelectionSets-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="26359-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="26359-133">Types-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="26359-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="26359-134">Schreiben Sie eine Windows PowerShell Formatierungsdatei</span><span class="sxs-lookup"><span data-stu-id="26359-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
