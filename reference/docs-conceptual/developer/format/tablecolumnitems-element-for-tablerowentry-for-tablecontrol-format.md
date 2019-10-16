---
title: Tablecolumnitems-Element für tablerowentry für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361809"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="8b382-102">Element „TableColumnItems“ für TableRowEntry für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8b382-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="8b382-103">Definiert die Eigenschaften oder Skripts, deren Werte in einer Zeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8b382-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="8b382-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element für tablecontrol (Format) tablerowentry-Element für tablerowentries für tablecontrol (Format) Tablecolumnitems-Element für tablecontrolentry für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="8b382-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b382-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8b382-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b382-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8b382-106">Attributes and Elements</span></span>

<span data-ttu-id="8b382-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `TableColumnItems`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8b382-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b382-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="8b382-108">Attributes</span></span>

<span data-ttu-id="8b382-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="8b382-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b382-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8b382-110">Child Elements</span></span>

|<span data-ttu-id="8b382-111">Element</span><span class="sxs-lookup"><span data-stu-id="8b382-111">Element</span></span>|<span data-ttu-id="8b382-112">Description</span><span class="sxs-lookup"><span data-stu-id="8b382-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b382-113">Tablecolumnitem-Element für tablecolumnitems für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="8b382-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="8b382-114">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="8b382-114">Required element.</span></span><br /><br /> <span data-ttu-id="8b382-115">Definiert die Eigenschaft oder das Skript, dessen Wert in einer Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b382-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8b382-116">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8b382-116">Parent Elements</span></span>

|<span data-ttu-id="8b382-117">Element</span><span class="sxs-lookup"><span data-stu-id="8b382-117">Element</span></span>|<span data-ttu-id="8b382-118">Description</span><span class="sxs-lookup"><span data-stu-id="8b382-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b382-119">Tablerowentry-Element für tablerowentries für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="8b382-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="8b382-120">Definiert die Daten, die in einer Zeile der Tabelle angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8b382-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8b382-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8b382-121">Remarks</span></span>

<span data-ttu-id="8b382-122">Für jede Spalte der Zeile ist ein `TableColumnItem`-Element erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8b382-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="8b382-123">Der erste Eintrag wird in der ersten Spalte angezeigt, der zweite Eintrag in der zweiten Spalte usw.</span><span class="sxs-lookup"><span data-stu-id="8b382-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="8b382-124">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="8b382-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8b382-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8b382-125">Example</span></span>

<span data-ttu-id="8b382-126">Das folgende Beispiel zeigt ein `TableColumnItems`-Element, das drei Eigenschaften des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts definiert.</span><span class="sxs-lookup"><span data-stu-id="8b382-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
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

```

## <a name="see-also"></a><span data-ttu-id="8b382-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8b382-127">See Also</span></span>

[<span data-ttu-id="8b382-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="8b382-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="8b382-129">Tablecolumnitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8b382-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="8b382-130">Tablerowentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8b382-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="8b382-131">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="8b382-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
