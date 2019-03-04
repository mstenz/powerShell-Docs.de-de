---
title: SelectionSets-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853566"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="5bfcd-102">Element „SelectionSets“ (Format)</span><span class="sxs-lookup"><span data-stu-id="5bfcd-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="5bfcd-103">Definiert die allgemeine Sätze von .NET-Objekten, die von allen Ansichten des die Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="5bfcd-104">Die Ansichten und die Steuerelemente die Formatierungsdatei können den vollständigen Satz von Objekten mit nur den Namen des Satzes Auswahl verweisen.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="5bfcd-105">Configuration Element SelectionSets-Elementformat</span><span class="sxs-lookup"><span data-stu-id="5bfcd-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="5bfcd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5bfcd-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5bfcd-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5bfcd-107">Attributes and Elements</span></span>

<span data-ttu-id="5bfcd-108">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `SelectionSets` Element.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="5bfcd-109">Jedes untergeordnete Element definiert einen Satz von Objekten, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="5bfcd-110">Die Reihenfolge der untergeordneten Elemente ist nicht wichtig.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="5bfcd-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="5bfcd-111">Attributes</span></span>

<span data-ttu-id="5bfcd-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5bfcd-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5bfcd-113">Child Elements</span></span>

|<span data-ttu-id="5bfcd-114">Element</span><span class="sxs-lookup"><span data-stu-id="5bfcd-114">Element</span></span>|<span data-ttu-id="5bfcd-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5bfcd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5bfcd-116">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5bfcd-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="5bfcd-117">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-117">Required element.</span></span><br /><br /> <span data-ttu-id="5bfcd-118">Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5bfcd-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5bfcd-119">Parent Elements</span></span>

|<span data-ttu-id="5bfcd-120">Element</span><span class="sxs-lookup"><span data-stu-id="5bfcd-120">Element</span></span>|<span data-ttu-id="5bfcd-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5bfcd-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5bfcd-122">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="5bfcd-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="5bfcd-123">Das Element das obersten Ebene eine Formatierungsdatei darstellt.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5bfcd-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5bfcd-124">Remarks</span></span>

<span data-ttu-id="5bfcd-125">Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="5bfcd-126">Wenn Sie Ihre Ansichten definieren, können Sie den Satz von Objekten angeben, mit dem Namen der Markierung anstelle Auflisten aller Objekte in jeder Ansicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="5bfcd-127">Typische Auswahl Sets werden anhand ihres Namens angegeben, bei der Definition der Ansichten die Formatierungsdatei oder die Definitionen der Ansichten.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="5bfcd-128">In diesen Fällen die `SelectionSetName` untergeordnetes Element von der `ViewSelectedBy` und `EntrySelectedBy` Elemente gibt den Satz verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5bfcd-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="5bfcd-129">Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5bfcd-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5bfcd-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5bfcd-130">See Also</span></span>

[<span data-ttu-id="5bfcd-131">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="5bfcd-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="5bfcd-132">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="5bfcd-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5bfcd-133">SelectionSet-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5bfcd-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="5bfcd-134">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5bfcd-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
