---
title: ListEntries-Element für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856786"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="3a317-102">Element „ListEntries“ für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3a317-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="3a317-103">Enthält die Definitionen der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a317-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="3a317-104">Eine oder mehrere Definitionen muss die Listenansicht angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="3a317-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="3a317-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="3a317-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3a317-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a317-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3a317-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3a317-107">Attributes and Elements</span></span>

<span data-ttu-id="3a317-108">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `ListEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="3a317-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="3a317-109">Mindestens ein untergeordnetes Element muss angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="3a317-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3a317-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="3a317-110">Attributes</span></span>

<span data-ttu-id="3a317-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="3a317-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3a317-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3a317-112">Child Elements</span></span>

|<span data-ttu-id="3a317-113">Element</span><span class="sxs-lookup"><span data-stu-id="3a317-113">Element</span></span>|<span data-ttu-id="3a317-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a317-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a317-115">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3a317-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="3a317-116">Stellt eine Definition der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a317-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3a317-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3a317-117">Parent Elements</span></span>

|<span data-ttu-id="3a317-118">Element</span><span class="sxs-lookup"><span data-stu-id="3a317-118">Element</span></span>|<span data-ttu-id="3a317-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a317-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3a317-120">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3a317-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="3a317-121">Definiert eine Listenformat für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="3a317-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3a317-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3a317-122">Remarks</span></span>

<span data-ttu-id="3a317-123">Weitere Informationen zu Ansichten aufzulisten, finden Sie unter [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3a317-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3a317-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3a317-124">Example</span></span>

<span data-ttu-id="3a317-125">Dieses Beispiel zeigt die XML-Elemente, die definieren, die Listenansicht die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="3a317-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3a317-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3a317-126">See Also</span></span>

[<span data-ttu-id="3a317-127">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3a317-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="3a317-128">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3a317-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="3a317-129">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="3a317-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3a317-130">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="3a317-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
