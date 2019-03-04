---
title: Frame-Element für CustomItem für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859816"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="3c77c-102">Element „Frame“ für CustomItem für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="3c77c-103">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="3c77c-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="3c77c-104">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3c77c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3c77c-105">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format)-Frame-Element für CustomItem für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c77c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c77c-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c77c-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3c77c-107">Attributes and Elements</span></span>

<span data-ttu-id="3c77c-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="3c77c-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c77c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3c77c-109">Attributes</span></span>

<span data-ttu-id="3c77c-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="3c77c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c77c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3c77c-111">Child Elements</span></span>

|<span data-ttu-id="3c77c-112">Element</span><span class="sxs-lookup"><span data-stu-id="3c77c-112">Element</span></span>|<span data-ttu-id="3c77c-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3c77c-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="3c77c-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="3c77c-114">Required Element</span></span>|
|[<span data-ttu-id="3c77c-115">FirstLineHanging-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3c77c-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3c77c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3c77c-117">Gibt an, wie viele Zeichen, die auf der linken Seite die erste Zeile verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="3c77c-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="3c77c-118">FirstLineIndent-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3c77c-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3c77c-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3c77c-120">Gibt an, wie viele Zeichen, die die erste Zeile nach rechts verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="3c77c-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="3c77c-121">LeftIndent-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3c77c-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3c77c-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3c77c-123">Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="3c77c-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="3c77c-124">RightIndent-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="3c77c-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="3c77c-125">Optional element.</span></span><br /><br /> <span data-ttu-id="3c77c-126">Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="3c77c-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c77c-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3c77c-127">Parent Elements</span></span>

|<span data-ttu-id="3c77c-128">Element</span><span class="sxs-lookup"><span data-stu-id="3c77c-128">Element</span></span>|<span data-ttu-id="3c77c-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3c77c-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c77c-130">CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="3c77c-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3c77c-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c77c-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3c77c-132">Remarks</span></span>

<span data-ttu-id="3c77c-133">Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Elemente in der gleichen `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="3c77c-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c77c-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3c77c-134">See Also</span></span>

[<span data-ttu-id="3c77c-135">FirstLineHanging-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3c77c-136">FirstLineIndent-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3c77c-137">LeftIndent-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3c77c-138">RightIndent-Element des Frames von Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="3c77c-139">CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c77c-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="3c77c-140">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c77c-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
