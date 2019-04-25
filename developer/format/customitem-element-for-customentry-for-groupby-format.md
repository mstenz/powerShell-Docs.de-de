---
title: CustomItem-Element für CustomEntry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066396"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="42ce2-102">Element „CustomItem“ für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="42ce2-103">Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="42ce2-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="42ce2-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="42ce2-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="42ce2-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42ce2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="42ce2-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42ce2-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="42ce2-107">Attributes and Elements</span></span>

<span data-ttu-id="42ce2-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomItem` Element.</span><span class="sxs-lookup"><span data-stu-id="42ce2-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42ce2-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="42ce2-109">Attributes</span></span>

<span data-ttu-id="42ce2-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="42ce2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42ce2-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="42ce2-111">Child Elements</span></span>

|<span data-ttu-id="42ce2-112">Element</span><span class="sxs-lookup"><span data-stu-id="42ce2-112">Element</span></span>|<span data-ttu-id="42ce2-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="42ce2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42ce2-114">ExpressionBinding-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="42ce2-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="42ce2-115">Optional element.</span></span><br /><br /> <span data-ttu-id="42ce2-116">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="42ce2-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="42ce2-117">Frame-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="42ce2-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="42ce2-118">Optional element.</span></span><br /><br /> <span data-ttu-id="42ce2-119">Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="42ce2-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="42ce2-120">Neue-Zeile-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="42ce2-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="42ce2-121">Optional element.</span></span><br /><br /> <span data-ttu-id="42ce2-122">Eine leere Zeile eingefügt, um die Anzeige des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="42ce2-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="42ce2-123">Text-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="42ce2-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="42ce2-124">Optional element.</span></span><br /><br /> <span data-ttu-id="42ce2-125">Gibt die zusätzlichen Text ein, die vom Steuerelement angezeigten Daten an.</span><span class="sxs-lookup"><span data-stu-id="42ce2-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="42ce2-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="42ce2-126">Parent Elements</span></span>

|<span data-ttu-id="42ce2-127">Element</span><span class="sxs-lookup"><span data-stu-id="42ce2-127">Element</span></span>|<span data-ttu-id="42ce2-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="42ce2-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42ce2-129">CustomEntry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="42ce2-130">Stellt eine Definition der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="42ce2-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="42ce2-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="42ce2-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="42ce2-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="42ce2-132">See Also</span></span>

[<span data-ttu-id="42ce2-133">CustomEntry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="42ce2-134">ExpressionBinding-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="42ce2-135">Frame-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="42ce2-136">Neue-Zeile-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="42ce2-137">Text-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="42ce2-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="42ce2-138">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="42ce2-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
