---
title: CustomEntry-Element für CustomControl für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860366"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="9ea9e-102">Element „CustomEntry“ für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="9ea9e-103">Stellt eine Definition des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-103">Provides a definition of the control.</span></span> <span data-ttu-id="9ea9e-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9ea9e-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ea9e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ea9e-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ea9e-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9ea9e-107">Attributes and Elements</span></span>

<span data-ttu-id="9ea9e-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ea9e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9ea9e-109">Attributes</span></span>

<span data-ttu-id="9ea9e-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ea9e-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9ea9e-111">Child Elements</span></span>

|<span data-ttu-id="9ea9e-112">Element</span><span class="sxs-lookup"><span data-stu-id="9ea9e-112">Element</span></span>|<span data-ttu-id="9ea9e-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ea9e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ea9e-114">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9ea9e-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9ea9e-116">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="9ea9e-117">CustomItem-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9ea9e-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-118">Required element.</span></span><br /><br /> <span data-ttu-id="9ea9e-119">Definiert, wie das Steuerelement für die Daten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9ea9e-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9ea9e-120">Parent Elements</span></span>

|<span data-ttu-id="9ea9e-121">Element</span><span class="sxs-lookup"><span data-stu-id="9ea9e-121">Element</span></span>|<span data-ttu-id="9ea9e-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ea9e-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ea9e-123">CustomEntries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="9ea9e-124">Enthält die Definitionen für das Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="9ea9e-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9ea9e-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9ea9e-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9ea9e-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9ea9e-126">See Also</span></span>

[<span data-ttu-id="9ea9e-127">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9ea9e-128">CustomItem-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9ea9e-129">CustomEntries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ea9e-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="9ea9e-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="9ea9e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
