---
title: Erstellen eine Tabellensicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057364"
---
# <a name="creating-a-table-view"></a><span data-ttu-id="ca153-102">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="ca153-102">Creating a Table View</span></span>

<span data-ttu-id="ca153-103">Eine Tabellenansicht zeigt Daten in einer oder mehreren Spalten.</span><span class="sxs-lookup"><span data-stu-id="ca153-103">A table view displays data in one or more columns.</span></span> <span data-ttu-id="ca153-104">Jede Zeile in der Tabelle darstellt, ein, und jede Spalte der Tabelle steht für eine Eigenschaft des Objekts oder ein Skriptwert.</span><span class="sxs-lookup"><span data-stu-id="ca153-104">Each row in the table represents a .NET object, and each column of the table represents a property of the object or a script value.</span></span> <span data-ttu-id="ca153-105">Sie können eine Tabellenansicht definieren, die alle Eigenschaften eines Objekts oder einer Teilmenge der Eigenschaften eines Objekts anzeigt.</span><span class="sxs-lookup"><span data-stu-id="ca153-105">You can define a table view that displays all the properties of an object or a subset of the properties of an object.</span></span>

## <a name="a-table-view-display"></a><span data-ttu-id="ca153-106">Anzeige einer Tabelle</span><span class="sxs-lookup"><span data-stu-id="ca153-106">A Table View Display</span></span>

<span data-ttu-id="ca153-107">Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) von zurückgegebene Objekt der [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ca153-107">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="ca153-108">Für dieses Objekt wurde Windows PowerShell definiert eine Tabellenansicht, das anzeigt der `Status` -Eigenschaft, die `Name` Eigenschaft (diese Eigenschaft ist ein aliaseigenschaft für die `ServiceName` Eigenschaft), und die `DisplayName` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ca153-108">For this object, Windows PowerShell has defined a table view that displays the `Status` property, the `Name` property (this property is an alias property for the `ServiceName` property), and the `DisplayName` property.</span></span> <span data-ttu-id="ca153-109">Jede Zeile in der Tabelle stellt ein vom Cmdlet zurückgegebenes Objekt dar.</span><span class="sxs-lookup"><span data-stu-id="ca153-109">Each row in the table represents an object returned by the cmdlet.</span></span>

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a><span data-ttu-id="ca153-110">Definieren der Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="ca153-110">Defining the Table View</span></span>

<span data-ttu-id="ca153-111">Das folgende XML zeigt das Schema der Ansicht zum Anzeigen der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="ca153-111">The following XML shows the table view schema for displaying the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ca153-112">Sie müssen jede Eigenschaft angeben, die in der Tabellenansicht angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ca153-112">You must specify each property that you want displayed in the table view.</span></span>

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

<span data-ttu-id="ca153-113">Die folgende XML-Elemente werden verwendet, um eine Ansicht zu definieren:</span><span class="sxs-lookup"><span data-stu-id="ca153-113">The following XML elements are used to define a list view:</span></span>

- <span data-ttu-id="ca153-114">Die [Ansicht](./view-element-format.md) Element ist das übergeordnete Element der Tabellenansicht.</span><span class="sxs-lookup"><span data-stu-id="ca153-114">The [View](./view-element-format.md) element is the parent element of the table view.</span></span> <span data-ttu-id="ca153-115">(Dies ist das über dasselbe übergeordnete Element der Liste, Breite und benutzerdefinierte Steuerelementansicht.)</span><span class="sxs-lookup"><span data-stu-id="ca153-115">(This is the same parent element for the list, wide, and custom control views.)</span></span>

- <span data-ttu-id="ca153-116">Die [Namen](./name-element-for-view-format.md) Element gibt den Namen der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="ca153-116">The [Name](./name-element-for-view-format.md) element specifies the name of the view.</span></span> <span data-ttu-id="ca153-117">Dieses Element ist für alle Ansichten erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ca153-117">This element is required for all views.</span></span>

- <span data-ttu-id="ca153-118">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ca153-118">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view.</span></span> <span data-ttu-id="ca153-119">Dieses Element ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ca153-119">This element is required.</span></span>

- <span data-ttu-id="ca153-120">Die [GroupBy](./groupby-element-for-view-format.md) -Element (nicht in diesem Beispiel dargestellt) definiert, wenn eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-120">The [GroupBy](./groupby-element-for-view-format.md) element (not shown in this example) defines when a new group of objects is displayed.</span></span> <span data-ttu-id="ca153-121">Eine neue Gruppe wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="ca153-121">A new group is started whenever the value of a specific property or script changes.</span></span> <span data-ttu-id="ca153-122">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-122">This element is optional.</span></span>

- <span data-ttu-id="ca153-123">Die [Steuerelemente](./controls-element-for-view-format.md) -Element (nicht in diesem Beispiel dargestellt) definiert die benutzerdefinierten Steuerelemente, die von der Tabellenansicht definiert sind.</span><span class="sxs-lookup"><span data-stu-id="ca153-123">The [Controls](./controls-element-for-view-format.md) element (not shown in this example) defines the custom controls that are defined by the table view.</span></span> <span data-ttu-id="ca153-124">Steuerelemente bieten Ihnen eine Möglichkeit, festzulegen, wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-124">Controls give you a way to further specify how the data is displayed.</span></span> <span data-ttu-id="ca153-125">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-125">This element is optional.</span></span> <span data-ttu-id="ca153-126">Eine Ansicht kann eine eigene benutzerdefinierte Steuerelemente zu definieren, oder sie können allgemeine Steuerelemente, die von einer beliebigen Ansicht in der Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-126">A view can define its own custom controls, or it can use common controls that can be used by any view in the formatting file.</span></span> <span data-ttu-id="ca153-127">Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ca153-127">For more information about custom controls, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

- <span data-ttu-id="ca153-128">Die [HideTableHeaders](./hidetableheaders-element-format.md) Element (nicht mehr anzeigen in diesem Beispiel) gibt an, dass die Tabelle keine Bezeichnungen am oberen Rand der Tabelle nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-128">The [HideTableHeaders](./hidetableheaders-element-format.md) element (not show in this example) specifies that the table will not show any labels at the top of the table.</span></span> <span data-ttu-id="ca153-129">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-129">This element is optional.</span></span>

- <span data-ttu-id="ca153-130">Die [TableControl](./tablecontrol-element-format.md) Element, das Informationen für den Kopf- und die Zeile der Tabelle definiert.</span><span class="sxs-lookup"><span data-stu-id="ca153-130">The [TableControl](./tablecontrol-element-format.md) element that defines the header and row information of the table.</span></span> <span data-ttu-id="ca153-131">Ähnlich wie bei allen anderen Ansichten, kann eine Tabellenansicht die Werte der Objekteigenschaften oder von Skripts generierte Werte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ca153-131">Similar to all other views, a table view can display the values of object properties or values generated by scripts.</span></span>

## <a name="defining-column-headers"></a><span data-ttu-id="ca153-132">Definieren von Spaltenüberschriften</span><span class="sxs-lookup"><span data-stu-id="ca153-132">Defining Column Headers</span></span>

1. <span data-ttu-id="ca153-133">Die [TableHeaders](./tableheaders-element-format.md) -Element und seine untergeordneten Elemente definieren, was am oberen Rand der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-133">The [TableHeaders](./tableheaders-element-format.md) element and its child elements define what is displayed at the top of the table.</span></span>

2. <span data-ttu-id="ca153-134">Die [TableColumnHeader](./tablecolumnheader-element-format.md) -Element definiert, was am oberen Rand einer Spalte der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-134">The [TableColumnHeader](./tablecolumnheader-element-format.md) element defines what is displayed at the top of a column of the table.</span></span> <span data-ttu-id="ca153-135">Geben Sie diese Elemente in der Reihenfolge, in den Headern, die angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ca153-135">Specify these elements in the order that you want the headers displayed.</span></span>

   <span data-ttu-id="ca153-136">Es gibt keine Beschränkung der Anzahl von diesen-Element, das Sie verwenden können, aber die Anzahl der [TableColumnHeader](./tablecolumnheader-element-format.md) Elemente in der Tabellenansicht müssen gleich der Anzahl der [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) Elemente, die Sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="ca153-136">There is no limit to the number of these element that you can use, but the number of [TableColumnHeader](./tablecolumnheader-element-format.md) elements in your table view must equal the number of [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) elements that you use.</span></span>

3. <span data-ttu-id="ca153-137">Die [Bezeichnung](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) Element gibt den Text, der angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-137">The [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the text that is displayed.</span></span> <span data-ttu-id="ca153-138">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-138">This element is optional.</span></span>

4. <span data-ttu-id="ca153-139">Die [Breite](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) Element gibt die Breite (in Zeichen) der Spalte an.</span><span class="sxs-lookup"><span data-stu-id="ca153-139">The [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies the width (in characters) of the column.</span></span> <span data-ttu-id="ca153-140">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-140">This element is optional.</span></span>

5. <span data-ttu-id="ca153-141">Die [Ausrichtung](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt an, wie die Bezeichnung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-141">The [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) element specifies how the label is displayed.</span></span> <span data-ttu-id="ca153-142">Die Bezeichnung kann auf der linken Seite nach rechts ausgerichtet werden oder zentriert.</span><span class="sxs-lookup"><span data-stu-id="ca153-142">The label can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="ca153-143">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-143">This element is optional.</span></span>

## <a name="defining-the-table-rows"></a><span data-ttu-id="ca153-144">Definieren die Zeilen der Tabelle</span><span class="sxs-lookup"><span data-stu-id="ca153-144">Defining the Table Rows</span></span>

<span data-ttu-id="ca153-145">Tabellenansichten bieten eine oder mehrere Definitionen an, die angeben, welche Daten in den Zeilen der Tabelle angezeigt werden, die untergeordneten Elemente mit den [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="ca153-145">Table views can provide one or more definitions that specify what data is displayed in the rows of the table by using the child elements of the [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="ca153-146">Beachten Sie, dass Sie können mehrere Definitionen für die Zeilen der Tabelle angeben, die Header für die Zeilen bleibt jedoch gleich, unabhängig davon, welche Zeilendefinition verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-146">Notice that you can specify multiple definitions for the rows of the table, but the headers for the rows remains the same, regardless of what row definition is used.</span></span> <span data-ttu-id="ca153-147">In der Regel wird eine Tabelle nur eine Definition enthalten.</span><span class="sxs-lookup"><span data-stu-id="ca153-147">Typically, a table will have only one definition.</span></span>

<span data-ttu-id="ca153-148">Im folgenden Beispiel die Ansicht bietet eine einzige Definition, die den Werten verschiedener Eigenschaften der an die ["System.Diagnostics.Process"? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="ca153-148">In the following example, the view provides a single definition that displays the values of several properties of the [System.Diagnostics.Process?Displayproperty=Fullname](/dotnet/api/System.Diagnostics.Process) object.</span></span> <span data-ttu-id="ca153-149">Eine Tabellenansicht kann den Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel gezeigt) in seinen Zeilen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ca153-149">A table view can display the value of a property or the value of a script (not shown in the example) in its rows.</span></span>

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

<span data-ttu-id="ca153-150">Die folgende XML-Elemente können verwendet werden, um Definitionen für eine Zeile bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="ca153-150">The following XML elements can be used to provide definitions for a row:</span></span>

- <span data-ttu-id="ca153-151">Die [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -Element und seine untergeordneten Elemente definieren, was in den Zeilen der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-151">The [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) element and its child elements define what is displayed in the rows of the table.</span></span>

- <span data-ttu-id="ca153-152">Die [TableRowEntry](./listentry-element-for-listcontrol-format.md) Element enthält eine Definition der Zeile.</span><span class="sxs-lookup"><span data-stu-id="ca153-152">The [TableRowEntry](./listentry-element-for-listcontrol-format.md) element provides a definition of the row.</span></span> <span data-ttu-id="ca153-153">Mindestens ein [TableRowEntry](./listentry-element-for-listcontrol-format.md) ist erforderlich; Es ist jedoch nicht begrenzt auf die Anzahl der Elemente, die Sie hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="ca153-153">At least one [TableRowEntry](./listentry-element-for-listcontrol-format.md) is required; however, there is no maximum limit to the number of elements that you can add.</span></span> <span data-ttu-id="ca153-154">In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.</span><span class="sxs-lookup"><span data-stu-id="ca153-154">In most cases, a view will have only one definition.</span></span>

- <span data-ttu-id="ca153-155">Die [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Element gibt an, die Objekte, die von einer bestimmten Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-155">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element specifies the objects that are displayed by a specific definition.</span></span> <span data-ttu-id="ca153-156">Dieses Element ist optional und ist nur erforderlich, wenn Sie mehrere definieren [TableRowEntry](./listentry-element-for-listcontrol-format.md) Elemente, die verschiedene Objekte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ca153-156">This element is optional and is needed only when you define multiple [TableRowEntry](./listentry-element-for-listcontrol-format.md) elements that display different objects.</span></span>

- <span data-ttu-id="ca153-157">Die [umschließen](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) Element gibt an, dass Text, der die Spaltenbreite überschreitet, die in der nächsten Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-157">The [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) element specifies that text that exceeds the column width is displayed on the next line.</span></span> <span data-ttu-id="ca153-158">Standardmäßig wird Text, der die Spaltenbreite überschreitet, abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="ca153-158">By default, text that exceeds the column width is truncated.</span></span>

- <span data-ttu-id="ca153-159">Die [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -Element definiert die Eigenschaften oder Skripts, deren Werte werden in der Zeile angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ca153-159">The [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) element defines the properties or scripts whose values are displayed in the row.</span></span>

- <span data-ttu-id="ca153-160">Die [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-160">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ca153-161">Ein [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Element ist erforderlich für jede Spalte der Zeile.</span><span class="sxs-lookup"><span data-stu-id="ca153-161">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ca153-162">Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.</span><span class="sxs-lookup"><span data-stu-id="ca153-162">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ca153-163">Die [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt die Eigenschaft, deren Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-163">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="ca153-164">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="ca153-164">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ca153-165">Die ["scriptblock"](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-165">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="ca153-166">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="ca153-166">You must specify either a script or a property, but you cannot specify both.</span></span>

- <span data-ttu-id="ca153-167">Die [FormatString](./label-element-for-listitem-for-listcontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-167">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span> <span data-ttu-id="ca153-168">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-168">This element is optional.</span></span>

- <span data-ttu-id="ca153-169">Die [Ausrichtung](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt an, wie der Wert der Eigenschaft oder des Skripts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-169">The [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies how the value of the property or script is displayed.</span></span> <span data-ttu-id="ca153-170">Der Wert kann auf der linken Seite nach rechts ausgerichtet werden oder zentriert.</span><span class="sxs-lookup"><span data-stu-id="ca153-170">The value can be aligned to the left, to the right, or centered.</span></span> <span data-ttu-id="ca153-171">Dieses Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="ca153-171">This element is optional.</span></span>

## <a name="defining-the-objects-that-use-the-table-view"></a><span data-ttu-id="ca153-172">Definieren die Objekte, mit denen die Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="ca153-172">Defining the Objects That Use the Table View</span></span>

<span data-ttu-id="ca153-173">Es gibt zwei Möglichkeiten, die definieren, welche .NET Objekte die Tabellenansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="ca153-173">There are two ways to define which .NET objects use the table view.</span></span> <span data-ttu-id="ca153-174">Können Sie die [ViewSelectedBy](./viewselectedby-element-format.md) Element, das die Objekte zu definieren, die durch alle Definitionen oder der Ansicht angezeigt werden können. die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element zum definieren, welche Objekte angezeigt werden ein spezifische Definition der Sicht.</span><span class="sxs-lookup"><span data-stu-id="ca153-174">You can use the [ViewSelectedBy](./viewselectedby-element-format.md) element to define the objects that can be displayed by all the definitions of the view, or you can use the [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) element to define which objects are displayed by a specific definition of the view.</span></span> <span data-ttu-id="ca153-175">In den meisten Fällen eine Ansicht hat nur eine Definition, sodass Objekte in der Regel, indem definiert werden die [ViewSelectedBy](./viewselectedby-element-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="ca153-175">In most cases, a view has only one definition, so objects are typically defined by the [ViewSelectedBy](./viewselectedby-element-format.md) element.</span></span>

<span data-ttu-id="ca153-176">Das folgende Beispiel zeigt, wie Sie die Objekte zu definieren, die von der Ansicht mit Tabelle angezeigt werden die [ViewSelectedBy](./viewselectedby-element-format.md) und [TypeName](./typename-element-for-viewselectedby-format.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="ca153-176">The following example shows how to define the objects that are displayed by the table view using the [ViewSelectedBy](./viewselectedby-element-format.md) and [TypeName](./typename-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ca153-177">Es gibt keine Beschränkung der Anzahl der [TypeName](./typename-element-for-viewselectedby-format.md) Elementen, die Sie angeben können und ihre Reihenfolge ist nicht von Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="ca153-177">There is no limit to the number of [TypeName](./typename-element-for-viewselectedby-format.md) elements that you can specify, and their order is not significant.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="ca153-178">Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Tabellenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="ca153-178">The following XML elements can be used to specify the objects that are used by the table view:</span></span>

- <span data-ttu-id="ca153-179">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-179">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ca153-180">Die [TypeName](./typename-element-for-viewselectedby-format.md) -Element gibt an, das .NET-Objekt, das von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-180">The [TypeName](./typename-element-for-viewselectedby-format.md) element specifies the .NET object that is displayed by the view.</span></span> <span data-ttu-id="ca153-181">Der vollqualifizierte Typname des .NET ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ca153-181">The fully qualified .NET type name is required.</span></span> <span data-ttu-id="ca153-182">Geben Sie mindestens einen Typ oder Auswahl für die Ansicht festgelegt, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-182">You must specify at least one type or selection set for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ca153-183">Im folgenden Beispiel wird die [ViewSelectedBy](./viewselectedby-element-format.md) und [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Elemente.</span><span class="sxs-lookup"><span data-stu-id="ca153-183">The following example uses the [ViewSelectedBy](./viewselectedby-element-format.md) and [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) elements.</span></span> <span data-ttu-id="ca153-184">Verwenden Sie die Auswahl legt, haben eine zusammengehörige Gruppe von Objekten, die über mehrere Ansichten, z. B. Wenn Sie eine Listenansicht definieren und eine Tabellenansicht für diese Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-184">Use selection sets where you have a related set of objects that are displayed using multiple views, such as when you define a list view and a table view for the same objects.</span></span> <span data-ttu-id="ca153-185">Weitere Informationen dazu, wie Sie einen Auswahlsatz zu erstellen, finden Sie unter [definieren Auswahl legt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ca153-185">For more information about how to create a selection set, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

<span data-ttu-id="ca153-186">Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="ca153-186">The following XML elements can be used to specify the objects that are used by the list view:</span></span>

- <span data-ttu-id="ca153-187">Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-187">The [ViewSelectedBy](./viewselectedby-element-format.md) element defines which objects are displayed by the list view.</span></span>

- <span data-ttu-id="ca153-188">Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element gibt einen Satz von Objekten, die von der Ansicht angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-188">The [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) element specifies a set of objects that can be displayed by the view.</span></span> <span data-ttu-id="ca153-189">Geben Sie mindestens einen Auswahlsatz oder Typ, für die Sicht, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-189">You must specify at least one selection set or type for the view, but there is no maximum number of elements that can be specified.</span></span>

<span data-ttu-id="ca153-190">Das folgende Beispiel zeigt, wie Sie die Objekte angezeigt, die von einer bestimmten Definition der Ansicht mit Tabelle definieren die [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="ca153-190">The following example shows how to define the objects displayed by a specific definition of the table view using the [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element.</span></span> <span data-ttu-id="ca153-191">Verwenden dieses Element, können Sie den Namen des Objekts, einer Auswahlsatz von Objekten oder eine auswahlbedingung, die angibt, wenn die Definition verwendet wird angeben.</span><span class="sxs-lookup"><span data-stu-id="ca153-191">Using this element, you can specify the .NET type name of the object, a selection set of objects, or a selection condition that specifies when the definition is used.</span></span> <span data-ttu-id="ca153-192">Weitere Informationen dazu, wie Sie eine Auswahl Bedingungen zu erstellen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ca153-192">For more information about how to create a selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ca153-193">Wenn Sie mehrere Definitionen der Tabellenansicht erstellen angeben nicht unterschiedliche Spaltenüberschriften.</span><span class="sxs-lookup"><span data-stu-id="ca153-193">When creating multiple definitions of the table view you cannot specify different column headers.</span></span> <span data-ttu-id="ca153-194">Sie können angeben, nur Anzeige in den Zeilen der Tabelle aus, wie z. B., welche Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-194">You can specify only what is displayed in the rows of the table, such as what objects are displayed.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

<span data-ttu-id="ca153-195">Die folgende XML-Elemente können verwendet werden, die Objekte an, die von einer bestimmten Definition der Listenansicht verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="ca153-195">The following XML elements can be used to specify the objects that are used by a specific definition of the list view:</span></span>

- <span data-ttu-id="ca153-196">Die [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Element definiert, welche Objekte durch die Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-196">The [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) element defines which objects are displayed by the definition.</span></span>

- <span data-ttu-id="ca153-197">Die [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt an, das .NET-Objekt, das durch die Definition angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-197">The [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) element specifies the .NET object that is displayed by the definition.</span></span> <span data-ttu-id="ca153-198">Wenn Sie dieses Element zu verwenden, ist der vollqualifizierte Typname des .NET erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ca153-198">When using this element, the fully qualified .NET type name is required.</span></span> <span data-ttu-id="ca153-199">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-199">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ca153-200">Die [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt einen Satz von Objekten, die von dieser Definition angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-200">The [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a set of objects that can be displayed by this definition.</span></span> <span data-ttu-id="ca153-201">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-201">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span>

- <span data-ttu-id="ca153-202">Die [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt an, eine Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-202">The [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) element (not shown) specifies a condition that must exist for this definition to be used.</span></span> <span data-ttu-id="ca153-203">Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="ca153-203">You must specify at least one type, selection set, or selection condition for the definition, but there is no maximum number of elements that can be specified.</span></span> <span data-ttu-id="ca153-204">Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ca153-204">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="using-format-strings"></a><span data-ttu-id="ca153-205">Verwenden von Formatzeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="ca153-205">Using Format Strings</span></span>

<span data-ttu-id="ca153-206">Formatieren von Zeichenfolgen können hinzugefügt werden, zu einer Ansicht genauer definieren, wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ca153-206">Formatting strings can be added to a view to further define how the data is displayed.</span></span> <span data-ttu-id="ca153-207">Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="ca153-207">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

<span data-ttu-id="ca153-208">Die folgende XML-Elemente können verwendet werden, ein Formatmuster angeben:</span><span class="sxs-lookup"><span data-stu-id="ca153-208">The following XML elements can be used to specify a format pattern:</span></span>

- <span data-ttu-id="ca153-209">Die [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-209">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ca153-210">Ein [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Element ist erforderlich für jede Spalte der Zeile.</span><span class="sxs-lookup"><span data-stu-id="ca153-210">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ca153-211">Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.</span><span class="sxs-lookup"><span data-stu-id="ca153-211">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ca153-212">Die [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt die Eigenschaft, deren Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-212">The [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the property whose value is displayed in the row.</span></span> <span data-ttu-id="ca153-213">Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="ca153-213">You must specify either a property or a script, but you cannot specify both.</span></span>

- <span data-ttu-id="ca153-214">Die [FormatString](./label-element-for-listitem-for-listcontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-214">The [FormatString](./label-element-for-listitem-for-listcontrol-format.md) element specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="ca153-215">Im folgenden Beispiel die `ToString` aufgerufen, um den Wert des Skripts zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="ca153-215">In the following example, the `ToString` method is called to format the value of the script.</span></span> <span data-ttu-id="ca153-216">Skripts können auf jede Methode eines Objekts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ca153-216">Scripts can call any method of an object.</span></span> <span data-ttu-id="ca153-217">Daher verfügt ein Objekt eine Methode, wie z. B. `ToString`über Formatierung Parameter verfügt, das Skript kann diese Methode zum Formatieren des Werts der Ausgabe des Skripts aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="ca153-217">Therefore, if an object has a method, such as `ToString`, that has formatting parameters, the script can call that method to format the output value of the script.</span></span>

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

<span data-ttu-id="ca153-218">Das folgende XML-Element kann zum Aufrufen der `ToString` Methode:</span><span class="sxs-lookup"><span data-stu-id="ca153-218">The following XML element can be used to calling the `ToString` method:</span></span>

- <span data-ttu-id="ca153-219">Die [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-219">The [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element defines the property or script whose value is displayed in the column of the row.</span></span> <span data-ttu-id="ca153-220">Ein [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Element ist erforderlich für jede Spalte der Zeile.</span><span class="sxs-lookup"><span data-stu-id="ca153-220">A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) element is required for each column of the row.</span></span> <span data-ttu-id="ca153-221">Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.</span><span class="sxs-lookup"><span data-stu-id="ca153-221">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

- <span data-ttu-id="ca153-222">Die ["scriptblock"](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ca153-222">The [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) element specifies the script whose value is displayed in the row.</span></span> <span data-ttu-id="ca153-223">Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="ca153-223">You must specify either a script or a property, but you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca153-224">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ca153-224">See Also</span></span>

[<span data-ttu-id="ca153-225">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca153-225">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
