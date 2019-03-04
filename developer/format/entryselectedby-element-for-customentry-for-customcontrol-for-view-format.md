---
title: EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859586"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="19d40-102">Element „EntrySelectedBy“ für CustomEntry für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-102">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="19d40-103">Definiert die .NET-Typen, die dieser benutzerdefinierten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="19d40-103">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>

<span data-ttu-id="19d40-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) EntrySelectedBy -Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19d40-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="19d40-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19d40-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="19d40-106">Attributes and Elements</span></span>

<span data-ttu-id="19d40-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="19d40-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19d40-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="19d40-108">Attributes</span></span>

<span data-ttu-id="19d40-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="19d40-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19d40-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="19d40-110">Child Elements</span></span>

|<span data-ttu-id="19d40-111">Element</span><span class="sxs-lookup"><span data-stu-id="19d40-111">Element</span></span>|<span data-ttu-id="19d40-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="19d40-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19d40-113">SelectionCondition-Element für EntrySelectedBy für CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-113">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="19d40-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="19d40-114">Optional element.</span></span><br /><br /> <span data-ttu-id="19d40-115">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="19d40-115">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="19d40-116">SelectionSetName-Element für EntrySelectedBy für CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-116">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|<span data-ttu-id="19d40-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="19d40-117">Optional element.</span></span><br /><br /> <span data-ttu-id="19d40-118">Gibt einen Satz von .NET-Typen, die dieser Definition der Ansicht des Steuerelement zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="19d40-118">Specifies a set of .NET types that use this definition of the control view.</span></span>|
|[<span data-ttu-id="19d40-119">TypeName-Element für EntrySelectedBy für CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-119">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="19d40-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="19d40-120">Optional element.</span></span><br /><br /> <span data-ttu-id="19d40-121">Gibt einen .NET-Typ, ein, der dieser Definition der Ansicht des Steuerelement verwendet.</span><span class="sxs-lookup"><span data-stu-id="19d40-121">Specifies a .NET type that uses this definition of the control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="19d40-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="19d40-122">Parent Elements</span></span>

|<span data-ttu-id="19d40-123">Element</span><span class="sxs-lookup"><span data-stu-id="19d40-123">Element</span></span>|<span data-ttu-id="19d40-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="19d40-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19d40-125">CustomEntry-Element für CustomEntries für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-125">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="19d40-126">Definiert die Steuerelemente, die von bestimmten .NET Objekten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="19d40-126">Defines the controls used by specific .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="19d40-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="19d40-127">Remarks</span></span>

<span data-ttu-id="19d40-128">Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung nach einem Eintrag angeben.</span><span class="sxs-lookup"><span data-stu-id="19d40-128">You must specify at least one type, selection set, or selection condition for an entry.</span></span> <span data-ttu-id="19d40-129">Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="19d40-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="19d40-130">Auswahlbedingungen werden verwendet, um eine Bedingung, die vorhanden sein muss, für den Eintrag, der verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder einen bestimmten Eigenschaftswert zu definieren oder Skripts ergibt `true`.</span><span class="sxs-lookup"><span data-stu-id="19d40-130">Selection conditions are used to define a condition that must exist for the entry to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="19d40-131">Weitere Informationen zu auswahlbedingungen, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="19d40-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="19d40-132">Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [benutzerdefinierte Ansicht des Steuerelement](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="19d40-132">For more information about the components of a custom control view, see [Custom Control View](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19d40-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="19d40-133">See Also</span></span>

[<span data-ttu-id="19d40-134">SelectionCondition-Element für EntrySelectedBy für CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-134">SelectionCondition Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="19d40-135">SelectionSetName-Element für EntrySelectedBy für CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-135">SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[<span data-ttu-id="19d40-136">TypeName-Element für EntrySelectedBy für CustomEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-136">TypeName Element for EntrySelectedBy for CustomEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="19d40-137">CustomEntry-Element für CustomEntries für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="19d40-137">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="19d40-138">Benutzerdefiniertes Steuerelement anzeigen</span><span class="sxs-lookup"><span data-stu-id="19d40-138">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="19d40-139">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="19d40-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
