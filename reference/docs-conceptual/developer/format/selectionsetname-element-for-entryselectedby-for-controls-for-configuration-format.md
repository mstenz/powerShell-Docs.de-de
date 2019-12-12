---
title: Selectionsetname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364789"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="ea3b0-102">Element „SelectionSetName“ für EntrySelectedBy für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="ea3b0-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="ea3b0-103">Gibt einen Satz von .NET-Typen an, die diese Definition des-Steuer Elements verwenden.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="ea3b0-104">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="ea3b0-105">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für das Configuration (Format) entryselectedby-Element für customentry for Controls for Configuration (Format) selectionsetname-Element für entryselectedby for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="ea3b0-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea3b0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ea3b0-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea3b0-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ea3b0-107">Attributes and Elements</span></span>

<span data-ttu-id="ea3b0-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea3b0-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="ea3b0-109">Attributes</span></span>

<span data-ttu-id="ea3b0-110">Keine</span><span class="sxs-lookup"><span data-stu-id="ea3b0-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea3b0-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ea3b0-111">Child Elements</span></span>

<span data-ttu-id="ea3b0-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea3b0-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ea3b0-113">Parent Elements</span></span>

|<span data-ttu-id="ea3b0-114">Element</span><span class="sxs-lookup"><span data-stu-id="ea3b0-114">Element</span></span>|<span data-ttu-id="ea3b0-115">Description</span><span class="sxs-lookup"><span data-stu-id="ea3b0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea3b0-116">Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="ea3b0-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="ea3b0-117">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea3b0-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="ea3b0-118">Text Value</span></span>

<span data-ttu-id="ea3b0-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea3b0-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ea3b0-120">Remarks</span></span>

<span data-ttu-id="ea3b0-121">Für jede Steuerelement Definition muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ea3b0-122">Auswahl Sätze werden in der Regel verwendet, wenn Sie eine Gruppe von Objekten definieren möchten, die in mehreren Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ea3b0-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="ea3b0-123">Weitere Informationen zum Definieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ea3b0-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea3b0-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ea3b0-124">See Also</span></span>

[<span data-ttu-id="ea3b0-125">Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="ea3b0-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="ea3b0-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="ea3b0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
