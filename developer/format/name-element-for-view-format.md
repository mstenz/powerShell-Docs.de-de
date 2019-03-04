---
title: Nennen Sie Element anzeigen (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859506"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="5a81c-102">Element „Name“ für View (Format)</span><span class="sxs-lookup"><span data-stu-id="5a81c-102">Name Element for View (Format)</span></span>

<span data-ttu-id="5a81c-103">Gibt den Namen, der verwendet wird, um die Ansicht zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="5a81c-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="5a81c-104">Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Name-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5a81c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5a81c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a81c-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5a81c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5a81c-106">Attributes and Elements</span></span>

<span data-ttu-id="5a81c-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Name` Element.</span><span class="sxs-lookup"><span data-stu-id="5a81c-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="5a81c-108">Nur ein `Name` Element ist für jede Ansicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="5a81c-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="5a81c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="5a81c-109">Attributes</span></span>

<span data-ttu-id="5a81c-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="5a81c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5a81c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5a81c-111">Child Elements</span></span>

<span data-ttu-id="5a81c-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="5a81c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5a81c-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5a81c-113">Parent Elements</span></span>

|<span data-ttu-id="5a81c-114">Element</span><span class="sxs-lookup"><span data-stu-id="5a81c-114">Element</span></span>|<span data-ttu-id="5a81c-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a81c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5a81c-116">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5a81c-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5a81c-117">Definiert eine Ansicht, die verwendet wird, um die Mitglieder von .NET-Objekten für eine oder mehrere anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5a81c-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5a81c-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="5a81c-118">Text Value</span></span>

<span data-ttu-id="5a81c-119">Geben Sie einen eindeutigen Anzeigenamen für die Ansicht ein.</span><span class="sxs-lookup"><span data-stu-id="5a81c-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="5a81c-120">Dieser Name kann einen Verweis auf den Typ der Ansicht (z. B. eine Tabelle oder Ansicht), welches Objekt oder ein Satz von Objekten verwenden Sie die Ansicht, welcher Befehl gibt zurück, die Objekte oder eine Kombination aus diesen enthalten.</span><span class="sxs-lookup"><span data-stu-id="5a81c-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a81c-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5a81c-121">Remarks</span></span>

<span data-ttu-id="5a81c-122">Weitere Informationen zu den verschiedenen Typen von Ansichten finden Sie unter den folgenden Themen: [Tabellenansicht](./creating-a-table-view.md), [Listenansicht](./creating-a-list-view.md), [Breite Ansicht](./creating-a-wide-view.md), und [benutzerdefinierte Ansicht](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5a81c-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="5a81c-123">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5a81c-123">Example</span></span>

<span data-ttu-id="5a81c-124">Das folgende Beispiel zeigt eine `View` Element, das eine Tabellenansicht für definiert die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="5a81c-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="5a81c-125">Der Name der Ansicht lautet "Service".</span><span class="sxs-lookup"><span data-stu-id="5a81c-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="5a81c-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5a81c-126">See Also</span></span>

[<span data-ttu-id="5a81c-127">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="5a81c-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5a81c-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="5a81c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5a81c-129">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="5a81c-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5a81c-130">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="5a81c-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="5a81c-131">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5a81c-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5a81c-132">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a81c-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
