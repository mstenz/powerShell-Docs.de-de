---
title: FormatString-Element für wideitem für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363029"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="00c79-102">Element „FormatString“ für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="00c79-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="00c79-103">Gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="00c79-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="00c79-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element für widecontrol (Format) wideitem-Element für widecontrol (Format) FormatString-Element für wideitem für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="00c79-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00c79-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="00c79-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00c79-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="00c79-106">Attributes and Elements</span></span>

<span data-ttu-id="00c79-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `FormatString`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="00c79-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00c79-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="00c79-108">Attributes</span></span>

<span data-ttu-id="00c79-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="00c79-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00c79-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="00c79-110">Child Elements</span></span>

<span data-ttu-id="00c79-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="00c79-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="00c79-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="00c79-112">Parent Elements</span></span>

|<span data-ttu-id="00c79-113">Element</span><span class="sxs-lookup"><span data-stu-id="00c79-113">Element</span></span>|<span data-ttu-id="00c79-114">Description</span><span class="sxs-lookup"><span data-stu-id="00c79-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00c79-115">Wideitem-Element für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="00c79-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="00c79-116">Definiert die Eigenschaft oder das Skript, dessen Wert in einer Zeile der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="00c79-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="00c79-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="00c79-117">Text Value</span></span>

<span data-ttu-id="00c79-118">Geben Sie das Muster an, das zum Formatieren der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="00c79-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="00c79-119">Beispielsweise können Sie dieses Muster verwenden, um den Wert einer beliebigen Eigenschaft vom Typ " [System. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}" zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="00c79-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="00c79-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="00c79-120">Remarks</span></span>

<span data-ttu-id="00c79-121">Format Zeichenfolgen können beim Erstellen von Tabellen Sichten, Listen Sichten, breiten Ansichten oder benutzerdefinierten Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="00c79-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="00c79-122">Weitere Informationen zum Formatieren eines in einer Ansicht angezeigten Werts finden Sie unter [Formatieren von angezeigten Daten](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="00c79-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="00c79-123">Weitere Informationen zum Verwenden von Format Zeichenfolgen in breiten Ansichten finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="00c79-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="00c79-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="00c79-124">Example</span></span>

<span data-ttu-id="00c79-125">Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.</span><span class="sxs-lookup"><span data-stu-id="00c79-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="00c79-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="00c79-126">See Also</span></span>

[<span data-ttu-id="00c79-127">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="00c79-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="00c79-128">Wideitem-Element für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="00c79-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="00c79-129">Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="00c79-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
