---
title: Selectionsetname-Element für entryselectedby für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368349"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="584dd-102">Element „SelectionSetName“ für EntrySelectedBy für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="584dd-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="584dd-103">Gibt einen Satz von .NET-Typen an, die diese Definition des-Steuer Elements verwenden.</span><span class="sxs-lookup"><span data-stu-id="584dd-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="584dd-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="584dd-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="584dd-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für das View (Format) customentry-Element für customentries für Steuerelemente für das View (Format) entryselectedby-Element für customentry für Steuerelemente für das View (Format) selectionsetname-Element für entryselectedby für Steuerelemente für Ansicht ( Ges</span><span class="sxs-lookup"><span data-stu-id="584dd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="584dd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="584dd-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="584dd-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="584dd-107">Attributes and Elements</span></span>

<span data-ttu-id="584dd-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="584dd-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="584dd-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="584dd-109">Attributes</span></span>

<span data-ttu-id="584dd-110">Keine</span><span class="sxs-lookup"><span data-stu-id="584dd-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="584dd-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="584dd-111">Child Elements</span></span>

<span data-ttu-id="584dd-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="584dd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="584dd-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="584dd-113">Parent Elements</span></span>

|<span data-ttu-id="584dd-114">Element</span><span class="sxs-lookup"><span data-stu-id="584dd-114">Element</span></span>|<span data-ttu-id="584dd-115">Description</span><span class="sxs-lookup"><span data-stu-id="584dd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="584dd-116">Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="584dd-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="584dd-117">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="584dd-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="584dd-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="584dd-118">Text Value</span></span>

<span data-ttu-id="584dd-119">Geben Sie den Namen des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="584dd-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="584dd-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="584dd-120">Remarks</span></span>

<span data-ttu-id="584dd-121">Für jede Steuerelement Definition muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="584dd-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="584dd-122">Auswahl Sätze werden in der Regel verwendet, wenn Sie eine Gruppe von Objekten definieren möchten, die in mehreren Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="584dd-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="584dd-123">Weitere Informationen zum Definieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="584dd-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="584dd-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="584dd-124">See Also</span></span>

[<span data-ttu-id="584dd-125">Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="584dd-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="584dd-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="584dd-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
