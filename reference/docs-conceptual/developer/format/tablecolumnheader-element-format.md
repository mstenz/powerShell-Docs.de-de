---
title: Tablecolumnheader-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361849"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="64b97-102">Element „TableColumnHeader“ (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="64b97-103">Definiert die Bezeichnung, die Breite der Spalte und die Ausrichtung der Bezeichnung für eine Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="64b97-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="64b97-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tableHeaders-Element für tablecontrol (Format) tablecolumnheader-Element für tableHeaders für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="64b97-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="64b97-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="64b97-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="64b97-106">Attributes and Elements</span></span>

<span data-ttu-id="64b97-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TableColumnHeader`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="64b97-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="64b97-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="64b97-108">Attributes</span></span>

<span data-ttu-id="64b97-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="64b97-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="64b97-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="64b97-110">Child Elements</span></span>

|<span data-ttu-id="64b97-111">Element</span><span class="sxs-lookup"><span data-stu-id="64b97-111">Element</span></span>|<span data-ttu-id="64b97-112">Description</span><span class="sxs-lookup"><span data-stu-id="64b97-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64b97-113">Label-Element für tablecolumnheader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="64b97-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="64b97-114">Optional element.</span></span><br /><br /> <span data-ttu-id="64b97-115">Definiert die Bezeichnung, die am oberen Rand der Spalte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="64b97-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="64b97-116">Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft verwendet, deren Wert in den Zeilen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="64b97-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="64b97-117">Width-Element für tablecolumnheader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="64b97-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="64b97-118">Required element.</span></span><br /><br /> <span data-ttu-id="64b97-119">Gibt die Breite (in Zeichen) der Spalte an.</span><span class="sxs-lookup"><span data-stu-id="64b97-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="64b97-120">Alignment-Element für tablecolumnheader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="64b97-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="64b97-121">Optional element.</span></span><br /><br /> <span data-ttu-id="64b97-122">Gibt an, wie die Bezeichnung der Spalte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="64b97-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="64b97-123">Wenn keine Ausrichtung angegeben wird, wird die Bezeichnung linksbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="64b97-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="64b97-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="64b97-124">Parent Elements</span></span>

|<span data-ttu-id="64b97-125">Element</span><span class="sxs-lookup"><span data-stu-id="64b97-125">Element</span></span>|<span data-ttu-id="64b97-126">Description</span><span class="sxs-lookup"><span data-stu-id="64b97-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="64b97-127">TableHeaders-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="64b97-128">Definiert die Spalten einer Tabellen Sicht.</span><span class="sxs-lookup"><span data-stu-id="64b97-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="64b97-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="64b97-129">Remarks</span></span>

<span data-ttu-id="64b97-130">Geben Sie einen Header für jede Spalte der Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="64b97-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="64b97-131">Die Spalten werden in der Reihenfolge angezeigt, in der die `TableColumnHeader`-Elemente definiert sind.</span><span class="sxs-lookup"><span data-stu-id="64b97-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="64b97-132">Eine Tabelle muss die gleiche Anzahl von `TableColumnHeader`-Elementen wie `TableRowEntry`-Elemente aufweisen.</span><span class="sxs-lookup"><span data-stu-id="64b97-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="64b97-133">Der Spaltenheader definiert, wie der Text oben in der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="64b97-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="64b97-134">Die Zeilen Einträge definieren, welche Daten in den Zeilen der Tabelle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="64b97-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="64b97-135">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="64b97-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="64b97-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="64b97-136">Example</span></span>

<span data-ttu-id="64b97-137">Das folgende Beispiel zeigt zwei `TableColumnHeader`-Elemente.</span><span class="sxs-lookup"><span data-stu-id="64b97-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="64b97-138">Das erste Element definiert eine Spalte, deren Bezeichnung "Column 1" ist, eine Breite von 16 Zeichen hat und deren Bezeichnung linksbündig ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="64b97-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="64b97-139">Das zweite Element definiert eine Spalte, deren Bezeichnung "Column 2" ist, eine Breite von 10 Zeichen aufweist und deren Bezeichnung in der Spalte zentriert ist.</span><span class="sxs-lookup"><span data-stu-id="64b97-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="64b97-140">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="64b97-140">See Also</span></span>

[<span data-ttu-id="64b97-141">Alignment-Element für tablecolumnheader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="64b97-142">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="64b97-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="64b97-143">Label-Element für tablecolumnheader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="64b97-144">TableHeaders-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="64b97-145">Breite für tablecolumnheader für tablecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="64b97-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="64b97-146">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="64b97-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
