---
title: Übersicht über die Formatierung von Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363689"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="b7b0c-102">Formatierungsdatei: Übersicht</span><span class="sxs-lookup"><span data-stu-id="b7b0c-102">Formatting File Overview</span></span>

<span data-ttu-id="b7b0c-103">Das Anzeige Format für die Objekte, die von Befehlen (Cmdlets, Funktionen und Skripts) zurückgegeben werden, wird mithilfe von Formatierungs Dateien (Format. ps1xml-Dateien) definiert.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="b7b0c-104">Einige dieser Dateien werden von PowerShell bereitgestellt, um das Anzeige Format für die Objekte zu definieren, die von von PowerShell bereitgestellten Befehlen zurückgegeben werden, z. b. das vom Cmdlet "`Get-Process`" zurückgegebene [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="b7b0c-105">Sie können jedoch auch eigene benutzerdefinierte Formatierungs Dateien erstellen, um die Standard Anzeige Formate zu überschreiben, oder Sie können eine benutzerdefinierte Formatierungs Datei schreiben, um die Anzeige von Objekten zu definieren, die von ihren eigenen Befehlen zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7b0c-106">Beim Formatieren von Dateien werden die Elemente eines Objekts, die an die Pipeline zurückgegeben werden, nicht bestimmt.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="b7b0c-107">Wenn ein Objekt an die Pipeline zurückgegeben wird, sind alle Member dieses Objekts verfügbar, auch wenn einige nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="b7b0c-108">PowerShell verwendet die Daten in diesen Formatierungs Dateien, um zu bestimmen, was angezeigt wird und wie die angezeigten Daten formatiert werden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="b7b0c-109">Die angezeigten Daten können die Eigenschaften eines Objekts oder den Wert eines Skripts enthalten.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="b7b0c-110">Skripts werden verwendet, wenn Sie einen Wert anzeigen möchten, der nicht direkt aus den Eigenschaften eines Objekts verfügbar ist, z. b. das Hinzufügen des Werts von zwei Eigenschaften eines Objekts und anschließendes Anzeigen der Summe als Datenelement.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="b7b0c-111">Die Formatierung der angezeigten Daten erfolgt durch Definieren von Sichten für die Objekte, die Sie anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="b7b0c-112">Sie können für jedes Objekt eine einzelne Ansicht definieren, Sie können eine einzelne Ansicht für mehrere Objekte definieren, oder Sie können mehrere Ansichten für dasselbe Objekt definieren.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="b7b0c-113">Es gibt keine Beschränkung für die Anzahl der Sichten, die Sie definieren können.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="b7b0c-114">Allgemeine Funktionen zum Formatieren von Dateien</span><span class="sxs-lookup"><span data-stu-id="b7b0c-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="b7b0c-115">Jede Formatierungs Datei kann die folgenden Komponenten definieren, die für alle Ansichten freigegeben werden können, die in der Datei definiert sind:</span><span class="sxs-lookup"><span data-stu-id="b7b0c-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="b7b0c-116">Standard Konfigurationseinstellung, z. b. ob die in den Zeilen der Tabellen angezeigten Daten in der nächsten Zeile angezeigt werden, wenn die Daten länger als die Spaltenbreite sind.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="b7b0c-117">Weitere Informationen zu diesen Einstellungen finden Sie unter [Definieren allgemeiner Konfigurationseinstellungen](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0c-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="b7b0c-118">Sätze von-Objekten, die von einer beliebigen Ansicht der Formatierungs Datei angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="b7b0c-119">Weitere Informationen zu diesen Sätzen (als *Auswahl Sätze*bezeichnet) finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0c-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="b7b0c-120">Allgemeine Steuerelemente, die von allen Ansichten der Formatierungs Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="b7b0c-121">Mit Steuerelementen können Sie besser steuern, wie Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="b7b0c-122">Weitere Informationen zu-Steuerelementen finden Sie unter [Definieren von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0c-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="b7b0c-123">Formatieren von Sichten</span><span class="sxs-lookup"><span data-stu-id="b7b0c-123">Formatting Views</span></span>

<span data-ttu-id="b7b0c-124">Durch das Formatieren von Sichten können Objekte in einem Tabellenformat, einem Listenformat, einem breiten Format und einem benutzerdefinierten Format angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="b7b0c-125">In den meisten Fällen wird jede Formatierungs Definition durch eine Reihe von XML-Tags beschrieben, die die Sicht beschreiben.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="b7b0c-126">Jede Ansicht enthält den Namen der Ansicht, die Objekte, die die Sicht verwenden, und die Elemente der Ansicht, z. b. die Spalten-und Zeilen Informationen für eine Tabellen Sicht.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="b7b0c-127">In der Tabellenansicht werden die Eigenschaften eines Objekts oder eines Skriptblock Werts in mindestens einer Spalte aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="b7b0c-128">Jede Spalte stellt eine einzelne Eigenschaft des Objekts oder einen Skript Wert dar.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="b7b0c-129">Sie können eine Tabellen Sicht definieren, in der alle Eigenschaften eines Objekts, eine Teilmenge der Eigenschaften eines Objekts oder eine Kombination von Eigenschaften und Skript Werten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="b7b0c-130">Jede Zeile der Tabelle stellt ein zurück gegebenes Objekt dar.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="b7b0c-131">Das Erstellen einer Tabellenansicht ist sehr ähnlich, wenn Sie ein Objekt an das `Format-Table`-Cmdlet weiterreichen.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="b7b0c-132">Weitere Informationen zu dieser Ansicht finden Sie unter [Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0c-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="b7b0c-133">In der Listenansicht werden die Eigenschaften eines Objekts oder eines Skript Werts in einer einzelnen Spalte aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="b7b0c-134">In jeder Zeile der Liste wird eine optionale Bezeichnung oder der Eigenschaftsname, gefolgt vom Wert der Eigenschaft oder des Skripts, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="b7b0c-135">Das Erstellen einer Listenansicht ähnelt der Weiterleitung eines Objekts an das `Format-List`-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="b7b0c-136">Weitere Informationen zu dieser Ansicht finden Sie in der [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0c-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="b7b0c-137">Die Breite Ansicht Listet eine einzelne Eigenschaft eines Objekts oder einen Skript Wert in einer oder mehreren Spalten auf.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="b7b0c-138">Für diese Ansicht gibt es keine Bezeichnung oder einen Header.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-138">There is no label or header for this view.</span></span> <span data-ttu-id="b7b0c-139">Das Erstellen einer breiten Ansicht ähnelt der Weiterleitung eines Objekts an das `Format-Wide`-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="b7b0c-140">Weitere Informationen zu dieser Ansicht finden Sie unter [Wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0c-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="b7b0c-141">Die benutzerdefinierte Ansicht zeigt eine anpassbare Ansicht von Objekteigenschaften oder Skript Werten an, die nicht der festen Struktur von Tabellen Sichten, Listenansichten oder breiten Ansichten entspricht.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="b7b0c-142">Sie können eine eigenständige benutzerdefinierte Sicht definieren, oder Sie können eine benutzerdefinierte Ansicht definieren, die von einer anderen Ansicht verwendet wird, z. b. eine Tabellen-oder Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="b7b0c-143">Das Erstellen einer benutzerdefinierten Ansicht ähnelt der Weiterleitung eines Objekts an das `Format-Custom`-Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="b7b0c-144">Weitere Informationen zu dieser Ansicht finden Sie unter [benutzerdefinierte Ansicht](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b7b0c-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="b7b0c-145">Komponenten einer Ansicht</span><span class="sxs-lookup"><span data-stu-id="b7b0c-145">Components of a View</span></span>

<span data-ttu-id="b7b0c-146">Die folgenden XML-Beispiele zeigen die grundlegenden XML-Komponenten einer Ansicht.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="b7b0c-147">Die einzelnen XML-Elemente variieren abhängig von der Sicht, die Sie erstellen möchten, aber die grundlegenden Komponenten der Sichten sind identisch.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="b7b0c-148">Um mit zu beginnen, verfügt jede Ansicht über ein `Name`-Element, das einen benutzerfreundlichen Namen angibt, der zum Verweisen auf die Sicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="b7b0c-149">ein `ViewSelectedBy`-Element, das definiert, welche .NET-Objekte von der Sicht angezeigt werden, und ein *Steuer* Element, das die Ansicht definiert.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="b7b0c-150">Innerhalb des Control-Elements können Sie ein oder mehrere *Einstiegs* Elemente definieren.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="b7b0c-151">Wenn Sie mehrere Definitionen verwenden, müssen Sie angeben, welche .NET-Objekte die einzelnen Definitionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="b7b0c-152">In der Regel ist nur ein Eintrag mit nur einer Definition für jedes Steuerelement erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="b7b0c-153">In jedem Eintrags Element einer Ansicht geben Sie die *Element* Elemente an, die die .net-Eigenschaften oder-Skripts definieren, die von dieser Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="b7b0c-154">Wie in den vorherigen Beispielen gezeigt, kann die Formatierungs Datei mehrere Sichten enthalten, eine Sicht kann mehrere Definitionen enthalten, und jede Definition kann mehrere Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="b7b0c-155">Beispiel für eine Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="b7b0c-155">Example of a Table View</span></span>

<span data-ttu-id="b7b0c-156">Das folgende Beispiel zeigt die XML-Tags, mit denen eine Tabellen Sicht definiert wird, die zwei Spalten enthält.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="b7b0c-157">Das [viewdefinitions](./viewdefinitions-element-format.md) -Element ist das Containerelement für alle Sichten, die in der Formatierungs Datei definiert sind.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="b7b0c-158">Das [Ansichts](./view-element-format.md) Element definiert die spezifische Tabelle, die Liste, die Breite oder die benutzerdefinierte Sicht.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="b7b0c-159">Innerhalb jedes [Ansichts](./view-element-format.md) Elements gibt das [Name](./name-element-for-view-format.md) -Element den Namen der Ansicht an, das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht verwenden, und die verschiedenen Steuerelement Elemente (z. b. das `TableControl`-Element, das im folgenden dargestellt ist). Beispiel) definieren Sie den Typ der Sicht.</span><span class="sxs-lookup"><span data-stu-id="b7b0c-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="b7b0c-160">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b7b0c-160">See Also</span></span>

[<span data-ttu-id="b7b0c-161">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="b7b0c-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b7b0c-162">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="b7b0c-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b7b0c-163">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="b7b0c-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="b7b0c-164">Erstellen benutzerdefinierter Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="b7b0c-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="b7b0c-165">Schreiben einer PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="b7b0c-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
