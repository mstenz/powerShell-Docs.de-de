---
title: ScriptBlock-Element für selectioncondition für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368619"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="d9149-102">Element „ScriptBlock“ für SelectionCondition für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d9149-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d9149-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="d9149-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="d9149-104">Wenn dieses Skript zum `true`ausgewertet wird, wird die Bedingung erfüllt, und die Definition wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="d9149-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="d9149-105">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d9149-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="d9149-106">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für das Configuration (Format) entryselectedby-Element für customentry for Controls for Configuration (Format) selectioncondition-Element für entryselectedby for Controls for Configuration (Format) ScriptBlock-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d9149-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d9149-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9149-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9149-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d9149-108">Attributes and Elements</span></span>

<span data-ttu-id="d9149-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d9149-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9149-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d9149-110">Attributes</span></span>

<span data-ttu-id="d9149-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="d9149-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d9149-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d9149-112">Child Elements</span></span>

<span data-ttu-id="d9149-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="d9149-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d9149-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d9149-114">Parent Elements</span></span>

|<span data-ttu-id="d9149-115">Element</span><span class="sxs-lookup"><span data-stu-id="d9149-115">Element</span></span>|<span data-ttu-id="d9149-116">Description</span><span class="sxs-lookup"><span data-stu-id="d9149-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9149-117">Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d9149-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="d9149-118">Definiert eine Bedingung, die vorhanden sein muss, damit die allgemeine Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="d9149-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d9149-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="d9149-119">Text Value</span></span>

<span data-ttu-id="d9149-120">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="d9149-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9149-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d9149-121">Remarks</span></span>

<span data-ttu-id="d9149-122">Die Auswahlbedingung muss mindestens ein Skript oder einen Eigenschaftsnamen angeben, um ausgewertet zu werden, aber nicht beides.</span><span class="sxs-lookup"><span data-stu-id="d9149-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="d9149-123">Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d9149-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d9149-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d9149-124">See Also</span></span>

[<span data-ttu-id="d9149-125">Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d9149-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="d9149-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="d9149-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
