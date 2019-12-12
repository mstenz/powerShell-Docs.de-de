---
title: View-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361459"
---
# <a name="view-element-format"></a><span data-ttu-id="8fa13-102">Element „View“ (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-102">View Element (Format)</span></span>

<span data-ttu-id="8fa13-103">Definiert eine Ansicht, in der ein oder mehrere .NET-Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8fa13-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="8fa13-104">Es gibt keine Beschränkung für die Anzahl der Sichten, die in einer Formatierungs Datei definiert werden können.</span><span class="sxs-lookup"><span data-stu-id="8fa13-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="8fa13-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fa13-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fa13-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="8fa13-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8fa13-107">Attributes and Elements</span></span>

<span data-ttu-id="8fa13-108">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `View`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8fa13-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="8fa13-109">Sie müssen nur eines der untergeordneten Steuerelemente des Steuer Elements angeben, und Sie müssen den Namen der Ansicht und die Objekte, die die Sicht verwenden, angeben.</span><span class="sxs-lookup"><span data-stu-id="8fa13-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="8fa13-110">Definieren von benutzerdefinierten Steuerelementen, Gruppieren von Objekten und angeben, ob die Ansicht out-of-Band ist, sind optional.</span><span class="sxs-lookup"><span data-stu-id="8fa13-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fa13-111">Attributes</span><span class="sxs-lookup"><span data-stu-id="8fa13-111">Attributes</span></span>

<span data-ttu-id="8fa13-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="8fa13-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fa13-113">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8fa13-113">Child Elements</span></span>

|<span data-ttu-id="8fa13-114">Element</span><span class="sxs-lookup"><span data-stu-id="8fa13-114">Element</span></span>|<span data-ttu-id="8fa13-115">Description</span><span class="sxs-lookup"><span data-stu-id="8fa13-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fa13-116">Controls-Element für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="8fa13-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-117">Optional element.</span></span><br /><br /> <span data-ttu-id="8fa13-118">Definiert eine Gruppe von Steuerelementen, auf die über Ihren Namen in der Ansicht verwiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="8fa13-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="8fa13-119">CustomControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="8fa13-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-120">Optional element.</span></span><br /><br /> <span data-ttu-id="8fa13-121">Definiert ein benutzerdefiniertes Steuerelement Format für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="8fa13-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="8fa13-122">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="8fa13-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-123">Optional element.</span></span><br /><br /> <span data-ttu-id="8fa13-124">Definiert, wie die Member der .NET-Objekte gruppiert werden.</span><span class="sxs-lookup"><span data-stu-id="8fa13-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="8fa13-125">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="8fa13-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-126">Optional element.</span></span><br /><br /> <span data-ttu-id="8fa13-127">Definiert ein Listenformat für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="8fa13-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="8fa13-128">Name-Element für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="8fa13-129">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-129">Required element.</span></span><br /><br /> <span data-ttu-id="8fa13-130">Gibt den Namen an, der zum Verweisen auf die Sicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8fa13-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="8fa13-131">Tablecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="8fa13-132">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-132">Optional element.</span></span><br /><br /> <span data-ttu-id="8fa13-133">Definiert ein Tabellenformat für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="8fa13-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="8fa13-134">Viewselectedby-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="8fa13-135">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-135">Required element.</span></span><br /><br /> <span data-ttu-id="8fa13-136">Definiert die .NET-Objekte, die in dieser Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8fa13-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="8fa13-137">Widecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="8fa13-138">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="8fa13-138">Optional element.</span></span><br /><br /> <span data-ttu-id="8fa13-139">Definiert ein breites Listenformat (Einzelwert) für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="8fa13-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8fa13-140">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8fa13-140">Parent Elements</span></span>

|<span data-ttu-id="8fa13-141">Element</span><span class="sxs-lookup"><span data-stu-id="8fa13-141">Element</span></span>|<span data-ttu-id="8fa13-142">Description</span><span class="sxs-lookup"><span data-stu-id="8fa13-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fa13-143">Viewdefinitions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="8fa13-144">Definiert die Sichten, die zum Anzeigen von Objekten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8fa13-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8fa13-145">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8fa13-145">Remarks</span></span>

<span data-ttu-id="8fa13-146">Weitere Informationen zu den Komponenten verschiedener Sichten und benutzerdefinierte Steuerelemente finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="8fa13-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="8fa13-147">Tabellen Ansichts Komponenten</span><span class="sxs-lookup"><span data-stu-id="8fa13-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="8fa13-148">Listen Ansichts Komponenten</span><span class="sxs-lookup"><span data-stu-id="8fa13-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="8fa13-149">Breite Ansichts Komponenten</span><span class="sxs-lookup"><span data-stu-id="8fa13-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="8fa13-150">Benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="8fa13-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="8fa13-151">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8fa13-151">Example</span></span>

<span data-ttu-id="8fa13-152">Dieses Beispiel zeigt ein `View`-Element, das eine Tabellenansicht für das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt definiert.</span><span class="sxs-lookup"><span data-stu-id="8fa13-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8fa13-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8fa13-153">See Also</span></span>

[<span data-ttu-id="8fa13-154">Viewdefinitions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="8fa13-155">Name-Element für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="8fa13-156">Viewselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="8fa13-157">Controls-Element für View (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="8fa13-158">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8fa13-159">Tablecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="8fa13-160">ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="8fa13-161">Widecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="8fa13-162">CustomControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8fa13-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="8fa13-163">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="8fa13-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
