---
title: ScriptBlock-Element für ItemSelectionCondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064542"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="d26b5-102">Element „ScriptBlock“ für ItemSeclectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d26b5-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="d26b5-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="d26b5-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d26b5-104">Wenn dieses Skript ergab `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="d26b5-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="d26b5-105">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d26b5-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="d26b5-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format) ExpressionBinding-Element für CustomItem für GroupBy (Format) ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)-ScriptBlock-Element für ItemSelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d26b5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d26b5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d26b5-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d26b5-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d26b5-108">Attributes and Elements</span></span>

<span data-ttu-id="d26b5-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="d26b5-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d26b5-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d26b5-110">Attributes</span></span>

<span data-ttu-id="d26b5-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="d26b5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d26b5-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d26b5-112">Child Elements</span></span>

<span data-ttu-id="d26b5-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="d26b5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d26b5-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d26b5-114">Parent Elements</span></span>

|<span data-ttu-id="d26b5-115">Element</span><span class="sxs-lookup"><span data-stu-id="d26b5-115">Element</span></span>|<span data-ttu-id="d26b5-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d26b5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d26b5-117">ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d26b5-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="d26b5-118">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="d26b5-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d26b5-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="d26b5-119">Text Value</span></span>

<span data-ttu-id="d26b5-120">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="d26b5-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d26b5-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d26b5-121">Remarks</span></span>

<span data-ttu-id="d26b5-122">Wenn dieses Element verwendet wird, Sie können nicht angeben, die [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) -Element, wenn die auswahlbedingung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="d26b5-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="d26b5-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d26b5-123">See Also</span></span>

[<span data-ttu-id="d26b5-124">ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d26b5-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="d26b5-125">PropertyName-Element für ItemSelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="d26b5-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="d26b5-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d26b5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
