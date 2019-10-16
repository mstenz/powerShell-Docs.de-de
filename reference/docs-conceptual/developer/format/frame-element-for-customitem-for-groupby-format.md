---
title: Frame-Element für customItem für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362949"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="6e2df-102">Element „Frame“ für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="6e2df-103">Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="6e2df-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="6e2df-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e2df-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6e2df-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) Frame-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e2df-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e2df-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e2df-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6e2df-107">Attributes and Elements</span></span>

<span data-ttu-id="6e2df-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Frame`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6e2df-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e2df-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6e2df-109">Attributes</span></span>

<span data-ttu-id="6e2df-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6e2df-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e2df-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6e2df-111">Child Elements</span></span>

|<span data-ttu-id="6e2df-112">Element</span><span class="sxs-lookup"><span data-stu-id="6e2df-112">Element</span></span>|<span data-ttu-id="6e2df-113">Description</span><span class="sxs-lookup"><span data-stu-id="6e2df-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="6e2df-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="6e2df-114">Required Element</span></span>|
|[<span data-ttu-id="6e2df-115">Firstlinehanging-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="6e2df-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="6e2df-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6e2df-117">Gibt an, wie viele Zeichen die erste Zeile der Daten nach links verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="6e2df-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="6e2df-118">FirstLineIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="6e2df-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="6e2df-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6e2df-120">Gibt an, wie viele Zeichen die erste Zeile der Daten nach rechts verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="6e2df-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="6e2df-121">LeftIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="6e2df-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="6e2df-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6e2df-123">Gibt an, wie viele Zeichen die Daten vom linken Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="6e2df-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="6e2df-124">[RightIndent-Element für Frame für GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="6e2df-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="6e2df-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="6e2df-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6e2df-126">Gibt an, wie viele Zeichen die Daten vom rechten Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="6e2df-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6e2df-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6e2df-127">Parent Elements</span></span>

|<span data-ttu-id="6e2df-128">Element</span><span class="sxs-lookup"><span data-stu-id="6e2df-128">Element</span></span>|<span data-ttu-id="6e2df-129">Description</span><span class="sxs-lookup"><span data-stu-id="6e2df-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e2df-130">CustomItem-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="6e2df-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e2df-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e2df-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6e2df-132">Remarks</span></span>

<span data-ttu-id="6e2df-133">Sie können die Elemente [firstlinehanging](./firstlinehanging-element-for-frame-for-groupby-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) nicht im selben `Frame`-Element angeben.</span><span class="sxs-lookup"><span data-stu-id="6e2df-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e2df-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6e2df-134">See Also</span></span>

[<span data-ttu-id="6e2df-135">Firstlinehanging-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6e2df-136">FirstLineIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6e2df-137">LeftIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6e2df-138">RightIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="6e2df-139">CustomItem-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6e2df-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="6e2df-140">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="6e2df-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
