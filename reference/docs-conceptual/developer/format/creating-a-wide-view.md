---
title: Erstellen einer breiten Ansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368949"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="a118f-102">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="a118f-102">Creating a Wide View</span></span>

<span data-ttu-id="a118f-103">Eine breite Ansicht zeigt einen einzelnen Wert für jedes angezeigte Objekt an.</span><span class="sxs-lookup"><span data-stu-id="a118f-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="a118f-104">Der angezeigte Wert kann der Wert einer .NET-Objekt Eigenschaft oder der Wert eines Skripts sein.</span><span class="sxs-lookup"><span data-stu-id="a118f-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="a118f-105">Standardmäßig gibt es für diese Ansicht keine Bezeichnung oder einen Header.</span><span class="sxs-lookup"><span data-stu-id="a118f-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="a118f-106">Eine breite Anzeige Ansicht</span><span class="sxs-lookup"><span data-stu-id="a118f-106">A Wide View Display</span></span>

<span data-ttu-id="a118f-107">Das folgende Beispiel zeigt, wie Windows PowerShell das [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekt anzeigt, das vom Cmdlet " [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) " zurückgegeben wird, wenn die Ausgabe an das Cmdlet " [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) " weitergeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="a118f-108">(Standardmäßig gibt das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet eine Tabellenansicht zurück.) In diesem Beispiel werden die beiden Spalten verwendet, um den Namen des Prozesses für jedes zurückgegebene Objekt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a118f-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="a118f-109">Der Name der Eigenschaft des Objekts wird nicht angezeigt, sondern nur der Wert der Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="a118f-109">The name of the object's property is not displayed, only the value of the property.</span></span>

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a><span data-ttu-id="a118f-110">Definieren der breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="a118f-110">Defining the Wide View</span></span>

<span data-ttu-id="a118f-111">Der folgende XML-Code zeigt das breite Ansichts Schema für das [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="a118f-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

<span data-ttu-id="a118f-112">Die folgenden XML-Elemente werden zum Definieren einer breiten Ansicht verwendet:</span><span class="sxs-lookup"><span data-stu-id="a118f-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="a118f-113">Das [View](./view-element-format.md) -Element ist das übergeordnete Element der breiten Ansicht.</span><span class="sxs-lookup"><span data-stu-id="a118f-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="a118f-114">(Dies ist dasselbe übergeordnete Element für die Tabellen-, Listen-und benutzerdefinierten Steuerelement Sichten.)</span><span class="sxs-lookup"><span data-stu-id="a118f-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="a118f-115">Das [Name](./name-element-for-view-format.md) -Element gibt den Namen der Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="a118f-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="a118f-116">Dieses Element ist für alle Sichten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a118f-116">This element is required for all views.</span></span>

- <span data-ttu-id="a118f-117">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="a118f-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="a118f-118">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a118f-118">This element is required.</span></span>

- <span data-ttu-id="a118f-119">Das [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wann eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="a118f-120">Eine neue Gruppe wird immer dann gestartet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="a118f-121">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-121">This element is optional.</span></span>

- <span data-ttu-id="a118f-122">Die [Steuerelemente der](./controls-element-for-view-format.md) Steuerelemente definieren die benutzerdefinierten Steuerelemente, die von der breiten Ansicht definiert werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="a118f-123">Steuerelemente geben Ihnen eine Möglichkeit, die Anzeige der Daten weiter anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="a118f-124">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-124">This element is optional.</span></span> <span data-ttu-id="a118f-125">Eine Sicht kann eigene benutzerdefinierte Steuerelemente definieren, oder Sie kann allgemeine Steuerelemente verwenden, die von jeder Ansicht in der Formatierungs Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="a118f-126">Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="a118f-127">Das [widecontrol](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="a118f-128">Im vorherigen Beispiel wurde die-Sicht entworfen, um die [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) -Eigenschaft anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a118f-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="a118f-129">Ein Beispiel für eine komplette Formatierungs Datei, die eine einfache Breite Ansicht definiert, finden Sie unter [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="a118f-130">Bereitstellen von Definitionen für Ihre breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="a118f-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="a118f-131">Breite Ansichten können mithilfe der untergeordneten Elemente des [widecontrol](./widecontrol-element-format.md) -Elements eine oder mehrere Definitionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a118f-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="a118f-132">In der Regel hat eine Ansicht nur eine Definition.</span><span class="sxs-lookup"><span data-stu-id="a118f-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="a118f-133">Im folgenden Beispiel stellt die Sicht eine einzelne Definition bereit, in der der Wert der [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) -Eigenschaft angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="a118f-134">In einer breiten Ansicht kann der Wert einer Eigenschaft oder der Wert eines Skripts angezeigt werden (nicht im Beispiel dargestellt).</span><span class="sxs-lookup"><span data-stu-id="a118f-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="a118f-135">Die folgenden XML-Elemente können verwendet werden, um Definitionen für eine breite Ansicht bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="a118f-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="a118f-136">Das [widecontrol](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="a118f-137">Das [AutoSize](./autosize-element-for-widecontrol-format.md) -Element gibt an, ob die Spaltengröße und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="a118f-138">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-138">This element is optional.</span></span>

- <span data-ttu-id="a118f-139">Das [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -Element gibt die Anzahl der Spalten an, die in der breiten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="a118f-140">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-140">This element is optional.</span></span>

- <span data-ttu-id="a118f-141">Das [wideentries](./wideentries-element-for-widecontrol-format.md) -Element stellt die Definitionen der Sicht bereit.</span><span class="sxs-lookup"><span data-stu-id="a118f-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="a118f-142">In den meisten Fällen weist eine Ansicht nur eine Definition auf.</span><span class="sxs-lookup"><span data-stu-id="a118f-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="a118f-143">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a118f-143">This element is required.</span></span>

- <span data-ttu-id="a118f-144">Das [wideentry](./wideentry-element-for-widecontrol-format.md) -Element stellt eine Definition der Sicht bereit.</span><span class="sxs-lookup"><span data-stu-id="a118f-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="a118f-145">Mindestens ein " [wideentry](./wideentry-element-for-widecontrol-format.md) " ist erforderlich. Es gibt jedoch keine maximale Beschränkung für die Anzahl der Elemente, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="a118f-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="a118f-146">In den meisten Fällen weist eine Ansicht nur eine Definition auf.</span><span class="sxs-lookup"><span data-stu-id="a118f-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="a118f-147">Das [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Element gibt die Objekte an, die von einer bestimmten Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="a118f-148">Dieses Element ist optional und nur erforderlich, wenn Sie mehrere [wideentry](./wideentry-element-for-widecontrol-format.md) -Elemente definieren, die verschiedene-Objekte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a118f-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="a118f-149">Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="a118f-150">Im Gegensatz zu anderen Sicht Typen kann ein breites Steuerelement nur ein Element anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a118f-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="a118f-151">Das [propertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) -Element gibt die Eigenschaft an, deren Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="a118f-152">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a118f-153">Das [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -Element gibt das Skript an, dessen Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="a118f-154">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="a118f-155">Das [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) -Element gibt ein Muster an, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="a118f-156">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-156">This element is optional.</span></span>

<span data-ttu-id="a118f-157">Ein Beispiel für eine komplette Formatierungs Datei, die eine breite Sicht Definition definiert, finden Sie unter [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="a118f-158">Definieren der Objekte, die die Breite Ansicht verwenden</span><span class="sxs-lookup"><span data-stu-id="a118f-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="a118f-159">Es gibt zwei Möglichkeiten, um zu definieren, welche .NET-Objekte die Breite Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="a118f-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="a118f-160">Sie können das [viewselectedby](./viewselectedby-element-format.md) -Element verwenden, um die Objekte zu definieren, die von allen Definitionen der Sicht angezeigt werden können, oder Sie können das [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Element verwenden, um zu definieren, welche Objekte von einer bestimmten Definition der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="a118f-161">In den meisten Fällen verfügt eine Sicht nur über eine Definition, sodass Objekte normalerweise durch das [viewselectedby](./viewselectedby-element-format.md) -Element definiert werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="a118f-162">Im folgenden Beispiel wird gezeigt, wie die-Objekte definiert werden, die von der breiten Ansicht mithilfe der Elemente [viewselectedby](./viewselectedby-element-format.md) und [tygtame](./typename-element-for-viewselectedby-format.md) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a118f-163">Es gibt keine Beschränkung für die Anzahl der [tyname](./typename-element-for-viewselectedby-format.md) -Elemente, die Sie angeben können, und ihre Reihenfolge ist nicht signifikant.</span><span class="sxs-lookup"><span data-stu-id="a118f-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="a118f-164">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der breiten Ansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="a118f-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="a118f-165">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="a118f-166">Das [tygtame](./typename-element-for-viewselectedby-format.md) -Element gibt das von der Sicht angezeigte .net an.</span><span class="sxs-lookup"><span data-stu-id="a118f-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="a118f-167">Der voll qualifizierte .net-Typname ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a118f-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="a118f-168">Sie müssen mindestens einen Typ oder einen Auswahl Satz für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a118f-169">Ein Beispiel für eine komplette Formatierungs Datei finden Sie unter [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="a118f-170">Im folgenden Beispiel werden die Elemente [viewselectedby](./viewselectedby-element-format.md) und [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) verwendet.</span><span class="sxs-lookup"><span data-stu-id="a118f-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="a118f-171">Verwenden Sie Auswahl Sätze, bei denen Sie über einen zugehörigen Satz von Objekten verfügen, die mithilfe mehrerer Sichten angezeigt werden, z. b. Wenn Sie eine breite Ansicht und eine Tabellenansicht für dieselben Objekte definieren.</span><span class="sxs-lookup"><span data-stu-id="a118f-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="a118f-172">Weitere Informationen zum Erstellen eines Auswahl Satzes finden Sie unter Definieren von [Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="a118f-173">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der breiten Ansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="a118f-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="a118f-174">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="a118f-175">Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element gibt eine Gruppe von-Objekten an, die von der Sicht angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="a118f-176">Sie müssen mindestens einen Auswahl Satz oder-Typ für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="a118f-177">Im folgenden Beispiel wird gezeigt, wie die-Objekte, die durch eine bestimmte Definition der breiten Ansicht angezeigt werden, mithilfe des [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Elements definiert werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="a118f-178">Mit diesem Element können Sie den .NET-Typnamen des Objekts, einen Auswahl Satz von Objekten oder eine Auswahlbedingung angeben, die angibt, wann die Definition verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="a118f-179">Weitere Informationen zum Erstellen von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="a118f-180">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von einer bestimmten Definition der breiten Ansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="a118f-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="a118f-181">Das [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Element definiert, welche Objekte von der Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="a118f-182">Das [tykame](./typename-element-for-viewselectedby-format.md) -Element gibt das .net an, das von der Definition angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="a118f-183">Wenn Sie dieses Element verwenden, ist der voll qualifizierte .net-Typname erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a118f-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="a118f-184">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a118f-185">Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element (nicht angezeigt) gibt eine Gruppe von Objekten an, die von dieser Definition angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="a118f-186">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="a118f-187">Das [selectioncondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) -Element (nicht angezeigt) gibt eine Bedingung an, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="a118f-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="a118f-188">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="a118f-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="a118f-189">Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="a118f-190">Anzeigen von Gruppen von Objekten in einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="a118f-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="a118f-191">Sie können die Objekte, die von der breiten Ansicht angezeigt werden, in Gruppen aufteilen.</span><span class="sxs-lookup"><span data-stu-id="a118f-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="a118f-192">Dies bedeutet nicht, dass Sie eine Gruppe definieren, sondern nur, dass Windows PowerShell eine neue Gruppe startet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="a118f-193">Im folgenden Beispiel wird eine neue Gruppe immer dann gestartet, wenn sich der Wert der [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) -Eigenschaft ändert.</span><span class="sxs-lookup"><span data-stu-id="a118f-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="a118f-194">Die folgenden XML-Elemente werden verwendet, um zu definieren, wann eine Gruppe gestartet wird:</span><span class="sxs-lookup"><span data-stu-id="a118f-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="a118f-195">Das [GroupBy](./groupby-element-for-view-format.md) -Element definiert die Eigenschaft oder das Skript, das die neue Gruppe startet und definiert, wie die Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="a118f-196">Das [propertyName](./propertyname-element-for-groupby-format.md) -Element gibt die Eigenschaft an, die eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="a118f-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="a118f-197">Sie müssen eine Eigenschaft oder ein Skript angeben, um die Gruppe zu starten, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="a118f-198">Das [ScriptBlock](./scriptblock-element-for-groupby-format.md) -Element gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="a118f-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="a118f-199">Sie müssen ein Skript oder eine Eigenschaft angeben, um die Gruppe zu starten, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="a118f-200">Das [Label](./label-element-for-groupby-format.md) -Element definiert eine Bezeichnung, die am Anfang jeder Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="a118f-201">Zusätzlich zu dem Text, der von diesem Element angegeben wird, zeigt Windows PowerShell den Wert an, der die neue Gruppe ausgelöst hat, und fügt vor und nach der Bezeichnung eine leere Zeile hinzu.</span><span class="sxs-lookup"><span data-stu-id="a118f-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="a118f-202">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-202">This element is optional.</span></span>

- <span data-ttu-id="a118f-203">Das [CustomControl](./customcontrol-element-for-groupby-format.md) -Element definiert ein Steuerelement, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="a118f-204">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-204">This element is optional.</span></span>

- <span data-ttu-id="a118f-205">Das [customcontrolname](./customcontrolname-element-for-groupby-format.md) -Element gibt ein Common-oder View-Steuerelement an, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="a118f-206">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="a118f-206">This element is optional.</span></span>

<span data-ttu-id="a118f-207">Ein Beispiel für eine komplette Formatierungs Datei, die Gruppen definiert, finden Sie unter [Wide View (GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="a118f-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="a118f-208">Using-Format</span><span class="sxs-lookup"><span data-stu-id="a118f-208">Using Format Strings</span></span>

<span data-ttu-id="a118f-209">Formatierungs Zeichenfolgen können einer breiten Ansicht hinzugefügt werden, um die Anzeige der Daten weiter zu definieren.</span><span class="sxs-lookup"><span data-stu-id="a118f-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="a118f-210">Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="a118f-211">Die folgenden XML-Elemente können verwendet werden, um ein Format Muster anzugeben:</span><span class="sxs-lookup"><span data-stu-id="a118f-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="a118f-212">Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="a118f-213">Das [propertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) -Element gibt die Eigenschaft an, deren Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="a118f-214">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="a118f-215">Das Format [String](./formatstring-element-for-wideitem-for-widecontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="a118f-216">Das [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="a118f-217">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="a118f-218">Im folgenden Beispiel wird die `ToString`-Methode aufgerufen, um den Wert des Skripts zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="a118f-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="a118f-219">Skripts können beliebige Methoden eines Objekts aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="a118f-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="a118f-220">Wenn ein Objekt über eine-Methode verfügt, z. b. `ToString`, die Formatierungs Parameter hat, kann das Skript daher diese Methode zum Formatieren des Ausgabe Werts des Skripts aufruft.</span><span class="sxs-lookup"><span data-stu-id="a118f-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="a118f-221">Das folgende XML-Element kann verwendet werden, um die `ToString`-Methode aufrufen:</span><span class="sxs-lookup"><span data-stu-id="a118f-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="a118f-222">Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a118f-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="a118f-223">Das [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a118f-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="a118f-224">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a118f-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a118f-225">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a118f-225">See Also</span></span>

[<span data-ttu-id="a118f-226">Breite Ansicht (Basic)</span><span class="sxs-lookup"><span data-stu-id="a118f-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="a118f-227">Breite Ansicht (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="a118f-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="a118f-228">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a118f-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
