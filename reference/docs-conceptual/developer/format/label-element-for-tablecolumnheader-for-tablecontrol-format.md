---
title: Label-Element für tablecolumnheader für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365169"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="d72bb-102">Element „Label“ für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d72bb-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="d72bb-103">Definiert die Bezeichnung, die oben in einer Spalte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d72bb-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="d72bb-104">Dieses Element wird verwendet, wenn eine Tabellen Sicht definiert wird.</span><span class="sxs-lookup"><span data-stu-id="d72bb-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="d72bb-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tableHeaders-Element für tablecontrol (Format) tablecolumnheader-Element für tableHeaders für tablecontrol (Format) Label-Element für Tablecolumnheader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d72bb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d72bb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d72bb-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d72bb-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d72bb-107">Attributes and Elements</span></span>

<span data-ttu-id="d72bb-108">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Label`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d72bb-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="d72bb-109">Für jede Spalte ist nur eine Bezeichnung zulässig.</span><span class="sxs-lookup"><span data-stu-id="d72bb-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="d72bb-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d72bb-110">Attributes</span></span>

<span data-ttu-id="d72bb-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="d72bb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d72bb-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d72bb-112">Child Elements</span></span>

<span data-ttu-id="d72bb-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="d72bb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d72bb-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d72bb-114">Parent Elements</span></span>

|<span data-ttu-id="d72bb-115">Element</span><span class="sxs-lookup"><span data-stu-id="d72bb-115">Element</span></span>|<span data-ttu-id="d72bb-116">Description</span><span class="sxs-lookup"><span data-stu-id="d72bb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d72bb-117">Tablecolumnheader-Element für tableHeaders für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="d72bb-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="d72bb-118">Definiert eine Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="d72bb-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d72bb-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="d72bb-119">Text Value</span></span>

<span data-ttu-id="d72bb-120">Geben Sie den Text an, der oben in der Spalte der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d72bb-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="d72bb-121">Es sind keine eingeschränkten Zeichen für die Spalten Bezeichnung vorhanden.</span><span class="sxs-lookup"><span data-stu-id="d72bb-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="d72bb-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d72bb-122">Remarks</span></span>

<span data-ttu-id="d72bb-123">Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft verwendet, deren Wert in den Zeilen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d72bb-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="d72bb-124">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d72bb-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d72bb-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d72bb-125">Example</span></span>

<span data-ttu-id="d72bb-126">Dieses Beispiel zeigt ein `TableColumnHeader` Element, dessen Bezeichnung "Column 1" ist.</span><span class="sxs-lookup"><span data-stu-id="d72bb-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="d72bb-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d72bb-127">See Also</span></span>

[<span data-ttu-id="d72bb-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="d72bb-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d72bb-129">Tablecolumnheader-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d72bb-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="d72bb-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="d72bb-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
