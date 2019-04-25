---
title: ScriptBlock-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064423"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="14376-102">Element „ScriptBlock“ für SelectionCondition für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="14376-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="14376-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="14376-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="14376-104">Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet.</span><span class="sxs-lookup"><span data-stu-id="14376-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="14376-105">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="14376-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="14376-106">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für (Format) SelectionCondition Konfigurationselement für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)-Format) ScriptBlock-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="14376-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="14376-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="14376-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="14376-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="14376-108">Attributes and Elements</span></span>

<span data-ttu-id="14376-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="14376-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="14376-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="14376-110">Attributes</span></span>

<span data-ttu-id="14376-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="14376-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="14376-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="14376-112">Child Elements</span></span>

<span data-ttu-id="14376-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="14376-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="14376-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="14376-114">Parent Elements</span></span>

|<span data-ttu-id="14376-115">Element</span><span class="sxs-lookup"><span data-stu-id="14376-115">Element</span></span>|<span data-ttu-id="14376-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14376-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="14376-117">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="14376-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="14376-118">Definiert eine Bedingung, die vorhanden sein muss, für die allgemeine Steuerelementdefinition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="14376-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="14376-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="14376-119">Text Value</span></span>

<span data-ttu-id="14376-120">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="14376-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="14376-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="14376-121">Remarks</span></span>

<span data-ttu-id="14376-122">Die auswahlbedingung muss einen angeben mindestens ein Skript oder eine Eigenschaft zu evaluieren, aber nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="14376-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="14376-123">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="14376-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14376-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="14376-124">See Also</span></span>

[<span data-ttu-id="14376-125">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="14376-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="14376-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="14376-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
