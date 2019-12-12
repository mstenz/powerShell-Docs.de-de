---
title: CustomItem-Element für customentry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363879"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="e01ef-102">Element „CustomItem“ für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-102">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="e01ef-103">Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e01ef-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="e01ef-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e01ef-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e01ef-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customItem-Element für Customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e01ef-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e01ef-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e01ef-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e01ef-107">Attributes and Elements</span></span>

<span data-ttu-id="e01ef-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomItem`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e01ef-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e01ef-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e01ef-109">Attributes</span></span>

<span data-ttu-id="e01ef-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="e01ef-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e01ef-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e01ef-111">Child Elements</span></span>

|<span data-ttu-id="e01ef-112">Element</span><span class="sxs-lookup"><span data-stu-id="e01ef-112">Element</span></span>|<span data-ttu-id="e01ef-113">Description</span><span class="sxs-lookup"><span data-stu-id="e01ef-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e01ef-114">ExpressionBinding-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-114">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e01ef-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e01ef-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e01ef-116">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e01ef-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="e01ef-117">Frame-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-117">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e01ef-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e01ef-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e01ef-119">Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e01ef-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="e01ef-120">NewLine-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-120">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e01ef-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e01ef-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e01ef-122">Fügt der Anzeige des-Steuer Elements eine leere Zeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="e01ef-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="e01ef-123">Text-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-123">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="e01ef-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e01ef-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e01ef-125">Gibt zusätzlichen Text zu den Daten an, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e01ef-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e01ef-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e01ef-126">Parent Elements</span></span>

|<span data-ttu-id="e01ef-127">Element</span><span class="sxs-lookup"><span data-stu-id="e01ef-127">Element</span></span>|<span data-ttu-id="e01ef-128">Description</span><span class="sxs-lookup"><span data-stu-id="e01ef-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e01ef-129">Customentry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e01ef-130">Stellt eine Definition der benutzerdefinierten Steuerelement Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="e01ef-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e01ef-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e01ef-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e01ef-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e01ef-132">See Also</span></span>

[<span data-ttu-id="e01ef-133">Customentry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-133">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="e01ef-134">ExpressionBinding-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-134">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e01ef-135">Frame-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-135">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e01ef-136">NewLine-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-136">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e01ef-137">Text-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e01ef-137">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="e01ef-138">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="e01ef-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
