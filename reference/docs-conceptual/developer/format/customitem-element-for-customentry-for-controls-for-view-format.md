---
title: CustomItem-Element für customentry für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363939"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="408a1-102">Element „CustomItem“ für CustomEntry für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="408a1-103">Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="408a1-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="408a1-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="408a1-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="408a1-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für Ansicht (Format) customItem-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="408a1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="408a1-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="408a1-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="408a1-107">Attributes and Elements</span></span>

<span data-ttu-id="408a1-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomItem`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="408a1-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="408a1-109">Weitere Informationen finden Sie in den Hinweisen.</span><span class="sxs-lookup"><span data-stu-id="408a1-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="408a1-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="408a1-110">Attributes</span></span>

<span data-ttu-id="408a1-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="408a1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="408a1-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="408a1-112">Child Elements</span></span>

|<span data-ttu-id="408a1-113">Element</span><span class="sxs-lookup"><span data-stu-id="408a1-113">Element</span></span>|<span data-ttu-id="408a1-114">Description</span><span class="sxs-lookup"><span data-stu-id="408a1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="408a1-115">ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="408a1-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="408a1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="408a1-117">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="408a1-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="408a1-118">Frame-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="408a1-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="408a1-119">Optional element.</span></span><br /><br /> <span data-ttu-id="408a1-120">Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="408a1-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="408a1-121">NewLine-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="408a1-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="408a1-122">Optional element.</span></span><br /><br /> <span data-ttu-id="408a1-123">Fügt der Anzeige des-Steuer Elements eine leere Zeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="408a1-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="408a1-124">Text-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="408a1-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="408a1-125">Optional element.</span></span><br /><br /> <span data-ttu-id="408a1-126">Fügt der Anzeige des-Steuer Elements Text, z. b. Klammern oder eckige Klammern, hinzu.</span><span class="sxs-lookup"><span data-stu-id="408a1-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="408a1-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="408a1-127">Parent Elements</span></span>

|<span data-ttu-id="408a1-128">Element</span><span class="sxs-lookup"><span data-stu-id="408a1-128">Element</span></span>|<span data-ttu-id="408a1-129">Description</span><span class="sxs-lookup"><span data-stu-id="408a1-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="408a1-130">Customentry-Element für customentries für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="408a1-131">Stellt eine Definition des-Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="408a1-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="408a1-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="408a1-132">Remarks</span></span>

<span data-ttu-id="408a1-133">Beachten Sie Folgendes, wenn Sie die untergeordneten Elemente des `CustomItem` Elements angeben:</span><span class="sxs-lookup"><span data-stu-id="408a1-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="408a1-134">Die untergeordneten Elemente müssen in der folgenden Reihenfolge hinzugefügt werden: `ExpressionBinding`, `NewLine`, `Text`und `Frame`.</span><span class="sxs-lookup"><span data-stu-id="408a1-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="408a1-135">Es gibt keine maximale Beschränkung für die Anzahl der Sequenzen, die Sie angeben können.</span><span class="sxs-lookup"><span data-stu-id="408a1-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="408a1-136">In jeder Sequenz gibt es keine maximale Beschränkung für die Anzahl der `ExpressionBinding` Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="408a1-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="408a1-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="408a1-137">See Also</span></span>

[<span data-ttu-id="408a1-138">ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="408a1-139">Frame-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="408a1-140">NewLine-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="408a1-141">Text-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="408a1-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="408a1-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="408a1-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
