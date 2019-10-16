---
title: PropertyName-Element für selectioncondition für entryselectedby für wideentry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362239"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="dc108-102">Element „PropertyName“ für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="dc108-102">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="dc108-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="dc108-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="dc108-104">Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und die Definition wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="dc108-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="dc108-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) entryselectedby-Element für wideentry (Format) selectioncondition-Element für Entryselectedby für wideentry (Format) propertyName-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="dc108-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc108-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="dc108-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc108-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="dc108-107">Attributes and Elements</span></span>

<span data-ttu-id="dc108-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="dc108-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc108-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="dc108-109">Attributes</span></span>

<span data-ttu-id="dc108-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="dc108-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc108-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="dc108-111">Child Elements</span></span>

<span data-ttu-id="dc108-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="dc108-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dc108-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="dc108-113">Parent Elements</span></span>

|<span data-ttu-id="dc108-114">Element</span><span class="sxs-lookup"><span data-stu-id="dc108-114">Element</span></span>|<span data-ttu-id="dc108-115">Description</span><span class="sxs-lookup"><span data-stu-id="dc108-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc108-116">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="dc108-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="dc108-117">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="dc108-117">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dc108-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="dc108-118">Text Value</span></span>

<span data-ttu-id="dc108-119">Geben Sie den Namen der .net-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="dc108-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc108-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="dc108-120">Remarks</span></span>

<span data-ttu-id="dc108-121">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder ein auszuwertende Skript angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="dc108-121">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="dc108-122">Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="dc108-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="dc108-123">Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="dc108-123">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc108-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="dc108-124">See Also</span></span>

[<span data-ttu-id="dc108-125">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="dc108-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="dc108-126">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="dc108-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="dc108-127">ScriptBlock-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="dc108-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dc108-128">Selectioncondition-Element für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="dc108-128">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="dc108-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="dc108-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
