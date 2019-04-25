---
title: PropertyName-Element für den ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064914"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="8e74e-102">Element „PropertyName“ für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8e74e-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="8e74e-103">Gibt die .NET-Eigenschaft, deren Wert in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8e74e-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="8e74e-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) ListItems-Element (Format) ListItem-Element (Format) PropertyName Konfigurationselement für ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="8e74e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e74e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e74e-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e74e-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8e74e-106">Attributes and Elements</span></span>

<span data-ttu-id="8e74e-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="8e74e-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e74e-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="8e74e-108">Attributes</span></span>

<span data-ttu-id="8e74e-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="8e74e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e74e-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8e74e-110">Child Elements</span></span>

<span data-ttu-id="8e74e-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="8e74e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8e74e-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8e74e-112">Parent Elements</span></span>

|<span data-ttu-id="8e74e-113">Element</span><span class="sxs-lookup"><span data-stu-id="8e74e-113">Element</span></span>|<span data-ttu-id="8e74e-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8e74e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e74e-115">ListItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8e74e-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="8e74e-116">Definiert die Eigenschaft oder ein Skript, dessen Wert in der Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8e74e-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8e74e-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="8e74e-117">Text Value</span></span>

<span data-ttu-id="8e74e-118">Geben Sie den Namen der Eigenschaft, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8e74e-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e74e-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8e74e-119">Remarks</span></span>

<span data-ttu-id="8e74e-120">Wenn dieses Element angegeben ist, können Sie nicht angeben der ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="8e74e-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="8e74e-121">Zusätzlich zur Anzeige der Wert der Eigenschaft, können Sie auch eine Bezeichnung für den Wert oder eine Zeichenfolge, die verwendet werden kann, so ändern Sie die Anzeige des Werts angeben.</span><span class="sxs-lookup"><span data-stu-id="8e74e-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="8e74e-122">Weitere Informationen zum Angeben von Daten in einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e74e-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e74e-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8e74e-123">Example</span></span>

<span data-ttu-id="8e74e-124">Das folgende Beispiel zeigt, wie Sie angeben, die Bezeichnung und die Eigenschaft, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8e74e-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="8e74e-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8e74e-125">See Also</span></span>

[<span data-ttu-id="8e74e-126">ScriptBlock-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8e74e-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="8e74e-127">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="8e74e-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8e74e-128">ListItem-Element für ListControl(Format)</span><span class="sxs-lookup"><span data-stu-id="8e74e-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="8e74e-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e74e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
