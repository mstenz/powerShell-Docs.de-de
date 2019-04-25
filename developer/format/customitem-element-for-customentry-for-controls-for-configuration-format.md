---
title: CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066429"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="01de8-102">Element „CustomItem“ für CustomEntry für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="01de8-103">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="01de8-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="01de8-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="01de8-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="01de8-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( Format) CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="01de8-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="01de8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="01de8-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01de8-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="01de8-107">Attributes and Elements</span></span>

<span data-ttu-id="01de8-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomItem` Element.</span><span class="sxs-lookup"><span data-stu-id="01de8-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="01de8-109">Weitere Informationen finden Sie unter "Hinweise".</span><span class="sxs-lookup"><span data-stu-id="01de8-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="01de8-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="01de8-110">Attributes</span></span>

<span data-ttu-id="01de8-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="01de8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="01de8-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="01de8-112">Child Elements</span></span>

|<span data-ttu-id="01de8-113">Element</span><span class="sxs-lookup"><span data-stu-id="01de8-113">Element</span></span>|<span data-ttu-id="01de8-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01de8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01de8-115">ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="01de8-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="01de8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="01de8-117">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="01de8-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="01de8-118">Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="01de8-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="01de8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="01de8-120">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="01de8-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="01de8-121">Neue-Zeile-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="01de8-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="01de8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="01de8-123">Eine leere Zeile eingefügt, um die Anzeige des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="01de8-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="01de8-124">Text-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="01de8-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="01de8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="01de8-126">Fügt Text an, wie z. B. Klammern oder durch Klammern, der Anzeige des Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="01de8-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="01de8-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="01de8-127">Parent Elements</span></span>

|<span data-ttu-id="01de8-128">Element</span><span class="sxs-lookup"><span data-stu-id="01de8-128">Element</span></span>|<span data-ttu-id="01de8-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="01de8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="01de8-130">CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="01de8-131">Stellt eine Definition des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="01de8-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="01de8-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="01de8-132">Remarks</span></span>

<span data-ttu-id="01de8-133">Wenn Sie die untergeordneten Elemente angeben die `CustomItem` -Element, Bedenken Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="01de8-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="01de8-134">Die untergeordneten Elemente müssen in der folgenden Reihenfolge hinzugefügt werden: `ExpressionBinding`, `NewLine`, `Text`, und `Frame`.</span><span class="sxs-lookup"><span data-stu-id="01de8-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="01de8-135">Es ist nicht begrenzt auf die Anzahl der Sequenzen, die Sie angeben können.</span><span class="sxs-lookup"><span data-stu-id="01de8-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="01de8-136">In der Sequenz vorhanden ist nicht begrenzt auf die Anzahl der `ExpressionBinding` Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="01de8-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="01de8-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="01de8-137">See Also</span></span>

[<span data-ttu-id="01de8-138">ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="01de8-139">Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="01de8-140">Neue-Zeile-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="01de8-141">Text-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="01de8-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="01de8-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="01de8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
