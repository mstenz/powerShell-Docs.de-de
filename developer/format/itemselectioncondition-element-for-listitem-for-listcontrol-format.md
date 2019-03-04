---
title: ItemSelectionCondition-Element für den ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861866"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="77714-102">Element „ItemSelectionCondition“ für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="77714-103">Definiert die Bedingung, die für dieses Listenelement zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="77714-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="77714-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry ListControl (Format) für ListControl (Format) ListItem-Element für ListItems für ListControl (Format) ItemSelectionCondition-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77714-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="77714-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77714-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="77714-106">Attributes and Elements</span></span>

<span data-ttu-id="77714-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ItemSelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="77714-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77714-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="77714-108">Attributes</span></span>

<span data-ttu-id="77714-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="77714-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77714-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="77714-110">Child Elements</span></span>

|<span data-ttu-id="77714-111">Element</span><span class="sxs-lookup"><span data-stu-id="77714-111">Element</span></span>|<span data-ttu-id="77714-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="77714-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77714-113">PropertyName-Element für ItemSelectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="77714-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="77714-114">Optional element.</span></span><br /><br /> <span data-ttu-id="77714-115">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="77714-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="77714-116">ScriptBlock-Element für ItemSelectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="77714-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="77714-117">Optional element.</span></span><br /><br /> <span data-ttu-id="77714-118">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="77714-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="77714-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="77714-119">Parent Elements</span></span>

|<span data-ttu-id="77714-120">Element</span><span class="sxs-lookup"><span data-stu-id="77714-120">Element</span></span>|<span data-ttu-id="77714-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="77714-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77714-122">ListItem-Element für ListItems für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="77714-123">Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="77714-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="77714-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="77714-124">Remarks</span></span>

<span data-ttu-id="77714-125">Sie können einen Eigenschaftennamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="77714-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="77714-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="77714-126">See Also</span></span>

[<span data-ttu-id="77714-127">ListItem-Element für ListItems für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="77714-128">PropertyName-Element für ItemSelectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="77714-129">ScriptBlock-Element für ItemSelectionCondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="77714-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="77714-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="77714-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
