---
title: Erstellen einer Tabellenansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363409"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="66bbd-102">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="66bbd-102">Creating a Table View</span></span>

<span data-ttu-id="66bbd-103">Eine Tabellen Sicht zeigt Daten in einer oder mehreren Spalten an.</span><span class="sxs-lookup"><span data-stu-id="66bbd-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="66bbd-104">Jede Zeile in der Tabelle stellt ein .NET-Objekt dar, und jede Spalte der Tabelle stellt eine Eigenschaft des Objekts oder einen Skript Wert dar.</span><span class="sxs-lookup"><span data-stu-id="66bbd-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="66bbd-105">Sie können eine Tabellen Sicht definieren, in der alle Eigenschaften eines Objekts oder eine Teilmenge der Eigenschaften eines Objekts angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="66bbd-106">Anzeige der Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="66bbd-106">A Table View Display</span></span>

<span data-ttu-id="66bbd-107">Das folgende Beispiel zeigt, wie Windows PowerShell das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt anzeigt, das vom Cmdlet " [Get-Service](/powershell/module/microsoft.powershell.management/get-service) " zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="66bbd-108">Für dieses Objekt hat Windows PowerShell eine Tabellen Sicht definiert, in der die `Status`-Eigenschaft, die `Name`-Eigenschaft (diese Eigenschaft ist eine Alias Eigenschaft für die `ServiceName`-Eigenschaft) und die `DisplayName`-Eigenschaft angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="66bbd-109">Jede Zeile in der Tabelle stellt ein vom Cmdlet zurück gegebenes Objekt dar.</span><span class="sxs-lookup"><span data-stu-id="66bbd-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="66bbd-110">Definieren der Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="66bbd-110">Defining the Table View</span></span>

<span data-ttu-id="66bbd-111">Der folgende XML-Code zeigt das Tabellen Ansichts Schema zum Anzeigen von [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="66bbd-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="66bbd-112">Sie müssen jede Eigenschaft angeben, die in der Tabellenansicht angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="66bbd-112">You must specify each property that you want displayed in the table view.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="66bbd-113">Die folgenden XML-Elemente werden verwendet, um eine Listenansicht zu definieren:</span><span class="sxs-lookup"><span data-stu-id="66bbd-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="66bbd-114">Das [View](./view-element-format.md) -Element ist das übergeordnete Element der Tabellen Sicht.</span><span class="sxs-lookup"><span data-stu-id="66bbd-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="66bbd-115">(Dies ist dasselbe übergeordnete Element für die Listen-, Wide-und Custom-Steuerelement Sichten.)</span><span class="sxs-lookup"><span data-stu-id="66bbd-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="66bbd-116">Das [Name](./name-element-for-view-format.md) -Element gibt den Namen der Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="66bbd-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="66bbd-117">Dieses Element ist für alle Sichten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66bbd-117">This element is required for all views.</span></span>

- <span data-ttu-id="66bbd-118">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="66bbd-119">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66bbd-119">This element is required.</span></span>

- <span data-ttu-id="66bbd-120">Das [GroupBy](./groupby-element-for-view-format.md) -Element (in diesem Beispiel nicht gezeigt) definiert, wann eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="66bbd-121">Eine neue Gruppe wird immer dann gestartet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="66bbd-122">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-122">This element is optional.</span></span>

- <span data-ttu-id="66bbd-123">Das [Controls](./controls-element-for-view-format.md) -Element (in diesem Beispiel nicht gezeigt) definiert die benutzerdefinierten Steuerelemente, die von der Tabellenansicht definiert werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="66bbd-124">Steuerelemente geben Ihnen eine Möglichkeit, die Anzeige der Daten weiter anzugeben.</span><span class="sxs-lookup"><span data-stu-id="66bbd-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="66bbd-125">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-125">This element is optional.</span></span> <span data-ttu-id="66bbd-126">Eine Sicht kann eigene benutzerdefinierte Steuerelemente definieren, oder Sie kann allgemeine Steuerelemente verwenden, die von jeder Ansicht in der Formatierungs Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="66bbd-127">Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="66bbd-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="66bbd-128">Das [hidetableheaders](./hidetableheaders-element-format.md) -Element (in diesem Beispiel nicht angezeigt) gibt an, dass in der Tabelle keine Bezeichnungen am Anfang der Tabelle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="66bbd-129">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-129">This element is optional.</span></span>

- <span data-ttu-id="66bbd-130">Das [tablecontrol](./tablecontrol-element-format.md) -Element, das die Header-und Zeilen Informationen der Tabelle definiert.</span><span class="sxs-lookup"><span data-stu-id="66bbd-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="66bbd-131">Ähnlich wie alle anderen Sichten kann eine Tabellenansicht die Werte der Objekteigenschaften oder von Skripts generierten Werte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="66bbd-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="66bbd-132">Definieren von Spalten Headern</span><span class="sxs-lookup"><span data-stu-id="66bbd-132">Defining Column Headers</span></span>

1. <span data-ttu-id="66bbd-133">Das [tableHeaders](./tableheaders-element-format.md) -Element und seine untergeordneten Elemente definieren, was am oberen Rand der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="66bbd-134">Das [tablecolumnheader](./tablecolumnheader-element-format.md) -Element definiert, was oben in einer Spalte der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="66bbd-135">Geben Sie diese Elemente in der Reihenfolge an, in der die Header angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="66bbd-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="66bbd-136">Es gibt keine Beschränkung für die Anzahl dieser Elemente, die Sie verwenden können, aber die Anzahl der [tablecolumnheader](./tablecolumnheader-element-format.md) -Elemente in der Tabellenansicht muss der Anzahl der [tablerowentry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) -Elemente entsprechen, die Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="66bbd-137">Das [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt den Text an, der angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="66bbd-138">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-138">This element is optional.</span></span>

4. <span data-ttu-id="66bbd-139">Das [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt die Breite (in Zeichen) der Spalte an.</span><span class="sxs-lookup"><span data-stu-id="66bbd-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="66bbd-140">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-140">This element is optional.</span></span>

5. <span data-ttu-id="66bbd-141">Das [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt an, wie die Bezeichnung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="66bbd-142">Die Bezeichnung kann Links, rechts oder zentriert ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="66bbd-143">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="66bbd-144">Definieren der Tabellenzeilen</span><span class="sxs-lookup"><span data-stu-id="66bbd-144">Defining the Table Rows</span></span>

<span data-ttu-id="66bbd-145">Tabellen Sichten können eine oder mehrere Definitionen bereitstellen, die angeben, welche Daten in den Zeilen der Tabelle angezeigt werden, indem die untergeordneten Elemente des [tablerowentries](./tablerowentries-element-for-tablecontrol-format.md) -Elements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="66bbd-146">Beachten Sie, dass Sie mehrere Definitionen für die Zeilen der Tabelle angeben können, die Header für die Zeilen jedoch unverändert bleiben, unabhängig davon, welche Zeilen Definition verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="66bbd-147">In der Regel enthält eine Tabelle nur eine Definition.</span><span class="sxs-lookup"><span data-stu-id="66bbd-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="66bbd-148">Im folgenden Beispiel stellt die Sicht eine einzelne Definition bereit, in der die Werte mehrerer Eigenschaften von [System. Diagnostics. Process angezeigt werden? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="66bbd-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="66bbd-149">In einer Tabellen Sicht kann der Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel) in den Zeilen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

<span data-ttu-id="66bbd-150">Die folgenden XML-Elemente können verwendet werden, um Definitionen für eine Zeile bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="66bbd-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="66bbd-151">Das [tablerowentries](./tablerowentries-element-for-tablecontrol-format.md) -Element und seine untergeordneten Elemente definieren, was in den Zeilen der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="66bbd-152">Das [tablerowentry](./listentry-element-for-listcontrol-format.md) -Element stellt eine Definition der Zeile bereit.</span><span class="sxs-lookup"><span data-stu-id="66bbd-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="66bbd-153">Mindestens ein [tablerowentry](./listentry-element-for-listcontrol-format.md) ist erforderlich. Es gibt jedoch keine maximale Beschränkung für die Anzahl der Elemente, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="66bbd-154">In den meisten Fällen weist eine Ansicht nur eine Definition auf.</span><span class="sxs-lookup"><span data-stu-id="66bbd-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="66bbd-155">Das [entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -Element gibt die Objekte an, die von einer bestimmten Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="66bbd-156">Dieses Element ist optional und wird nur benötigt, wenn Sie mehrere [tablerowentry](./listentry-element-for-listcontrol-format.md) -Elemente definieren, die verschiedene-Objekte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="66bbd-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="66bbd-157">Das [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) -Element gibt an, dass der Text, der die Spaltenbreite überschreitet, in der nächsten Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="66bbd-158">Standardmäßig wird Text, der die Spaltenbreite überschreitet, abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="66bbd-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="66bbd-159">Das [tablecolumnitems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -Element definiert die Eigenschaften oder Skripts, deren Werte in der Zeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="66bbd-160">Das [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="66bbd-161">Für jede Spalte der Zeile ist ein [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66bbd-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="66bbd-162">Der erste Eintrag wird in der ersten Spalte angezeigt, der zweite Eintrag in der zweiten Spalte usw.</span><span class="sxs-lookup"><span data-stu-id="66bbd-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="66bbd-163">Das [propertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt die-Eigenschaft an, deren Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="66bbd-164">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="66bbd-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="66bbd-165">Das [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="66bbd-166">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="66bbd-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="66bbd-167">Das Format [String](./label-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="66bbd-168">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-168">This element is optional.</span></span>

- <span data-ttu-id="66bbd-169">Das [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt an, wie der Wert der Eigenschaft oder des Skripts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="66bbd-170">Der Wert kann Links, rechts oder zentriert ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="66bbd-171">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="66bbd-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="66bbd-172">Definieren der Objekte, die die Tabellenansicht verwenden</span><span class="sxs-lookup"><span data-stu-id="66bbd-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="66bbd-173">Es gibt zwei Möglichkeiten, um zu definieren, welche .NET-Objekte die Tabellenansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="66bbd-174">Sie können das [viewselectedby](./viewselectedby-element-format.md) -Element verwenden, um die Objekte zu definieren, die von allen Definitionen der Sicht angezeigt werden können, oder Sie können das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element verwenden, um zu definieren, welche Objekte von einer bestimmten Definition der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="66bbd-175">In den meisten Fällen verfügt eine Sicht nur über eine Definition, sodass Objekte normalerweise durch das [viewselectedby](./viewselectedby-element-format.md) -Element definiert werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="66bbd-176">Im folgenden Beispiel wird gezeigt, wie die Objekte definiert werden, die von der Tabellenansicht mithilfe der Elemente [viewselectedby](./viewselectedby-element-format.md) und [tygtame](./typename-element-for-viewselectedby-format.md) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="66bbd-177">Es gibt keine Beschränkung für die Anzahl der [tyname](./typename-element-for-viewselectedby-format.md) -Elemente, die Sie angeben können, und ihre Reihenfolge ist nicht signifikant.</span><span class="sxs-lookup"><span data-stu-id="66bbd-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="66bbd-178">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Tabellenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="66bbd-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="66bbd-179">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="66bbd-180">Das [tykame](./typename-element-for-viewselectedby-format.md) -Element gibt das .NET-Objekt an, das von der Sicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="66bbd-181">Der voll qualifizierte .net-Typname ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66bbd-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="66bbd-182">Sie müssen mindestens einen Typ oder einen Auswahl Satz für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="66bbd-183">Im folgenden Beispiel werden die Elemente [viewselectedby](./viewselectedby-element-format.md) und [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) verwendet.</span><span class="sxs-lookup"><span data-stu-id="66bbd-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="66bbd-184">Verwenden Sie Auswahl Sätze, bei denen Sie über einen zugehörigen Satz von Objekten verfügen, die mithilfe mehrerer Sichten angezeigt werden, z. b. Wenn Sie eine Listenansicht und eine Tabellenansicht für dieselben Objekte definieren.</span><span class="sxs-lookup"><span data-stu-id="66bbd-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="66bbd-185">Weitere Informationen zum Erstellen eines Auswahl Satzes finden Sie unter Definieren von [Auswahl Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="66bbd-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="66bbd-186">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="66bbd-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="66bbd-187">Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="66bbd-188">Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element gibt eine Gruppe von-Objekten an, die von der Sicht angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="66bbd-189">Sie müssen mindestens einen Auswahl Satz oder-Typ für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="66bbd-190">Im folgenden Beispiel wird gezeigt, wie die Objekte, die durch eine bestimmte Definition der Tabellenansicht angezeigt werden, mithilfe des [entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -Elements definiert werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="66bbd-191">Mit diesem Element können Sie den .NET-Typnamen des Objekts, einen Auswahl Satz von Objekten oder eine Auswahlbedingung angeben, die angibt, wann die Definition verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="66bbd-192">Weitere Informationen zum Erstellen von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="66bbd-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="66bbd-193">Wenn Sie mehrere Definitionen der Tabellenansicht erstellen, können Sie keine anderen Spaltenheader angeben.</span><span class="sxs-lookup"><span data-stu-id="66bbd-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="66bbd-194">Sie können nur angeben, was in den Zeilen der Tabelle angezeigt wird, z. b. welche Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="66bbd-195">Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von einer bestimmten Definition der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="66bbd-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="66bbd-196">Das [entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -Element definiert, welche Objekte von der Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="66bbd-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="66bbd-197">Das [tykame](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt das .NET-Objekt an, das von der Definition angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="66bbd-198">Wenn Sie dieses Element verwenden, ist der voll qualifizierte .net-Typname erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66bbd-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="66bbd-199">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="66bbd-200">Das [selectionsetname](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Gruppe von Objekten an, die von dieser Definition angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="66bbd-201">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="66bbd-202">Das [selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Bedingung an, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="66bbd-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="66bbd-203">Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="66bbd-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="66bbd-204">Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="66bbd-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="66bbd-205">Using-Format</span><span class="sxs-lookup"><span data-stu-id="66bbd-205">Using Format Strings</span></span>

<span data-ttu-id="66bbd-206">Formatierungs Zeichenfolgen können einer Ansicht hinzugefügt werden, um die Anzeige der Daten weiter zu definieren.</span><span class="sxs-lookup"><span data-stu-id="66bbd-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="66bbd-207">Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="66bbd-208">Die folgenden XML-Elemente können verwendet werden, um ein Format Muster anzugeben:</span><span class="sxs-lookup"><span data-stu-id="66bbd-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="66bbd-209">Das [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="66bbd-210">Für jede Spalte der Zeile ist ein [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66bbd-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="66bbd-211">Der erste Eintrag wird in der ersten Spalte angezeigt, der zweite Eintrag in der zweiten Spalte usw.</span><span class="sxs-lookup"><span data-stu-id="66bbd-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="66bbd-212">Das [propertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt die-Eigenschaft an, deren Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="66bbd-213">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="66bbd-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="66bbd-214">Das Format [String](./label-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="66bbd-215">Im folgenden Beispiel wird die `ToString`-Methode aufgerufen, um den Wert des Skripts zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="66bbd-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="66bbd-216">Skripts können beliebige Methoden eines Objekts aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="66bbd-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="66bbd-217">Wenn ein Objekt über eine-Methode verfügt, z. b. `ToString`, die Formatierungs Parameter hat, kann das Skript daher diese Methode zum Formatieren des Ausgabe Werts des Skripts aufruft.</span><span class="sxs-lookup"><span data-stu-id="66bbd-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="66bbd-218">Das folgende XML-Element kann verwendet werden, um die `ToString`-Methode aufrufen:</span><span class="sxs-lookup"><span data-stu-id="66bbd-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="66bbd-219">Das [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="66bbd-220">Für jede Spalte der Zeile ist ein [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element erforderlich.</span><span class="sxs-lookup"><span data-stu-id="66bbd-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="66bbd-221">Der erste Eintrag wird in der ersten Spalte angezeigt, der zweite Eintrag in der zweiten Spalte usw.</span><span class="sxs-lookup"><span data-stu-id="66bbd-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="66bbd-222">Das [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bbd-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="66bbd-223">Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="66bbd-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="66bbd-224">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="66bbd-224">See Also</span></span>

[<span data-ttu-id="66bbd-225">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="66bbd-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
