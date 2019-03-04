---
title: PropertyName-Element für TableColumnItem für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859466"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="7102c-102">Element „PropertyName“ für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7102c-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="7102c-103">Gibt die Eigenschaft, deren Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7102c-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="7102c-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) TableColumnItems-Element (Format) TableColumnItem Konfigurationselement (Format) PropertyName-Element für TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="7102c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7102c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7102c-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7102c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7102c-106">Attributes and Elements</span></span>

<span data-ttu-id="7102c-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="7102c-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7102c-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7102c-108">Attributes</span></span>

<span data-ttu-id="7102c-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="7102c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7102c-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7102c-110">Child Elements</span></span>

<span data-ttu-id="7102c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="7102c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7102c-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7102c-112">Parent Elements</span></span>

|<span data-ttu-id="7102c-113">Element</span><span class="sxs-lookup"><span data-stu-id="7102c-113">Element</span></span>|<span data-ttu-id="7102c-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7102c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7102c-115">TableColumnItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7102c-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="7102c-116">Definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7102c-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7102c-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="7102c-117">Text Value</span></span>

<span data-ttu-id="7102c-118">Geben Sie den Namen der Eigenschaft, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7102c-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="7102c-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7102c-119">Remarks</span></span>

<span data-ttu-id="7102c-120">Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7102c-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7102c-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7102c-121">Example</span></span>

<span data-ttu-id="7102c-122">Dieses Beispiel zeigt eine `TableColumnItem` Element, das angibt der `Status` Eigenschaft der ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="7102c-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="7102c-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7102c-123">See Also</span></span>

[<span data-ttu-id="7102c-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="7102c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7102c-125">TableColumnItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7102c-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="7102c-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="7102c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
