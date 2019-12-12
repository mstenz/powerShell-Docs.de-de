---
title: PropertyName-Element für itemselectioncondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362409"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="aade1-102">Element „PropertyName“ für ItemSeclectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="aade1-102">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="aade1-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="aade1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="aade1-104">Wenn diese Eigenschaft vorhanden ist oder als zu `true`ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="aade1-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="aade1-105">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="aade1-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="aade1-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) ExpressionBinding-Element für customItem für GroupBy (Format) itemselectioncondition-Element für ExpressionBinding für GroupBy (Format) propertyName-Element für Itemselectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="aade1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aade1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="aade1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aade1-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="aade1-108">Attributes and Elements</span></span>

<span data-ttu-id="aade1-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="aade1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aade1-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="aade1-110">Attributes</span></span>

<span data-ttu-id="aade1-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="aade1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aade1-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="aade1-112">Child Elements</span></span>

<span data-ttu-id="aade1-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="aade1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aade1-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="aade1-114">Parent Elements</span></span>

|<span data-ttu-id="aade1-115">Element</span><span class="sxs-lookup"><span data-stu-id="aade1-115">Element</span></span>|<span data-ttu-id="aade1-116">Description</span><span class="sxs-lookup"><span data-stu-id="aade1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aade1-117">Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="aade1-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="aade1-118">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="aade1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aade1-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="aade1-119">Text Value</span></span>

<span data-ttu-id="aade1-120">Geben Sie den Namen der .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="aade1-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="aade1-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="aade1-121">Remarks</span></span>

<span data-ttu-id="aade1-122">Wenn dieses Element verwendet wird, können Sie das [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -Element nicht angeben, wenn Sie die Auswahlbedingung definieren.</span><span class="sxs-lookup"><span data-stu-id="aade1-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="aade1-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aade1-123">See Also</span></span>

[<span data-ttu-id="aade1-124">ScriptBlock-Element für itemselectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="aade1-124">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="aade1-125">Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="aade1-125">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="aade1-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="aade1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
