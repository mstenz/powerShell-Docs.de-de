---
title: Versehen Sie Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862396"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="f2422-102">Element „Label“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f2422-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="f2422-103">Gibt eine Bezeichnung, die angezeigt wird, wenn eine neue Gruppe gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="f2422-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="f2422-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Ansicht (Format)-Beschriftungselement für die GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f2422-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f2422-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2422-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f2422-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f2422-106">Attributes and Elements</span></span>

<span data-ttu-id="f2422-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Label` Element.</span><span class="sxs-lookup"><span data-stu-id="f2422-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f2422-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f2422-108">Attributes</span></span>

<span data-ttu-id="f2422-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="f2422-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f2422-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f2422-110">Child Elements</span></span>

<span data-ttu-id="f2422-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="f2422-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f2422-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f2422-112">Parent Elements</span></span>

|<span data-ttu-id="f2422-113">Element</span><span class="sxs-lookup"><span data-stu-id="f2422-113">Element</span></span>|<span data-ttu-id="f2422-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f2422-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f2422-115">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f2422-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="f2422-116">Definiert, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f2422-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f2422-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="f2422-117">Text Value</span></span>

<span data-ttu-id="f2422-118">Geben Sie den Text, der angezeigt wird, wenn Windows PowerShell eine neue Eigenschaft oder eines Werts trifft.</span><span class="sxs-lookup"><span data-stu-id="f2422-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2422-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f2422-119">Remarks</span></span>

<span data-ttu-id="f2422-120">Zusätzlich zu den Text, der von diesem Element angegeben wird zeigt Windows PowerShell den neuen Wert, der die Gruppe beginnt und eine leere Zeile vor und nach der Gruppe eingefügt.</span><span class="sxs-lookup"><span data-stu-id="f2422-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="f2422-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f2422-121">Example</span></span>

<span data-ttu-id="f2422-122">Das folgende Beispiel zeigt die Bezeichnung für eine neue Gruppe.</span><span class="sxs-lookup"><span data-stu-id="f2422-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="f2422-123">Die angezeigte Bezeichnung würde etwa wie folgt aussehen: `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="f2422-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="f2422-124">Ein Beispiel für eine vollständige Formatierung-Datei, die dieses Element enthält, finden Sie unter [Breite Ansicht (-GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="f2422-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2422-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f2422-125">See Also</span></span>

[<span data-ttu-id="f2422-126">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f2422-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="f2422-127">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2422-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
