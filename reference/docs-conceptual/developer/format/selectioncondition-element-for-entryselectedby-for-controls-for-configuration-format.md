---
title: Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368449"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="9d2e4-102">Element „SelectionCondition“ für EntrySelectedBy für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9d2e4-103">Definiert eine Bedingung, die vorhanden sein muss, damit eine allgemeine Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="9d2e4-104">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9d2e4-105">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl für Steuerelemente Configuration (Format) customentry-Element für CustomControl für Steuerelemente für das Configuration (Format) entryselectedby-Element für customentry für Steuerelemente für Configuration (Format) selectioncondition-Element für entryselectedby für customentry für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d2e4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d2e4-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d2e4-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9d2e4-107">Attributes and Elements</span></span>

<span data-ttu-id="9d2e4-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d2e4-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9d2e4-109">Attributes</span></span>

<span data-ttu-id="9d2e4-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d2e4-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9d2e4-111">Child Elements</span></span>

|<span data-ttu-id="9d2e4-112">Element</span><span class="sxs-lookup"><span data-stu-id="9d2e4-112">Element</span></span>|<span data-ttu-id="9d2e4-113">Description</span><span class="sxs-lookup"><span data-stu-id="9d2e4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d2e4-114">PropertyName-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="9d2e4-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9d2e4-116">Gibt eine .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="9d2e4-117">ScriptBlock-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="9d2e4-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="9d2e4-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="9d2e4-120">Selectionsetname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="9d2e4-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-121">Optional element.</span></span><br /><br /> <span data-ttu-id="9d2e4-122">Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="9d2e4-123">Typname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="9d2e4-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="9d2e4-125">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9d2e4-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9d2e4-126">Parent Elements</span></span>

|<span data-ttu-id="9d2e4-127">Element</span><span class="sxs-lookup"><span data-stu-id="9d2e4-127">Element</span></span>|<span data-ttu-id="9d2e4-128">Description</span><span class="sxs-lookup"><span data-stu-id="9d2e4-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d2e4-129">Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="9d2e4-130">Definiert die .NET-Typen, die diesen Eintrag der allgemeinen Steuerelement Definition verwenden.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9d2e4-131">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9d2e4-131">Remarks</span></span>

<span data-ttu-id="9d2e4-132">Die folgenden Richtlinien müssen befolgt werden, wenn eine Auswahlbedingung definiert wird:</span><span class="sxs-lookup"><span data-stu-id="9d2e4-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="9d2e4-133">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="9d2e4-134">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="9d2e4-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="9d2e4-135">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="9d2e4-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d2e4-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9d2e4-136">See Also</span></span>

[<span data-ttu-id="9d2e4-137">PropertyName-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="9d2e4-138">ScriptBlock-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="9d2e4-139">Selectionsetname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="9d2e4-140">Typname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="9d2e4-141">Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="9d2e4-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="9d2e4-142">Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="9d2e4-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
