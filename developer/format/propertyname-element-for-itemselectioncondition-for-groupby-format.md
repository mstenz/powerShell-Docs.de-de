---
title: PropertyName-Element für ItemSelectionCondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064763"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="451c6-102">Element „PropertyName“ für ItemSeclectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="451c6-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="451c6-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="451c6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="451c6-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="451c6-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="451c6-105">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="451c6-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="451c6-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format) ExpressionBinding-Element für CustomItem für GroupBy (Format) ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)-PropertyName-Element für ItemSelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="451c6-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="451c6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="451c6-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="451c6-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="451c6-108">Attributes and Elements</span></span>

<span data-ttu-id="451c6-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="451c6-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="451c6-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="451c6-110">Attributes</span></span>

<span data-ttu-id="451c6-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="451c6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="451c6-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="451c6-112">Child Elements</span></span>

<span data-ttu-id="451c6-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="451c6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="451c6-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="451c6-114">Parent Elements</span></span>

|<span data-ttu-id="451c6-115">Element</span><span class="sxs-lookup"><span data-stu-id="451c6-115">Element</span></span>|<span data-ttu-id="451c6-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="451c6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="451c6-117">ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="451c6-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="451c6-118">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="451c6-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="451c6-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="451c6-119">Text Value</span></span>

<span data-ttu-id="451c6-120">Geben Sie den Namen der .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="451c6-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="451c6-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="451c6-121">Remarks</span></span>

<span data-ttu-id="451c6-122">Wenn dieses Element verwendet wird, Sie können nicht angeben, die ["scriptblock"](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -Element, wenn die auswahlbedingung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="451c6-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="451c6-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="451c6-123">See Also</span></span>

[<span data-ttu-id="451c6-124">ScriptBlock-Element für ItemSelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="451c6-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="451c6-125">ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="451c6-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="451c6-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="451c6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
