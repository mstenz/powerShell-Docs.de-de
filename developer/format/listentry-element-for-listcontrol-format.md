---
title: ListEntry-Element für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862246"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="b9669-102">Element „ListEntry“ für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="b9669-103">Stellt eine Definition der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b9669-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="b9669-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries-Element (Format) ListEntry Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9669-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9669-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9669-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b9669-106">Attributes and Elements</span></span>

<span data-ttu-id="b9669-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `ListEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="b9669-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9669-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="b9669-108">Attributes</span></span>

<span data-ttu-id="b9669-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="b9669-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9669-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9669-110">Child Elements</span></span>

|<span data-ttu-id="b9669-111">Element</span><span class="sxs-lookup"><span data-stu-id="b9669-111">Element</span></span>|<span data-ttu-id="b9669-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9669-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9669-113">EntrySelectedBy-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b9669-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b9669-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b9669-115">Definiert die .NET Objekte, die diese Liste View Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b9669-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="b9669-116">ListItems-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b9669-117">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="b9669-117">Required element.</span></span><br /><br /> <span data-ttu-id="b9669-118">Definiert die Eigenschaften und Skripts, deren Werte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b9669-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b9669-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9669-119">Parent Elements</span></span>

|<span data-ttu-id="b9669-120">Element</span><span class="sxs-lookup"><span data-stu-id="b9669-120">Element</span></span>|<span data-ttu-id="b9669-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9669-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9669-122">ListEntries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="b9669-123">Enthält die Definitionen der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b9669-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b9669-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b9669-124">Remarks</span></span>

<span data-ttu-id="b9669-125">Eine Listenansicht ist einer Liste an, in der Eigenschaft oder Skriptwerte für jedes Objekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b9669-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="b9669-126">Weitere Informationen zu Ansichten aufzulisten, finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b9669-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9669-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b9669-127">Example</span></span>

<span data-ttu-id="b9669-128">Dieses Beispiel zeigt die XML-Elemente, die definieren, die Listenansicht die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="b9669-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="b9669-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b9669-129">See Also</span></span>

[<span data-ttu-id="b9669-130">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="b9669-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b9669-131">EntrySelectedBy-Element für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b9669-132">ListEntries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="b9669-133">ListItems-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9669-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b9669-134">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="b9669-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
