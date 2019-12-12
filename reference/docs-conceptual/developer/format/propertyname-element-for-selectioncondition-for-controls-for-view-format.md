---
title: PropertyName-Element für selectioncondition für Steuerelemente für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92c4237d-c2b2-4908-82ac-f36070f89d26
caps.latest.revision: 6
ms.openlocfilehash: 79859bed3d762948182e03babf71d4270278bae7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362359"
---
# <a name="propertyname-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="33dcf-102">Element „PropertyName“ für SelectionCondition für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="33dcf-102">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="33dcf-103">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="33dcf-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="33dcf-104">Wenn diese Eigenschaft vorhanden ist oder als zu `true`ausgewertet wird, wird die Bedingung erfüllt, und der Eintrag wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="33dcf-104">When this property is present or when it evaluates to `true`, the condition is met, and the entry is used.</span></span> <span data-ttu-id="33dcf-105">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="33dcf-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="33dcf-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für das View (Format) customentry-Element für customentries für Steuerelemente für das View (Format) entryselectedby-Element für customentry für Steuerelemente für das View (Format) selectioncondition-Element für entryselectedby für Steuerelemente für View ( Format) propertyName-Element für selectioncondition für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="33dcf-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33dcf-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="33dcf-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33dcf-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="33dcf-108">Attributes and Elements</span></span>

<span data-ttu-id="33dcf-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="33dcf-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33dcf-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="33dcf-110">Attributes</span></span>

<span data-ttu-id="33dcf-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="33dcf-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33dcf-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="33dcf-112">Child Elements</span></span>

<span data-ttu-id="33dcf-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="33dcf-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33dcf-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="33dcf-114">Parent Elements</span></span>

|<span data-ttu-id="33dcf-115">Element</span><span class="sxs-lookup"><span data-stu-id="33dcf-115">Element</span></span>|<span data-ttu-id="33dcf-116">Description</span><span class="sxs-lookup"><span data-stu-id="33dcf-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33dcf-117">Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="33dcf-117">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="33dcf-118">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="33dcf-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="33dcf-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="33dcf-119">Text Value</span></span>

<span data-ttu-id="33dcf-120">Geben Sie den Namen der .net-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="33dcf-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="33dcf-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="33dcf-121">Remarks</span></span>

<span data-ttu-id="33dcf-122">Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder ein Skript angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="33dcf-122">The selection condition must specify a least one property name or a script, but cannot specify both.</span></span> <span data-ttu-id="33dcf-123">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="33dcf-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33dcf-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="33dcf-124">See Also</span></span>

[<span data-ttu-id="33dcf-125">Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="33dcf-125">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="33dcf-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="33dcf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
