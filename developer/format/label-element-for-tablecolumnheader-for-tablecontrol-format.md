---
title: Versehen Sie Element für TableColumnHeader für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054508"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="3419c-102">Element „Label“ für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3419c-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="3419c-103">Definiert die Bezeichnung, die am oberen Rand einer Spalte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3419c-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="3419c-104">Dieses Element wird verwendet, wenn Sie eine Tabellensicht definieren.</span><span class="sxs-lookup"><span data-stu-id="3419c-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="3419c-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders Konfigurationselement für TableControl (Format) TableColumnHeader-Element für TableHeaders für TableControl (Format)-Label-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3419c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3419c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3419c-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3419c-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3419c-107">Attributes and Elements</span></span>

<span data-ttu-id="3419c-108">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Label` Element.</span><span class="sxs-lookup"><span data-stu-id="3419c-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="3419c-109">Nur eine Bezeichnung ist für die einzelnen Spalten zulässig.</span><span class="sxs-lookup"><span data-stu-id="3419c-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="3419c-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="3419c-110">Attributes</span></span>

<span data-ttu-id="3419c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="3419c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3419c-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3419c-112">Child Elements</span></span>

<span data-ttu-id="3419c-113">Keine.</span><span class="sxs-lookup"><span data-stu-id="3419c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3419c-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3419c-114">Parent Elements</span></span>

|<span data-ttu-id="3419c-115">Element</span><span class="sxs-lookup"><span data-stu-id="3419c-115">Element</span></span>|<span data-ttu-id="3419c-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3419c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3419c-117">TableColumnHeader-Element für TableHeaders für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3419c-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="3419c-118">Definiert eine Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="3419c-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3419c-119">Textwert</span><span class="sxs-lookup"><span data-stu-id="3419c-119">Text Value</span></span>

<span data-ttu-id="3419c-120">Geben Sie den Text, der am oberen Rand der Spalte der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3419c-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="3419c-121">Es gibt keine eingeschränkten Zeichen für die Bezeichnung der Spalte.</span><span class="sxs-lookup"><span data-stu-id="3419c-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="3419c-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3419c-122">Remarks</span></span>

<span data-ttu-id="3419c-123">Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft, deren Wert in den Zeilen angezeigt wird, verwendet.</span><span class="sxs-lookup"><span data-stu-id="3419c-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="3419c-124">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="3419c-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3419c-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3419c-125">Example</span></span>

<span data-ttu-id="3419c-126">Dieses Beispiel zeigt eine `TableColumnHeader` Element, dessen Bezeichnung ist "Spalte 1".</span><span class="sxs-lookup"><span data-stu-id="3419c-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="3419c-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3419c-127">See Also</span></span>

[<span data-ttu-id="3419c-128">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="3419c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3419c-129">TableColumnHeader-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="3419c-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="3419c-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="3419c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
