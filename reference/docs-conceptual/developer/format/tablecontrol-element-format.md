---
title: Tablecontrol-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368199"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="f239f-102">Element „TableControl“ (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-102">TableControl Element (Format)</span></span>

<span data-ttu-id="f239f-103">Definiert ein Tabellenformat für eine Sicht.</span><span class="sxs-lookup"><span data-stu-id="f239f-103">Defines a table format for a view.</span></span>

<span data-ttu-id="f239f-104">Viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f239f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f239f-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f239f-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f239f-106">Attributes and Elements</span></span>

<span data-ttu-id="f239f-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TableControl`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f239f-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="f239f-108">Sie müssen die Zeilen der Tabelle angeben.</span><span class="sxs-lookup"><span data-stu-id="f239f-108">You must specify the rows of the table.</span></span> <span data-ttu-id="f239f-109">Alle anderen untergeordneten Elemente sind optional.</span><span class="sxs-lookup"><span data-stu-id="f239f-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="f239f-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f239f-110">Attributes</span></span>

<span data-ttu-id="f239f-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="f239f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f239f-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f239f-112">Child Elements</span></span>

|<span data-ttu-id="f239f-113">Element</span><span class="sxs-lookup"><span data-stu-id="f239f-113">Element</span></span>|<span data-ttu-id="f239f-114">Description</span><span class="sxs-lookup"><span data-stu-id="f239f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f239f-115">AutoSize-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="f239f-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f239f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f239f-117">Gibt an, ob die Spaltengröße und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="f239f-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="f239f-118">Hidetableheaders-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="f239f-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f239f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f239f-120">Gibt an, ob der Header der Tabelle nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f239f-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="f239f-121">TableHeaders-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="f239f-122">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="f239f-122">Required element.</span></span><br /><br /> <span data-ttu-id="f239f-123">Definiert die Bezeichnungen, die Breite und die Ausrichtung der Daten für die Spalten der Tabellenansicht.</span><span class="sxs-lookup"><span data-stu-id="f239f-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="f239f-124">Tablerowentries-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="f239f-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f239f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f239f-126">Stellt die Definitionen der Tabellenansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="f239f-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f239f-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f239f-127">Parent Elements</span></span>

|<span data-ttu-id="f239f-128">Element</span><span class="sxs-lookup"><span data-stu-id="f239f-128">Element</span></span>|<span data-ttu-id="f239f-129">Description</span><span class="sxs-lookup"><span data-stu-id="f239f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f239f-130">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="f239f-131">Definiert eine Ansicht, die zum Anzeigen der Member von einem oder mehreren-Objekten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f239f-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f239f-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f239f-132">Remarks</span></span>

<span data-ttu-id="f239f-133">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f239f-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f239f-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f239f-134">Example</span></span>

<span data-ttu-id="f239f-135">Dieses Beispiel zeigt ein `TableControl`-Element, das verwendet wird, um die Eigenschaften des [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f239f-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="f239f-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f239f-136">See Also</span></span>

[<span data-ttu-id="f239f-137">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="f239f-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f239f-138">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="f239f-139">AutoSize-Element für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="f239f-140">Hidetableheaders-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="f239f-141">TableHeaders-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="f239f-142">Tablerowentries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f239f-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="f239f-143">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="f239f-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
