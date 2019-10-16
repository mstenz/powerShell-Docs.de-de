---
title: Label-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365199"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="62801-102">Element „Label“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="62801-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="62801-103">Gibt eine Bezeichnung an, die beim Auftreten einer neuen Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="62801-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="62801-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) Label-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="62801-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62801-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="62801-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62801-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="62801-106">Attributes and Elements</span></span>

<span data-ttu-id="62801-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `Label`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="62801-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62801-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="62801-108">Attributes</span></span>

<span data-ttu-id="62801-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="62801-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62801-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="62801-110">Child Elements</span></span>

<span data-ttu-id="62801-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="62801-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="62801-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="62801-112">Parent Elements</span></span>

|<span data-ttu-id="62801-113">Element</span><span class="sxs-lookup"><span data-stu-id="62801-113">Element</span></span>|<span data-ttu-id="62801-114">Description</span><span class="sxs-lookup"><span data-stu-id="62801-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62801-115">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="62801-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="62801-116">Definiert, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="62801-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="62801-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="62801-117">Text Value</span></span>

<span data-ttu-id="62801-118">Geben Sie den Text an, der angezeigt wird, wenn Windows PowerShell auf einen neuen Eigenschafts-oder Skript Wert stößt.</span><span class="sxs-lookup"><span data-stu-id="62801-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="62801-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="62801-119">Remarks</span></span>

<span data-ttu-id="62801-120">Zusätzlich zum von diesem Element angegebenen Text zeigt Windows PowerShell den neuen Wert an, der die Gruppe startet, und fügt vor und nach der Gruppe eine leere Zeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="62801-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="62801-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="62801-121">Example</span></span>

<span data-ttu-id="62801-122">Das folgende Beispiel zeigt die Bezeichnung für eine neue Gruppe.</span><span class="sxs-lookup"><span data-stu-id="62801-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="62801-123">Die angezeigte Bezeichnung sieht in etwa wie folgt aus: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="62801-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="62801-124">Ein Beispiel für eine komplette Formatierungs Datei, die dieses Element enthält, finden Sie unter [Wide View (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="62801-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="62801-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="62801-125">See Also</span></span>

[<span data-ttu-id="62801-126">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="62801-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="62801-127">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="62801-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
