---
title: PropertyName-Element für SelectionCondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853186"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="37ba2-102">Element „PropertyName“ für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="37ba2-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="37ba2-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="37ba2-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="37ba2-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="37ba2-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="37ba2-105">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="37ba2-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="37ba2-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)-PropertyName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="37ba2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37ba2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="37ba2-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37ba2-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="37ba2-108">Attributes and Elements</span></span>

<span data-ttu-id="37ba2-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="37ba2-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="37ba2-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="37ba2-110">Attributes</span></span>

<span data-ttu-id="37ba2-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="37ba2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37ba2-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="37ba2-112">Child Elements</span></span>

<span data-ttu-id="37ba2-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="37ba2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37ba2-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="37ba2-114">Parent Elements</span></span>

|<span data-ttu-id="37ba2-115">Element</span><span class="sxs-lookup"><span data-stu-id="37ba2-115">Element</span></span>|<span data-ttu-id="37ba2-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="37ba2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37ba2-117">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="37ba2-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="37ba2-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="37ba2-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="37ba2-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="37ba2-119">Text Value</span></span>

<span data-ttu-id="37ba2-120">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="37ba2-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="37ba2-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="37ba2-121">Remarks</span></span>

<span data-ttu-id="37ba2-122">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="37ba2-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="37ba2-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="37ba2-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37ba2-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="37ba2-124">See Also</span></span>

[<span data-ttu-id="37ba2-125">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="37ba2-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="37ba2-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="37ba2-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
