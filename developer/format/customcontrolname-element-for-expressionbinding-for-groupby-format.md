---
title: CustomControlName-Element für die ExpressionBinding für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854296"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="50720-102">Element „CustomControlName“ für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="50720-103">Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="50720-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="50720-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="50720-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="50720-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format) ExpressionBinding-Element für CustomItem für GroupBy (Format) CustomControlName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50720-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="50720-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50720-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="50720-107">Attributes and Elements</span></span>

<span data-ttu-id="50720-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControlName` Element.</span><span class="sxs-lookup"><span data-stu-id="50720-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="50720-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="50720-109">Attributes</span></span>

<span data-ttu-id="50720-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="50720-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50720-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="50720-111">Child Elements</span></span>

<span data-ttu-id="50720-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="50720-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="50720-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="50720-113">Parent Elements</span></span>

|<span data-ttu-id="50720-114">Element</span><span class="sxs-lookup"><span data-stu-id="50720-114">Element</span></span>|<span data-ttu-id="50720-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="50720-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50720-116">ExpressionBinding-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="50720-117">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="50720-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="50720-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="50720-118">Text Value</span></span>

<span data-ttu-id="50720-119">Geben Sie den Namen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="50720-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="50720-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="50720-120">Remarks</span></span>

<span data-ttu-id="50720-121">Sie können allgemeine Steuerelemente, die von allen Ansichten des eine Formatierungsdatei verwendet werden können erstellen und Sie können Steuerelemente, die von einer bestimmten Ansicht verwendet werden können erstellen.</span><span class="sxs-lookup"><span data-stu-id="50720-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="50720-122">Die folgenden Elemente geben Sie die Namen dieser Steuerelemente:</span><span class="sxs-lookup"><span data-stu-id="50720-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="50720-123">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="50720-124">Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="50720-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="50720-125">See Also</span></span>

[<span data-ttu-id="50720-126">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="50720-127">Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="50720-128">ExpressionBinding-Element für CustomItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="50720-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="50720-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="50720-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
