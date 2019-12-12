---
title: FormatString-Element für ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363019"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="ee517-102">Element „FormatString“ für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ee517-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="ee517-103">Gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ee517-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="ee517-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListControl (Format) ListItems-Element für ListControl (Format) ListItem-Element für ListControl (Format) FormatString-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ee517-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee517-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee517-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ee517-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ee517-106">Attributes and Elements</span></span>

<span data-ttu-id="ee517-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `FormatString`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ee517-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ee517-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="ee517-108">Attributes</span></span>

<span data-ttu-id="ee517-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="ee517-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ee517-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ee517-110">Child Elements</span></span>

<span data-ttu-id="ee517-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="ee517-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ee517-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ee517-112">Parent Elements</span></span>

|<span data-ttu-id="ee517-113">Element</span><span class="sxs-lookup"><span data-stu-id="ee517-113">Element</span></span>|<span data-ttu-id="ee517-114">Description</span><span class="sxs-lookup"><span data-stu-id="ee517-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ee517-115">ListItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="ee517-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="ee517-116">Definiert die Eigenschaft oder das Skript, dessen Wert in einer Zeile der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ee517-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ee517-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="ee517-117">Text Value</span></span>

<span data-ttu-id="ee517-118">Geben Sie das Muster an, das zum Formatieren der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ee517-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="ee517-119">Beispielsweise können Sie dieses Muster verwenden, um den Wert einer beliebigen Eigenschaft vom Typ " [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}" zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="ee517-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee517-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ee517-120">Remarks</span></span>

<span data-ttu-id="ee517-121">Format Zeichenfolgen können beim Erstellen von Tabellen Sichten, Listen Sichten, breiten Ansichten oder benutzerdefinierten Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ee517-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="ee517-122">Weitere Informationen zum Formatieren eines in einer Ansicht angezeigten Werts finden Sie unter [Formatieren von angezeigten Daten](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="ee517-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="ee517-123">Weitere Informationen zum Verwenden von Format Zeichenfolgen in Listenansichten finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="ee517-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ee517-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ee517-124">Example</span></span>

<span data-ttu-id="ee517-125">Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.</span><span class="sxs-lookup"><span data-stu-id="ee517-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="ee517-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ee517-126">See Also</span></span>

[<span data-ttu-id="ee517-127">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="ee517-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ee517-128">ListItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="ee517-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="ee517-129">Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="ee517-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
