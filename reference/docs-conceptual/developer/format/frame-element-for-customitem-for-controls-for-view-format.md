---
title: Frame-Element für customItem für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363649"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a><span data-ttu-id="22613-102">Element „Frame“ für CustomItem für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-102">Frame Element for CustomItem for Controls for View (Format)</span></span>

<span data-ttu-id="22613-103">Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="22613-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="22613-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="22613-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="22613-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für Ansicht (Format) Frame Element für customItem für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) Frame Element for CustomItem for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22613-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="22613-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22613-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="22613-107">Attributes and Elements</span></span>

<span data-ttu-id="22613-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Frame`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="22613-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="22613-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="22613-109">Attributes</span></span>

<span data-ttu-id="22613-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="22613-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22613-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="22613-111">Child Elements</span></span>

|<span data-ttu-id="22613-112">Element</span><span class="sxs-lookup"><span data-stu-id="22613-112">Element</span></span>|<span data-ttu-id="22613-113">Description</span><span class="sxs-lookup"><span data-stu-id="22613-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="22613-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="22613-114">Required Element</span></span>|
|[<span data-ttu-id="22613-115">Firstlinehanging-Element von Frame der Steuerelemente der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-115">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="22613-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="22613-116">Optional element.</span></span><br /><br /> <span data-ttu-id="22613-117">Gibt an, wie viele Zeichen die erste Zeile nach links verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="22613-117">Specifies how many characters the first line is shifted to the left.</span></span>|
|[<span data-ttu-id="22613-118">FirstLineIndent-Element von Frame der Steuerelemente der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-118">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="22613-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="22613-119">Optional element.</span></span><br /><br /> <span data-ttu-id="22613-120">Gibt an, wie viele Zeichen die erste Zeile nach rechts verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="22613-120">Specifies how many characters the first line is shifted to the right.</span></span>|
|[<span data-ttu-id="22613-121">LeftIndent-Element von Frame der Steuerelemente der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-121">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="22613-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="22613-122">Optional element.</span></span><br /><br /> <span data-ttu-id="22613-123">Gibt an, wie viele Zeichen die Daten vom linken Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="22613-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="22613-124">RightIndent-Element von Frame-Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-124">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)|<span data-ttu-id="22613-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="22613-125">Optional element.</span></span><br /><br /> <span data-ttu-id="22613-126">Gibt an, wie viele Zeichen die Daten vom rechten Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="22613-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="22613-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="22613-127">Parent Elements</span></span>

|<span data-ttu-id="22613-128">Element</span><span class="sxs-lookup"><span data-stu-id="22613-128">Element</span></span>|<span data-ttu-id="22613-129">Description</span><span class="sxs-lookup"><span data-stu-id="22613-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22613-130">CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-130">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="22613-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="22613-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22613-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="22613-132">Remarks</span></span>

<span data-ttu-id="22613-133">Sie können die Elemente [firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) nicht im selben `Frame` Element angeben.</span><span class="sxs-lookup"><span data-stu-id="22613-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="22613-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="22613-134">See Also</span></span>

[<span data-ttu-id="22613-135">Firstlinehanging-Element von Frame der Steuerelemente der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-135">FirstLineHanging Element of Frame of Controls of View (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="22613-136">FirstLineIndent-Element von Frame der Steuerelemente der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-136">FirstLineIndent Element of Frame of Controls of View (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="22613-137">LeftIndent-Element von Frame der Steuerelemente der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-137">LeftIndent Element of Frame of Controls of View (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="22613-138">RightIndent-Element von Frame-Steuerelementen der Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-138">RightIndent Element of Frame of Controls of View (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-view-format.md)

[<span data-ttu-id="22613-139">CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22613-139">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="22613-140">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="22613-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
