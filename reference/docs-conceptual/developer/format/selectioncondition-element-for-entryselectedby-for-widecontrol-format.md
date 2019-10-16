---
title: Selectioncondition-Element für entryselectedby für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364779"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="cd871-102">Element „SelectionCondition“ für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="cd871-103">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="cd871-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="cd871-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die für eine breite Eingabe Definition angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="cd871-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="cd871-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) entryselectedby-Element für wideentry (Format) selectioncondition-Element für Entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd871-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd871-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd871-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="cd871-107">Attributes and Elements</span></span>

<span data-ttu-id="cd871-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="cd871-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="cd871-109">Sie müssen ein einzelnes `PropertyName`-oder `ScriptBlock`-Element angeben.</span><span class="sxs-lookup"><span data-stu-id="cd871-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="cd871-110">Die `SelectionSetName`-und `TypeName`-Elemente sind optional.</span><span class="sxs-lookup"><span data-stu-id="cd871-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="cd871-111">Sie können eines der beiden Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="cd871-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd871-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="cd871-112">Attributes</span></span>

<span data-ttu-id="cd871-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="cd871-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cd871-114">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cd871-114">Child Elements</span></span>

|<span data-ttu-id="cd871-115">Element</span><span class="sxs-lookup"><span data-stu-id="cd871-115">Element</span></span>|<span data-ttu-id="cd871-116">Description</span><span class="sxs-lookup"><span data-stu-id="cd871-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd871-117">PropertyName-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="cd871-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="cd871-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cd871-119">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="cd871-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="cd871-120">ScriptBlock-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="cd871-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="cd871-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cd871-122">Gibt den Skriptblock an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="cd871-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="cd871-123">Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="cd871-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="cd871-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cd871-125">Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="cd871-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="cd871-126">Typname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="cd871-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="cd871-127">Optional element.</span></span><br /><br /> <span data-ttu-id="cd871-128">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="cd871-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cd871-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cd871-129">Parent Elements</span></span>

|<span data-ttu-id="cd871-130">Element</span><span class="sxs-lookup"><span data-stu-id="cd871-130">Element</span></span>|<span data-ttu-id="cd871-131">Description</span><span class="sxs-lookup"><span data-stu-id="cd871-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd871-132">Entryselectedby-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="cd871-133">Definiert die .NET-Typen, die diesen breiten Eintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="cd871-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cd871-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cd871-134">Remarks</span></span>

<span data-ttu-id="cd871-135">Für jeden breiten Eintrag muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="cd871-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="cd871-136">Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="cd871-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="cd871-137">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="cd871-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="cd871-138">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="cd871-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="cd871-139">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter Definieren von Bedingungen für den Fall, [dass ein Ansichts Eintrag oder Element verwendet wird](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="cd871-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="cd871-140">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="cd871-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd871-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cd871-141">See Also</span></span>

[<span data-ttu-id="cd871-142">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="cd871-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cd871-143">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="cd871-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="cd871-144">Entryselectedby-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="cd871-145">PropertyName-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="cd871-146">ScriptBlock-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cd871-147">Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="cd871-148">Typname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="cd871-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="cd871-149">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="cd871-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
