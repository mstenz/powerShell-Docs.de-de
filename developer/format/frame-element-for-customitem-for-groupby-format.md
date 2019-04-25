---
title: Frame-Element für CustomItem für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065596"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a><span data-ttu-id="21850-102">Element „Frame“ für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-102">Frame Element for CustomItem for GroupBy (Format)</span></span>

<span data-ttu-id="21850-103">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="21850-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="21850-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="21850-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="21850-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format)-Frame-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) Frame Element for CustomItem for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21850-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="21850-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21850-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="21850-107">Attributes and Elements</span></span>

<span data-ttu-id="21850-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="21850-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="21850-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="21850-109">Attributes</span></span>

<span data-ttu-id="21850-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="21850-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21850-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="21850-111">Child Elements</span></span>

|<span data-ttu-id="21850-112">Element</span><span class="sxs-lookup"><span data-stu-id="21850-112">Element</span></span>|<span data-ttu-id="21850-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="21850-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="21850-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="21850-114">Required Element</span></span>|
|[<span data-ttu-id="21850-115">FirstLineHanging-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-115">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)|<span data-ttu-id="21850-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="21850-116">Optional element.</span></span><br /><br /> <span data-ttu-id="21850-117">Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="21850-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="21850-118">FirstLineIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-118">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="21850-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="21850-119">Optional element.</span></span><br /><br /> <span data-ttu-id="21850-120">Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="21850-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="21850-121">LeftIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-121">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)|<span data-ttu-id="21850-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="21850-122">Optional element.</span></span><br /><br /> <span data-ttu-id="21850-123">Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="21850-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|<span data-ttu-id="21850-124">[RightIndent-Element für Frame für GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="21850-124">[RightIndent Element for Frame for GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent Element</span></span>|<span data-ttu-id="21850-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="21850-125">Optional element.</span></span><br /><br /> <span data-ttu-id="21850-126">Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="21850-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="21850-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="21850-127">Parent Elements</span></span>

|<span data-ttu-id="21850-128">Element</span><span class="sxs-lookup"><span data-stu-id="21850-128">Element</span></span>|<span data-ttu-id="21850-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="21850-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21850-130">CustomItem-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-130">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="21850-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="21850-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21850-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="21850-132">Remarks</span></span>

<span data-ttu-id="21850-133">Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) Elemente in der gleichen `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="21850-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="21850-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="21850-134">See Also</span></span>

[<span data-ttu-id="21850-135">FirstLineHanging-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-135">FirstLineHanging Element for Frame for GroupBy (Format)</span></span>](./firstlinehanging-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="21850-136">FirstLineIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-136">FirstLineIndent Element for Frame for GroupBy (Format)</span></span>](./firstlineindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="21850-137">LeftIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-137">LeftIndent Element for Frame for GroupBy (Format)</span></span>](./leftindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="21850-138">RightIndent-Element für Frame für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-138">RightIndent Element for Frame for GroupBy (Format)</span></span>](./rightindent-element-for-frame-for-groupby-format.md)

[<span data-ttu-id="21850-139">CustomItem-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="21850-139">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="21850-140">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="21850-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
