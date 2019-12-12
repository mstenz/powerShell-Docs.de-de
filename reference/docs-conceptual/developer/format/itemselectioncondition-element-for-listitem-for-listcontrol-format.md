---
title: Itemselectioncondition-Element für ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365189"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="b40ad-102">Element „ItemSelectionCondition“ für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="b40ad-103">Definiert die Bedingung, die vorhanden sein muss, damit dieses Listenelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="b40ad-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="b40ad-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry for ListControl (Format) ListItem-Element für ListItems für ListControl (Format) itemselectioncondition-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b40ad-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b40ad-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b40ad-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b40ad-106">Attributes and Elements</span></span>

<span data-ttu-id="b40ad-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ItemSelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b40ad-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b40ad-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="b40ad-108">Attributes</span></span>

<span data-ttu-id="b40ad-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="b40ad-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b40ad-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b40ad-110">Child Elements</span></span>

|<span data-ttu-id="b40ad-111">Element</span><span class="sxs-lookup"><span data-stu-id="b40ad-111">Element</span></span>|<span data-ttu-id="b40ad-112">Description</span><span class="sxs-lookup"><span data-stu-id="b40ad-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b40ad-113">PropertyName-Element für itemselectioncondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="b40ad-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b40ad-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b40ad-115">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="b40ad-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b40ad-116">ScriptBlock-Element für itemselectioncondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="b40ad-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b40ad-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b40ad-118">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="b40ad-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b40ad-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b40ad-119">Parent Elements</span></span>

|<span data-ttu-id="b40ad-120">Element</span><span class="sxs-lookup"><span data-stu-id="b40ad-120">Element</span></span>|<span data-ttu-id="b40ad-121">Description</span><span class="sxs-lookup"><span data-stu-id="b40ad-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b40ad-122">ListItem-Element für ListItems für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="b40ad-123">Definiert die Eigenschaft oder das Skript, dessen Wert in einer Zeile der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b40ad-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b40ad-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b40ad-124">Remarks</span></span>

<span data-ttu-id="b40ad-125">Sie können einen Eigenschaftsnamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="b40ad-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b40ad-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b40ad-126">See Also</span></span>

[<span data-ttu-id="b40ad-127">ListItem-Element für ListItems für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="b40ad-128">PropertyName-Element für itemselectioncondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="b40ad-129">ScriptBlock-Element für itemselectioncondition für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b40ad-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="b40ad-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="b40ad-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
