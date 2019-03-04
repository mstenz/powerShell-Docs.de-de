---
title: TableControl-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858916"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="006e4-102">Element „TableControl“ (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-102">TableControl Element (Format)</span></span>

<span data-ttu-id="006e4-103">Definiert ein Table-Format für eine Sicht.</span><span class="sxs-lookup"><span data-stu-id="006e4-103">Defines a table format for a view.</span></span>

<span data-ttu-id="006e4-104">ViewDefinitions-Element (Format) anzeigen (Format) TableControl-Elementen (-Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="006e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="006e4-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="006e4-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="006e4-106">Attributes and Elements</span></span>

<span data-ttu-id="006e4-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableControl` Element.</span><span class="sxs-lookup"><span data-stu-id="006e4-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="006e4-108">Sie müssen die Zeilen der Tabelle angeben.</span><span class="sxs-lookup"><span data-stu-id="006e4-108">You must specify the rows of the table.</span></span> <span data-ttu-id="006e4-109">Alle anderen untergeordneten Elemente sind optional.</span><span class="sxs-lookup"><span data-stu-id="006e4-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="006e4-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="006e4-110">Attributes</span></span>

<span data-ttu-id="006e4-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="006e4-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="006e4-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="006e4-112">Child Elements</span></span>

|<span data-ttu-id="006e4-113">Element</span><span class="sxs-lookup"><span data-stu-id="006e4-113">Element</span></span>|<span data-ttu-id="006e4-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="006e4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="006e4-115">AutoSize-Element für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="006e4-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="006e4-116">Optional element.</span></span><br /><br /> <span data-ttu-id="006e4-117">Gibt an, ob die Größe der Spalte und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="006e4-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="006e4-118">HideTableHeaders-Element für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="006e4-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="006e4-119">Optional element.</span></span><br /><br /> <span data-ttu-id="006e4-120">Gibt an, ob die Kopfzeile der Tabelle nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="006e4-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="006e4-121">TableHeaders-Element für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="006e4-122">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="006e4-122">Required element.</span></span><br /><br /> <span data-ttu-id="006e4-123">Definiert die Bezeichnungen, die Breite und die Ausrichtung der Daten für die Spalten der Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="006e4-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="006e4-124">TableRowEntries-Element für TableCotrol (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-124">TableRowEntries Element for TableCotrol (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="006e4-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="006e4-125">Optional element.</span></span><br /><br /> <span data-ttu-id="006e4-126">Enthält die Definitionen der Tabellenansicht.</span><span class="sxs-lookup"><span data-stu-id="006e4-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="006e4-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="006e4-127">Parent Elements</span></span>

|<span data-ttu-id="006e4-128">Element</span><span class="sxs-lookup"><span data-stu-id="006e4-128">Element</span></span>|<span data-ttu-id="006e4-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="006e4-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="006e4-130">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="006e4-131">Definiert eine Ansicht, die verwendet wird, um die Mitglieder von ein oder mehrere Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="006e4-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="006e4-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="006e4-132">Remarks</span></span>

<span data-ttu-id="006e4-133">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="006e4-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="006e4-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="006e4-134">Example</span></span>

<span data-ttu-id="006e4-135">Dieses Beispiel zeigt eine `TableControl` -Element, das verwendet wird, zum Anzeigen der Eigenschaften der [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.</span><span class="sxs-lookup"><span data-stu-id="006e4-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="006e4-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="006e4-136">See Also</span></span>

[<span data-ttu-id="006e4-137">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="006e4-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="006e4-138">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="006e4-139">AutoSize-Element für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="006e4-140">HideTableHeaders-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="006e4-141">TableHeaders-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="006e4-142">TableRowEntries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="006e4-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="006e4-143">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="006e4-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
