---
title: Name-Element für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362639"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="cf9bb-102">Element „Name“ für View (Format)</span><span class="sxs-lookup"><span data-stu-id="cf9bb-102">Name Element for View (Format)</span></span>

<span data-ttu-id="cf9bb-103">Gibt den Namen an, der zum Identifizieren der Sicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="cf9bb-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) Name-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cf9bb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf9bb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cf9bb-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cf9bb-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="cf9bb-106">Attributes and Elements</span></span>

<span data-ttu-id="cf9bb-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Name`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="cf9bb-108">Für jede Ansicht ist nur ein `Name`-Element zulässig.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="cf9bb-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="cf9bb-109">Attributes</span></span>

<span data-ttu-id="cf9bb-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cf9bb-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cf9bb-111">Child Elements</span></span>

<span data-ttu-id="cf9bb-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cf9bb-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cf9bb-113">Parent Elements</span></span>

|<span data-ttu-id="cf9bb-114">Element</span><span class="sxs-lookup"><span data-stu-id="cf9bb-114">Element</span></span>|<span data-ttu-id="cf9bb-115">Description</span><span class="sxs-lookup"><span data-stu-id="cf9bb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cf9bb-116">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cf9bb-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="cf9bb-117">Definiert eine Ansicht, die zum Anzeigen der Member von einem oder mehreren .NET-Objekten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cf9bb-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="cf9bb-118">Text Value</span></span>

<span data-ttu-id="cf9bb-119">Geben Sie einen eindeutigen anzeigen Amen für die Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="cf9bb-120">Dieser Name kann einen Verweis auf den Typ der Sicht enthalten (z. b. eine Tabellen-oder Listenansicht), welches Objekt oder welche Gruppe von Objekten die Sicht verwenden, welcher Befehl die Objekte zurückgibt, oder eine Kombination dieser Elemente.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf9bb-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cf9bb-121">Remarks</span></span>

<span data-ttu-id="cf9bb-122">Weitere Informationen zu den verschiedenen Sicht Typen finden Sie in den folgenden Themen: [Tabellenansicht](./creating-a-table-view.md), [Listenansicht](./creating-a-list-view.md), [Breite Ansicht](./creating-a-wide-view.md)und [benutzerdefinierte Sicht](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cf9bb-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf9bb-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="cf9bb-123">Example</span></span>

<span data-ttu-id="cf9bb-124">Das folgende Beispiel zeigt ein `View`-Element, das eine Tabellenansicht für das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt definiert.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="cf9bb-125">Der Name der Sicht lautet "Service".</span><span class="sxs-lookup"><span data-stu-id="cf9bb-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="cf9bb-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cf9bb-126">See Also</span></span>

[<span data-ttu-id="cf9bb-127">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="cf9bb-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cf9bb-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="cf9bb-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cf9bb-129">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="cf9bb-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cf9bb-130">Erstellen benutzerdefinierter Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="cf9bb-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="cf9bb-131">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cf9bb-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="cf9bb-132">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="cf9bb-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
