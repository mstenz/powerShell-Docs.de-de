---
title: PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc48a417-2083-46d4-ac38-16c12e65b6b9
caps.latest.revision: 7
ms.openlocfilehash: e08037d5d051d3be51e90193c7e87cc2e738f78a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064695"
---
# <a name="propertyname-element-for-selectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="70032-102">Element „PropertyName“ für SelectionCondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="70032-102">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="70032-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="70032-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="70032-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="70032-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="70032-105">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="70032-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="70032-106">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)-PropertyName-Format) -Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="70032-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70032-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="70032-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70032-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="70032-108">Attributes and Elements</span></span>

<span data-ttu-id="70032-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="70032-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70032-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="70032-110">Attributes</span></span>

<span data-ttu-id="70032-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="70032-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70032-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="70032-112">Child Elements</span></span>

<span data-ttu-id="70032-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="70032-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70032-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="70032-114">Parent Elements</span></span>

|<span data-ttu-id="70032-115">Element</span><span class="sxs-lookup"><span data-stu-id="70032-115">Element</span></span>|<span data-ttu-id="70032-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="70032-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70032-117">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="70032-117">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="70032-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="70032-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70032-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="70032-119">Text Value</span></span>

<span data-ttu-id="70032-120">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="70032-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="70032-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="70032-121">Remarks</span></span>

<span data-ttu-id="70032-122">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="70032-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="70032-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="70032-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70032-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="70032-124">See Also</span></span>

[<span data-ttu-id="70032-125">SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="70032-125">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="70032-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="70032-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
