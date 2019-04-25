---
title: TableRowEntries-Element für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075493"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="213eb-102">Element „TableRowEntries“ für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="213eb-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="213eb-103">Definiert die Zeilen der Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="213eb-103">Defines the rows of the table.</span></span>

<span data-ttu-id="213eb-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries Konfigurationselement für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="213eb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="213eb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="213eb-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="213eb-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="213eb-106">Attributes and Elements</span></span>

<span data-ttu-id="213eb-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableRowEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="213eb-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="213eb-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="213eb-108">Attributes</span></span>

<span data-ttu-id="213eb-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="213eb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="213eb-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="213eb-110">Child Elements</span></span>

|<span data-ttu-id="213eb-111">Element</span><span class="sxs-lookup"><span data-stu-id="213eb-111">Element</span></span>|<span data-ttu-id="213eb-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="213eb-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="213eb-113">TableRowEntry-Element für TableRowEntries für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="213eb-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="213eb-114">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="213eb-114">Required element.</span></span><br /><br /> <span data-ttu-id="213eb-115">Definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="213eb-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="213eb-116">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="213eb-116">Parent Elements</span></span>

|<span data-ttu-id="213eb-117">Element</span><span class="sxs-lookup"><span data-stu-id="213eb-117">Element</span></span>|<span data-ttu-id="213eb-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="213eb-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="213eb-119">TableControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="213eb-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="213eb-120">Definiert ein Table-Format für eine Sicht.</span><span class="sxs-lookup"><span data-stu-id="213eb-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="213eb-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="213eb-121">Remarks</span></span>

<span data-ttu-id="213eb-122">Sie müssen angeben, eine oder mehrere `TableRowEntry` Elemente für die Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="213eb-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="213eb-123">Es gibt keine maximale Beschränkung der Anzahl der `TableRowEntry` Elemente, die hinzugefügt werden können, noch ist die Reihenfolge von Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="213eb-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="213eb-124">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="213eb-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="213eb-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="213eb-125">Example</span></span>

<span data-ttu-id="213eb-126">Das folgende Beispiel zeigt eine `TableRowEntries` -Element, das eine Zeile definiert, die die Werte von zwei Eigenschaften des zeigt die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="213eb-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="213eb-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="213eb-127">See Also</span></span>

[<span data-ttu-id="213eb-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="213eb-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="213eb-129">TableControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="213eb-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="213eb-130">TableRowEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="213eb-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="213eb-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="213eb-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
