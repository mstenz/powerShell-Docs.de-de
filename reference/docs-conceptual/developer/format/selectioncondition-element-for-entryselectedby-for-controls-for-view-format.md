---
title: Selectioncondition-Element für entryselectedby für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362049"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="9bc67-102">Element „SelectionCondition“ für EntrySelectedBy für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="9bc67-103">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="9bc67-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="9bc67-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="9bc67-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="9bc67-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für das View (Format) customentry-Element für customentries für Steuerelemente für das View (Format) entryselectedby-Element für customentry für Steuerelemente für das View (Format) selectioncondition-Element für entryselectedby für Steuerelemente für View ( Ges</span><span class="sxs-lookup"><span data-stu-id="9bc67-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9bc67-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bc67-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9bc67-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9bc67-107">Attributes and Elements</span></span>

<span data-ttu-id="9bc67-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9bc67-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9bc67-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9bc67-109">Attributes</span></span>

<span data-ttu-id="9bc67-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9bc67-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9bc67-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9bc67-111">Child Elements</span></span>

|<span data-ttu-id="9bc67-112">Element</span><span class="sxs-lookup"><span data-stu-id="9bc67-112">Element</span></span>|<span data-ttu-id="9bc67-113">Description</span><span class="sxs-lookup"><span data-stu-id="9bc67-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bc67-114">PropertyName-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="9bc67-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9bc67-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9bc67-116">Gibt eine .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9bc67-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9bc67-117">ScriptBlock-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="9bc67-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9bc67-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9bc67-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9bc67-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="9bc67-120">Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="9bc67-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9bc67-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9bc67-122">Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9bc67-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="9bc67-123">Typname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="9bc67-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9bc67-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9bc67-125">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9bc67-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9bc67-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9bc67-126">Parent Elements</span></span>

|<span data-ttu-id="9bc67-127">Element</span><span class="sxs-lookup"><span data-stu-id="9bc67-127">Element</span></span>|<span data-ttu-id="9bc67-128">Description</span><span class="sxs-lookup"><span data-stu-id="9bc67-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bc67-129">Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="9bc67-130">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="9bc67-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9bc67-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9bc67-131">Remarks</span></span>

<span data-ttu-id="9bc67-132">Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="9bc67-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="9bc67-133">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="9bc67-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="9bc67-134">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="9bc67-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="9bc67-135">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9bc67-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9bc67-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9bc67-136">See Also</span></span>

[<span data-ttu-id="9bc67-137">PropertyName-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9bc67-138">ScriptBlock-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9bc67-139">Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9bc67-140">Typname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="9bc67-141">Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9bc67-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="9bc67-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="9bc67-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
