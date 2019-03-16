---
title: TableColumnItem-Element für TableColumnItems für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056990"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="e3b77-102">Element „TableColumnItem“ für TableColumnItems für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="e3b77-103">Definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3b77-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="e3b77-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries Konfigurationselement für TableControl (Format) TableRowEntry-Element für TableRowEntries für TableControl (Format) TableColumnItems-Element für TableControlEntry für TableControl (Format) TableColumnItem-Element für TableColumnItems für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3b77-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3b77-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3b77-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e3b77-106">Attributes and Elements</span></span>

<span data-ttu-id="e3b77-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableColumnItem` Element.</span><span class="sxs-lookup"><span data-stu-id="e3b77-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3b77-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="e3b77-108">Attributes</span></span>

<span data-ttu-id="e3b77-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="e3b77-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3b77-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e3b77-110">Child Elements</span></span>

|<span data-ttu-id="e3b77-111">Element</span><span class="sxs-lookup"><span data-stu-id="e3b77-111">Element</span></span>|<span data-ttu-id="e3b77-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e3b77-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3b77-113">Alignment-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e3b77-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e3b77-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e3b77-115">Definiert, wie die Daten in einer Spalte der Zeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3b77-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="e3b77-116">FormatString-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e3b77-117">Gibt ein Formatmuster, das zum Formatieren der Daten in der Spalte der Zeile verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3b77-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="e3b77-118">PropertyName-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e3b77-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e3b77-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e3b77-120">Gibt den Namen der Eigenschaft, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3b77-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="e3b77-121">ScriptBlock-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="e3b77-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e3b77-122">Optional element.</span></span><br /><br /> <span data-ttu-id="e3b77-123">Gibt das Skript an, dessen Wert in der Spalte einer Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3b77-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e3b77-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e3b77-124">Parent Elements</span></span>

|<span data-ttu-id="e3b77-125">Element</span><span class="sxs-lookup"><span data-stu-id="e3b77-125">Element</span></span>|<span data-ttu-id="e3b77-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e3b77-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3b77-127">TableColumnItems-Element für TableControlEntry für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e3b77-128">Definiert die Eigenschaften oder Skripts, die in der Zeile, deren Werte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e3b77-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e3b77-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e3b77-129">Remarks</span></span>

<span data-ttu-id="e3b77-130">Sie können eine Eigenschaft eines Objekts oder eines Skripts in jeder Spalte der Zeile angeben.</span><span class="sxs-lookup"><span data-stu-id="e3b77-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="e3b77-131">Wenn keine untergeordneten Elemente angegeben sind, wird das Element ist ein Platzhalter, und keine Daten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e3b77-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="e3b77-132">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e3b77-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e3b77-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e3b77-133">Example</span></span>

<span data-ttu-id="e3b77-134">Dieses Beispiel zeigt eine `TableColumnItem` -Element, das den Wert der `Status` Eigenschaft der ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="e3b77-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="e3b77-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e3b77-135">See Also</span></span>

[<span data-ttu-id="e3b77-136">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="e3b77-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e3b77-137">Alignment-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e3b77-138">TableColumnItems-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e3b77-139">FormatString-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e3b77-140">PropertyName-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e3b77-141">ScriptBlock-Element für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3b77-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="e3b77-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3b77-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
