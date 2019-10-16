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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362049"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="f7251-102">Element „SelectionCondition“ für EntrySelectedBy für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="f7251-103">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="f7251-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="f7251-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="f7251-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="f7251-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für das View (Format) customentry-Element für customentries für Steuerelemente für das View (Format) entryselectedby-Element für customentry für Steuerelemente für das View (Format) selectioncondition-Element für entryselectedby für Steuerelemente für View ( Ges</span><span class="sxs-lookup"><span data-stu-id="f7251-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7251-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7251-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7251-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f7251-107">Attributes and Elements</span></span>

<span data-ttu-id="f7251-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f7251-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7251-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f7251-109">Attributes</span></span>

<span data-ttu-id="f7251-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="f7251-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7251-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f7251-111">Child Elements</span></span>

|<span data-ttu-id="f7251-112">Element</span><span class="sxs-lookup"><span data-stu-id="f7251-112">Element</span></span>|<span data-ttu-id="f7251-113">Description</span><span class="sxs-lookup"><span data-stu-id="f7251-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7251-114">PropertyName-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f7251-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f7251-115">Optional element.</span></span><br /><br /> <span data-ttu-id="f7251-116">Gibt eine .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="f7251-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f7251-117">ScriptBlock-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f7251-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f7251-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f7251-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="f7251-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f7251-120">Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f7251-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f7251-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f7251-122">Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="f7251-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f7251-123">Typname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="f7251-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f7251-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f7251-125">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="f7251-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7251-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f7251-126">Parent Elements</span></span>

|<span data-ttu-id="f7251-127">Element</span><span class="sxs-lookup"><span data-stu-id="f7251-127">Element</span></span>|<span data-ttu-id="f7251-128">Description</span><span class="sxs-lookup"><span data-stu-id="f7251-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7251-129">Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="f7251-130">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="f7251-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7251-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f7251-131">Remarks</span></span>

<span data-ttu-id="f7251-132">Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="f7251-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f7251-133">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="f7251-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f7251-134">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="f7251-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f7251-135">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f7251-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7251-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f7251-136">See Also</span></span>

[<span data-ttu-id="f7251-137">PropertyName-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f7251-138">ScriptBlock-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f7251-139">Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f7251-140">Typname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="f7251-141">Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f7251-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="f7251-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="f7251-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
