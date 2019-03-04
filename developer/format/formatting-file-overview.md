---
title: Übersicht über die Datei Formatierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863296"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="d46c1-102">Formatierungsdatei: Übersicht</span><span class="sxs-lookup"><span data-stu-id="d46c1-102">Formatting File Overview</span></span>

<span data-ttu-id="d46c1-103">Das Anzeigeformat für die Objekte, die durch Befehle (Cmdlets, Funktionen und Skripts) zurückgegeben werden, werden mithilfe von Formatierungsdateien (Format. ps1xml-Dateien) definiert.</span><span class="sxs-lookup"><span data-stu-id="d46c1-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="d46c1-104">Einige dieser Dateien finden Sie PowerShell, um das Anzeigeformat für die bereitgestellte PowerShell-Befehle, wie z. B. zurückgegebenen Objekte definieren die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) zurückgegebenes Objekt der `Get-Process` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d46c1-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="d46c1-105">Allerdings können Sie auch eigene benutzerdefinierte Formatierungsdateien, um die Standardformate für die Anzeige zu überschreiben, erstellen, oder Sie können eine benutzerdefinierte Formatierung-Datei, um die Anzeige von Objekten zurückgegeben, die durch Ihre eigenen Befehle definieren, schreiben.</span><span class="sxs-lookup"><span data-stu-id="d46c1-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d46c1-106">Formatierungsdateien sind die Elemente eines Objekts nicht bestimmt werden, die an die Pipeline zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d46c1-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="d46c1-107">Wenn ein Objekt an die Pipeline zurückgegeben wird, sind alle Member des Objekts verfügbar, auch wenn einige nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d46c1-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="d46c1-108">PowerShell verwendet die Daten in diese Formatierungsdateien, um zu bestimmen, was angezeigt wird und wie die angezeigten Daten formatiert werden.</span><span class="sxs-lookup"><span data-stu-id="d46c1-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="d46c1-109">Die angezeigten Daten können es sich um die Eigenschaften eines Objekts oder der Wert eines Skripts enthalten.</span><span class="sxs-lookup"><span data-stu-id="d46c1-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="d46c1-110">Skripts werden verwendet, wenn einen Wert angezeigt werden sollen, nicht direkt über die Eigenschaften eines Objekts, z. B. den Wert von zwei Eigenschaften eines Objekts hinzufügen, und klicken Sie dann die Summe als ein Datenelement angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="d46c1-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="d46c1-111">Formatieren der angezeigten Daten erfolgt durch Definieren von Ansichten für die Objekte, die Sie anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="d46c1-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="d46c1-112">Sie können eine einzelne Ansicht für jedes Objekt definieren, können Sie eine einzelne Ansicht für mehrere Objekte definieren oder Sie können mehrere Ansichten für das gleiche Objekt definieren.</span><span class="sxs-lookup"><span data-stu-id="d46c1-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="d46c1-113">Es gibt keine Beschränkung für die Anzahl der Aufrufe, die Sie definieren können.</span><span class="sxs-lookup"><span data-stu-id="d46c1-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="d46c1-114">Allgemeine Funktionen der Formatierungsdateien</span><span class="sxs-lookup"><span data-stu-id="d46c1-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="d46c1-115">Jede Formatierungsdatei kann die folgenden Komponenten definieren, die alle von der Datei definierten Sichten gemeinsam verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="d46c1-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="d46c1-116">Standardeinstellung Konfiguration, z. B., ob die Daten angezeigt, die in den Zeilen der Tabellen in der nächsten Zeile angezeigt werden, wenn die Daten länger als die Breite der Spalte ist.</span><span class="sxs-lookup"><span data-stu-id="d46c1-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="d46c1-117">Weitere Informationen zu diesen Einstellungen finden Sie unter [allgemeinen Konfigurationseinstellungen definieren](./defining-common-configuration-features.md).</span><span class="sxs-lookup"><span data-stu-id="d46c1-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="d46c1-118">Legt fest, der Objekte, die von keiner der Ansichten der formatierungs-Datei angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="d46c1-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="d46c1-119">Weitere Informationen zu diesen Sätzen (bezeichnet als *Auswahl legt*), finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d46c1-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="d46c1-120">Allgemeine Steuerelemente, die von allen Ansichten der formatierungs-Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d46c1-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="d46c1-121">Steuerelemente bieten Ihnen eine präzisere Kontrolle auf wie die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d46c1-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="d46c1-122">Weitere Informationen zu Steuerelementen, finden Sie unter [Definieren von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d46c1-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="d46c1-123">Formatieren von Ansichten</span><span class="sxs-lookup"><span data-stu-id="d46c1-123">Formatting Views</span></span>

<span data-ttu-id="d46c1-124">Formatierung Ansichten können Objekte in ein Tabellenformat, Listenformat, Breiten Format und das benutzerdefinierte Format anzeigen.</span><span class="sxs-lookup"><span data-stu-id="d46c1-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="d46c1-125">Zum größten Teil, wird jede formatierungsdefinition durch eine Reihe von XML-Tags beschrieben, die die Ansicht beschreiben.</span><span class="sxs-lookup"><span data-stu-id="d46c1-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="d46c1-126">Jede Ansicht enthält den Namen der Ansicht der Objekte, die die Sicht und die Elemente in der Ansicht, z. B. die Spalten- und Informationen für eine Tabellenansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="d46c1-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="d46c1-127">Sehen Sie Listen die Eigenschaften eines Objekts oder einem Skript Block-Wert in einer oder mehreren Spalten der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="d46c1-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d46c1-128">Jede Spalte stellt eine einzelne Eigenschaft eines Objekts oder einen Skriptwert dar.</span><span class="sxs-lookup"><span data-stu-id="d46c1-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="d46c1-129">Sie können eine Tabellenansicht definieren, die alle Eigenschaften eines Objekts, das eine Teilmenge der Eigenschaften eines Objekts oder eine Kombination von Eigenschaften und Skriptwerte anzeigt.</span><span class="sxs-lookup"><span data-stu-id="d46c1-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="d46c1-130">Jede Zeile der Tabelle stellt dar, ein zurückgegebenes Objekt.</span><span class="sxs-lookup"><span data-stu-id="d46c1-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="d46c1-131">Erstellen eine Tabellenansicht ist sehr ähnlich, wenn Sie ein Objekt, das über die Pipeline die `Format-Table` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d46c1-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="d46c1-132">Weitere Informationen zu dieser Ansicht finden Sie unter [Tabellenansicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d46c1-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="d46c1-133">Liste Ansicht enthält die Eigenschaften eines Objekts oder einen Skriptwert in einer einzelnen Spalte an.</span><span class="sxs-lookup"><span data-stu-id="d46c1-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="d46c1-134">Jede Zeile der Liste zeigt eine optionale Bezeichnung oder den Eigenschaftennamen, gefolgt von den Wert der Eigenschaft oder des Skripts.</span><span class="sxs-lookup"><span data-stu-id="d46c1-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="d46c1-135">Erstellen einer Listenansicht ist sehr ähnlich, übergeben ein Objekt, das `Format-List` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d46c1-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="d46c1-136">Weitere Informationen zu dieser Ansicht finden Sie unter [Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d46c1-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="d46c1-137">Breite Ansicht enthält eine einzelne Eigenschaft eines Objekts oder ein Skriptwert in einer oder mehreren Spalten.</span><span class="sxs-lookup"><span data-stu-id="d46c1-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="d46c1-138">Es gibt keine Bezeichnung oder Header für diese Sicht.</span><span class="sxs-lookup"><span data-stu-id="d46c1-138">There is no label or header for this view.</span></span> <span data-ttu-id="d46c1-139">Erstellen eine Breite Ansicht ist sehr ähnlich, übergeben ein Objekt, das `Format-Wide` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d46c1-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="d46c1-140">Weitere Informationen zu dieser Ansicht finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d46c1-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="d46c1-141">Benutzerdefinierte Ansicht zeigt eine anpassbare Ansicht der Objekteigenschaften oder Skriptwerte, die die starre Struktur der Tabellenansichten, Listenansichten oder breiten Ansichten nicht entspricht.</span><span class="sxs-lookup"><span data-stu-id="d46c1-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="d46c1-142">Sie können eine eigenständige benutzerdefinierte Ansicht definieren, oder Sie können definieren, eine benutzerdefinierte Ansicht, die von einer anderen Ansicht, z. B. eine Tabelle oder Ansicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d46c1-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="d46c1-143">Erstellen einer benutzerdefinierten Ansicht ist sehr ähnlich, übergeben ein Objekt, das `Format-Custom` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d46c1-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="d46c1-144">Weitere Informationen zu dieser Ansicht finden Sie unter [benutzerdefinierte Sicht](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d46c1-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="d46c1-145">Komponenten einer Ansicht</span><span class="sxs-lookup"><span data-stu-id="d46c1-145">Components of a View</span></span>

<span data-ttu-id="d46c1-146">Die folgenden XML-Beispiele zeigen die grundlegenden XML-Komponenten einer Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d46c1-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="d46c1-147">Die einzelnen XML-Elemente variieren, je nachdem welche, die Ansicht Sie erstellen möchten, aber die grundlegenden Komponenten der Ansichten sind alle identisch.</span><span class="sxs-lookup"><span data-stu-id="d46c1-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="d46c1-148">Zu Beginn jeder Ansicht ist eine `Name` Element, das einen benutzerfreundlichen Namen, die verwendet wird angibt, um die Sicht verweisen.</span><span class="sxs-lookup"><span data-stu-id="d46c1-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="d46c1-149">eine `ViewSelectedBy` Element, das definiert, welche .NET Objekte von der Ansicht angezeigt werden und ein *Steuerelement* -Element, das die Sicht definiert.</span><span class="sxs-lookup"><span data-stu-id="d46c1-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

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

<span data-ttu-id="d46c1-150">Sie können in das Steuerelement definieren, eine oder mehrere *Eintrag* Elemente.</span><span class="sxs-lookup"><span data-stu-id="d46c1-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="d46c1-151">Wenn Sie mehrere Definitionen verwenden, müssen Sie angeben, welche Objekte .NET jede Definition verwenden.</span><span class="sxs-lookup"><span data-stu-id="d46c1-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="d46c1-152">In der Regel wird nur ein Eintrag, mit der nur eine Definition für jedes Steuerelement benötigt.</span><span class="sxs-lookup"><span data-stu-id="d46c1-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

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

<span data-ttu-id="d46c1-153">Innerhalb jeder Entry-Element, einer Sicht werden soll, geben Sie die *Element* Elemente, die definieren, die Eigenschaften von .NET oder Skripts, die von dieser Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d46c1-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="d46c1-154">Wie in den vorherigen Beispielen gezeigt, die Formatierungsdatei kann mehrere Sichten enthalten, eine Ansicht kann mehrere Definitionen enthalten, und jede Definition kann mehrere Elemente enthalten.</span><span class="sxs-lookup"><span data-stu-id="d46c1-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="d46c1-155">Beispiel für eine Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="d46c1-155">Example of a Table View</span></span>

<span data-ttu-id="d46c1-156">Das folgende Beispiel zeigt die XML-Tags verwendet, um eine Tabellenansicht zu definieren, die zwei Spalten enthält.</span><span class="sxs-lookup"><span data-stu-id="d46c1-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="d46c1-157">Die [ViewDefinitions](./viewdefinitions-element-format.md) Element ist das Containerelement für alle Ansichten in der Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="d46c1-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="d46c1-158">Die [Ansicht](./view-element-format.md) -Element definiert, die bestimmte Tabelle, Liste, Breite oder benutzerdefinierte Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d46c1-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="d46c1-159">In jedem [Ansicht](./view-element-format.md) -Element, die [Name](./name-element-for-view-format.md) Element gibt den Namen der Ansicht der [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht und die verschiedenen verwenden Elemente (z. B. die `TableControl` -Element wird im folgenden Beispiel gezeigt) definieren Sie den Typ der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d46c1-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d46c1-160">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d46c1-160">See Also</span></span>

[<span data-ttu-id="d46c1-161">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="d46c1-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d46c1-162">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="d46c1-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d46c1-163">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="d46c1-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d46c1-164">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="d46c1-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d46c1-165">Schreiben eine PowerShell-Formatierung und Typendatei</span><span class="sxs-lookup"><span data-stu-id="d46c1-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
