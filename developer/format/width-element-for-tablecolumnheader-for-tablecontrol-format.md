---
title: Width-Element für TableColumnHeader für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055188"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="5376c-102">Element „Width“ für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5376c-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="5376c-103">Definiert die Breite einer Spalte (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="5376c-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="5376c-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders Konfigurationselement für TableControl (Format) TableColumnHeader Element TableHeaders für TableControl (Format)-Width-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5376c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5376c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5376c-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5376c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="5376c-106">Attributes and Elements</span></span>

<span data-ttu-id="5376c-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Width` Element, das verwendet wird, wenn Spaltenheader zu definieren.</span><span class="sxs-lookup"><span data-stu-id="5376c-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="5376c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="5376c-108">Attributes</span></span>

<span data-ttu-id="5376c-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="5376c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5376c-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5376c-110">Child Elements</span></span>

<span data-ttu-id="5376c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="5376c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5376c-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="5376c-112">Parent Elements</span></span>

|<span data-ttu-id="5376c-113">Element</span><span class="sxs-lookup"><span data-stu-id="5376c-113">Element</span></span>|<span data-ttu-id="5376c-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5376c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5376c-115">TableColumnHeader-Element für TableHeaders für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5376c-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="5376c-116">Definiert eine Bezeichnung, Breite und Ausrichtung der Daten für eine Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="5376c-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5376c-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="5376c-117">Text Value</span></span>

<span data-ttu-id="5376c-118">Geben Sie eine Breite (in Zeichen), die größer als die Länge der Eigenschaftswerte angezeigt wird, wenn bei der alle möglichen.</span><span class="sxs-lookup"><span data-stu-id="5376c-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="5376c-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5376c-119">Remarks</span></span>

<span data-ttu-id="5376c-120">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5376c-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5376c-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="5376c-121">Example</span></span>

<span data-ttu-id="5376c-122">Das folgende Beispiel zeigt eine `TableColumnHeader` Element, dessen Breite 16 Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="5376c-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="5376c-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5376c-123">See Also</span></span>

[<span data-ttu-id="5376c-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="5376c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5376c-125">TableColumnHeader-Element für TableHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5376c-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="5376c-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="5376c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
