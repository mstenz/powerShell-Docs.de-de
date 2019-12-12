---
title: CustomItem-Element für customentry für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363949"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="95c0a-102">Element „CustomItem“ für CustomEntry für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="95c0a-103">Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="95c0a-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="95c0a-104">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="95c0a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="95c0a-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95c0a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="95c0a-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="95c0a-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="95c0a-107">Attributes and Elements</span></span>

<span data-ttu-id="95c0a-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomItem`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="95c0a-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95c0a-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="95c0a-109">Attributes</span></span>

<span data-ttu-id="95c0a-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="95c0a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95c0a-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="95c0a-111">Child Elements</span></span>

|<span data-ttu-id="95c0a-112">Element</span><span class="sxs-lookup"><span data-stu-id="95c0a-112">Element</span></span>|<span data-ttu-id="95c0a-113">Description</span><span class="sxs-lookup"><span data-stu-id="95c0a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95c0a-114">ExpressionBinding-Element für customItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="95c0a-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="95c0a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="95c0a-116">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="95c0a-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="95c0a-117">Frame-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="95c0a-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="95c0a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="95c0a-119">Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="95c0a-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="95c0a-120">NewLine-Element für customItem für benutzerdefiniertes Steuer Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="95c0a-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="95c0a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="95c0a-122">Fügt der Anzeige des-Steuer Elements eine leere Zeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="95c0a-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="95c0a-123">Text-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="95c0a-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="95c0a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="95c0a-125">Gibt zusätzlichen Text zu den Daten an, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="95c0a-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="95c0a-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="95c0a-126">Parent Elements</span></span>

|<span data-ttu-id="95c0a-127">Element</span><span class="sxs-lookup"><span data-stu-id="95c0a-127">Element</span></span>|<span data-ttu-id="95c0a-128">Description</span><span class="sxs-lookup"><span data-stu-id="95c0a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95c0a-129">Customentry-Element für customentries für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="95c0a-130">Stellt eine Definition der benutzerdefinierten Steuerelement Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="95c0a-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="95c0a-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="95c0a-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="95c0a-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="95c0a-132">See Also</span></span>

[<span data-ttu-id="95c0a-133">Customentry-Element für customentries für View (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="95c0a-134">ExpressionBinding-Element für customItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="95c0a-135">Frame-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="95c0a-136">NewLine-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="95c0a-137">Text-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="95c0a-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="95c0a-138">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="95c0a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
