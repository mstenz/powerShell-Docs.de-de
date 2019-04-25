---
title: Control-Element für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066769"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="c1387-102">Element „Control“ für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="c1387-103">Definiert ein Steuerelement, das von der Ansicht und der Name, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c1387-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="c1387-104">-Element (Format) ViewDefinitions-Element (Format) Ansicht Konfigurationselement (Format) steuert Elementen (-Format)-Steuerelement für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1387-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1387-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1387-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="c1387-106">Attributes and Elements</span></span>

<span data-ttu-id="c1387-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Control` Element.</span><span class="sxs-lookup"><span data-stu-id="c1387-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1387-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="c1387-108">Attributes</span></span>

<span data-ttu-id="c1387-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="c1387-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1387-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c1387-110">Child Elements</span></span>

|<span data-ttu-id="c1387-111">Element</span><span class="sxs-lookup"><span data-stu-id="c1387-111">Element</span></span>|<span data-ttu-id="c1387-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1387-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1387-113">Name-Element für das Steuerelement für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c1387-114">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="c1387-114">Required element.</span></span><br /><br /> <span data-ttu-id="c1387-115">Gibt den Namen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="c1387-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="c1387-116">CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c1387-117">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="c1387-117">Required element.</span></span><br /><br /> <span data-ttu-id="c1387-118">Definiert das Steuerelement ab, die von dieser Sicht.</span><span class="sxs-lookup"><span data-stu-id="c1387-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1387-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c1387-119">Parent Elements</span></span>

|<span data-ttu-id="c1387-120">Element</span><span class="sxs-lookup"><span data-stu-id="c1387-120">Element</span></span>|<span data-ttu-id="c1387-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c1387-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1387-122">Controls-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="c1387-123">Definiert die Steuerelemente, die von einer bestimmten Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="c1387-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1387-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c1387-124">Remarks</span></span>

<span data-ttu-id="c1387-125">Dieses Steuerelement kann durch die folgenden Elemente angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="c1387-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="c1387-126">CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="c1387-127">CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="c1387-128">CustomControlName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="c1387-129">CustomControlName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="c1387-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c1387-130">See Also</span></span>

[<span data-ttu-id="c1387-131">CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c1387-132">CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="c1387-133">CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c1387-134">CustomControlName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="c1387-135">CustomControlName-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="c1387-136">Controls-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="c1387-137">Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c1387-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c1387-138">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1387-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
