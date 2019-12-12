---
title: Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363889"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="05c62-102">Element „EntrySelectedBy“ für CustomEntry für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="05c62-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="05c62-103">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="05c62-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="05c62-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="05c62-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="05c62-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05c62-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="05c62-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="05c62-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="05c62-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="05c62-107">Attributes and Elements</span></span>

<span data-ttu-id="05c62-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="05c62-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="05c62-109">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine Definition angeben.</span><span class="sxs-lookup"><span data-stu-id="05c62-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="05c62-110">Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="05c62-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="05c62-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="05c62-111">Attributes</span></span>

<span data-ttu-id="05c62-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="05c62-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="05c62-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="05c62-113">Child Elements</span></span>

|<span data-ttu-id="05c62-114">Element</span><span class="sxs-lookup"><span data-stu-id="05c62-114">Element</span></span>|<span data-ttu-id="05c62-115">Description</span><span class="sxs-lookup"><span data-stu-id="05c62-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05c62-116">Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="05c62-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="05c62-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="05c62-117">Optional element.</span></span><br /><br /> <span data-ttu-id="05c62-118">Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="05c62-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="05c62-119">Selectionsetname-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="05c62-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="05c62-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="05c62-120">Optional element.</span></span><br /><br /> <span data-ttu-id="05c62-121">Gibt einen Satz von .NET-Typen an, die diese Definition des-Steuer Elements verwenden.</span><span class="sxs-lookup"><span data-stu-id="05c62-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="05c62-122">Typname-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="05c62-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="05c62-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="05c62-123">Optional element.</span></span><br /><br /> <span data-ttu-id="05c62-124">Gibt einen .NET-Typ an, der diese Definition des-Steuer Elements verwendet.</span><span class="sxs-lookup"><span data-stu-id="05c62-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="05c62-125">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="05c62-125">Parent Elements</span></span>

|<span data-ttu-id="05c62-126">Element</span><span class="sxs-lookup"><span data-stu-id="05c62-126">Element</span></span>|<span data-ttu-id="05c62-127">Description</span><span class="sxs-lookup"><span data-stu-id="05c62-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="05c62-128">Customentry-Element für customentries für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05c62-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="05c62-129">Stellt eine Definition des-Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="05c62-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="05c62-130">Hinweise</span><span class="sxs-lookup"><span data-stu-id="05c62-130">Remarks</span></span>

<span data-ttu-id="05c62-131">Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt eine bestimmte Eigenschaft hat oder wenn ein bestimmter Eigenschafts Wert oder ein Skript zu `true`ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="05c62-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="05c62-132">Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="05c62-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="05c62-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="05c62-133">See Also</span></span>

[<span data-ttu-id="05c62-134">Customentry-Element für customentries für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="05c62-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="05c62-135">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="05c62-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
