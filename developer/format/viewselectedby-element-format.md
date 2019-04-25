---
title: ViewSelectedBy-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083823"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="0d5e9-102">Element „ViewSelectedBy“ (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5e9-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="0d5e9-103">Definiert die .NET Objekte, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="0d5e9-104">Jede Sicht muss mindestens ein .NET Objekt angeben.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="0d5e9-105">ViewDefinitions-Element (Format) anzeigen (Format) ViewSelectedBy Elementen (-Format)</span><span class="sxs-lookup"><span data-stu-id="0d5e9-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d5e9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d5e9-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d5e9-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0d5e9-107">Attributes and Elements</span></span>

<span data-ttu-id="0d5e9-108">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ViewSelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="0d5e9-109">Dieses Element muss mindestens einen enthalten `TypeName` oder `SelectionSetName` untergeordnetes Element.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="0d5e9-110">Es gibt keine Beschränkung der Anzahl der untergeordneten Elemente, die angegeben werden können, noch ist die Reihenfolge von Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d5e9-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="0d5e9-111">Attributes</span></span>

<span data-ttu-id="0d5e9-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d5e9-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0d5e9-113">Child Elements</span></span>

|<span data-ttu-id="0d5e9-114">Element</span><span class="sxs-lookup"><span data-stu-id="0d5e9-114">Element</span></span>|<span data-ttu-id="0d5e9-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d5e9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d5e9-116">TypeName-Element für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5e9-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="0d5e9-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="0d5e9-118">Gibt ein .NET-Objekt, das von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="0d5e9-119">SelectionSetName-Element für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5e9-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="0d5e9-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="0d5e9-121">Gibt einen Satz von .NET-Objekten, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d5e9-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0d5e9-122">Parent Elements</span></span>

|<span data-ttu-id="0d5e9-123">Element</span><span class="sxs-lookup"><span data-stu-id="0d5e9-123">Element</span></span>|<span data-ttu-id="0d5e9-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d5e9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d5e9-125">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5e9-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="0d5e9-126">Definiert eine Ansicht, in dem ein oder mehrere .NET Objekte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d5e9-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0d5e9-127">Remarks</span></span>

<span data-ttu-id="0d5e9-128">Weitere Informationen zur Verwendung dieses Elements in verschiedenen Ansichten finden Sie unter [Tabelle Ansichtskomponenten](./creating-a-table-view.md), [Liste Ansichtskomponenten](./creating-a-list-view.md), [Wide Ansichtskomponenten](./creating-a-wide-view.md), und [Benutzerdefinierte Steuerelementkomponenten](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0d5e9-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="0d5e9-129">Die `SelectionSetName` Element wird verwendet, wenn die Formatierungsdatei einen Satz von Objekten definiert, die von mehreren Ansichten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="0d5e9-130">Weitere Informationen wie Auswahl legt definiert, und auf die verwiesen wird, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0d5e9-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d5e9-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0d5e9-131">Example</span></span>

<span data-ttu-id="0d5e9-132">Das folgende Beispiel zeigt, wie die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt für eine Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="0d5e9-133">Das gleiche Schema wird für die Tabelle, Breite und benutzerdefinierte Ansichten verwendet.</span><span class="sxs-lookup"><span data-stu-id="0d5e9-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="0d5e9-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0d5e9-134">See Also</span></span>

[<span data-ttu-id="0d5e9-135">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="0d5e9-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0d5e9-136">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="0d5e9-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0d5e9-137">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="0d5e9-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0d5e9-138">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="0d5e9-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="0d5e9-139">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="0d5e9-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0d5e9-140">SelectionSetName-Element für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5e9-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="0d5e9-141">TypeName-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0d5e9-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="0d5e9-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="0d5e9-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
