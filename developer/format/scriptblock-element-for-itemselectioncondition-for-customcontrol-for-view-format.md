---
title: ScriptBlock-Element für ItemSelectionCondition für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862236"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="42438-102">Element „ScriptBlock“ für ItemSeclectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="42438-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="42438-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="42438-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="42438-104">Wenn dieses Skript ergab `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="42438-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="42438-105">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="42438-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="42438-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für Ansicht (Format) ExpressionBinding-Element für CustomItem für CustomControl für ItemSelectionCondition-Element für Ausdrucksbindung für CustomControl für Ansicht (Format)-ScriptBlock-Element für ItemSelectionCondition für Ansicht (Format) CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="42438-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42438-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="42438-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42438-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="42438-108">Attributes and Elements</span></span>

<span data-ttu-id="42438-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="42438-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42438-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="42438-110">Attributes</span></span>

<span data-ttu-id="42438-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="42438-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42438-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="42438-112">Child Elements</span></span>

<span data-ttu-id="42438-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="42438-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="42438-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="42438-114">Parent Elements</span></span>

|<span data-ttu-id="42438-115">Element</span><span class="sxs-lookup"><span data-stu-id="42438-115">Element</span></span>|<span data-ttu-id="42438-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="42438-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42438-117">ItemSelectionCondition-Element für Ausdrucksbindung für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="42438-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="42438-118">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="42438-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="42438-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="42438-119">Text Value</span></span>

<span data-ttu-id="42438-120">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="42438-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="42438-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="42438-121">Remarks</span></span>

<span data-ttu-id="42438-122">Wenn dieses Element verwendet wird, Sie können nicht angeben, die [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -Element, wenn die auswahlbedingung zu definieren.</span><span class="sxs-lookup"><span data-stu-id="42438-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="42438-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="42438-123">See Also</span></span>

[<span data-ttu-id="42438-124">PropertyName-Element für ItemSelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="42438-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="42438-125">ItemSelectionCondition-Element für Ausdrucksbindung für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="42438-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="42438-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="42438-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
