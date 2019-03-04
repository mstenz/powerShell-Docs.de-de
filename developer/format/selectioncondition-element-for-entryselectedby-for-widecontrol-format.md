---
title: SelectionCondition-Element für EntrySelectedBy für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854116"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="487c8-102">Element „SelectionCondition“ für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="487c8-103">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="487c8-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="487c8-104">Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine große Eintrag Definition angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="487c8-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="487c8-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="487c8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="487c8-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="487c8-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="487c8-107">Attributes and Elements</span></span>

<span data-ttu-id="487c8-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="487c8-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="487c8-109">Sie müssen angeben, dass eine einzelne `PropertyName` oder `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="487c8-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="487c8-110">Die `SelectionSetName` und `TypeName` Elemente sind optional.</span><span class="sxs-lookup"><span data-stu-id="487c8-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="487c8-111">Sie können eine der beiden Element angeben.</span><span class="sxs-lookup"><span data-stu-id="487c8-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="487c8-112">Attributes</span><span class="sxs-lookup"><span data-stu-id="487c8-112">Attributes</span></span>

<span data-ttu-id="487c8-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="487c8-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="487c8-114">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="487c8-114">Child Elements</span></span>

|<span data-ttu-id="487c8-115">Element</span><span class="sxs-lookup"><span data-stu-id="487c8-115">Element</span></span>|<span data-ttu-id="487c8-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="487c8-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="487c8-117">PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="487c8-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="487c8-118">Optional element.</span></span><br /><br /> <span data-ttu-id="487c8-119">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="487c8-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="487c8-120">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="487c8-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="487c8-121">Optional element.</span></span><br /><br /> <span data-ttu-id="487c8-122">Gibt den Skriptblock, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="487c8-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="487c8-123">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="487c8-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="487c8-124">Optional element.</span></span><br /><br /> <span data-ttu-id="487c8-125">Gibt den Satz von .NET-Typen, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="487c8-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="487c8-126">TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="487c8-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="487c8-127">Optional element.</span></span><br /><br /> <span data-ttu-id="487c8-128">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="487c8-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="487c8-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="487c8-129">Parent Elements</span></span>

|<span data-ttu-id="487c8-130">Element</span><span class="sxs-lookup"><span data-stu-id="487c8-130">Element</span></span>|<span data-ttu-id="487c8-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="487c8-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="487c8-132">EntrySelectedBy-Element für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="487c8-133">Definiert die .NET-Typen, die dieser breiten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="487c8-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="487c8-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="487c8-134">Remarks</span></span>

<span data-ttu-id="487c8-135">Jeder Eintrag Breite benötigen mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert.</span><span class="sxs-lookup"><span data-stu-id="487c8-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="487c8-136">Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="487c8-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="487c8-137">Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="487c8-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="487c8-138">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="487c8-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="487c8-139">Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="487c8-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="487c8-140">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="487c8-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="487c8-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="487c8-141">See Also</span></span>

[<span data-ttu-id="487c8-142">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="487c8-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="487c8-143">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="487c8-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="487c8-144">EntrySelectedBy-Element für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="487c8-145">PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="487c8-146">ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="487c8-147">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="487c8-148">TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="487c8-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="487c8-149">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="487c8-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
