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
ms.openlocfilehash: a38fcbef457e69e3ea08d25ba3a9843621036f1e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853106"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="b9649-102">Element „Width“ für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b9649-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="b9649-103">Definiert die Breite einer Spalte (in Zeichen).</span><span class="sxs-lookup"><span data-stu-id="b9649-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="b9649-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders Konfigurationselement für TableControl (Format) TableColumnHeader Element TableHeaders für TableControl (Format)-Width-Element für TableColumnHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b9649-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b9649-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9649-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b9649-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="b9649-106">Attributes and Elements</span></span>

<span data-ttu-id="b9649-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Width` Element, das verwendet wird, wenn Spaltenheader zu definieren.</span><span class="sxs-lookup"><span data-stu-id="b9649-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="b9649-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="b9649-108">Attributes</span></span>

<span data-ttu-id="b9649-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="b9649-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b9649-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9649-110">Child Elements</span></span>

<span data-ttu-id="b9649-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="b9649-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b9649-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="b9649-112">Parent Elements</span></span>

|<span data-ttu-id="b9649-113">Element</span><span class="sxs-lookup"><span data-stu-id="b9649-113">Element</span></span>|<span data-ttu-id="b9649-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9649-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9649-115">TableColumnHeader-Element für TableHeaders für TbleControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b9649-115">TableColumnHeader Element for TableHeaders for TbleControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="b9649-116">Definiert eine Bezeichnung, Breite und Ausrichtung der Daten für eine Spalte der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="b9649-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b9649-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="b9649-117">Text Value</span></span>

<span data-ttu-id="b9649-118">Geben Sie eine Breite (in Zeichen), die größer als die Länge der Eigenschaftswerte angezeigt wird, wenn bei der alle möglichen.</span><span class="sxs-lookup"><span data-stu-id="b9649-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9649-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b9649-119">Remarks</span></span>

<span data-ttu-id="b9649-120">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b9649-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b9649-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b9649-121">Example</span></span>

<span data-ttu-id="b9649-122">Das folgende Beispiel zeigt eine `TableColumnHeader` Element, dessen Breite 16 Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="b9649-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="b9649-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b9649-123">See Also</span></span>

[<span data-ttu-id="b9649-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="b9649-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b9649-125">TableColumnHeader-Element für TableHeader für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b9649-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="b9649-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9649-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
