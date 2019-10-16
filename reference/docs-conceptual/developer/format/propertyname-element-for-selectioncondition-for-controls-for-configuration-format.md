---
title: PropertyName-Element für selectioncondition für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec048408-e1c6-41ef-b39b-72f4c2dcf2ac
caps.latest.revision: 6
ms.openlocfilehash: b4b2440fdb7171d09fdc16ac7cc4f25ed1a4bb78
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362399"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="5db3a-102">Element „PropertyName“ für SelectionCondition für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5db3a-102">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5db3a-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="5db3a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="5db3a-104">Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und der Eintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="5db3a-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="5db3a-105">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="5db3a-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5db3a-106">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für das Configuration (Format) entryselectedby-Element für customentry für Steuerelemente für das Configuration (Format) selectioncondition-Element für entryselectedby für customentry for Configuration ( Format) propertyName-Element für selectioncondition für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5db3a-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5db3a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5db3a-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5db3a-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5db3a-108">Attributes and Elements</span></span>

<span data-ttu-id="5db3a-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5db3a-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5db3a-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="5db3a-110">Attributes</span></span>

<span data-ttu-id="5db3a-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="5db3a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5db3a-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5db3a-112">Child Elements</span></span>

<span data-ttu-id="5db3a-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="5db3a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5db3a-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5db3a-114">Parent Elements</span></span>

|<span data-ttu-id="5db3a-115">Element</span><span class="sxs-lookup"><span data-stu-id="5db3a-115">Element</span></span>|<span data-ttu-id="5db3a-116">Description</span><span class="sxs-lookup"><span data-stu-id="5db3a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5db3a-117">Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5db3a-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="5db3a-118">Definiert eine Bedingung, die vorhanden sein muss, damit eine allgemeine Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="5db3a-118">Defines a condition that must exist for a common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5db3a-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="5db3a-119">Text Value</span></span>

<span data-ttu-id="5db3a-120">Geben Sie den Namen der .net-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="5db3a-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="5db3a-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5db3a-121">Remarks</span></span>

<span data-ttu-id="5db3a-122">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder ein Skript angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5db3a-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="5db3a-123">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5db3a-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5db3a-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5db3a-124">See Also</span></span>

[<span data-ttu-id="5db3a-125">Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="5db3a-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="5db3a-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="5db3a-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
