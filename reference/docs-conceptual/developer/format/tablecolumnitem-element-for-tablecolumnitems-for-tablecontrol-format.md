---
title: Tablecolumnitem-Element für tablecolumnitems für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368229"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="af49b-102">Element „TableColumnItem“ für TableColumnItems für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="af49b-103">Definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="af49b-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="af49b-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element für tablecontrol (Format) tablerowentry-Element für tablerowentries für tablecontrol (Format) Tablecolumnitems-Element für tablecontrolentry für tablecontrol (Format) tablecolumnitem-Element für tablecolumnitems für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="af49b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="af49b-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="af49b-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="af49b-106">Attributes and Elements</span></span>

<span data-ttu-id="af49b-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `TableColumnItem`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="af49b-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="af49b-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="af49b-108">Attributes</span></span>

<span data-ttu-id="af49b-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="af49b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="af49b-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="af49b-110">Child Elements</span></span>

|<span data-ttu-id="af49b-111">Element</span><span class="sxs-lookup"><span data-stu-id="af49b-111">Element</span></span>|<span data-ttu-id="af49b-112">Description</span><span class="sxs-lookup"><span data-stu-id="af49b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af49b-113">Alignment-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="af49b-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="af49b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="af49b-115">Definiert, wie die Daten in einer Spalte der Zeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="af49b-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="af49b-116">FormatString-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="af49b-117">Gibt ein Format Muster an, das zum Formatieren der Daten in der Spalte der Zeile verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="af49b-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="af49b-118">PropertyName-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="af49b-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="af49b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="af49b-120">Gibt den Namen der Eigenschaft an, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="af49b-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="af49b-121">ScriptBlock-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="af49b-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="af49b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="af49b-123">Gibt das Skript an, dessen Wert in der Spalte einer Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="af49b-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="af49b-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="af49b-124">Parent Elements</span></span>

|<span data-ttu-id="af49b-125">Element</span><span class="sxs-lookup"><span data-stu-id="af49b-125">Element</span></span>|<span data-ttu-id="af49b-126">Description</span><span class="sxs-lookup"><span data-stu-id="af49b-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="af49b-127">Tablecolumnitems-Element für tablecontrolentry für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="af49b-128">Definiert die Eigenschaften oder Skripts, deren Werte in der Zeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="af49b-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="af49b-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="af49b-129">Remarks</span></span>

<span data-ttu-id="af49b-130">Sie können in jeder Spalte der Zeile eine Eigenschaft eines Objekts oder eines Skripts angeben.</span><span class="sxs-lookup"><span data-stu-id="af49b-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="af49b-131">Wenn keine untergeordneten Elemente angegeben werden, ist das Element ein Platzhalter, und es werden keine Daten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af49b-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="af49b-132">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="af49b-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="af49b-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af49b-133">Example</span></span>

<span data-ttu-id="af49b-134">Dieses Beispiel zeigt ein `TableColumnItem`-Element, das den Wert der `Status`-Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts anzeigt.</span><span class="sxs-lookup"><span data-stu-id="af49b-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="af49b-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="af49b-135">See Also</span></span>

[<span data-ttu-id="af49b-136">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="af49b-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="af49b-137">Alignment-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="af49b-138">Tablecolumnitems-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="af49b-139">FormatString-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="af49b-140">PropertyName-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="af49b-141">ScriptBlock-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="af49b-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="af49b-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="af49b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
