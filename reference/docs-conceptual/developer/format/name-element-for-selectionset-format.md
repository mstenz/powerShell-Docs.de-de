---
title: Name-Element für SelectionSet (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362669"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="5e84a-102">Element „Name“ für SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="5e84a-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="5e84a-103">Gibt den Namen an, mit dem auf den Auswahl Satz verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="5e84a-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="5e84a-104">Configuration-Element (Format) selectionsets-Element (Format) SelectionSet-Element (Format) Name-Element von SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="5e84a-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5e84a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e84a-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e84a-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5e84a-106">Attributes and Elements</span></span>

<span data-ttu-id="5e84a-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `Name`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5e84a-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e84a-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="5e84a-108">Attributes</span></span>

<span data-ttu-id="5e84a-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="5e84a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5e84a-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5e84a-110">Child Elements</span></span>

<span data-ttu-id="5e84a-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="5e84a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5e84a-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5e84a-112">Parent Elements</span></span>

|<span data-ttu-id="5e84a-113">Element</span><span class="sxs-lookup"><span data-stu-id="5e84a-113">Element</span></span>|<span data-ttu-id="5e84a-114">Description</span><span class="sxs-lookup"><span data-stu-id="5e84a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5e84a-115">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5e84a-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="5e84a-116">Definiert einen einzelnen Satz von .NET-Objekten, auf die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="5e84a-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5e84a-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="5e84a-117">Text Value</span></span>

<span data-ttu-id="5e84a-118">Geben Sie den Namen an, der auf den Auswahl Satz verweist.</span><span class="sxs-lookup"><span data-stu-id="5e84a-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="5e84a-119">Es gibt keine Einschränkungen, welche Zeichen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="5e84a-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="5e84a-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5e84a-120">Remarks</span></span>

<span data-ttu-id="5e84a-121">Der hier angegebene Name wird im `SelectionSetName`-Element verwendet.</span><span class="sxs-lookup"><span data-stu-id="5e84a-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="5e84a-122">Der Auswahl Satz, der von einer Ansicht verwendet werden kann, durch eine Definition einer Ansicht (Ansichten können mehrere Definitionen aufweisen) oder durch Angeben einer Auswahlbedingung.</span><span class="sxs-lookup"><span data-stu-id="5e84a-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="5e84a-123">Weitere Informationen zu Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5e84a-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="5e84a-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5e84a-124">Example</span></span>

<span data-ttu-id="5e84a-125">Dieses Beispiel zeigt ein `SelectionSet`-Element, das vier .NET-Typen definiert.</span><span class="sxs-lookup"><span data-stu-id="5e84a-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="5e84a-126">Der Name des Auswahl Satzes lautet "filesystemtypes".</span><span class="sxs-lookup"><span data-stu-id="5e84a-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5e84a-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5e84a-127">See Also</span></span>

[<span data-ttu-id="5e84a-128">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="5e84a-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5e84a-129">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5e84a-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="5e84a-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="5e84a-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
