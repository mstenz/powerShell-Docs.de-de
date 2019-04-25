---
title: SelectionCondition-Element für EntrySelectedBy für CustomControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075748"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="05a6b-102">Element „SelectionCondition“ für EntrySelectedBy für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="05a6b-103">Definiert eine Bedingung, die für die Steuerelementdefinition eines zu verwendenden vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="05a6b-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="05a6b-104">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="05a6b-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="05a6b-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05a6b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="05a6b-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05a6b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="05a6b-107">Attributes and Elements</span></span>

<span data-ttu-id="05a6b-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="05a6b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="05a6b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="05a6b-109">Attributes</span></span>

<span data-ttu-id="05a6b-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="05a6b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05a6b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="05a6b-111">Child Elements</span></span>

|<span data-ttu-id="05a6b-112">Element</span><span class="sxs-lookup"><span data-stu-id="05a6b-112">Element</span></span>|<span data-ttu-id="05a6b-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="05a6b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05a6b-114">PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="05a6b-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="05a6b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="05a6b-116">Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="05a6b-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="05a6b-117">ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="05a6b-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="05a6b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="05a6b-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="05a6b-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="05a6b-120">SelectionSetName-Element für SelectionCondition für benutzerdefiniertes Steuerelement für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="05a6b-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="05a6b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="05a6b-122">Gibt den Satz von .NET-Typen, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="05a6b-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="05a6b-123">TypeName-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="05a6b-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="05a6b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="05a6b-125">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="05a6b-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="05a6b-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="05a6b-126">Parent Elements</span></span>

|<span data-ttu-id="05a6b-127">Element</span><span class="sxs-lookup"><span data-stu-id="05a6b-127">Element</span></span>|<span data-ttu-id="05a6b-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="05a6b-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05a6b-129">EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="05a6b-130">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="05a6b-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="05a6b-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="05a6b-131">Remarks</span></span>

<span data-ttu-id="05a6b-132">Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="05a6b-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="05a6b-133">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="05a6b-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="05a6b-134">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="05a6b-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="05a6b-135">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="05a6b-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05a6b-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="05a6b-136">See Also</span></span>

[<span data-ttu-id="05a6b-137">PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="05a6b-138">ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="05a6b-139">SelectionSetName-Element für SelectionCondition für benutzerdefiniertes Steuerelement für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="05a6b-140">TypeName-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="05a6b-141">EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05a6b-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="05a6b-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="05a6b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
