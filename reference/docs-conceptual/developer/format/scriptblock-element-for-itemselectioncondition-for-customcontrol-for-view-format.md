---
title: ScriptBlock-Element für itemselectioncondition für CustomControl für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362069"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="afe8c-102">Element „ScriptBlock“ für ItemSeclectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8c-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="afe8c-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="afe8c-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="afe8c-104">Wenn dieses Skript `true` ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="afe8c-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="afe8c-105">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="afe8c-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="afe8c-106">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für das View (Format)-ExpressionBinding-Element für customItem für CustomControl für View (Format) itemselectioncondition-Element für die Ausdrucks Bindung von CustomControl für View (Format) ScriptBlock-Element für itemselectioncondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="afe8c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="afe8c-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="afe8c-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="afe8c-108">Attributes and Elements</span></span>

<span data-ttu-id="afe8c-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="afe8c-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="afe8c-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="afe8c-110">Attributes</span></span>

<span data-ttu-id="afe8c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="afe8c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="afe8c-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="afe8c-112">Child Elements</span></span>

<span data-ttu-id="afe8c-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="afe8c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="afe8c-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="afe8c-114">Parent Elements</span></span>

|<span data-ttu-id="afe8c-115">Element</span><span class="sxs-lookup"><span data-stu-id="afe8c-115">Element</span></span>|<span data-ttu-id="afe8c-116">Description</span><span class="sxs-lookup"><span data-stu-id="afe8c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="afe8c-117">Itemselectioncondition-Element für die Ausdrucks Bindung für "CustomControl" für "View" (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8c-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="afe8c-118">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="afe8c-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="afe8c-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="afe8c-119">Text Value</span></span>

<span data-ttu-id="afe8c-120">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="afe8c-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="afe8c-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="afe8c-121">Remarks</span></span>

<span data-ttu-id="afe8c-122">Wenn dieses Element verwendet wird, können Sie beim Definieren der Auswahlbedingung nicht das [propertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -Element angeben.</span><span class="sxs-lookup"><span data-stu-id="afe8c-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="afe8c-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="afe8c-123">See Also</span></span>

[<span data-ttu-id="afe8c-124">PropertyName-Element für itemselectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8c-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="afe8c-125">Itemselectioncondition-Element für die Ausdrucks Bindung für "CustomControl" für "View" (Format)</span><span class="sxs-lookup"><span data-stu-id="afe8c-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="afe8c-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="afe8c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
