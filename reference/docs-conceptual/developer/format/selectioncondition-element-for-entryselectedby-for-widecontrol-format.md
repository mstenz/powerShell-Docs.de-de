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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364779"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="73814-102">Element „SelectionCondition“ für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="73814-103">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="73814-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="73814-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die für eine breite Eingabe Definition angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="73814-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="73814-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) entryselectedby-Element für wideentry (Format) selectioncondition-Element für Entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73814-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="73814-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73814-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="73814-107">Attributes and Elements</span></span>

<span data-ttu-id="73814-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="73814-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="73814-109">Sie müssen ein einzelnes `PropertyName` oder `ScriptBlock` Element angeben.</span><span class="sxs-lookup"><span data-stu-id="73814-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="73814-110">Die `SelectionSetName`-und `TypeName` Elemente sind optional.</span><span class="sxs-lookup"><span data-stu-id="73814-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="73814-111">Sie können eines der beiden Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="73814-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73814-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="73814-112">Attributes</span></span>

<span data-ttu-id="73814-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="73814-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73814-114">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="73814-114">Child Elements</span></span>

|<span data-ttu-id="73814-115">Element</span><span class="sxs-lookup"><span data-stu-id="73814-115">Element</span></span>|<span data-ttu-id="73814-116">Description</span><span class="sxs-lookup"><span data-stu-id="73814-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73814-117">PropertyName-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="73814-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="73814-118">Optional element.</span></span><br /><br /> <span data-ttu-id="73814-119">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="73814-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="73814-120">ScriptBlock-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="73814-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="73814-121">Optional element.</span></span><br /><br /> <span data-ttu-id="73814-122">Gibt den Skriptblock an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="73814-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="73814-123">Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="73814-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="73814-124">Optional element.</span></span><br /><br /> <span data-ttu-id="73814-125">Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="73814-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="73814-126">Typname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="73814-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="73814-127">Optional element.</span></span><br /><br /> <span data-ttu-id="73814-128">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="73814-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="73814-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="73814-129">Parent Elements</span></span>

|<span data-ttu-id="73814-130">Element</span><span class="sxs-lookup"><span data-stu-id="73814-130">Element</span></span>|<span data-ttu-id="73814-131">Description</span><span class="sxs-lookup"><span data-stu-id="73814-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73814-132">Entryselectedby-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="73814-133">Definiert die .NET-Typen, die diesen breiten Eintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="73814-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="73814-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="73814-134">Remarks</span></span>

<span data-ttu-id="73814-135">Für jeden breiten Eintrag muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="73814-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="73814-136">Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="73814-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="73814-137">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="73814-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="73814-138">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="73814-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="73814-139">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter Definieren von Bedingungen für den Fall, [dass ein Ansichts Eintrag oder Element verwendet wird](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="73814-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="73814-140">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="73814-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73814-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="73814-141">See Also</span></span>

[<span data-ttu-id="73814-142">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="73814-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="73814-143">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="73814-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="73814-144">Entryselectedby-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="73814-145">PropertyName-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="73814-146">ScriptBlock-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="73814-147">Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="73814-148">Typname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="73814-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="73814-149">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="73814-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
