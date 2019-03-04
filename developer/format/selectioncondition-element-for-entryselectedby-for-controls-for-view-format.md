---
title: SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858016"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="77596-102">Element „SelectionCondition“ für EntrySelectedBy für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="77596-103">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="77596-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="77596-104">Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="77596-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="77596-105">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für Steuerelemente für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für Steuerelemente für Ansicht) -Format)</span><span class="sxs-lookup"><span data-stu-id="77596-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77596-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="77596-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77596-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="77596-107">Attributes and Elements</span></span>

<span data-ttu-id="77596-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="77596-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77596-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="77596-109">Attributes</span></span>

<span data-ttu-id="77596-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="77596-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77596-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="77596-111">Child Elements</span></span>

|<span data-ttu-id="77596-112">Element</span><span class="sxs-lookup"><span data-stu-id="77596-112">Element</span></span>|<span data-ttu-id="77596-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="77596-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77596-114">PropertyName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="77596-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="77596-115">Optional element.</span></span><br /><br /> <span data-ttu-id="77596-116">Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="77596-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="77596-117">ScriptBlock-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="77596-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="77596-118">Optional element.</span></span><br /><br /> <span data-ttu-id="77596-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="77596-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="77596-120">SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="77596-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="77596-121">Optional element.</span></span><br /><br /> <span data-ttu-id="77596-122">Gibt den Satz von .NET-Typen, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="77596-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="77596-123">TypeName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="77596-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="77596-124">Optional element.</span></span><br /><br /> <span data-ttu-id="77596-125">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="77596-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="77596-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="77596-126">Parent Elements</span></span>

|<span data-ttu-id="77596-127">Element</span><span class="sxs-lookup"><span data-stu-id="77596-127">Element</span></span>|<span data-ttu-id="77596-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="77596-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77596-129">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="77596-130">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="77596-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="77596-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="77596-131">Remarks</span></span>

<span data-ttu-id="77596-132">Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="77596-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="77596-133">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="77596-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="77596-134">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="77596-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="77596-135">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="77596-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77596-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="77596-136">See Also</span></span>

[<span data-ttu-id="77596-137">PropertyName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="77596-138">ScriptBlock-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="77596-139">SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="77596-140">TypeName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="77596-141">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="77596-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="77596-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="77596-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
