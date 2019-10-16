---
title: PropertyName-Element für itemselectioncondition für CustomControl für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362439"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="ac87f-102">Element „PropertyName“ für ItemSeclectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="ac87f-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="ac87f-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="ac87f-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ac87f-104">Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="ac87f-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ac87f-105">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="ac87f-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ac87f-106">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für das View (Format)-ExpressionBinding-Element für customItem für CustomControl für View (Format) itemselectioncondition-Element für die Ausdrucks Bindung für CustomControl für View (Format) propertyName-Element für itemselectioncondition für CustomControl für Ansicht (Format</span><span class="sxs-lookup"><span data-stu-id="ac87f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="ac87f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac87f-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ac87f-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ac87f-108">Attributes and Elements</span></span>

<span data-ttu-id="ac87f-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ac87f-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ac87f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="ac87f-110">Attributes</span></span>

<span data-ttu-id="ac87f-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="ac87f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ac87f-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ac87f-112">Child Elements</span></span>

<span data-ttu-id="ac87f-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="ac87f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ac87f-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ac87f-114">Parent Elements</span></span>

|<span data-ttu-id="ac87f-115">Element</span><span class="sxs-lookup"><span data-stu-id="ac87f-115">Element</span></span>|<span data-ttu-id="ac87f-116">Description</span><span class="sxs-lookup"><span data-stu-id="ac87f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ac87f-117">Itemselectioncondition-Element für die Ausdrucks Bindung für "CustomControl" für "View" (Format)</span><span class="sxs-lookup"><span data-stu-id="ac87f-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="ac87f-118">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="ac87f-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ac87f-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="ac87f-119">Text Value</span></span>

<span data-ttu-id="ac87f-120">Geben Sie den Namen der .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="ac87f-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac87f-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ac87f-121">Remarks</span></span>

<span data-ttu-id="ac87f-122">Wenn dieses Element verwendet wird, können Sie das [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -Element nicht angeben, wenn Sie die Auswahlbedingung definieren.</span><span class="sxs-lookup"><span data-stu-id="ac87f-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac87f-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ac87f-123">See Also</span></span>

[<span data-ttu-id="ac87f-124">ScriptBlock-Element für itemselectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="ac87f-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ac87f-125">Itemselectioncondition-Element für die Ausdrucks Bindung für "CustomControl" für "View" (Format)</span><span class="sxs-lookup"><span data-stu-id="ac87f-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="ac87f-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="ac87f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
