---
title: PropertyName-Element für selectioncondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1707317-6c26-4866-bcc1-8924103c9014
caps.latest.revision: 6
ms.openlocfilehash: 7241ea0ea364befa7ad4ab0af4c4209be72214a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364949"
---
# <a name="propertyname-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="2e203-102">Element „PropertyName“ für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e203-102">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="2e203-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="2e203-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="2e203-104">Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und die Definition wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="2e203-104">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="2e203-105">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2e203-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2e203-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format) selectioncondition-Element für entryselectedby für GroupBy (Format) propertyName-Element für selectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e203-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2e203-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e203-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2e203-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2e203-108">Attributes and Elements</span></span>

<span data-ttu-id="2e203-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2e203-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e203-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="2e203-110">Attributes</span></span>

<span data-ttu-id="2e203-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="2e203-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2e203-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2e203-112">Child Elements</span></span>

<span data-ttu-id="2e203-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="2e203-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2e203-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2e203-114">Parent Elements</span></span>

|<span data-ttu-id="2e203-115">Element</span><span class="sxs-lookup"><span data-stu-id="2e203-115">Element</span></span>|<span data-ttu-id="2e203-116">Description</span><span class="sxs-lookup"><span data-stu-id="2e203-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2e203-117">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e203-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="2e203-118">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="2e203-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2e203-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="2e203-119">Text Value</span></span>

<span data-ttu-id="2e203-120">Geben Sie den Namen der .net-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="2e203-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e203-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2e203-121">Remarks</span></span>

<span data-ttu-id="2e203-122">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder ein Skript angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="2e203-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="2e203-123">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2e203-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e203-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2e203-124">See Also</span></span>

[<span data-ttu-id="2e203-125">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2e203-125">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="2e203-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="2e203-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
