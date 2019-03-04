---
title: PropertyName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853526"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="a0130-102">Element „PropertyName“ für SelectionCondition für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a0130-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="a0130-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a0130-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="a0130-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Eintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="a0130-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="a0130-105">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a0130-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a0130-106">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für Steuerelemente für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für Steuerelemente für Ansicht) PropertyName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="a0130-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a0130-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0130-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a0130-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a0130-108">Attributes and Elements</span></span>

<span data-ttu-id="a0130-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="a0130-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a0130-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="a0130-110">Attributes</span></span>

<span data-ttu-id="a0130-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a0130-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a0130-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a0130-112">Child Elements</span></span>

<span data-ttu-id="a0130-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="a0130-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a0130-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a0130-114">Parent Elements</span></span>

|<span data-ttu-id="a0130-115">Element</span><span class="sxs-lookup"><span data-stu-id="a0130-115">Element</span></span>|<span data-ttu-id="a0130-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a0130-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a0130-117">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a0130-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="a0130-118">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a0130-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a0130-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="a0130-119">Text Value</span></span>

<span data-ttu-id="a0130-120">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a0130-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0130-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a0130-121">Remarks</span></span>

<span data-ttu-id="a0130-122">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a0130-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="a0130-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a0130-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0130-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a0130-124">See Also</span></span>

[<span data-ttu-id="a0130-125">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a0130-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="a0130-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0130-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
