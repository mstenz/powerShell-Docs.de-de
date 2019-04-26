---
title: FormatString-Element für TableColumnItem für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065629"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="f6246-102">Element „FormatString“ für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f6246-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="f6246-103">Gibt ein Formatmuster, das definiert, wie die Eigenschaft oder ein Skript-Wert, der in der Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f6246-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="f6246-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) TableColumnItems-Element (Format) TableColumnItem Konfigurationselement (Format) FormatString-Element für TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="f6246-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6246-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6246-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6246-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f6246-106">Attributes and Elements</span></span>

<span data-ttu-id="f6246-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `FormatString` Element.</span><span class="sxs-lookup"><span data-stu-id="f6246-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6246-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f6246-108">Attributes</span></span>

<span data-ttu-id="f6246-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="f6246-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6246-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f6246-110">Child Elements</span></span>

<span data-ttu-id="f6246-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="f6246-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f6246-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f6246-112">Parent Elements</span></span>

|<span data-ttu-id="f6246-113">Element</span><span class="sxs-lookup"><span data-stu-id="f6246-113">Element</span></span>|<span data-ttu-id="f6246-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f6246-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6246-115">TableColumnItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f6246-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f6246-116">Definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f6246-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f6246-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="f6246-117">Text Value</span></span>

<span data-ttu-id="f6246-118">Geben Sie das Muster, das zum Formatieren der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f6246-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="f6246-119">Dieses Muster kann z. B. zum Formatieren des Werts einer Eigenschaft, der den Typ verwendet werden [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: TT} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="f6246-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6246-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f6246-120">Remarks</span></span>

<span data-ttu-id="f6246-121">Formatzeichenfolgen können verwendet werden, wenn Sie Tabellenansichten, Listenansichten, Breiten Ansichten oder benutzerdefinierte Ansichten erstellen.</span><span class="sxs-lookup"><span data-stu-id="f6246-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="f6246-122">Weitere Informationen zum Formatieren eines Wert in einer Ansicht angezeigt, finden Sie unter [Formatieren von angezeigten Daten](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="f6246-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="f6246-123">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [Tabellenansicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f6246-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f6246-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6246-124">Example</span></span>

<span data-ttu-id="f6246-125">Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f6246-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="f6246-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f6246-126">See Also</span></span>

[<span data-ttu-id="f6246-127">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="f6246-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f6246-128">Formatieren der angezeigten Daten</span><span class="sxs-lookup"><span data-stu-id="f6246-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="f6246-129">TableColumnItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f6246-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="f6246-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6246-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
