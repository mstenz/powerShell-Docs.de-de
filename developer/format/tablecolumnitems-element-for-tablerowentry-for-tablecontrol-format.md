---
title: TableColumnItems-Element für TableRowEntry für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056905"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="6affb-102">Element „TableColumnItems“ für TableRowEntry für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6affb-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="6affb-103">Definiert die Eigenschaften oder Skripts, die in einer Zeile, deren Werte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6affb-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="6affb-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries Konfigurationselement für TableControl (Format) TableRowEntry-Element für TableRowEntries für TableControl (Format) TableColumnItems-Element für TableControlEntry für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6affb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6affb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6affb-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6affb-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6affb-106">Attributes and Elements</span></span>

<span data-ttu-id="6affb-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableColumnItems` Element.</span><span class="sxs-lookup"><span data-stu-id="6affb-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6affb-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6affb-108">Attributes</span></span>

<span data-ttu-id="6affb-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="6affb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6affb-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6affb-110">Child Elements</span></span>

|<span data-ttu-id="6affb-111">Element</span><span class="sxs-lookup"><span data-stu-id="6affb-111">Element</span></span>|<span data-ttu-id="6affb-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6affb-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6affb-113">TableColumnItem-Element für TableColumnItems für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6affb-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="6affb-114">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="6affb-114">Required element.</span></span><br /><br /> <span data-ttu-id="6affb-115">Definiert die Eigenschaft oder das Skript in einer Spalte der Zeile, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6affb-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6affb-116">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6affb-116">Parent Elements</span></span>

|<span data-ttu-id="6affb-117">Element</span><span class="sxs-lookup"><span data-stu-id="6affb-117">Element</span></span>|<span data-ttu-id="6affb-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6affb-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6affb-119">TableRowEntry-Element für TableRowEntries für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6affb-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="6affb-120">Definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6affb-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6affb-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6affb-121">Remarks</span></span>

<span data-ttu-id="6affb-122">Ein `TableColumnItem` Element ist erforderlich für jede Spalte der Zeile.</span><span class="sxs-lookup"><span data-stu-id="6affb-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="6affb-123">Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.</span><span class="sxs-lookup"><span data-stu-id="6affb-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="6affb-124">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="6affb-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6affb-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6affb-125">Example</span></span>

<span data-ttu-id="6affb-126">Das folgende Beispiel zeigt eine `TableColumnItems` Element, das drei Eigenschaften definiert die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="6affb-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6affb-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6affb-127">See Also</span></span>

[<span data-ttu-id="6affb-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="6affb-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6affb-129">TableColumnItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6affb-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="6affb-130">TableRowEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6affb-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="6affb-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="6affb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
