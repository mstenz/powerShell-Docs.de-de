---
title: SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063986"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="e331b-102">Element „SelectionSetName“ für EntrySelectedBy für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="e331b-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e331b-103">Gibt einen Satz von .NET-Typen, die dieser Definition des Steuerelements verwenden.</span><span class="sxs-lookup"><span data-stu-id="e331b-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="e331b-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="e331b-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e331b-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für (Format) SelectionSetName Konfigurationselement für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="e331b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e331b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e331b-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e331b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e331b-107">Attributes and Elements</span></span>

<span data-ttu-id="e331b-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="e331b-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e331b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="e331b-109">Attributes</span></span>

<span data-ttu-id="e331b-110">Keine</span><span class="sxs-lookup"><span data-stu-id="e331b-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e331b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e331b-111">Child Elements</span></span>

<span data-ttu-id="e331b-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="e331b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e331b-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e331b-113">Parent Elements</span></span>

|<span data-ttu-id="e331b-114">Element</span><span class="sxs-lookup"><span data-stu-id="e331b-114">Element</span></span>|<span data-ttu-id="e331b-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e331b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e331b-116">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e331b-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e331b-117">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e331b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e331b-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="e331b-118">Text Value</span></span>

<span data-ttu-id="e331b-119">Geben Sie den Namen des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="e331b-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="e331b-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e331b-120">Remarks</span></span>

<span data-ttu-id="e331b-121">Jedes Steuerelement muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e331b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e331b-122">Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e331b-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="e331b-123">Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="e331b-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e331b-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e331b-124">See Also</span></span>

[<span data-ttu-id="e331b-125">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e331b-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e331b-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="e331b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
