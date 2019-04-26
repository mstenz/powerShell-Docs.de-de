---
title: Erstellen einer Listenansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066854"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="bb42a-102">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="bb42a-102">Creating a List View</span></span>

<span data-ttu-id="bb42a-103">Eine Listenansicht zeigt Daten in eine einzelne Spalte (in sequenzieller Reihenfolge).</span><span class="sxs-lookup"><span data-stu-id="bb42a-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="bb42a-104">In der Liste angezeigten Daten möglich den Wert einer Eigenschaft .NET oder der Wert eines Skripts.</span><span class="sxs-lookup"><span data-stu-id="bb42a-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="bb42a-105">Anzeige einer Liste</span><span class="sxs-lookup"><span data-stu-id="bb42a-105">A List View Display</span></span>

<span data-ttu-id="bb42a-106">Die folgende Ausgabe zeigt, wie die Eigenschaften der von Windows PowerShell zeigt [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte, die von zurückgegeben werden die [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb42a-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="bb42a-107">In diesem Beispiel wurden drei Objekte zurückgegeben, mit jedem Objekt, das aus dem vorherigen Objekt durch eine leere Zeile getrennt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a><span data-ttu-id="bb42a-108">Definieren der Listenansicht</span><span class="sxs-lookup"><span data-stu-id="bb42a-108">Defining the List View</span></span>

<span data-ttu-id="bb42a-109">Das folgende XML zeigt das Schema Liste angezeigt, für die Anzeige von mehreren Eigenschaften der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="bb42a-110">Sie müssen jede Eigenschaft angeben, die in der Listenansicht angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bb42a-110">You must specify each property that you want displayed in the list view.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

<span data-ttu-id="bb42a-111">Die folgende XML-Elemente werden verwendet, um eine Ansicht zu definieren:</span><span class="sxs-lookup"><span data-stu-id="bb42a-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="bb42a-112">Die [Ansicht](./view-element-format.md) Element ist das übergeordnete Element der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="bb42a-113">(Dies ist der dasselbe übergeordnete Element für die Tabelle, Breite und benutzerdefinierte Steuerelementansicht.)</span><span class="sxs-lookup"><span data-stu-id="bb42a-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="bb42a-114">Die [Namen](./name-element-for-view-format.md) Element gibt den Namen der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="bb42a-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="bb42a-115">Dieses Element ist für alle Ansichten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb42a-115">This element is required for all views.</span></span>

- <span data-ttu-id="bb42a-116">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="bb42a-117">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb42a-117">This element is required.</span></span>

- <span data-ttu-id="bb42a-118">Die [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wenn eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="bb42a-119">Eine neue Gruppe wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="bb42a-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="bb42a-120">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-120">This element is optional.</span></span>

- <span data-ttu-id="bb42a-121">Die [Steuerelemente](./controls-element-for-view-format.md) -Element definiert die benutzerdefinierten Steuerelemente, die von der Listenansicht definiert sind.</span><span class="sxs-lookup"><span data-stu-id="bb42a-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="bb42a-122">Steuerelemente bieten Ihnen eine Möglichkeit, festzulegen, wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="bb42a-123">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-123">This element is optional.</span></span> <span data-ttu-id="bb42a-124">Eine Ansicht kann eine eigene benutzerdefinierte Steuerelemente zu definieren, oder sie können allgemeine Steuerelemente, die von einer beliebigen Ansicht in der Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="bb42a-125">Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="bb42a-126">Die [ListControl](./listcontrol-element-format.md) -Element definiert, was in der Ansicht angezeigt wird und wie es formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="bb42a-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="bb42a-127">Ähnlich wie bei allen anderen Ansichten, kann eine Listenansicht die Werte der Objekteigenschaften oder Werte, die vom Skript generiert anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="bb42a-128">Ein Beispiel für eine vollständige Formatierung-Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="bb42a-129">Bereitstellen von Definitionen für Ihre Listenansicht</span><span class="sxs-lookup"><span data-stu-id="bb42a-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="bb42a-130">Listenansichten können eine oder mehrere Definitionen bereitstellen, indem die untergeordneten Elemente des mithilfe der [ListControl](./listcontrol-element-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="bb42a-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="bb42a-131">Eine Sicht wird in der Regel nur eine Definition verfügen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="bb42a-132">Im folgenden Beispiel die Ansicht bietet eine einzige Definition, die mehrere Eigenschaften der zeigt die ["System.Diagnostics.Process"? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="bb42a-133">Eine Listenansicht kann den Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel gezeigt) anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

<span data-ttu-id="bb42a-134">Die folgende XML-Elemente können verwendet werden, um Definitionen für eine Listenansicht bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="bb42a-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="bb42a-135">Die [ListControl](./listcontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="bb42a-136">Die [ListEntries](./listentries-element-for-listcontrol-format.md) Element enthält die Definitionen der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="bb42a-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="bb42a-137">In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="bb42a-138">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb42a-138">This element is required.</span></span>

- <span data-ttu-id="bb42a-139">Die [ListEntry](./listentry-element-for-listcontrol-format.md) Element enthält eine Definition der Sicht.</span><span class="sxs-lookup"><span data-stu-id="bb42a-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="bb42a-140">Mindestens ein [ListEntry](./listentry-element-for-listcontrol-format.md) ist erforderlich; Es ist jedoch nicht begrenzt auf die Anzahl der Elemente, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="bb42a-141">In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="bb42a-142">Die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Element gibt an, die Objekte, die von einer bestimmten Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="bb42a-143">Dieses Element ist optional und ist nur erforderlich, wenn Sie mehrere definieren [ListEntry](./listentry-element-for-listcontrol-format.md) Elemente, die verschiedene Objekte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="bb42a-144">Die [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) Element gibt die Eigenschaften und Skripts, deren Werte werden in den Zeilen der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="bb42a-145">Die [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) Element gibt an, eine Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="bb42a-146">Eine Listenansicht muss mindestens eine Eigenschaft oder ein Skript angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="bb42a-147">Es gibt keine Obergrenze, die Anzahl der Zeilen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="bb42a-148">Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) Element gibt die Eigenschaft, deren Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="bb42a-149">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="bb42a-150">Die ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="bb42a-151">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="bb42a-152">Die [Bezeichnung](./label-element-for-listitem-for-listcontrol-format.md) Element gibt die Bezeichnung, die auf der linken Seite des Eigenschaft oder des Skripts in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="bb42a-153">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-153">This element is optional.</span></span> <span data-ttu-id="bb42a-154">Wenn eine Bezeichnung nicht angegeben ist, wird der Name der Eigenschaft oder des Skripts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="bb42a-155">Ein vollständiges Beispiel finden Sie unter [Listenansicht (Bezeichnungen)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="bb42a-156">Die [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) Element gibt eine Bedingung, die vorhanden sein muss, für die Zeile, die angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="bb42a-157">Weitere Informationen zum Hinzufügen von Bedingungen zur Listenansicht wechseln, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="bb42a-158">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-158">This element is optional.</span></span>

- <span data-ttu-id="bb42a-159">Die [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) Element gibt ein Muster, das verwendet wird, um den Wert der Eigenschaft oder des Skripts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="bb42a-160">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-160">This element is optional.</span></span>

<span data-ttu-id="bb42a-161">Ein Beispiel für eine vollständige Formatierung-Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="bb42a-162">Definieren die Objekte, die der Listenansicht</span><span class="sxs-lookup"><span data-stu-id="bb42a-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="bb42a-163">Es gibt zwei Möglichkeiten, die definieren, welche .NET Objekte der Listenansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="bb42a-164">Können Sie die [ViewSelectedBy](./viewselectedby-element-format.md) Element, das die Objekte zu definieren, die durch alle Definitionen oder der Ansicht angezeigt werden können. die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element zum definieren, welche Objekte angezeigt werden ein spezifische Definition der Sicht.</span><span class="sxs-lookup"><span data-stu-id="bb42a-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="bb42a-165">In den meisten Fällen eine Ansicht hat nur eine Definition, sodass Objekte in der Regel, indem definiert werden die [ViewSelectedBy](./viewselectedby-element-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="bb42a-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="bb42a-166">Das folgende Beispiel zeigt, wie Sie die Objekte zu definieren, die mithilfe der Liste Ansicht angezeigt werden die [ViewSelectedBy](./viewselectedby-element-format.md) und [TypeName](./typename-element-for-viewselectedby-format.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="bb42a-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="bb42a-167">Es gibt keine Beschränkung der Anzahl der [TypeName](./typename-element-for-viewselectedby-format.md) Elementen, die Sie angeben können und ihre Reihenfolge ist nicht von Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="bb42a-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="bb42a-168">Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="bb42a-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="bb42a-169">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="bb42a-170">Die [TypeName](./typename-element-for-viewselectedby-format.md) -Element gibt an, das .NET-Objekt, das von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="bb42a-171">Der vollqualifizierte Typname des .NET ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb42a-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="bb42a-172">Geben Sie mindestens einen Typ oder Auswahl für die Ansicht festgelegt, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="bb42a-173">Ein Beispiel für eine vollständige Formatierungsdatei, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="bb42a-174">Im folgenden Beispiel wird die [ViewSelectedBy](./viewselectedby-element-format.md) und [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="bb42a-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="bb42a-175">Verwenden Sie die Auswahl legt, haben eine zusammengehörige Gruppe von Objekten, die über mehrere Ansichten, z. B. Wenn Sie eine Listenansicht definieren und eine Tabellenansicht für diese Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="bb42a-176">Weitere Informationen dazu, wie Sie einen Auswahlsatz zu erstellen, finden Sie unter [definieren Auswahl legt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="bb42a-177">Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="bb42a-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="bb42a-178">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="bb42a-179">Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element gibt einen Satz von Objekten, die von der Ansicht angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="bb42a-180">Geben Sie mindestens einen Auswahlsatz oder Typ, für die Sicht, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="bb42a-181">Das folgende Beispiel zeigt, wie Sie definieren die Objekte angezeigt, die von einer bestimmten Definition der Liste Ansicht mithilfe der [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="bb42a-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="bb42a-182">Verwenden dieses Element, können Sie den Namen des Objekts, einer Auswahlsatz von Objekten oder eine auswahlbedingung, die angibt, wenn die Definition verwendet wird angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="bb42a-183">Weitere Informationen dazu, wie Sie eine Auswahl Bedingungen zu erstellen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="bb42a-184">Die folgende XML-Elemente können verwendet werden, die Objekte an, die von einer bestimmten Definition der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="bb42a-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="bb42a-185">Die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Element definiert, welche Objekte durch die Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="bb42a-186">Die [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt an, das .NET-Objekt, das durch die Definition angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="bb42a-187">Wenn Sie dieses Element zu verwenden, ist der vollqualifizierte Typname des .NET erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bb42a-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="bb42a-188">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="bb42a-189">Die [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt einen Satz von Objekten, die von dieser Definition angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="bb42a-190">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="bb42a-191">Die [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt an, eine Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="bb42a-192">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="bb42a-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="bb42a-193">Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="bb42a-194">Anzeigen von Gruppen von Objekten in einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="bb42a-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="bb42a-195">Sie können die Objekte trennen, die von der Listenansicht in Gruppen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="bb42a-196">Dies bedeutet nicht, dass Sie eine Gruppe definieren nur die eine neue Gruppe, die Windows PowerShell wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="bb42a-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="bb42a-197">Im folgenden Beispiel wird eine neue Gruppe gestartet Wenn der Wert des der [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) eigenschaftenänderungen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="bb42a-198">Die folgende XML-Elemente werden zum definieren, wenn Sie eine Gruppe gestartet wird:</span><span class="sxs-lookup"><span data-stu-id="bb42a-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="bb42a-199">Die [GroupBy](./groupby-element-for-view-format.md) -Element definiert die Eigenschaft oder ein Skript, das die neue Gruppe gestartet und definiert, wie die Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="bb42a-200">Die [PropertyName](./propertyname-element-for-groupby-format.md) Element gibt die Eigenschaft, die eine neue Gruppe wird gestartet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="bb42a-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="bb42a-201">Sie müssen eine Eigenschaft oder ein Skript zum Starten der Gruppe angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="bb42a-202">Die ["scriptblock"](./scriptblock-element-for-groupby-format.md) Element gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="bb42a-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="bb42a-203">Sie müssen angeben, ein Skript oder eine Eigenschaft, um die Gruppe zu starten, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="bb42a-204">Die [Bezeichnung](./label-element-for-groupby-format.md) -Element definiert eine Bezeichnung, die am Anfang der Gruppe "Jeder" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="bb42a-205">Zusätzlich zu den Text, der von diesem Element angegeben wird wird der Wert, der die neue Gruppe ausgelöst und fügt eine leere Zeile vor und nach der die Bezeichnung von Windows PowerShell angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="bb42a-206">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-206">This element is optional.</span></span>

- <span data-ttu-id="bb42a-207">Die [CustomControl](./customcontrol-element-for-groupby-format.md) -Element definiert ein Steuerelement, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="bb42a-208">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-208">This element is optional.</span></span>

- <span data-ttu-id="bb42a-209">Die [CustomControlName](./customcontrolname-element-for-groupby-format.md) Element gibt einen allgemeinen oder Steuerelements, die zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="bb42a-210">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="bb42a-210">This element is optional.</span></span>

<span data-ttu-id="bb42a-211">Ein Beispiel für eine vollständige Formatierung-Datei, die Gruppen definiert, finden Sie unter [Listenansicht (-GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="bb42a-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="bb42a-212">Verwenden von Formatzeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="bb42a-212">Using Format Strings</span></span>

<span data-ttu-id="bb42a-213">Formatieren von Zeichenfolgen können hinzugefügt werden, zu einer Ansicht genauer definieren, wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="bb42a-214">Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="bb42a-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="bb42a-215">Die folgende XML-Elemente können verwendet werden, ein Formatmuster angeben:</span><span class="sxs-lookup"><span data-stu-id="bb42a-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="bb42a-216">Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="bb42a-217">Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) Element gibt die Eigenschaft, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="bb42a-218">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="bb42a-219">Die [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bb42a-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="bb42a-220">Die ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="bb42a-221">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="bb42a-222">Im folgenden Beispiel die `ToString` aufgerufen, um den Wert des Skripts zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="bb42a-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="bb42a-223">Skripts können auf jede Methode eines Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="bb42a-224">Daher verfügt ein Objekt eine Methode, wie z. B. `ToString`über Formatierung Parameter verfügt, das Skript kann diese Methode zum Formatieren des Werts der Ausgabe des Skripts aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="bb42a-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="bb42a-225">Das folgende XML-Element kann zum Aufrufen der `ToString` Methode:</span><span class="sxs-lookup"><span data-stu-id="bb42a-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="bb42a-226">Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bb42a-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="bb42a-227">Die ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bb42a-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="bb42a-228">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="bb42a-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb42a-229">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bb42a-229">See Also</span></span>

[<span data-ttu-id="bb42a-230">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="bb42a-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
