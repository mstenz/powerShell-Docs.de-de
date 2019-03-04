---
title: CustomEntries-Element für CustomControl für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853676"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="7b3dc-102">Element „CustomEntries“ für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b3dc-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="7b3dc-103">Enthält die Definitionen für das Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-103">Provides the definitions for the control.</span></span> <span data-ttu-id="7b3dc-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7b3dc-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b3dc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b3dc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7b3dc-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b3dc-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7b3dc-107">Attributes and Elements</span></span>

<span data-ttu-id="7b3dc-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente von der `CustomEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="7b3dc-109">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b3dc-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="7b3dc-110">Attributes</span></span>

<span data-ttu-id="7b3dc-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b3dc-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7b3dc-112">Child Elements</span></span>

|<span data-ttu-id="7b3dc-113">Element</span><span class="sxs-lookup"><span data-stu-id="7b3dc-113">Element</span></span>|<span data-ttu-id="7b3dc-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7b3dc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b3dc-115">CustomEntry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b3dc-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="7b3dc-116">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-116">Required element.</span></span><br /><br /> <span data-ttu-id="7b3dc-117">Stellt eine Definition des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7b3dc-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7b3dc-118">Parent Elements</span></span>

|<span data-ttu-id="7b3dc-119">Element</span><span class="sxs-lookup"><span data-stu-id="7b3dc-119">Element</span></span>|<span data-ttu-id="7b3dc-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7b3dc-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b3dc-121">CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b3dc-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="7b3dc-122">Definiert das benutzerdefinierte Steuerelement, das die neue Gruppe anzeigt.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7b3dc-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7b3dc-123">Remarks</span></span>

<span data-ttu-id="7b3dc-124">In den meisten Fällen hat ein Steuerelement nur eine Definition, die in einem einzelnen angegeben wird `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="7b3dc-125">Allerdings ist es möglich, mehrere Definitionen bereitzustellen, wenn das Steuerelement zu verwenden, um unterschiedliche Gruppen angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="7b3dc-126">In diesen Fällen können Sie definieren eine `CustomEntry` -Element für eine Gruppe.</span><span class="sxs-lookup"><span data-stu-id="7b3dc-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b3dc-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7b3dc-127">See Also</span></span>

[<span data-ttu-id="7b3dc-128">CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="7b3dc-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="7b3dc-129">CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b3dc-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="7b3dc-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b3dc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
