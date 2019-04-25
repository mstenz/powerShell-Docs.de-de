---
title: CustomEntries-Element für CustomControl für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066582"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="188d3-102">Element „CustomEntries“ für CustomControl für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="188d3-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="188d3-103">Enthält die Definitionen für das Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="188d3-103">Provides the definitions for the control.</span></span> <span data-ttu-id="188d3-104">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="188d3-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="188d3-105">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="188d3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="188d3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="188d3-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="188d3-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="188d3-107">Attributes and Elements</span></span>

<span data-ttu-id="188d3-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente von der `CustomEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="188d3-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="188d3-109">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="188d3-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="188d3-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="188d3-110">Attributes</span></span>

<span data-ttu-id="188d3-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="188d3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="188d3-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="188d3-112">Child Elements</span></span>

|<span data-ttu-id="188d3-113">Element</span><span class="sxs-lookup"><span data-stu-id="188d3-113">Element</span></span>|<span data-ttu-id="188d3-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="188d3-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="188d3-115">CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="188d3-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="188d3-116">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="188d3-116">Required element.</span></span><br /><br /> <span data-ttu-id="188d3-117">Stellt eine Definition des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="188d3-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="188d3-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="188d3-118">Parent Elements</span></span>

|<span data-ttu-id="188d3-119">Element</span><span class="sxs-lookup"><span data-stu-id="188d3-119">Element</span></span>|<span data-ttu-id="188d3-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="188d3-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="188d3-121">CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="188d3-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="188d3-122">Definiert das Steuerelement, das von der Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="188d3-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="188d3-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="188d3-123">Remarks</span></span>

<span data-ttu-id="188d3-124">In den meisten Fällen hat ein Steuerelement nur eine Definition, die in einem einzelnen angegeben wird `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="188d3-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="188d3-125">Allerdings ist es möglich, mehrere Definitionen bereitzustellen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="188d3-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="188d3-126">In diesen Fällen können Sie definieren eine `CustomEntry` -Element für jedes Objekt oder eine Gruppe von Objekten.</span><span class="sxs-lookup"><span data-stu-id="188d3-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="188d3-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="188d3-127">See Also</span></span>

[<span data-ttu-id="188d3-128">CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="188d3-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="188d3-129">CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="188d3-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="188d3-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="188d3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
