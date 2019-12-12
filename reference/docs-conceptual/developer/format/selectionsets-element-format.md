---
title: Selectionsets-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361869"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="625d1-102">Element „SelectionSets“ (Format)</span><span class="sxs-lookup"><span data-stu-id="625d1-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="625d1-103">Definiert die allgemeinen Sätze von .NET-Objekten, die von allen Sichten der Formatierungs Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="625d1-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="625d1-104">Die Sichten und Steuerelemente der Formatierungs Datei können auf den gesamten Satz von Objekten verweisen, indem Sie nur den Namen des Auswahl Satzes verwenden.</span><span class="sxs-lookup"><span data-stu-id="625d1-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="625d1-105">Konfigurationselement selectionsets-Element Format</span><span class="sxs-lookup"><span data-stu-id="625d1-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="625d1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="625d1-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="625d1-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="625d1-107">Attributes and Elements</span></span>

<span data-ttu-id="625d1-108">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `SelectionSets`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="625d1-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="625d1-109">Jedes untergeordnete Element definiert einen Satz von Objekten, auf die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="625d1-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="625d1-110">Die Reihenfolge der untergeordneten Elemente ist nicht signifikant.</span><span class="sxs-lookup"><span data-stu-id="625d1-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="625d1-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="625d1-111">Attributes</span></span>

<span data-ttu-id="625d1-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="625d1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="625d1-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="625d1-113">Child Elements</span></span>

|<span data-ttu-id="625d1-114">Element</span><span class="sxs-lookup"><span data-stu-id="625d1-114">Element</span></span>|<span data-ttu-id="625d1-115">Description</span><span class="sxs-lookup"><span data-stu-id="625d1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="625d1-116">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="625d1-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="625d1-117">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="625d1-117">Required element.</span></span><br /><br /> <span data-ttu-id="625d1-118">Definiert einen einzelnen Satz von .NET-Objekten, auf die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="625d1-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="625d1-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="625d1-119">Parent Elements</span></span>

|<span data-ttu-id="625d1-120">Element</span><span class="sxs-lookup"><span data-stu-id="625d1-120">Element</span></span>|<span data-ttu-id="625d1-121">Description</span><span class="sxs-lookup"><span data-stu-id="625d1-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="625d1-122">Configuration-Element</span><span class="sxs-lookup"><span data-stu-id="625d1-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="625d1-123">Stellt das Element der obersten Ebene einer Formatierungs Datei dar.</span><span class="sxs-lookup"><span data-stu-id="625d1-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="625d1-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="625d1-124">Remarks</span></span>

<span data-ttu-id="625d1-125">Sie können Auswahl Sätze verwenden, wenn Sie über einen Satz verwandter Objekte verfügen, auf die Sie verweisen möchten, indem Sie einen einzelnen Namen verwenden, z. b. eine Gruppe von Objekten, die durch Vererbung verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="625d1-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="625d1-126">Wenn Sie die Ansichten definieren, können Sie den Satz von-Objekten angeben, indem Sie den Namen des Auswahl Satzes verwenden, anstatt alle Objekte in jeder Ansicht aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="625d1-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="625d1-127">Beim Definieren der Sichten der Formatierungs Datei oder der Definitionen der Sichten werden allgemeine Auswahl Sätze durch ihren Namen angegeben.</span><span class="sxs-lookup"><span data-stu-id="625d1-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="625d1-128">In diesen Fällen gibt das `SelectionSetName` untergeordnete Element der `ViewSelectedBy`-und `EntrySelectedBy`-Elemente die zu verwendende Gruppe an.</span><span class="sxs-lookup"><span data-stu-id="625d1-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="625d1-129">Weitere Informationen zu Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="625d1-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="625d1-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="625d1-130">See Also</span></span>

[<span data-ttu-id="625d1-131">Configuration-Element</span><span class="sxs-lookup"><span data-stu-id="625d1-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="625d1-132">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="625d1-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="625d1-133">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="625d1-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="625d1-134">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="625d1-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
