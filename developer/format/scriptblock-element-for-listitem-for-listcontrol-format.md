---
title: ScriptBlock-Element für den ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064576"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="80022-102">Element „ScriptBlock“ für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80022-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="80022-103">Gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="80022-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="80022-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry ListControl (Format) für ListControl (Format) ListItem-Element für ListItems für ListControl (Format)-ScriptBlock-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80022-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="80022-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="80022-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="80022-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="80022-106">Attributes and Elements</span></span>

<span data-ttu-id="80022-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="80022-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="80022-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="80022-108">Attributes</span></span>

<span data-ttu-id="80022-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="80022-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="80022-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="80022-110">Child Elements</span></span>

<span data-ttu-id="80022-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="80022-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="80022-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="80022-112">Parent Elements</span></span>

|<span data-ttu-id="80022-113">Element</span><span class="sxs-lookup"><span data-stu-id="80022-113">Element</span></span>|<span data-ttu-id="80022-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="80022-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="80022-115">ListItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="80022-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="80022-116">Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="80022-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="80022-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="80022-117">Text Value</span></span>

<span data-ttu-id="80022-118">Geben Sie das Skript, das in der Zeile, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="80022-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="80022-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="80022-119">Remarks</span></span>

<span data-ttu-id="80022-120">Wenn dieses Element angegeben ist, können Sie nicht angeben der [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="80022-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="80022-121">Weitere Informationen zum Angeben von Skripts in einer Listenansicht finden Sie unter [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="80022-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="80022-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="80022-122">Example</span></span>

<span data-ttu-id="80022-123">Das folgende Beispiel zeigt, wie Sie die Eigenschaft angeben, dessen Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="80022-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="80022-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="80022-124">See Also</span></span>

[<span data-ttu-id="80022-125">PropertyName-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80022-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="80022-126">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="80022-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="80022-127">ListItem-Element für ListItems für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="80022-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="80022-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="80022-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
