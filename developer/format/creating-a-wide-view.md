---
title: Erstellen eine Breite Ansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066718"
---
# <a name="creating-a-wide-view"></a><span data-ttu-id="5a6d4-102">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="5a6d4-102">Creating a Wide View</span></span>

<span data-ttu-id="5a6d4-103">Eine Breite Ansicht zeigt einen einzelnen Wert für jedes Objekt, das angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-103">A wide view displays a single value for each object that is displayed.</span></span> <span data-ttu-id="5a6d4-104">Der angezeigte Wert möglich den Wert einer Objekteigenschaft .NET oder der Wert von einem Skript.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-104">The displayed value can be the value of a .NET object property or the value of a script.</span></span> <span data-ttu-id="5a6d4-105">Es wird standardmäßig keine Bezeichnung oder Header für diese Sicht.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-105">By default, there is no label or header for this view.</span></span>

## <a name="a-wide-view-display"></a><span data-ttu-id="5a6d4-106">Eine Breite Ansicht anzeigen</span><span class="sxs-lookup"><span data-stu-id="5a6d4-106">A Wide View Display</span></span>

<span data-ttu-id="5a6d4-107">Das folgende Beispiel zeigt, wie Windows PowerShell zeigt die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) -Objekt, das von zurückgegeben wird die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet aus, wenn die Ausgabe, um weitergeleitet werden die [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-107">The following example shows how Windows PowerShell displays the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object that is returned by the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet when its output is piped to the [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet.</span></span> <span data-ttu-id="5a6d4-108">(Standardmäßig die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -Cmdlet wird eine Tabellenansicht zurückgegeben.) In diesem Beispiel werden die beiden Spalten verwendet, um den Namen des Prozesses für jedes zurückgegebene Objekt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-108">(By default, the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns a table view.) In this example, the two columns are used to display the name of the process for each returned object.</span></span> <span data-ttu-id="5a6d4-109">Der Name der Eigenschaft des Objekts nicht angezeigt wird, nur den Wert der Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-109">The name of the object's property is not displayed, only the value of the property.</span></span>

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

## <a name="defining-the-wide-view"></a><span data-ttu-id="5a6d4-110">Definieren die Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="5a6d4-110">Defining the Wide View</span></span>

<span data-ttu-id="5a6d4-111">Das folgende XML zeigt das Schema Breite Ansicht, für die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-111">The following XML shows the wide view schema for the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="5a6d4-112">Die folgende XML-Elemente werden verwendet, um eine Breite Ansicht zu definieren:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-112">The following XML elements are used to define a wide view:</span></span>

- <span data-ttu-id="5a6d4-113">Die [Ansicht](./view-element-format.md) Element ist das übergeordnete Element der breiten Ansicht.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-113">The [View](./view-element-format.md) element is the parent element of the wide view.</span></span> <span data-ttu-id="5a6d4-114">(Dies ist das über dasselbe übergeordnete Element für die Tabelle, eine Liste und ein benutzerdefiniertes Steuerelement Ansichten).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-114">(This is the same parent element for the table, list, and custom control views.)</span></span>

- <span data-ttu-id="5a6d4-115">Die [Namen](./name-element-for-view-format.md) Element gibt den Namen der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-115">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="5a6d4-116">Dieses Element ist für alle Ansichten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-116">This element is required for all views.</span></span>

- <span data-ttu-id="5a6d4-117">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="5a6d4-118">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-118">This element is required.</span></span>

- <span data-ttu-id="5a6d4-119">Die [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wenn eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-119">The [GroupBy](./groupby-element-for-view-format.md) element defines when a new group of objects is displayed.</span></span> <span data-ttu-id="5a6d4-120">Eine neue Gruppe wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-120">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="5a6d4-121">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-121">This element is optional.</span></span>

- <span data-ttu-id="5a6d4-122">Die [Steuerelemente](./controls-element-for-view-format.md) Elemente definiert, das die benutzerdefinierten Steuerelemente, die von der breiten Ansicht definiert sind.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-122">The [Controls](./controls-element-for-view-format.md) elements defines the custom controls that are defined by the wide view.</span></span> <span data-ttu-id="5a6d4-123">Steuerelemente bieten Ihnen eine Möglichkeit, festzulegen, wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-123">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="5a6d4-124">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-124">This element is optional.</span></span> <span data-ttu-id="5a6d4-125">Eine Ansicht kann eine eigene benutzerdefinierte Steuerelemente zu definieren, oder sie können allgemeine Steuerelemente, die von einer beliebigen Ansicht in der Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-125">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="5a6d4-126">Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-126">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="5a6d4-127">Die [WideControl](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-127">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span> <span data-ttu-id="5a6d4-128">Im vorherigen Beispiel dient zum Anzeigen die Ansicht der [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-128">In the preceding example, the view is designed to display the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span>

<span data-ttu-id="5a6d4-129">Ein Beispiel für eine vollständige Formatierung-Datei, die eine einfache Breite Ansicht definiert, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-129">For an example of a complete formatting file that defines a simple wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="providing-definitions-for-your-wide-view"></a><span data-ttu-id="5a6d4-130">Bereitstellen von Definitionen für die Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="5a6d4-130">Providing Definitions for Your Wide View</span></span>

<span data-ttu-id="5a6d4-131">Breite Ansichten können eine oder mehrere Definitionen bereitstellen, indem die untergeordneten Elemente des mithilfe der [WideControl](./widecontrol-element-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-131">Wide views can provide one or more definitions by using the child elements of the [WideControl](./widecontrol-element-format.md) element.</span></span> <span data-ttu-id="5a6d4-132">Eine Sicht wird in der Regel nur eine Definition verfügen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-132">Typically, a view will have only one definition.</span></span> <span data-ttu-id="5a6d4-133">Im folgenden Beispiel ist die Ansicht bietet eine einzige Definition, die den Wert der [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-133">In the following example, the view provides a single definition that displays the value of the [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) property.</span></span> <span data-ttu-id="5a6d4-134">Eine Breite Ansicht kann es sich um den Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel gezeigt) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-134">A wide view can display the value of a property or the value of a script (not shown in the example).</span></span>

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

<span data-ttu-id="5a6d4-135">Die folgende XML-Elemente können verwendet werden, um Definitionen für eine Breite Ansicht bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-135">The following XML elements can be used to provide definitions for a wide view:</span></span>

- <span data-ttu-id="5a6d4-136">Die [WideControl](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-136">The [WideControl](./widecontrol-element-format.md) element and its child elements define what is displayed in the view.</span></span>

- <span data-ttu-id="5a6d4-137">Die [AutoSize](./autosize-element-for-widecontrol-format.md) Element gibt an, ob die Größe der Spalte und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-137">The [AutoSize](./autosize-element-for-widecontrol-format.md) element specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span> <span data-ttu-id="5a6d4-138">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-138">This element is optional.</span></span>

- <span data-ttu-id="5a6d4-139">Die [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) Element gibt die Anzahl der Spalten in der breiten Ansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-139">The [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element specifies the number of columns displayed in the wide view.</span></span> <span data-ttu-id="5a6d4-140">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-140">This element is optional.</span></span>

- <span data-ttu-id="5a6d4-141">Die [WideEntries](./wideentries-element-for-widecontrol-format.md) Element enthält die Definitionen der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-141">The [WideEntries](./wideentries-element-for-widecontrol-format.md) element provides the definitions of the view.</span></span> <span data-ttu-id="5a6d4-142">In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-142">In most cases, a view will have only one definition.</span></span> <span data-ttu-id="5a6d4-143">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-143">This element is required.</span></span>

- <span data-ttu-id="5a6d4-144">Die [WideEntry](./wideentry-element-for-widecontrol-format.md) Element enthält eine Definition der Sicht.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-144">The [WideEntry](./wideentry-element-for-widecontrol-format.md) element provides a definition of the view.</span></span> <span data-ttu-id="5a6d4-145">Mindestens ein [WideEntry](./wideentry-element-for-widecontrol-format.md) ist erforderlich; Es ist jedoch nicht begrenzt auf die Anzahl der Elemente, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-145">At least one [WideEntry](./wideentry-element-for-widecontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="5a6d4-146">In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-146">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="5a6d4-147">Die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) Element gibt an, die Objekte, die von einer bestimmten Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-147">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="5a6d4-148">Dieses Element ist optional und ist nur erforderlich, wenn Sie mehrere definieren [WideEntry](./wideentry-element-for-widecontrol-format.md) Elemente, die verschiedene Objekte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-148">This element is optional and is needed only when you define multiple [WideEntry](./wideentry-element-for-widecontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="5a6d4-149">Die [WideItem](./wideitem-element-for-widecontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-149">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span> <span data-ttu-id="5a6d4-150">Im Gegensatz zu anderen Ansichten kann ein Breite-Steuerelement nur ein Element anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-150">In contrast to other types of views, a wide control can display only one item.</span></span>

- <span data-ttu-id="5a6d4-151">Die [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) Element gibt die Eigenschaft, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-151">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="5a6d4-152">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-152">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="5a6d4-153">Die ["scriptblock"](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Element gibt das Skript an, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-153">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="5a6d4-154">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-154">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="5a6d4-155">Die [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) Element gibt ein Muster, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-155">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a pattern that is used to display the data.</span></span> <span data-ttu-id="5a6d4-156">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-156">This element is optional.</span></span>

<span data-ttu-id="5a6d4-157">Ein Beispiel für eine vollständige Formatierung-Datei, die eine Breite Ansichtsdefinition definiert, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-157">For an example of a complete formatting file that defines a wide view definition, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="defining-the-objects-that-use-the-wide-view"></a><span data-ttu-id="5a6d4-158">Definieren die Objekte, die die Breite Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-158">Defining the Objects That Use the Wide View</span></span>

<span data-ttu-id="5a6d4-159">Es gibt zwei Möglichkeiten, die definieren, welche .NET Objekte auf die Breite Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-159">There are two ways to define which .NET objects use the wide view.</span></span> <span data-ttu-id="5a6d4-160">Können Sie die [ViewSelectedBy](./viewselectedby-element-format.md) Element, das die Objekte zu definieren, die durch alle Definitionen oder der Ansicht angezeigt werden können. die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -Element zum definieren, welche Objekte angezeigt werden ein spezifische Definition der Sicht.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-160">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="5a6d4-161">In den meisten Fällen eine Ansicht hat nur eine Definition, sodass Objekte in der Regel, indem definiert werden die [ViewSelectedBy](./viewselectedby-element-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-161">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="5a6d4-162">Das folgende Beispiel zeigt, wie Sie die Objekte zu definieren, die mithilfe der Breite Ansicht angezeigt werden die [ViewSelectedBy](./viewselectedby-element-format.md) und [TypeName](./typename-element-for-viewselectedby-format.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-162">The following example shows how to define the objects that are displayed by the wide view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="5a6d4-163">Es gibt keine Beschränkung der Anzahl der [TypeName](./typename-element-for-viewselectedby-format.md) Elementen, die Sie angeben können und ihre Reihenfolge ist nicht von Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-163">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="5a6d4-164">Die folgenden XML-Elemente können verwendet werden, um die Objekte angeben, die von der breiten Ansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-164">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="5a6d4-165">Die [ViewSelectedBy](./viewselectedby-element-format.md) Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-165">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="5a6d4-166">Die [TypeName](./typename-element-for-viewselectedby-format.md) Element gibt an, die .NET, die von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-166">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the view.</span></span> <span data-ttu-id="5a6d4-167">Der vollqualifizierte Typname des .NET ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-167">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="5a6d4-168">Geben Sie mindestens einen Typ oder Auswahl für die Ansicht festgelegt, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-168">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="5a6d4-169">Ein Beispiel für eine vollständige Formatierungsdatei, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-169">For an example of a complete formatting file, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

<span data-ttu-id="5a6d4-170">Im folgenden Beispiel wird die [ViewSelectedBy](./viewselectedby-element-format.md) und [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-170">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="5a6d4-171">Verwenden Sie die Auswahl legt, haben eine zusammengehörige Gruppe von Objekten, die über mehrere Ansichten, z. B. Wenn Sie eine Breite Ansicht definieren und eine Tabellenansicht für diese Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-171">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a wide view and a table view for the same objects.</span></span> <span data-ttu-id="5a6d4-172">Weitere Informationen dazu, wie Sie einen Auswahlsatz zu erstellen, finden Sie unter [definieren Auswahl legt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-172">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

<span data-ttu-id="5a6d4-173">Die folgenden XML-Elemente können verwendet werden, um die Objekte angeben, die von der breiten Ansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-173">The following XML elements can be used to specify the objects that are used by the wide view:</span></span>

- <span data-ttu-id="5a6d4-174">Die [ViewSelectedBy](./viewselectedby-element-format.md) Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-174">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the wide view.</span></span>

- <span data-ttu-id="5a6d4-175">Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element gibt einen Satz von Objekten, die von der Ansicht angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-175">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="5a6d4-176">Geben Sie mindestens einen Auswahlsatz oder Typ, für die Sicht, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-176">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="5a6d4-177">Das folgende Beispiel zeigt, wie die Objekte angezeigt, die von der breiten Ansicht mithilfe einer bestimmten Definition definiert die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-177">The following example shows how to define the objects displayed by a specific definition of the wide view using the [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element.</span></span> <span data-ttu-id="5a6d4-178">Verwenden dieses Element, können Sie den Namen des Objekts, einer Auswahlsatz von Objekten oder eine auswahlbedingung, die angibt, wenn die Definition verwendet wird angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-178">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="5a6d4-179">Weitere Informationen dazu, wie Sie eine Auswahl Bedingungen zu erstellen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-179">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

<span data-ttu-id="5a6d4-180">Die folgende XML-Elemente können verwendet werden, die Objekte an, die von einer bestimmten Definition der breiten Ansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-180">The following XML elements can be used to specify the objects that are used by a specific definition of the wide view:</span></span>

- <span data-ttu-id="5a6d4-181">Die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) Element definiert, welche Objekte durch die Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-181">The [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="5a6d4-182">Die [TypeName](./typename-element-for-viewselectedby-format.md) Element gibt an, die .NET, die durch die Definition angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-182">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET that is displayed by the definition.</span></span> <span data-ttu-id="5a6d4-183">Bei Verwendung dieses Elements ist der vollqualifizierte Typname des .NET erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-183">When using this element the fully qualified .NET type name is required.</span></span> <span data-ttu-id="5a6d4-184">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-184">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="5a6d4-185">Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element (nicht dargestellt) gibt einen Satz von Objekten, die von dieser Definition angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-185">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="5a6d4-186">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-186">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="5a6d4-187">Die [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) Element (nicht dargestellt) gibt an, eine Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-187">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="5a6d4-188">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-188">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="5a6d4-189">Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-189">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="displaying-groups-of-objects-in-a-wide-view"></a><span data-ttu-id="5a6d4-190">Anzeigen von Gruppen von Objekten in eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="5a6d4-190">Displaying Groups of objects in a Wide View</span></span>

<span data-ttu-id="5a6d4-191">Sie können die Objekte trennen, die von der breiten Ansicht in Gruppen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-191">You can separate the objects that are displayed by the wide view into groups.</span></span> <span data-ttu-id="5a6d4-192">Dies bedeutet nicht, dass Sie eine Gruppe definieren nur die eine neue Gruppe, die Windows PowerShell wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-192">This does not mean that you define a group, only that Windows PowerShell starts a new group whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="5a6d4-193">Im folgenden Beispiel wird eine neue Gruppe gestartet Wenn der Wert des der [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) eigenschaftenänderungen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-193">In the following example, a new group is started whenever the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="5a6d4-194">Die folgende XML-Elemente werden zum definieren, wenn Sie eine Gruppe gestartet wird:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-194">The following XML elements are used to define when a group is started:</span></span>

- <span data-ttu-id="5a6d4-195">Die [GroupBy](./groupby-element-for-view-format.md) -Element definiert die Eigenschaft oder ein Skript, das die neue Gruppe gestartet und definiert, wie die Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-195">The [GroupBy](./groupby-element-for-view-format.md) element defines the property or script that starts the new group and defines how the group is displayed.</span></span>

- <span data-ttu-id="5a6d4-196">Die [PropertyName](./propertyname-element-for-groupby-format.md) Element gibt die Eigenschaft, die eine neue Gruppe wird gestartet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-196">The [PropertyName](./propertyname-element-for-groupby-format.md) element specifies the property that starts a new group whenever its value changes.</span></span> <span data-ttu-id="5a6d4-197">Sie müssen eine Eigenschaft oder ein Skript zum Starten der Gruppe angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-197">You must specify a property or script to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="5a6d4-198">Die ["scriptblock"](./scriptblock-element-for-groupby-format.md) Element gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-198">The [ScriptBlock](./scriptblock-element-for-groupby-format.md) element specifies the script that starts a new group whenever its value changes.</span></span> <span data-ttu-id="5a6d4-199">Sie müssen angeben, ein Skript oder eine Eigenschaft, um die Gruppe zu starten, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-199">You must specify a script or property to start the group, but you cannot specify both.</span></span>

- <span data-ttu-id="5a6d4-200">Die [Bezeichnung](./label-element-for-groupby-format.md) -Element definiert eine Bezeichnung, die am Anfang der Gruppe "Jeder" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-200">The [Label](./label-element-for-groupby-format.md) element defines a label that is displayed at the beginning of each group.</span></span> <span data-ttu-id="5a6d4-201">Zusätzlich zu den Text, der von diesem Element angegeben wird wird der Wert, der die neue Gruppe ausgelöst und fügt eine leere Zeile vor und nach der die Bezeichnung von Windows PowerShell angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-201">In addition to the text specified by this element, Windows PowerShell displays the value that triggered the new group and adds a blank line before and after the label.</span></span> <span data-ttu-id="5a6d4-202">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-202">This element is optional.</span></span>

- <span data-ttu-id="5a6d4-203">Die [CustomControl](./customcontrol-element-for-groupby-format.md) -Element definiert ein Steuerelement, das zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-203">The [CustomControl](./customcontrol-element-for-groupby-format.md) element defines a control that is used to display the data.</span></span> <span data-ttu-id="5a6d4-204">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-204">This element is optional.</span></span>

- <span data-ttu-id="5a6d4-205">Die [CustomControlName](./customcontrolname-element-for-groupby-format.md) Element gibt einen allgemeinen oder Steuerelements, die zum Anzeigen der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-205">The [CustomControlName](./customcontrolname-element-for-groupby-format.md) element specifies a common or view control that is used to display the data.</span></span> <span data-ttu-id="5a6d4-206">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-206">This element is optional.</span></span>

<span data-ttu-id="5a6d4-207">Ein Beispiel für eine vollständige Formatierung-Datei, die Gruppen definiert, finden Sie unter [Breite Ansicht (-GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="5a6d4-207">For an example of a complete formatting file that defines groups, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="5a6d4-208">Verwenden von Formatzeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="5a6d4-208">Using Format Strings</span></span>

<span data-ttu-id="5a6d4-209">Formatieren von Zeichenfolgen können hinzugefügt werden, um eine Breite Ansicht genauer definieren, wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-209">Formatting strings can be added to a wide view to further define how the data is displayed.</span></span> <span data-ttu-id="5a6d4-210">Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-210">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

<span data-ttu-id="5a6d4-211">Die folgende XML-Elemente können verwendet werden, ein Formatmuster angeben:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-211">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="5a6d4-212">Die [WideItem](./wideitem-element-for-widecontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-212">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="5a6d4-213">Die [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) Element gibt die Eigenschaft, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-213">The [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) element specifies the property whose value is displayed by the view.</span></span> <span data-ttu-id="5a6d4-214">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-214">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="5a6d4-215">Die [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="5a6d4-215">The [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed in the view</span></span>

- <span data-ttu-id="5a6d4-216">Die ["scriptblock"](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-216">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="5a6d4-217">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-217">You must specify either a script or a property, but you cannot specify both.</span></span>

<span data-ttu-id="5a6d4-218">Im folgenden Beispiel die `ToString` aufgerufen, um den Wert des Skripts zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-218">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="5a6d4-219">Skripts können auf jede Methode eines Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-219">Scripts can call any method of an object.</span></span> <span data-ttu-id="5a6d4-220">Daher verfügt ein Objekt eine Methode, wie z. B. `ToString`über Formatierung Parameter verfügt, das Skript kann diese Methode zum Formatieren des Werts der Ausgabe des Skripts aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-220">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

<span data-ttu-id="5a6d4-221">Das folgende XML-Element kann zum Aufrufen der `ToString` Methode:</span><span class="sxs-lookup"><span data-stu-id="5a6d4-221">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="5a6d4-222">Die [WideItem](./wideitem-element-for-widecontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-222">The [WideItem](./wideitem-element-for-widecontrol-format.md) element specifies the data that is displayed by the view.</span></span>

- <span data-ttu-id="5a6d4-223">Die ["scriptblock"](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-223">The [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) element (not shown) specifies the script whose value is displayed by the view.</span></span> <span data-ttu-id="5a6d4-224">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="5a6d4-224">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a6d4-225">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5a6d4-225">See Also</span></span>

[<span data-ttu-id="5a6d4-226">Breite Ansicht (Basic)</span><span class="sxs-lookup"><span data-stu-id="5a6d4-226">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="5a6d4-227">Breite Ansicht (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="5a6d4-227">Wide View (GroupBy)</span></span>](./wide-view-groupby.md)

[<span data-ttu-id="5a6d4-228">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a6d4-228">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
