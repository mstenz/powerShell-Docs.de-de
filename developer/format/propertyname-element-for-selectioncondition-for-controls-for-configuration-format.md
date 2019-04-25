---
title: PropertyName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064726"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="2f7c6-102">Element „PropertyName“ für SelectionCondition für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="2f7c6-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2f7c6-103">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="2f7c6-104">Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und der Eintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="2f7c6-105">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2f7c6-106">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( Format) CustomEntry-Element für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für (Format) SelectionCondition Konfigurationselement für EntrySelectedBy für CustomEntry für Konfiguration) PropertyName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="2f7c6-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f7c6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f7c6-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f7c6-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2f7c6-108">Attributes and Elements</span></span>

<span data-ttu-id="2f7c6-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f7c6-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2f7c6-110">Attributes</span></span>

<span data-ttu-id="2f7c6-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f7c6-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2f7c6-112">Child Elements</span></span>

<span data-ttu-id="2f7c6-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f7c6-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2f7c6-114">Parent Elements</span></span>

|<span data-ttu-id="2f7c6-115">Element</span><span class="sxs-lookup"><span data-stu-id="2f7c6-115">Element</span></span>|<span data-ttu-id="2f7c6-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2f7c6-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f7c6-117">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2f7c6-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="2f7c6-118">Definiert eine Bedingung, die vorhanden sein muss, für die Steuerelementdefinition eines allgemeinen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2f7c6-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="2f7c6-119">Text Value</span></span>

<span data-ttu-id="2f7c6-120">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f7c6-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2f7c6-121">Remarks</span></span>

<span data-ttu-id="2f7c6-122">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="2f7c6-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="2f7c6-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2f7c6-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f7c6-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2f7c6-124">See Also</span></span>

[<span data-ttu-id="2f7c6-125">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2f7c6-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="2f7c6-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f7c6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
