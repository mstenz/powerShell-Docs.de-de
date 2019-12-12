---
title: Width-Element für tablecolumnheader für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367869"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="ecda8-102">Element „Width“ für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ecda8-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="ecda8-103">Definiert die Breite einer Spalte (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="ecda8-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="ecda8-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tableHeaders-Element für tablecontrol (Format) tablecolumnheader-Element tableHeaders für tablecontrol (Format) width-Element für Tablecolumnheader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="ecda8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ecda8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ecda8-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ecda8-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ecda8-106">Attributes and Elements</span></span>

<span data-ttu-id="ecda8-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Width`-Elements beschrieben, das beim Definieren von Spalten Headern verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ecda8-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="ecda8-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="ecda8-108">Attributes</span></span>

<span data-ttu-id="ecda8-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="ecda8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ecda8-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ecda8-110">Child Elements</span></span>

<span data-ttu-id="ecda8-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="ecda8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ecda8-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ecda8-112">Parent Elements</span></span>

|<span data-ttu-id="ecda8-113">Element</span><span class="sxs-lookup"><span data-stu-id="ecda8-113">Element</span></span>|<span data-ttu-id="ecda8-114">Description</span><span class="sxs-lookup"><span data-stu-id="ecda8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ecda8-115">Tablecolumnheader-Element für tableHeaders für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="ecda8-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="ecda8-116">Definiert eine Bezeichnung, eine Breite und eine Ausrichtung der Daten für eine Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="ecda8-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ecda8-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="ecda8-117">Text Value</span></span>

<span data-ttu-id="ecda8-118">Geben Sie ggf. eine Breite (in Zeichen) an, die größer als die Länge der angezeigten Eigenschaftswerte ist.</span><span class="sxs-lookup"><span data-stu-id="ecda8-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecda8-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ecda8-119">Remarks</span></span>

<span data-ttu-id="ecda8-120">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ecda8-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ecda8-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ecda8-121">Example</span></span>

<span data-ttu-id="ecda8-122">Das folgende Beispiel zeigt ein `TableColumnHeader`-Element, dessen Breite aus 16 Zeichen besteht.</span><span class="sxs-lookup"><span data-stu-id="ecda8-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="ecda8-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ecda8-123">See Also</span></span>

[<span data-ttu-id="ecda8-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="ecda8-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ecda8-125">Tablecolumnheader-Element für TableHeader für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="ecda8-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="ecda8-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="ecda8-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
