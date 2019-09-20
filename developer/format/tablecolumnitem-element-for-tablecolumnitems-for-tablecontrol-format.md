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
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143581"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="b9032-102">Element „TableColumnItem“ für TableColumnItems für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="b9032-103">Definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b9032-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="b9032-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element für tablecontrol (Format) tablerowentry-Element für tablerowentries für tablecontrol (Format) Tablecolumnitems-Element für tablecontrolentry für tablecontrol (Format) tablecolumnitem-Element für tablecolumnitems für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9032-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9032-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9032-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b9032-106">Attributes and Elements</span></span>

<span data-ttu-id="b9032-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das über `TableColumnItem` geordnete Element des-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b9032-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9032-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="b9032-108">Attributes</span></span>

<span data-ttu-id="b9032-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="b9032-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9032-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9032-110">Child Elements</span></span>

|<span data-ttu-id="b9032-111">Element</span><span class="sxs-lookup"><span data-stu-id="b9032-111">Element</span></span>|<span data-ttu-id="b9032-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9032-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9032-113">Alignment-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b9032-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b9032-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b9032-115">Definiert, wie die Daten in einer Spalte der Zeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b9032-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="b9032-116">FormatString-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b9032-117">Gibt ein Format Muster an, das zum Formatieren der Daten in der Spalte der Zeile verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b9032-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="b9032-118">PropertyName-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b9032-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b9032-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b9032-120">Gibt den Namen der Eigenschaft an, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b9032-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="b9032-121">ScriptBlock-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="b9032-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="b9032-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b9032-123">Gibt das Skript an, dessen Wert in der Spalte einer Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b9032-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b9032-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9032-124">Parent Elements</span></span>

|<span data-ttu-id="b9032-125">Element</span><span class="sxs-lookup"><span data-stu-id="b9032-125">Element</span></span>|<span data-ttu-id="b9032-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9032-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9032-127">Tablecolumnitems-Element für tablecontrolentry für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="b9032-128">Definiert die Eigenschaften oder Skripts, deren Werte in der Zeile angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b9032-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b9032-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b9032-129">Remarks</span></span>

<span data-ttu-id="b9032-130">Sie können in jeder Spalte der Zeile eine Eigenschaft eines Objekts oder eines Skripts angeben.</span><span class="sxs-lookup"><span data-stu-id="b9032-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="b9032-131">Wenn keine untergeordneten Elemente angegeben werden, ist das Element ein Platzhalter, und es werden keine Daten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b9032-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="b9032-132">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b9032-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9032-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b9032-133">Example</span></span>

<span data-ttu-id="b9032-134">Dieses Beispiel zeigt ein `TableColumnItem` -Element, das den Wert `Status` der-Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts anzeigt.</span><span class="sxs-lookup"><span data-stu-id="b9032-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="b9032-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b9032-135">See Also</span></span>

[<span data-ttu-id="b9032-136">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="b9032-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b9032-137">Alignment-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b9032-138">Tablecolumnitems-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="b9032-139">FormatString-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b9032-140">PropertyName-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b9032-141">ScriptBlock-Element für tablecolumnitem für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b9032-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="b9032-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="b9032-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
