---
title: PropertyName-Element für itemselectioncondition für Steuerelemente für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362479"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="81ca1-102">Element „PropertyName“ für ItemSeclectionCondition für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="81ca1-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="81ca1-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="81ca1-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="81ca1-104">Wenn diese Eigenschaft vorhanden ist oder als zu `true`ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="81ca1-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="81ca1-105">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="81ca1-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="81ca1-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für View (Format) ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format) Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für das View (Format) propertyName-Element für itemselectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="81ca1-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81ca1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="81ca1-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81ca1-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="81ca1-108">Attributes and Elements</span></span>

<span data-ttu-id="81ca1-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="81ca1-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81ca1-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="81ca1-110">Attributes</span></span>

<span data-ttu-id="81ca1-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="81ca1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81ca1-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="81ca1-112">Child Elements</span></span>

<span data-ttu-id="81ca1-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="81ca1-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="81ca1-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="81ca1-114">Parent Elements</span></span>

|<span data-ttu-id="81ca1-115">Element</span><span class="sxs-lookup"><span data-stu-id="81ca1-115">Element</span></span>|<span data-ttu-id="81ca1-116">Description</span><span class="sxs-lookup"><span data-stu-id="81ca1-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81ca1-117">Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="81ca1-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="81ca1-118">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="81ca1-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="81ca1-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="81ca1-119">Text Value</span></span>

<span data-ttu-id="81ca1-120">Geben Sie den Namen der .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="81ca1-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="81ca1-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="81ca1-121">Remarks</span></span>

<span data-ttu-id="81ca1-122">Wenn dieses Element verwendet wird, können Sie das [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -Element nicht angeben, wenn Sie die Auswahlbedingung definieren.</span><span class="sxs-lookup"><span data-stu-id="81ca1-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="81ca1-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="81ca1-123">See Also</span></span>

[<span data-ttu-id="81ca1-124">ScriptBlock-Element für itemselectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="81ca1-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="81ca1-125">Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="81ca1-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="81ca1-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="81ca1-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
