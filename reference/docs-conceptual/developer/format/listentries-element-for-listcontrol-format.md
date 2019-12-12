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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362759"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="fdfbe-102">Element „ListEntries“ für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fdfbe-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="fdfbe-103">Stellt die Definitionen der Listenansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="fdfbe-104">In der Listenansicht muss mindestens eine Definition angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="fdfbe-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fdfbe-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fdfbe-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fdfbe-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fdfbe-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fdfbe-107">Attributes and Elements</span></span>

<span data-ttu-id="fdfbe-108">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `ListEntries`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="fdfbe-109">Es muss mindestens ein untergeordnetes Element angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="fdfbe-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="fdfbe-110">Attributes</span></span>

<span data-ttu-id="fdfbe-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fdfbe-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fdfbe-112">Child Elements</span></span>

|<span data-ttu-id="fdfbe-113">Element</span><span class="sxs-lookup"><span data-stu-id="fdfbe-113">Element</span></span>|<span data-ttu-id="fdfbe-114">Description</span><span class="sxs-lookup"><span data-stu-id="fdfbe-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdfbe-115">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fdfbe-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="fdfbe-116">Stellt eine Definition der Listenansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fdfbe-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fdfbe-117">Parent Elements</span></span>

|<span data-ttu-id="fdfbe-118">Element</span><span class="sxs-lookup"><span data-stu-id="fdfbe-118">Element</span></span>|<span data-ttu-id="fdfbe-119">Description</span><span class="sxs-lookup"><span data-stu-id="fdfbe-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fdfbe-120">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fdfbe-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="fdfbe-121">Definiert ein Listenformat für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fdfbe-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fdfbe-122">Remarks</span></span>

<span data-ttu-id="fdfbe-123">Weitere Informationen zu Listenansichten finden Sie in der [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="fdfbe-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="fdfbe-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fdfbe-124">Example</span></span>

<span data-ttu-id="fdfbe-125">Dieses Beispiel zeigt die XML-Elemente, die die Listenansicht für das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt definieren.</span><span class="sxs-lookup"><span data-stu-id="fdfbe-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fdfbe-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fdfbe-126">See Also</span></span>

[<span data-ttu-id="fdfbe-127">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fdfbe-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="fdfbe-128">ListEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fdfbe-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="fdfbe-129">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="fdfbe-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="fdfbe-130">Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="fdfbe-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
