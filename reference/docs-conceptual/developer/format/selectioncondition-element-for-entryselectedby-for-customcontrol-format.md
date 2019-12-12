---
title: Selectioncondition-Element für entryselectedby für CustomControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368439"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="a7b7e-102">Element „SelectionCondition“ für EntrySelectedBy für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="a7b7e-103">Definiert eine Bedingung, die vorhanden sein muss, damit eine Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="a7b7e-104">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="a7b7e-105">Konfigurationselement (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element für View (Format) customentries-Element für CustomControl for View (Format) customentry-Element für customentries für CustomControl für Ansicht ( Format) customItem-Element für customentry für CustomControl for View (Format) entryselectedby-Element für customentry für CustomControl for View (Format) selectioncondition-Element für entryselectedby für CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7b7e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7b7e-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7b7e-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a7b7e-107">Attributes and Elements</span></span>

<span data-ttu-id="a7b7e-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7b7e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="a7b7e-109">Attributes</span></span>

<span data-ttu-id="a7b7e-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7b7e-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a7b7e-111">Child Elements</span></span>

|<span data-ttu-id="a7b7e-112">Element</span><span class="sxs-lookup"><span data-stu-id="a7b7e-112">Element</span></span>|<span data-ttu-id="a7b7e-113">Description</span><span class="sxs-lookup"><span data-stu-id="a7b7e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7b7e-114">PropertyName-Element für selectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a7b7e-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a7b7e-116">Gibt eine .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a7b7e-117">ScriptBlock-Element für selectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a7b7e-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a7b7e-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="a7b7e-120">Selectionsetname-Element für selectioncondition für benutzerdefiniertes Steuer Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a7b7e-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a7b7e-122">Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="a7b7e-123">Typname-Element für selectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="a7b7e-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a7b7e-125">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a7b7e-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a7b7e-126">Parent Elements</span></span>

|<span data-ttu-id="a7b7e-127">Element</span><span class="sxs-lookup"><span data-stu-id="a7b7e-127">Element</span></span>|<span data-ttu-id="a7b7e-128">Description</span><span class="sxs-lookup"><span data-stu-id="a7b7e-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7b7e-129">Entryselectedby-Element für customentry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="a7b7e-130">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a7b7e-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a7b7e-131">Remarks</span></span>

<span data-ttu-id="a7b7e-132">Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="a7b7e-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="a7b7e-133">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="a7b7e-134">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a7b7e-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="a7b7e-135">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a7b7e-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7b7e-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a7b7e-136">See Also</span></span>

[<span data-ttu-id="a7b7e-137">PropertyName-Element für selectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a7b7e-138">ScriptBlock-Element für selectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a7b7e-139">Selectionsetname-Element für selectioncondition für benutzerdefiniertes Steuer Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a7b7e-140">Typname-Element für selectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a7b7e-141">Entryselectedby-Element für customentry für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="a7b7e-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="a7b7e-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a7b7e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
