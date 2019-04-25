---
title: SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075765"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="0dacc-102">Element „SelectionCondition“ für EntrySelectedBy für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0dacc-103">Definiert eine Bedingung, die vorhanden sein muss, für die Steuerelementdefinition eines allgemeinen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0dacc-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="0dacc-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0dacc-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0dacc-105">Konfigurationselement-Element (Format)-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Steuerelemente für (-Format) CustomEntry Konfigurationselement für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für (Format) SelectionCondition Konfigurationselement für EntrySelectedBy für CustomEntry für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0dacc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0dacc-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0dacc-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0dacc-107">Attributes and Elements</span></span>

<span data-ttu-id="0dacc-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="0dacc-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0dacc-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="0dacc-109">Attributes</span></span>

<span data-ttu-id="0dacc-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="0dacc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0dacc-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0dacc-111">Child Elements</span></span>

|<span data-ttu-id="0dacc-112">Element</span><span class="sxs-lookup"><span data-stu-id="0dacc-112">Element</span></span>|<span data-ttu-id="0dacc-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0dacc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0dacc-114">PropertyName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0dacc-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0dacc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0dacc-116">Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0dacc-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0dacc-117">ScriptBlock-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0dacc-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0dacc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0dacc-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0dacc-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="0dacc-120">SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0dacc-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0dacc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0dacc-122">Gibt den Satz von .NET-Typen, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0dacc-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0dacc-123">TypeName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="0dacc-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0dacc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0dacc-125">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="0dacc-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0dacc-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0dacc-126">Parent Elements</span></span>

|<span data-ttu-id="0dacc-127">Element</span><span class="sxs-lookup"><span data-stu-id="0dacc-127">Element</span></span>|<span data-ttu-id="0dacc-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0dacc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0dacc-129">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="0dacc-130">Definiert die .NET-Typen, die diesen Eintrag, der Steuerelementdefinition der allgemeinen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0dacc-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0dacc-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0dacc-131">Remarks</span></span>

<span data-ttu-id="0dacc-132">Wenn Sie eine auswahlbedingung zu definieren, müssen die folgenden Richtlinien eingehalten werden:</span><span class="sxs-lookup"><span data-stu-id="0dacc-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="0dacc-133">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="0dacc-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0dacc-134">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="0dacc-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0dacc-135">Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0dacc-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0dacc-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0dacc-136">See Also</span></span>

[<span data-ttu-id="0dacc-137">PropertyName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0dacc-138">ScriptBlock-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0dacc-139">SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0dacc-140">TypeName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0dacc-141">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="0dacc-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="0dacc-142">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="0dacc-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
