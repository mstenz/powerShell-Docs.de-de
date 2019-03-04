---
title: Anzeigen des Elements (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856146"
---
# <a name="view-element-format"></a><span data-ttu-id="c66b1-102">Element „View“ (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-102">View Element (Format)</span></span>

<span data-ttu-id="c66b1-103">Definiert eine Ansicht, in dem ein oder mehrere .NET Objekte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c66b1-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="c66b1-104">Es gibt keine Beschränkung für die Anzahl der Aufrufe, die in einer Formatierungsdatei definiert werden können.</span><span class="sxs-lookup"><span data-stu-id="c66b1-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="c66b1-105">Konfiguration-Element (Format) ViewDefinitions-Element (Format)-View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c66b1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c66b1-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c66b1-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="c66b1-107">Attributes and Elements</span></span>

<span data-ttu-id="c66b1-108">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `View` Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="c66b1-109">Geben Sie nur eines der untergeordneten Steuerelemente, und Sie müssen den Namen der Sicht und die Objekte, die der Ansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="c66b1-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="c66b1-110">Definieren von benutzerdefinierten Steuerelementen zum Gruppieren von Objekten und angibt, ob die Sicht Out-of-Band-ist, sind optional.</span><span class="sxs-lookup"><span data-stu-id="c66b1-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="c66b1-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="c66b1-111">Attributes</span></span>

<span data-ttu-id="c66b1-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="c66b1-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c66b1-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c66b1-113">Child Elements</span></span>

|<span data-ttu-id="c66b1-114">Element</span><span class="sxs-lookup"><span data-stu-id="c66b1-114">Element</span></span>|<span data-ttu-id="c66b1-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c66b1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c66b1-116">Controls-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="c66b1-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c66b1-118">Definiert einen Satz von Steuerelementen, die durch ihren Namen aus, in der Ansicht verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="c66b1-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="c66b1-119">CustomControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="c66b1-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c66b1-121">Definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="c66b1-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="c66b1-122">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="c66b1-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-123">Optional element.</span></span><br /><br /> <span data-ttu-id="c66b1-124">Definiert, wie die Elemente der .NET Objekte gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="c66b1-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="c66b1-125">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="c66b1-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-126">Optional element.</span></span><br /><br /> <span data-ttu-id="c66b1-127">Definiert eine Listenformat für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="c66b1-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="c66b1-128">Name-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="c66b1-129">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-129">Required element.</span></span><br /><br /> <span data-ttu-id="c66b1-130">Gibt den Namen verwendet, um die Sicht verweisen.</span><span class="sxs-lookup"><span data-stu-id="c66b1-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="c66b1-131">TableControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="c66b1-132">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-132">Optional element.</span></span><br /><br /> <span data-ttu-id="c66b1-133">Definiert ein Tabellenformat für die Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="c66b1-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="c66b1-134">ViewSelectedBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="c66b1-135">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-135">Required element.</span></span><br /><br /> <span data-ttu-id="c66b1-136">Definiert die .NET Objekte, die dieser Ansicht wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c66b1-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="c66b1-137">WideControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="c66b1-138">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="c66b1-138">Optional element.</span></span><br /><br /> <span data-ttu-id="c66b1-139">Definiert eine Vielzahl (Einzelwert) Listenformat für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="c66b1-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c66b1-140">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c66b1-140">Parent Elements</span></span>

|<span data-ttu-id="c66b1-141">Element</span><span class="sxs-lookup"><span data-stu-id="c66b1-141">Element</span></span>|<span data-ttu-id="c66b1-142">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c66b1-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c66b1-143">ViewDefinitions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="c66b1-144">Definiert die Ansichten verwendet, um die Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c66b1-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c66b1-145">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c66b1-145">Remarks</span></span>

<span data-ttu-id="c66b1-146">Weitere Informationen zu den Komponenten von verschiedenen Ansichten und benutzerdefinierten Steuerelementen finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="c66b1-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="c66b1-147">Tabelle anzeigen von Komponenten</span><span class="sxs-lookup"><span data-stu-id="c66b1-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="c66b1-148">Liste Anzeigen von Komponenten</span><span class="sxs-lookup"><span data-stu-id="c66b1-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="c66b1-149">Breite Ansichtskomponenten</span><span class="sxs-lookup"><span data-stu-id="c66b1-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="c66b1-150">Benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="c66b1-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="c66b1-151">Beispiel</span><span class="sxs-lookup"><span data-stu-id="c66b1-151">Example</span></span>

<span data-ttu-id="c66b1-152">Dieses Beispiel zeigt eine `View` Element, das eine Tabellenansicht für definiert die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="c66b1-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="c66b1-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c66b1-153">See Also</span></span>

[<span data-ttu-id="c66b1-154">ViewDefinitions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="c66b1-155">Name-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="c66b1-156">ViewSelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="c66b1-157">Controls-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="c66b1-158">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c66b1-159">TableControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="c66b1-160">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="c66b1-161">WideControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="c66b1-162">CustomControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c66b1-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="c66b1-163">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="c66b1-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
