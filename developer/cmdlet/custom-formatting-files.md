---
title: Benutzerdefinierte Formatierung von Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068299"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="cf37f-102">Benutzerdefinierte Formatierungsdateien</span><span class="sxs-lookup"><span data-stu-id="cf37f-102">Custom Formatting Files</span></span>

<span data-ttu-id="cf37f-103">Das Anzeigeformat für die von Cmdlets, Funktionen und Skripts zurückgegebenen Objekte werden mithilfe von Formatierungsdateien (Format. ps1xml-Dateien) definiert.</span><span class="sxs-lookup"><span data-stu-id="cf37f-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="cf37f-104">Einige dieser Dateien werden von Windows PowerShell zum Definieren von des Standardanzeigeformat für diejenigen Objekte zurückgegeben, die von Windows PowerShell-Cmdlets bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="cf37f-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="cf37f-105">Sie können jedoch auch eigene benutzerdefinierte Formatierungsdateien die Standardformate für die Anzeige überschrieben oder die Anzeige von Objekten zurückgegeben, die durch Ihre eigenen Befehle definieren, erstellen.</span><span class="sxs-lookup"><span data-stu-id="cf37f-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="cf37f-106">Windows PowerShell verwendet die Daten in diese Formatierungsdateien, um zu bestimmen, was angezeigt wird und wie die Daten formatiert werden.</span><span class="sxs-lookup"><span data-stu-id="cf37f-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="cf37f-107">Die angezeigten Daten zählen die Eigenschaften eines Objekts oder der Wert eines Skriptblocks.</span><span class="sxs-lookup"><span data-stu-id="cf37f-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="cf37f-108">Skriptblöcke werden verwendet, wenn einen Wert, der nicht direkt über die Eigenschaften eines Objekts verfügbar ist, angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="cf37f-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="cf37f-109">Beispielsweise empfiehlt es sich, fügen Sie den Wert von zwei Eigenschaften eines Objekts und die Summe wird als ein separater Teil der Daten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cf37f-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="cf37f-110">Wenn Sie eine eigene Formatierung-Datei schreiben, müssen Sie definieren *Ansichten* für die Objekte, die Sie anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="cf37f-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="cf37f-111">Sie können eine einzelne Ansicht für jedes Objekt definieren, können Sie eine einzelne Ansicht für mehrere Objekte definieren oder Sie können mehrere Ansichten für das gleiche Objekt definieren.</span><span class="sxs-lookup"><span data-stu-id="cf37f-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="cf37f-112">Es gibt keine Beschränkung für die Anzahl der Aufrufe, die Sie definieren können.</span><span class="sxs-lookup"><span data-stu-id="cf37f-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf37f-113">Formatierungsdateien sind die Elemente eines Objekts nicht bestimmt werden, die an die Pipeline zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="cf37f-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="cf37f-114">Wenn ein Objekt an die Pipeline zurückgegeben wird, sind alle Member des Objekts verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cf37f-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="cf37f-115">Formatieren von Ansichten</span><span class="sxs-lookup"><span data-stu-id="cf37f-115">Format Views</span></span>

<span data-ttu-id="cf37f-116">Formatierung Ansichten können Objekte in ein Tabellenformat, einer Liste an, einen breiten Format und ein benutzerdefiniertes Format anzeigen.</span><span class="sxs-lookup"><span data-stu-id="cf37f-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="cf37f-117">Zum größten Teil, wird jede formatierungsdefinition durch eine Reihe von XML-Tags beschrieben, die eine Ansicht zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="cf37f-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="cf37f-118">Jede Ansicht enthält den Namen der Ansicht der Objekte, die die Sicht und die Elemente in der Ansicht, z. B. die Spalten- und Informationen für eine Tabellenansicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="cf37f-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="cf37f-119">Die folgenden Ansichten sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="cf37f-119">The following views are available.</span></span>

<span data-ttu-id="cf37f-120">Tabellenansicht werden die Eigenschaften eines Objekts oder einem Skript Block-Wert in einer oder mehreren Spalten aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="cf37f-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="cf37f-121">Jede Spalte stellt eine Eigenschaft des Objekts oder einen scriptblockwert Skript dar.</span><span class="sxs-lookup"><span data-stu-id="cf37f-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="cf37f-122">Sie können eine Tabellenansicht definieren, die alle Eigenschaften eines Objekts, das eine Teilmenge der Eigenschaften eines Objekts oder eine Kombination von Eigenschaften und Werte der Skript-Block wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cf37f-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="cf37f-123">Jede Zeile der Tabelle stellt dar, ein zurückgegebenes Objekt.</span><span class="sxs-lookup"><span data-stu-id="cf37f-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="cf37f-124">Weitere Informationen zu dieser Ansicht finden Sie unter [Tabellenansicht](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="cf37f-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="cf37f-125">Listenansicht sind die Eigenschaften eines Objekts oder einer Skript-Block-Wert in einer einzelnen Spalte aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="cf37f-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="cf37f-126">Jede Zeile der Liste zeigt eine optionale Bezeichnung oder den Eigenschaftennamen, gefolgt von den Wert des Blocks-Eigenschaft oder ein Skript.</span><span class="sxs-lookup"><span data-stu-id="cf37f-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="cf37f-127">Weitere Informationen zu dieser Ansicht finden Sie unter [Listenansicht](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="cf37f-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="cf37f-128">Breite Ansicht enthält eine einzelne Eigenschaft eines Objekts oder einem Skript Block-Wert in einer oder mehreren Spalten.</span><span class="sxs-lookup"><span data-stu-id="cf37f-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="cf37f-129">Es gibt keine Bezeichnung oder Header für diese Sicht.</span><span class="sxs-lookup"><span data-stu-id="cf37f-129">There is no label or header for this view.</span></span> <span data-ttu-id="cf37f-130">Weitere Informationen zu dieser Ansicht finden Sie unter [Breite Ansicht](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="cf37f-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="cf37f-131">Benutzerdefinierte Ansicht zeigt eine anpassbare Ansicht der Objekteigenschaften oder Skriptwerte-Block, die die starre Struktur der Tabellenansichten, Listenansichten oder breiten Ansichten nicht entspricht.</span><span class="sxs-lookup"><span data-stu-id="cf37f-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="cf37f-132">Sie können eine eigenständige benutzerdefinierte Ansicht definieren, oder Sie können definieren, eine benutzerdefinierte Ansicht, die von einer anderen Ansicht, z. B. eine Tabelle oder Ansicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cf37f-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="cf37f-133">Weitere Informationen zu dieser Ansicht finden Sie unter [benutzerdefinierte Sicht](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cf37f-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="cf37f-134">Die XML-Elemente anzeigen</span><span class="sxs-lookup"><span data-stu-id="cf37f-134">View XML Elements</span></span>

<span data-ttu-id="cf37f-135">Das folgende Beispiel zeigt die XML-Tags verwendet, um eine Tabellenansicht zu definieren, die zwei Spalten enthält.</span><span class="sxs-lookup"><span data-stu-id="cf37f-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="cf37f-136">Die [ViewDefinitions](../format/viewdefinitions-element-format.md) Element ist das Containerelement für alle Ansichten in der Formatierungsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="cf37f-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="cf37f-137">Die [Ansicht](../format/view-element-format.md) -Element definiert, die bestimmte Tabelle, Liste, Breite oder benutzerdefinierte Ansicht.</span><span class="sxs-lookup"><span data-stu-id="cf37f-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="cf37f-138">In jeder Ansicht der [Namen](../format/name-element-for-view-format.md) Element gibt den Namen der Ansicht der [ViewSelectedBy](../format/viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht und die verschiedenen Steuerelemente verwenden (z. B. die `TableControl` -Element) definieren Sie das Format der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="cf37f-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
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

## <a name="see-also"></a><span data-ttu-id="cf37f-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cf37f-139">See Also</span></span>

[<span data-ttu-id="cf37f-140">Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="cf37f-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="cf37f-141">Listenansicht</span><span class="sxs-lookup"><span data-stu-id="cf37f-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="cf37f-142">Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="cf37f-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="cf37f-143">Benutzerdefinierte Ansicht</span><span class="sxs-lookup"><span data-stu-id="cf37f-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="cf37f-144">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="cf37f-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
