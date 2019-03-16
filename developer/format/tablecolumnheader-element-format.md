---
title: TableColumnHeader-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057874"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="bc524-102">Element „TableColumnHeader“ (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="bc524-103">Definiert die Bezeichnung, die die Breite der Spalte und die Ausrichtung der Beschriftung für eine Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="bc524-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="bc524-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders Konfigurationselement für TableControl (Format) TableColumnHeader-Element für TableHeaders für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc524-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc524-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc524-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="bc524-106">Attributes and Elements</span></span>

<span data-ttu-id="bc524-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TableColumnHeader` Element.</span><span class="sxs-lookup"><span data-stu-id="bc524-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc524-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="bc524-108">Attributes</span></span>

<span data-ttu-id="bc524-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="bc524-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc524-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bc524-110">Child Elements</span></span>

|<span data-ttu-id="bc524-111">Element</span><span class="sxs-lookup"><span data-stu-id="bc524-111">Element</span></span>|<span data-ttu-id="bc524-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bc524-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc524-113">Label-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="bc524-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bc524-114">Optional element.</span></span><br /><br /> <span data-ttu-id="bc524-115">Definiert die Bezeichnung, die am oberen Rand der Spalte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bc524-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="bc524-116">Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft, deren Wert in den Zeilen angezeigt wird, verwendet.</span><span class="sxs-lookup"><span data-stu-id="bc524-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="bc524-117">Width-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="bc524-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="bc524-118">Required element.</span></span><br /><br /> <span data-ttu-id="bc524-119">Gibt die Breite (in Zeichen) der Spalte.</span><span class="sxs-lookup"><span data-stu-id="bc524-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="bc524-120">Alignment-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="bc524-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bc524-121">Optional element.</span></span><br /><br /> <span data-ttu-id="bc524-122">Gibt an, wie die Bezeichnung der Spalte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bc524-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="bc524-123">Wenn keine Ausrichtung angegeben wird, wird die Bezeichnung auf der linken Seite ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="bc524-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc524-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bc524-124">Parent Elements</span></span>

|<span data-ttu-id="bc524-125">Element</span><span class="sxs-lookup"><span data-stu-id="bc524-125">Element</span></span>|<span data-ttu-id="bc524-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bc524-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc524-127">TableHeaders-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="bc524-128">Definiert die Spalten einer Tabelle-Sicht.</span><span class="sxs-lookup"><span data-stu-id="bc524-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc524-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bc524-129">Remarks</span></span>

<span data-ttu-id="bc524-130">Geben Sie einen Header für jede Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="bc524-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="bc524-131">Die Spalten werden angezeigt, in der Reihenfolge, in dem die `TableColumnHeader` Elemente definiert werden.</span><span class="sxs-lookup"><span data-stu-id="bc524-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="bc524-132">Eine Tabelle muss die gleiche Anzahl von besitzen `TableColumnHeader` Elemente wie `TableRowEntry` Elemente.</span><span class="sxs-lookup"><span data-stu-id="bc524-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="bc524-133">Die Kopfzeile der Spalte definiert, wie der Text am oberen Rand der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bc524-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="bc524-134">Die Zeileneinträge definieren, welche Daten in den Zeilen der Tabelle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bc524-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="bc524-135">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [Tabellenansicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="bc524-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bc524-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bc524-136">Example</span></span>

<span data-ttu-id="bc524-137">Das folgende Beispiel zeigt zwei `TableColumnHeader` Elemente.</span><span class="sxs-lookup"><span data-stu-id="bc524-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="bc524-138">Das erste Element definiert eine Spalte, deren Bezeichnung ist "Spalte 1" hat eine Breite von 16 Zeichen lang und auf der linken Seite, deren Bezeichnung ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="bc524-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="bc524-139">Das zweite Element definiert eine Spalte, deren Bezeichnung ist "Spalte 2" hat eine Breite von 10 Zeichen und, dessen Bezeichnung in der Spalte zentriert ist.</span><span class="sxs-lookup"><span data-stu-id="bc524-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bc524-140">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bc524-140">See Also</span></span>

[<span data-ttu-id="bc524-141">Alignment-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="bc524-142">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="bc524-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bc524-143">Label-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="bc524-144">TableHeaders-Element für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="bc524-145">Die Breite für TableColumnHeader für TableControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="bc524-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="bc524-146">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc524-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
