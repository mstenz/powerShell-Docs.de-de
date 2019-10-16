---
title: Control-Element für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363469"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="d0d06-102">Element „Control“ für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="d0d06-103">Definiert ein Steuerelement, das von der Ansicht verwendet werden kann, und den Namen, der verwendet wird, um auf das Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="d0d06-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="d0d06-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0d06-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0d06-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0d06-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d0d06-106">Attributes and Elements</span></span>

<span data-ttu-id="d0d06-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Control`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d0d06-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0d06-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="d0d06-108">Attributes</span></span>

<span data-ttu-id="d0d06-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="d0d06-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0d06-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d0d06-110">Child Elements</span></span>

|<span data-ttu-id="d0d06-111">Element</span><span class="sxs-lookup"><span data-stu-id="d0d06-111">Element</span></span>|<span data-ttu-id="d0d06-112">Description</span><span class="sxs-lookup"><span data-stu-id="d0d06-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0d06-113">Name-Element für das Steuer Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="d0d06-114">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="d0d06-114">Required element.</span></span><br /><br /> <span data-ttu-id="d0d06-115">Gibt den Namen des Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="d0d06-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="d0d06-116">CustomControl-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="d0d06-117">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="d0d06-117">Required element.</span></span><br /><br /> <span data-ttu-id="d0d06-118">Definiert das Steuerelement, das von dieser Ansicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d0d06-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0d06-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d0d06-119">Parent Elements</span></span>

|<span data-ttu-id="d0d06-120">Element</span><span class="sxs-lookup"><span data-stu-id="d0d06-120">Element</span></span>|<span data-ttu-id="d0d06-121">Description</span><span class="sxs-lookup"><span data-stu-id="d0d06-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0d06-122">Controls-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="d0d06-123">Definiert die Sicht Steuerelemente, die von einer bestimmten Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d0d06-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0d06-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d0d06-124">Remarks</span></span>

<span data-ttu-id="d0d06-125">Dieses Steuerelement kann durch die folgenden Elemente angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="d0d06-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="d0d06-126">Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="d0d06-127">Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="d0d06-128">Customcontrolname-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="d0d06-129">Customcontrolname-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="d0d06-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d0d06-130">See Also</span></span>

[<span data-ttu-id="d0d06-131">CustomControl-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d0d06-132">Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="d0d06-133">Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d0d06-134">Customcontrolname-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="d0d06-135">Customcontrolname-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="d0d06-136">Controls-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="d0d06-137">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d0d06-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d0d06-138">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="d0d06-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
