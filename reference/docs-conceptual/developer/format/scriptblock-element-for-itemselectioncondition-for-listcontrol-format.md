---
title: ScriptBlock-Element für itemselectioncondition für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362099"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="a6517-102">Element „ScriptBlock“ für ItemSeclectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a6517-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="a6517-103">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a6517-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="a6517-104">Wenn dieses Skript zum `true`ausgewertet wird, wird die Bedingung erfüllt, und das Listenelement wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="a6517-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="a6517-105">Dieses Element wird beim Definieren einer Listenansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="a6517-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="a6517-106">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry for ListControl (Format) ListItem-Element für ListItems für das Listen Steuerelement (Format) itemselectioncondition-Element für ListItem für ListControl (Format) ScriptBlock-Element für itemselectioncondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a6517-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6517-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6517-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6517-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a6517-108">Attributes and Elements</span></span>

<span data-ttu-id="a6517-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a6517-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6517-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="a6517-110">Attributes</span></span>

<span data-ttu-id="a6517-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a6517-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6517-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a6517-112">Child Elements</span></span>

<span data-ttu-id="a6517-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="a6517-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6517-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a6517-114">Parent Elements</span></span>

|<span data-ttu-id="a6517-115">Element</span><span class="sxs-lookup"><span data-stu-id="a6517-115">Element</span></span>|<span data-ttu-id="a6517-116">Description</span><span class="sxs-lookup"><span data-stu-id="a6517-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6517-117">Itemselectioncondition-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a6517-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="a6517-118">Definiert die Bedingung, die vorhanden sein muss, damit dieses Listenelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="a6517-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6517-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="a6517-119">Text Value</span></span>

<span data-ttu-id="a6517-120">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="a6517-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6517-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a6517-121">Remarks</span></span>

<span data-ttu-id="a6517-122">Wenn dieses Element verwendet wird, können Sie das `PropertyName`-Element beim Definieren der Auswahlbedingung nicht angeben.</span><span class="sxs-lookup"><span data-stu-id="a6517-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6517-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a6517-123">See Also</span></span>

[<span data-ttu-id="a6517-124">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a6517-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
