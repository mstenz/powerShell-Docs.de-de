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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368979"
---
# <a name="creating-a-list-view"></a><span data-ttu-id="99e35-102">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="99e35-102">Creating a List View</span></span>

<span data-ttu-id="99e35-103">Eine Listenansicht zeigt Daten in einer einzelnen Spalte (in sequenzieller Reihenfolge) an.</span><span class="sxs-lookup"><span data-stu-id="99e35-103">A list view displays data in a single column (in sequential order).</span></span> <span data-ttu-id="99e35-104">Bei den in der Liste angezeigten Daten kann es sich um den Wert einer .net-Eigenschaft oder den Wert eines Skripts handeln.</span><span class="sxs-lookup"><span data-stu-id="99e35-104">The data displayed in the list can be the value of a .NET property or the value of a script.</span></span>

## <a name="a-list-view-display"></a><span data-ttu-id="99e35-105">Eine Listen Ansichts Anzeige</span><span class="sxs-lookup"><span data-stu-id="99e35-105">A List View Display</span></span>

<span data-ttu-id="99e35-106">Die folgende Ausgabe zeigt, wie die Eigenschaften von [System. ServiceProcess. ServiceController in Windows PowerShell angezeigt werden. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, die vom Cmdlet " [Get-Service](/powershell/module/microsoft.powershell.management/get-service) " zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-106">The following output shows how Windows PowerShell displays the properties of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects that are returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="99e35-107">In diesem Beispiel wurden drei Objekte zurückgegeben, wobei jedes Objekt durch eine leere Zeile vom vorangehenden Objekt getrennt wurde.</span><span class="sxs-lookup"><span data-stu-id="99e35-107">In this example, three objects were returned, with each object separated from the preceding object by a blank line.</span></span>

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

## <a name="defining-the-list-view"></a><span data-ttu-id="99e35-108">Definieren der Listenansicht</span><span class="sxs-lookup"><span data-stu-id="99e35-108">Defining the List View</span></span>

<span data-ttu-id="99e35-109">Der folgende XML-Code zeigt das Listen Ansichts Schema zum Anzeigen verschiedener Eigenschaften von [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="99e35-109">The following XML shows the list view schema for displaying several properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="99e35-110">Sie müssen jede Eigenschaft angeben, die in der Listenansicht angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="99e35-110">You must specify each property that you want displayed in the list view.</span></span>

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

<span data-ttu-id="99e35-111">Die folgenden XML-Elemente werden verwendet, um eine Listenansicht zu definieren:</span><span class="sxs-lookup"><span data-stu-id="99e35-111">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="99e35-112">Das [View](./view-element-format.md) -Element ist das übergeordnete Element der Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="99e35-112">The [View](./view-element-format.md) element is the parent element of the list view.</span></span> <span data-ttu-id="99e35-113">(Dies ist dasselbe übergeordnete Element für die Tabellen-, Wide-und Custom-Steuerelement Sichten.)</span><span class="sxs-lookup"><span data-stu-id="99e35-113">(This is the same parent element for the table, wide, and custom control views.)</span></span>

- <span data-ttu-id="99e35-114">Das [Name](./name-element-for-view-format.md) -Element gibt den Namen der Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="99e35-114">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="99e35-115">Dieses Element ist für alle Sichten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99e35-115">This element is required for all views.</span></span>

- <span data-ttu-id="99e35-116">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="99e35-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="99e35-117">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99e35-117">This element is required.</span></span>

- <span data-ttu-id="99e35-118">Das [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wann eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-118">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="99e35-119">Eine neue Gruppe wird immer dann gestartet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-119">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="99e35-120">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-120">This element is optional.</span></span>

- <span data-ttu-id="99e35-121">Das [Controls](./controls-element-for-view-format.md) -Element definiert die benutzerdefinierten Steuerelemente, die von der Listenansicht definiert werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-121">The [Controls](./controls-element-for-view-format.md) element defines the custom controls that are defined by the list view.</span></span> <span data-ttu-id="99e35-122">Steuerelemente geben Ihnen eine Möglichkeit, die Anzeige der Daten weiter anzugeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-122">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="99e35-123">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-123">This element is optional.</span></span> <span data-ttu-id="99e35-124">Eine Sicht kann eigene benutzerdefinierte Steuerelemente definieren, oder Sie kann allgemeine Steuerelemente verwenden, die von jeder Ansicht in der Formatierungs Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-124">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="99e35-125">Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-125">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="99e35-126">Das [ListControl](./listcontrol-element-format.md) -Element definiert, was in der Ansicht angezeigt wird und wie es formatiert wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-126">The [ListControl](./listcontrol-element-format.md) element defines what is displayed in the view and how it is formatted.</span></span> <span data-ttu-id="99e35-127">Ähnlich wie bei allen anderen Ansichten können in einer Listenansicht die Werte der Objekteigenschaften oder Werte angezeigt werden, die vom Skript generiert werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-127">Similar to all other views, a list view can display the values of object properties or values generated by script.</span></span>

<span data-ttu-id="99e35-128">Ein Beispiel für eine komplette Formatierungs Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-128">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-list-view"></a><span data-ttu-id="99e35-129">Bereitstellen von Definitionen für die Listenansicht</span><span class="sxs-lookup"><span data-stu-id="99e35-129">Providing Definitions for Your List View</span></span>

<span data-ttu-id="99e35-130">Listenansichten können mithilfe der untergeordneten Elemente des [ListControl](./listcontrol-element-format.md) -Elements eine oder mehrere Definitionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="99e35-130">List views can provide one or more definitions by using the child elements of the [ListControl](./listcontrol-element-format.md) element.</span></span> <span data-ttu-id="99e35-131">In der Regel hat eine Ansicht nur eine Definition.</span><span class="sxs-lookup"><span data-stu-id="99e35-131">Typically, a view will have only one definition.</span></span> <span data-ttu-id="99e35-132">Im folgenden Beispiel stellt die Sicht eine einzelne Definition bereit, die mehrere Eigenschaften von [System. Diagnostics. Process anzeigt? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="99e35-132">In the following example, the view provides a single definition that displays several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="99e35-133">In einer Listenansicht kann der Wert einer Eigenschaft oder der Wert eines Skripts angezeigt werden (nicht im Beispiel dargestellt).</span><span class="sxs-lookup"><span data-stu-id="99e35-133">A list view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="99e35-134">Die folgenden XML-Elemente können verwendet werden, um Definitionen für eine Listenansicht bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="99e35-134">The following XML elements can be used to provide definitions for a list view:</span></span>

- <span data-ttu-id="99e35-135">Das [ListControl](./listcontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-135">The [ListControl](./listcontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="99e35-136">Das [ListEntries](./listentries-element-for-listcontrol-format.md) -Element stellt die Definitionen der Sicht bereit.</span><span class="sxs-lookup"><span data-stu-id="99e35-136">The [ListEntries](./listentries-element-for-listcontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="99e35-137">In den meisten Fällen weist eine Ansicht nur eine Definition auf.</span><span class="sxs-lookup"><span data-stu-id="99e35-137">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="99e35-138">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99e35-138">This element is required.</span></span>

- <span data-ttu-id="99e35-139">Das [ListEntry](./listentry-element-for-listcontrol-format.md) -Element stellt eine Definition der Sicht bereit.</span><span class="sxs-lookup"><span data-stu-id="99e35-139">The [ListEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="99e35-140">Mindestens ein [ListEntry](./listentry-element-for-listcontrol-format.md) ist erforderlich. Es gibt jedoch keine maximale Beschränkung für die Anzahl der Elemente, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="99e35-140">At least one [ListEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="99e35-141">In den meisten Fällen weist eine Ansicht nur eine Definition auf.</span><span class="sxs-lookup"><span data-stu-id="99e35-141">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="99e35-142">Das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element gibt die Objekte an, die von einer bestimmten Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-142">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="99e35-143">Dieses Element ist optional und wird nur benötigt, wenn Sie mehrere [ListEntry](./listentry-element-for-listcontrol-format.md) -Elemente definieren, die verschiedene-Objekte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="99e35-143">This element is optional and is needed only when you define multiple [ListEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="99e35-144">Das [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) -Element gibt die Eigenschaften und Skripts an, deren Werte in den Zeilen der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-144">The [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies the properties and scripts whose values are displayed in the rows of the list view.</span></span>

- <span data-ttu-id="99e35-145">Das [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) -Element gibt eine Eigenschaft oder ein Skript an, dessen Wert in einer Zeile der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-145">The [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) element specifies a property or script whose value is displayed in a row of the list view.</span></span> <span data-ttu-id="99e35-146">In einer Listenansicht muss mindestens eine Eigenschaft oder ein Skript angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-146">A list view must specify at least one property or script.</span></span> <span data-ttu-id="99e35-147">Es gibt keine maximale Beschränkung für die Anzahl der Zeilen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-147">There is no maximum limit to the number of rows that can be specified.</span></span>

- <span data-ttu-id="99e35-148">Das [propertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element gibt die-Eigenschaft an, deren Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-148">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="99e35-149">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-149">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="99e35-150">Das [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) -Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-150">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="99e35-151">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-151">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="99e35-152">Das [Label](./label-element-for-listitem-for-listcontrol-format.md) -Element gibt die Bezeichnung an, die auf der linken Seite des Eigenschafts-oder Skript Werts in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-152">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element specifies the label that is displayed to the left of the property or script value in the row.</span></span> <span data-ttu-id="99e35-153">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-153">This element is optional.</span></span> <span data-ttu-id="99e35-154">Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft oder des Skripts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="99e35-154">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="99e35-155">Ein umfassendes Beispiel finden Sie unter [Listenansicht (Bezeichnungen)](./list-view-labels.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-155">For a complete example, see [List View (Labels)](./list-view-labels.md).</span></span>

- <span data-ttu-id="99e35-156">Das [itemselectioncondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) -Element gibt eine Bedingung an, die vorhanden sein muss, damit die Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-156">The [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) element specifies a condition that must exist for the row to be displayed.</span></span> <span data-ttu-id="99e35-157">Weitere Informationen zum Hinzufügen von Bedingungen zur Listenansicht finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-157">For more information about adding conditions to the list view, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span> <span data-ttu-id="99e35-158">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-158">This element is optional.</span></span>

- <span data-ttu-id="99e35-159">Das [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Muster an, das verwendet wird, um den Wert der Eigenschaft oder des Skripts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="99e35-159">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a pattern that is used to display the value of the property or script.</span></span> <span data-ttu-id="99e35-160">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-160">This element is optional.</span></span>

<span data-ttu-id="99e35-161">Ein Beispiel für eine komplette Formatierungs Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-161">For an example of a complete formatting file that defines a simple list view, see [List View (Basic)](./list-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-list-view"></a><span data-ttu-id="99e35-162">Definieren der Objekte, die die Listenansicht verwenden</span><span class="sxs-lookup"><span data-stu-id="99e35-162">Defining the Objects That Use the List View</span></span>

<span data-ttu-id="99e35-163">Es gibt zwei Möglichkeiten, um zu definieren, welche .NET-Objekte die Listenansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="99e35-163">There are two ways to define which .NET objects use the list view.</span></span> <span data-ttu-id="99e35-164">Sie können das [viewselectedby](./viewselectedby-element-format.md) -Element verwenden, um die Objekte zu definieren, die von allen Definitionen der Sicht angezeigt werden können, oder Sie können das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element verwenden, um zu definieren, welche Objekte von einer bestimmten Definition der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-164">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="99e35-165">In den meisten Fällen verfügt eine Sicht nur über eine Definition, sodass Objekte normalerweise durch das [viewselectedby](./viewselectedby-element-format.md) -Element definiert werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-165">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="99e35-166">Im folgenden Beispiel wird gezeigt, wie die Objekte definiert werden, die in der Listenansicht mithilfe der Elemente [viewselectedby](./viewselectedby-element-format.md) und [tygtame](./typename-element-for-viewselectedby-format.md) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-166">The following example shows how to define the objects that are displayed by the list view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="99e35-167">Es gibt keine Beschränkung für die Anzahl der [tyname](./typename-element-for-viewselectedby-format.md) -Elemente, die Sie angeben können, und ihre Reihenfolge ist nicht signifikant.</span><span class="sxs-lookup"><span data-stu-id="99e35-167">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="99e35-168">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="99e35-168">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="99e35-169">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-169">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="99e35-170">Das [tykame](./typename-element-for-viewselectedby-format.md) -Element gibt das .NET-Objekt an, das von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-170">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="99e35-171">Der voll qualifizierte .net-Typname ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99e35-171">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="99e35-172">Sie müssen mindestens einen Typ oder einen Auswahl Satz für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-172">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="99e35-173">Ein Beispiel für eine komplette Formatierungs Datei finden Sie in der [Listenansicht (Basic)](./list-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-173">For an example of a complete formatting file, see [List View (Basic)](./list-view-basic.md).</span></span>

<span data-ttu-id="99e35-174">Im folgenden Beispiel werden die Elemente [viewselectedby](./viewselectedby-element-format.md) und [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) verwendet.</span><span class="sxs-lookup"><span data-stu-id="99e35-174">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="99e35-175">Verwenden Sie Auswahl Sätze, bei denen Sie über einen zugehörigen Satz von Objekten verfügen, die mithilfe mehrerer Sichten angezeigt werden, z. b. Wenn Sie eine Listenansicht und eine Tabellenansicht für dieselben Objekte definieren.</span><span class="sxs-lookup"><span data-stu-id="99e35-175">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="99e35-176">Weitere Informationen zum Erstellen eines Auswahl Satzes finden Sie unter Definieren von [Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-176">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

<span data-ttu-id="99e35-177">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="99e35-177">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="99e35-178">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-178">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="99e35-179">Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element gibt eine Gruppe von-Objekten an, die von der Sicht angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-179">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="99e35-180">Sie müssen mindestens einen Auswahl Satz oder-Typ für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-180">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="99e35-181">Im folgenden Beispiel wird gezeigt, wie die-Objekte, die durch eine bestimmte Definition der Listenansicht angezeigt werden, mit dem [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element definiert werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-181">The following example shows how to define the objects displayed by a specific definition of the list view using the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element.</span></span> <span data-ttu-id="99e35-182">Mit diesem Element können Sie den .NET-Typnamen des Objekts, einen Auswahl Satz von Objekten oder eine Auswahlbedingung angeben, die angibt, wann die Definition verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-182">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="99e35-183">Weitere Informationen zum Erstellen von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-183">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

<span data-ttu-id="99e35-184">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von einer bestimmten Definition der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="99e35-184">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="99e35-185">Das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element definiert, welche Objekte von der Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-185">The [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="99e35-186">Das [tykame](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt das .NET-Objekt an, das von der Definition angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-186">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="99e35-187">Wenn Sie dieses Element verwenden, ist der voll qualifizierte .net-Typname erforderlich.</span><span class="sxs-lookup"><span data-stu-id="99e35-187">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="99e35-188">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="99e35-189">Das [selectionsetname](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Gruppe von Objekten an, die von dieser Definition angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-189">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="99e35-190">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-190">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="99e35-191">Das [selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Bedingung an, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="99e35-191">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="99e35-192">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="99e35-192">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="99e35-193">Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-193">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-list-view"></a><span data-ttu-id="99e35-194">Anzeigen von Gruppen von Objekten in einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="99e35-194">Displaying Groups of Objects in a List View</span></span>

<span data-ttu-id="99e35-195">Sie können die Objekte, die von der Listenansicht angezeigt werden, in Gruppen aufteilen.</span><span class="sxs-lookup"><span data-stu-id="99e35-195">You can separate the objects that are displayed by the list view into groups.</span></span> <span data-ttu-id="99e35-196">Dies bedeutet nicht, dass Sie eine Gruppe definieren, sondern nur, dass Windows PowerShell eine neue Gruppe startet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-196">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="99e35-197">Im folgenden Beispiel wird eine neue Gruppe immer dann gestartet, wenn sich der Wert der [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) -Eigenschaft ändert.</span><span class="sxs-lookup"><span data-stu-id="99e35-197">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="99e35-198">Die folgenden XML-Elemente werden verwendet, um zu definieren, wann eine Gruppe gestartet wird:</span><span class="sxs-lookup"><span data-stu-id="99e35-198">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="99e35-199">Das [GroupBy](./groupby-element-for-view-format.md) -Element definiert die Eigenschaft oder das Skript, das die neue Gruppe startet und definiert, wie die Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-199">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="99e35-200">Das [propertyName](./propertyname-element-for-groupby-format.md) -Element gibt die Eigenschaft an, die eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="99e35-200">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="99e35-201">Sie müssen eine Eigenschaft oder ein Skript angeben, um die Gruppe zu starten, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-201">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="99e35-202">Das [ScriptBlock](./scriptblock-element-for-groupby-format.md) -Element gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="99e35-202">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="99e35-203">Sie müssen ein Skript oder eine Eigenschaft angeben, um die Gruppe zu starten, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-203">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="99e35-204">Das [Label](./label-element-for-groupby-format.md) -Element definiert eine Bezeichnung, die am Anfang jeder Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-204">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="99e35-205">Zusätzlich zu dem Text, der von diesem Element angegeben wird, zeigt Windows PowerShell den Wert an, der die neue Gruppe ausgelöst hat, und fügt vor und nach der Bezeichnung eine leere Zeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="99e35-205">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="99e35-206">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-206">This element is optional.</span></span>

- <span data-ttu-id="99e35-207">Das [CustomControl](./customcontrol-element-for-groupby-format.md) -Element definiert ein Steuerelement, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-207">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="99e35-208">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-208">This element is optional.</span></span>

- <span data-ttu-id="99e35-209">Das [customcontrolname](./customcontrolname-element-for-groupby-format.md) -Element gibt ein Common-oder View-Steuerelement an, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-209">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="99e35-210">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="99e35-210">This element is optional.</span></span>

<span data-ttu-id="99e35-211">Ein Beispiel für eine komplette Formatierungs Datei, die Gruppen definiert, finden Sie unter [Listenansicht (GroupBy)](./list-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="99e35-211">For an example of a complete formatting file that defines groups, see [List View (GroupBy)](./list-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="99e35-212">Using-Format</span><span class="sxs-lookup"><span data-stu-id="99e35-212">Using Format Strings</span></span>

<span data-ttu-id="99e35-213">Formatierungs Zeichenfolgen können einer Ansicht hinzugefügt werden, um die Anzeige der Daten weiter zu definieren.</span><span class="sxs-lookup"><span data-stu-id="99e35-213">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="99e35-214">Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-214">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

<span data-ttu-id="99e35-215">Die folgenden XML-Elemente können verwendet werden, um ein Format Muster anzugeben:</span><span class="sxs-lookup"><span data-stu-id="99e35-215">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="99e35-216">Das [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-216">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="99e35-217">Das [propertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element gibt die Eigenschaft an, deren Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-217">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="99e35-218">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-218">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="99e35-219">Das Format [String](./formatstring-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-219">The [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

- <span data-ttu-id="99e35-220">Das [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-220">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="99e35-221">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-221">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="99e35-222">Im folgenden Beispiel wird die `ToString`-Methode aufgerufen, um den Wert des Skripts zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="99e35-222">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="99e35-223">Skripts können beliebige Methoden eines Objekts aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="99e35-223">Scripts can call any method of an object.</span></span> <span data-ttu-id="99e35-224">Wenn ein Objekt über eine-Methode verfügt, z. b. `ToString`, die Formatierungs Parameter hat, kann das Skript daher diese Methode zum Formatieren des Ausgabe Werts des Skripts aufruft.</span><span class="sxs-lookup"><span data-stu-id="99e35-224">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="99e35-225">Das folgende XML-Element kann verwendet werden, um die `ToString`-Methode aufrufen:</span><span class="sxs-lookup"><span data-stu-id="99e35-225">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="99e35-226">Das [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99e35-226">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="99e35-227">Das [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="99e35-227">The [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="99e35-228">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="99e35-228">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="99e35-229">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="99e35-229">See Also</span></span>

[<span data-ttu-id="99e35-230">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="99e35-230">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/writing-a-windows-powershell-cmdlet.md)
