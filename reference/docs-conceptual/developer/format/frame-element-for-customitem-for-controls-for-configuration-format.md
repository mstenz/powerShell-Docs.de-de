---
title: Frame-Element für customItem für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363659"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="59fb5-102">Element „Frame“ für CustomItem für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="59fb5-103">Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="59fb5-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="59fb5-104">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="59fb5-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="59fb5-105">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für Configuration (Format) customItem-Element für customentry für Steuerelemente für das Configuration Frame-Element für customItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="59fb5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="59fb5-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59fb5-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="59fb5-107">Attributes and Elements</span></span>

<span data-ttu-id="59fb5-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Frame`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="59fb5-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="59fb5-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="59fb5-109">Attributes</span></span>

<span data-ttu-id="59fb5-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="59fb5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="59fb5-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="59fb5-111">Child Elements</span></span>

|<span data-ttu-id="59fb5-112">Element</span><span class="sxs-lookup"><span data-stu-id="59fb5-112">Element</span></span>|<span data-ttu-id="59fb5-113">Description</span><span class="sxs-lookup"><span data-stu-id="59fb5-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="59fb5-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="59fb5-114">Required Element</span></span>|
|[<span data-ttu-id="59fb5-115">Firstlinehanging-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="59fb5-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="59fb5-116">Optional element.</span></span><br /><br /> <span data-ttu-id="59fb5-117">Gibt an, wie viele Zeichen die erste Zeile der Daten nach links verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="59fb5-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="59fb5-118">FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="59fb5-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="59fb5-119">Optional element.</span></span><br /><br /> <span data-ttu-id="59fb5-120">Gibt an, wie viele Zeichen die erste Zeile der Daten nach rechts verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="59fb5-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="59fb5-121">LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="59fb5-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="59fb5-122">Optional element.</span></span><br /><br /> <span data-ttu-id="59fb5-123">Gibt an, wie viele Zeichen die Daten vom linken Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="59fb5-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="59fb5-124">RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="59fb5-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="59fb5-125">Optional element.</span></span><br /><br /> <span data-ttu-id="59fb5-126">Gibt an, wie viele Zeichen die Daten vom rechten Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="59fb5-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="59fb5-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="59fb5-127">Parent Elements</span></span>

|<span data-ttu-id="59fb5-128">Element</span><span class="sxs-lookup"><span data-stu-id="59fb5-128">Element</span></span>|<span data-ttu-id="59fb5-129">Description</span><span class="sxs-lookup"><span data-stu-id="59fb5-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59fb5-130">CustomItem-Element für customentry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="59fb5-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="59fb5-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="59fb5-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="59fb5-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="59fb5-132">Remarks</span></span>

<span data-ttu-id="59fb5-133">Sie können die Elemente [firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) nicht im selben `Frame` Element angeben.</span><span class="sxs-lookup"><span data-stu-id="59fb5-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="59fb5-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="59fb5-134">See Also</span></span>

[<span data-ttu-id="59fb5-135">Firstlinehanging-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="59fb5-136">FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="59fb5-137">LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="59fb5-138">RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="59fb5-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="59fb5-139">CustomItem-Element für customentry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="59fb5-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="59fb5-140">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="59fb5-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
