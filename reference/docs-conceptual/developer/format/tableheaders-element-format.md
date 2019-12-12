---
title: TableHeaders-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361819"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="4388f-102">Element „TableHeaders“ (Format)</span><span class="sxs-lookup"><span data-stu-id="4388f-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="4388f-103">Definiert die Header für die Spalten einer Tabelle.</span><span class="sxs-lookup"><span data-stu-id="4388f-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="4388f-104">Viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tableHeaders-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="4388f-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4388f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4388f-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4388f-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="4388f-106">Attributes and Elements</span></span>

<span data-ttu-id="4388f-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und die übergeordneten Elemente des `TableHeaders`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4388f-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="4388f-108">Es muss ein untergeordnetes-Element für jede Eigenschaft des Objekts vorhanden sein, das angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="4388f-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="4388f-109">Die Spaltenheader Informationen werden in der Reihenfolge angezeigt, in der die untergeordneten Elemente angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="4388f-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4388f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="4388f-110">Attributes</span></span>

<span data-ttu-id="4388f-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="4388f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4388f-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4388f-112">Child Elements</span></span>

|<span data-ttu-id="4388f-113">Element</span><span class="sxs-lookup"><span data-stu-id="4388f-113">Element</span></span>|<span data-ttu-id="4388f-114">Description</span><span class="sxs-lookup"><span data-stu-id="4388f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4388f-115">Tablecolumnheader-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4388f-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="4388f-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="4388f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4388f-117">Definiert die Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte einer Tabellen Sicht.</span><span class="sxs-lookup"><span data-stu-id="4388f-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4388f-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4388f-118">Parent Elements</span></span>

|<span data-ttu-id="4388f-119">Element</span><span class="sxs-lookup"><span data-stu-id="4388f-119">Element</span></span>|<span data-ttu-id="4388f-120">Description</span><span class="sxs-lookup"><span data-stu-id="4388f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4388f-121">Tablecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4388f-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="4388f-122">Definiert ein Tabellenformat für eine Sicht.</span><span class="sxs-lookup"><span data-stu-id="4388f-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4388f-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4388f-123">Remarks</span></span>

<span data-ttu-id="4388f-124">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="4388f-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4388f-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4388f-125">Example</span></span>

<span data-ttu-id="4388f-126">Dieses Beispiel zeigt ein `TableHeaders`-Element, das zwei Spaltenheader definiert.</span><span class="sxs-lookup"><span data-stu-id="4388f-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4388f-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4388f-127">See Also</span></span>

[<span data-ttu-id="4388f-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="4388f-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4388f-129">Tablecolumnheader-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4388f-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="4388f-130">Tablecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4388f-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="4388f-131">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="4388f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
