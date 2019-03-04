---
title: Namen von Element für SelectionSet (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858166"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="fdb68-102">Element „Name“ für SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb68-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="fdb68-103">Gibt den Namen verwendet, um den Auswahlsatz zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="fdb68-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="fdb68-104">Konfiguration-Element (Format) SelectionSets-Element (Format) SelectionSet-Element (Format)-Name-Element der SelectionSet (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb68-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdb68-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fdb68-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdb68-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fdb68-106">Attributes and Elements</span></span>

<span data-ttu-id="fdb68-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Name` Element.</span><span class="sxs-lookup"><span data-stu-id="fdb68-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdb68-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="fdb68-108">Attributes</span></span>

<span data-ttu-id="fdb68-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="fdb68-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdb68-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fdb68-110">Child Elements</span></span>

<span data-ttu-id="fdb68-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="fdb68-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fdb68-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fdb68-112">Parent Elements</span></span>

|<span data-ttu-id="fdb68-113">Element</span><span class="sxs-lookup"><span data-stu-id="fdb68-113">Element</span></span>|<span data-ttu-id="fdb68-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fdb68-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdb68-115">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb68-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="fdb68-116">Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="fdb68-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fdb68-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="fdb68-117">Text Value</span></span>

<span data-ttu-id="fdb68-118">Geben Sie den Namen auf den Auswahlsatz verweisen.</span><span class="sxs-lookup"><span data-stu-id="fdb68-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="fdb68-119">Es gibt keine Einschränkungen, welche Zeichen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="fdb68-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="fdb68-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fdb68-120">Remarks</span></span>

<span data-ttu-id="fdb68-121">Der hier angegebene Name wird verwendet, der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="fdb68-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="fdb68-122">Der Auswahlsatz, der durch eine Sicht, indem Sie eine Definition einer Sicht verwendet werden kann (Ansichten können hat mehrere Definitionen), oder wenn Sie eine auswahlbedingung angeben.</span><span class="sxs-lookup"><span data-stu-id="fdb68-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="fdb68-123">Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="fdb68-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="fdb68-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fdb68-124">Example</span></span>

<span data-ttu-id="fdb68-125">Dieses Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.</span><span class="sxs-lookup"><span data-stu-id="fdb68-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="fdb68-126">Der Name des Satzes Auswahl ist "FileSystemTypes".</span><span class="sxs-lookup"><span data-stu-id="fdb68-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fdb68-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fdb68-127">See Also</span></span>

[<span data-ttu-id="fdb68-128">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="fdb68-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="fdb68-129">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fdb68-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="fdb68-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdb68-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
