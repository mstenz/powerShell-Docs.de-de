---
title: PropertyName-Element für tablecolumnitem für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362249"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="a5382-102">Element „PropertyName“ für TableColumnItem für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a5382-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="a5382-103">Gibt die Eigenschaft an, deren Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a5382-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="a5382-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) tablecolumnitems-Element (Format) tablecolumnitem-Element (Format) PropertyName-Element für tablecolumnitem (Format)</span><span class="sxs-lookup"><span data-stu-id="a5382-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5382-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5382-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5382-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a5382-106">Attributes and Elements</span></span>

<span data-ttu-id="a5382-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a5382-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5382-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="a5382-108">Attributes</span></span>

<span data-ttu-id="a5382-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="a5382-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5382-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a5382-110">Child Elements</span></span>

<span data-ttu-id="a5382-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a5382-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5382-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a5382-112">Parent Elements</span></span>

|<span data-ttu-id="a5382-113">Element</span><span class="sxs-lookup"><span data-stu-id="a5382-113">Element</span></span>|<span data-ttu-id="a5382-114">Description</span><span class="sxs-lookup"><span data-stu-id="a5382-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5382-115">Tablecolumnitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a5382-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="a5382-116">Definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a5382-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a5382-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="a5382-117">Text Value</span></span>

<span data-ttu-id="a5382-118">Geben Sie den Namen der Eigenschaft an, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a5382-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5382-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a5382-119">Remarks</span></span>

<span data-ttu-id="a5382-120">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a5382-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5382-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a5382-121">Example</span></span>

<span data-ttu-id="a5382-122">Dieses Beispiel zeigt ein `TableColumnItem`-Element, das die `Status`-Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts angibt.</span><span class="sxs-lookup"><span data-stu-id="a5382-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="a5382-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a5382-123">See Also</span></span>

[<span data-ttu-id="a5382-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="a5382-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a5382-125">Tablecolumnitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a5382-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="a5382-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a5382-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
