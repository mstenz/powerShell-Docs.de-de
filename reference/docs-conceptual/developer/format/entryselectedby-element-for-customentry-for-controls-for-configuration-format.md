---
title: Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368769"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="d59b1-102">Element „EntrySelectedBy“ für CustomEntry für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d59b1-103">Definiert die .NET-Typen, die die Definition des allgemeinen Steuer Elements oder die Bedingung verwenden, die für die Verwendung dieses Steuer Elements vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="d59b1-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="d59b1-104">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d59b1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d59b1-105">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für das Configuration (Format) entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d59b1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d59b1-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d59b1-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d59b1-107">Attributes and Elements</span></span>

<span data-ttu-id="d59b1-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d59b1-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d59b1-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d59b1-109">Attributes</span></span>

<span data-ttu-id="d59b1-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="d59b1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d59b1-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d59b1-111">Child Elements</span></span>

|<span data-ttu-id="d59b1-112">Element</span><span class="sxs-lookup"><span data-stu-id="d59b1-112">Element</span></span>|<span data-ttu-id="d59b1-113">Description</span><span class="sxs-lookup"><span data-stu-id="d59b1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d59b1-114">Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d59b1-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d59b1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d59b1-116">Definiert die Bedingung, die vorhanden sein muss, damit die allgemeine Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="d59b1-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="d59b1-117">Selectionsetname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="d59b1-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d59b1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d59b1-119">Gibt einen Satz von .NET-Typen an, die diese Definition des allgemeinen Steuer Elements verwenden.</span><span class="sxs-lookup"><span data-stu-id="d59b1-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="d59b1-120">Typname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d59b1-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d59b1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d59b1-122">Gibt einen .NET-Typ an, der diese Definition des allgemeinen Steuer Elements verwendet.</span><span class="sxs-lookup"><span data-stu-id="d59b1-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d59b1-123">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d59b1-123">Parent Elements</span></span>

|<span data-ttu-id="d59b1-124">Element</span><span class="sxs-lookup"><span data-stu-id="d59b1-124">Element</span></span>|<span data-ttu-id="d59b1-125">Description</span><span class="sxs-lookup"><span data-stu-id="d59b1-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d59b1-126">Customentry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="d59b1-127">Stellt eine Definition des allgemeinen Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="d59b1-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d59b1-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d59b1-128">Remarks</span></span>

<span data-ttu-id="d59b1-129">Für jede Definition muss mindestens ein .NET-Typ, ein Auswahl Satz oder eine Auswahlbedingung angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d59b1-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="d59b1-130">Es gibt keine maximale Beschränkung für die Anzahl von Typen, Auswahl Sätzen oder Auswahl Bedingungen, die Sie angeben können.</span><span class="sxs-lookup"><span data-stu-id="d59b1-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="d59b1-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d59b1-131">See Also</span></span>

[<span data-ttu-id="d59b1-132">Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d59b1-133">Selectionsetname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="d59b1-134">Customentry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="d59b1-135">Typname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d59b1-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="d59b1-136">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="d59b1-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
