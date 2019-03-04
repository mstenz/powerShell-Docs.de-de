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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856876"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="66d64-102">Element „TableHeaders“ (Format)</span><span class="sxs-lookup"><span data-stu-id="66d64-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="66d64-103">Definiert die Header für die Spalten einer Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="66d64-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="66d64-104">ViewDefinitions-Element (Format) Element (Format) TableControl-Element (Format) TableHeaders Ansichtselement für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="66d64-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="66d64-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="66d64-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="66d64-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="66d64-106">Attributes and Elements</span></span>

<span data-ttu-id="66d64-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Elemente von der `TableHeaders` Element.</span><span class="sxs-lookup"><span data-stu-id="66d64-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="66d64-108">Es muss ein untergeordnetes Element für jede Eigenschaft des Objekts, das angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="66d64-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="66d64-109">Die Headerinformationen für die Spalte wird in der Reihenfolge angezeigt, dass die untergeordneten Elemente angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="66d64-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="66d64-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="66d64-110">Attributes</span></span>

<span data-ttu-id="66d64-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="66d64-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="66d64-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="66d64-112">Child Elements</span></span>

|<span data-ttu-id="66d64-113">Element</span><span class="sxs-lookup"><span data-stu-id="66d64-113">Element</span></span>|<span data-ttu-id="66d64-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="66d64-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66d64-115">TableColumnHeader-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="66d64-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="66d64-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="66d64-116">Optional element.</span></span><br /><br /> <span data-ttu-id="66d64-117">Definiert die Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte mit einer Tabellenansicht.</span><span class="sxs-lookup"><span data-stu-id="66d64-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="66d64-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="66d64-118">Parent Elements</span></span>

|<span data-ttu-id="66d64-119">Element</span><span class="sxs-lookup"><span data-stu-id="66d64-119">Element</span></span>|<span data-ttu-id="66d64-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="66d64-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="66d64-121">TableControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="66d64-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="66d64-122">Definiert ein Table-Format für eine Sicht.</span><span class="sxs-lookup"><span data-stu-id="66d64-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="66d64-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="66d64-123">Remarks</span></span>

<span data-ttu-id="66d64-124">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="66d64-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="66d64-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="66d64-125">Example</span></span>

<span data-ttu-id="66d64-126">Dieses Beispiel zeigt eine `TableHeaders` Element, das zwei Spaltenüberschriften definiert.</span><span class="sxs-lookup"><span data-stu-id="66d64-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="66d64-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="66d64-127">See Also</span></span>

[<span data-ttu-id="66d64-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="66d64-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="66d64-129">TableColumnHeader-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="66d64-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="66d64-130">TableControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="66d64-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="66d64-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="66d64-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
