---
title: Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862976"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="06924-102">Element „Frame“ für CustomItem für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-102">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="06924-103">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="06924-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="06924-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="06924-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="06924-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die Frame-Konfigurationselement für CustomItem für Steuerelemente für die Konfiguration (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="06924-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06924-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="06924-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06924-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="06924-107">Attributes and Elements</span></span>

<span data-ttu-id="06924-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="06924-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06924-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="06924-109">Attributes</span></span>

<span data-ttu-id="06924-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="06924-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06924-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="06924-111">Child Elements</span></span>

|<span data-ttu-id="06924-112">Element</span><span class="sxs-lookup"><span data-stu-id="06924-112">Element</span></span>|<span data-ttu-id="06924-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="06924-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="06924-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="06924-114">Required Element</span></span>|
|[<span data-ttu-id="06924-115">FirstLineHanging-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-115">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="06924-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="06924-116">Optional element.</span></span><br /><br /> <span data-ttu-id="06924-117">Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="06924-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="06924-118">FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-118">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="06924-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="06924-119">Optional element.</span></span><br /><br /> <span data-ttu-id="06924-120">Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="06924-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="06924-121">LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-121">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="06924-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="06924-122">Optional element.</span></span><br /><br /> <span data-ttu-id="06924-123">Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="06924-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="06924-124">RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-124">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|<span data-ttu-id="06924-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="06924-125">Optional element.</span></span><br /><br /> <span data-ttu-id="06924-126">Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="06924-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06924-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="06924-127">Parent Elements</span></span>

|<span data-ttu-id="06924-128">Element</span><span class="sxs-lookup"><span data-stu-id="06924-128">Element</span></span>|<span data-ttu-id="06924-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="06924-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06924-130">CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="06924-130">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="06924-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="06924-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06924-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="06924-132">Remarks</span></span>

<span data-ttu-id="06924-133">Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Elemente in der gleichen `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="06924-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="06924-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="06924-134">See Also</span></span>

[<span data-ttu-id="06924-135">FirstLineHanging-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-135">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="06924-136">FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-136">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="06924-137">LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-137">LeftIndent Element for Frame for Controls for Configuration (Format)</span></span>](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="06924-138">RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="06924-138">RightIndent Element for Frame for Controls for Configuration (Format)</span></span>](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="06924-139">CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="06924-139">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="06924-140">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="06924-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
