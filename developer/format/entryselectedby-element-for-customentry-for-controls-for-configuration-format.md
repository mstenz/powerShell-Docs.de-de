---
title: EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059217"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="65dac-102">Element „EntrySelectedBy“ für CustomEntry für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="65dac-103">Definiert die Typen von .NET, mit denen die Definition eines allgemeinen Steuerelement oder die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="65dac-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="65dac-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="65dac-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="65dac-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für die Konfiguration (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65dac-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="65dac-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65dac-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="65dac-107">Attributes and Elements</span></span>

<span data-ttu-id="65dac-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="65dac-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65dac-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="65dac-109">Attributes</span></span>

<span data-ttu-id="65dac-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="65dac-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65dac-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="65dac-111">Child Elements</span></span>

|<span data-ttu-id="65dac-112">Element</span><span class="sxs-lookup"><span data-stu-id="65dac-112">Element</span></span>|<span data-ttu-id="65dac-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="65dac-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65dac-114">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="65dac-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="65dac-115">Optional element.</span></span><br /><br /> <span data-ttu-id="65dac-116">Definiert die Bedingung, die vorhanden sein muss, für die allgemeine Steuerelementdefinition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="65dac-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="65dac-117">SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="65dac-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="65dac-118">Optional element.</span></span><br /><br /> <span data-ttu-id="65dac-119">Gibt einen Satz von .NET-Typen, die dieser Definition des allgemeinen Steuerelements verwenden.</span><span class="sxs-lookup"><span data-stu-id="65dac-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="65dac-120">TypeName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="65dac-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="65dac-121">Optional element.</span></span><br /><br /> <span data-ttu-id="65dac-122">Gibt einen .NET-Typ, ein, der dieser Definition des allgemeinen Steuerelements verwendet.</span><span class="sxs-lookup"><span data-stu-id="65dac-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="65dac-123">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="65dac-123">Parent Elements</span></span>

|<span data-ttu-id="65dac-124">Element</span><span class="sxs-lookup"><span data-stu-id="65dac-124">Element</span></span>|<span data-ttu-id="65dac-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="65dac-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65dac-126">CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="65dac-127">Stellt eine Definition des allgemeinen-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="65dac-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="65dac-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="65dac-128">Remarks</span></span>

<span data-ttu-id="65dac-129">Zumindest muss jede Definition mindestens .NET Typ, Auswahlsatz, oder auswahlbedingung angegeben sein.</span><span class="sxs-lookup"><span data-stu-id="65dac-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="65dac-130">Es ist nicht begrenzt auf die Anzahl der Typen, legt der Auswahl oder auswahlbedingungen, die Sie angeben können.</span><span class="sxs-lookup"><span data-stu-id="65dac-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="65dac-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="65dac-131">See Also</span></span>

[<span data-ttu-id="65dac-132">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="65dac-133">SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="65dac-134">CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="65dac-135">TypeName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="65dac-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="65dac-136">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="65dac-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
