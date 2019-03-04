---
title: FormatString-Element für WideItem für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860936"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="e3c6d-102">Element „FormatString“ für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3c6d-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="e3c6d-103">Gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="e3c6d-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry Konfigurationselement für WideControl (Format) WideItem-Element für WideControl (Format) FormatString-Element für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3c6d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3c6d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3c6d-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3c6d-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e3c6d-106">Attributes and Elements</span></span>

<span data-ttu-id="e3c6d-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `FormatString` Element.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3c6d-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="e3c6d-108">Attributes</span></span>

<span data-ttu-id="e3c6d-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3c6d-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e3c6d-110">Child Elements</span></span>

<span data-ttu-id="e3c6d-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3c6d-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e3c6d-112">Parent Elements</span></span>

|<span data-ttu-id="e3c6d-113">Element</span><span class="sxs-lookup"><span data-stu-id="e3c6d-113">Element</span></span>|<span data-ttu-id="e3c6d-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e3c6d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3c6d-115">WideItem-Element für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3c6d-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="e3c6d-116">Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3c6d-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="e3c6d-117">Text Value</span></span>

<span data-ttu-id="e3c6d-118">Geben Sie das Muster, das zum Formatieren der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="e3c6d-119">Sie können z. B. dieses Muster verwenden, zum Formatieren des Werts einer Eigenschaft, die vom Typ [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: TT} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3c6d-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e3c6d-120">Remarks</span></span>

<span data-ttu-id="e3c6d-121">Formatzeichenfolgen können verwendet werden, wenn Sie Tabellenansichten, Listenansichten, Breiten Ansichten oder benutzerdefinierte Ansichten erstellen.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="e3c6d-122">Weitere Informationen zum Formatieren eines Wert in einer Ansicht angezeigt, finden Sie unter [Formatieren von angezeigten Daten](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="e3c6d-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="e3c6d-123">Weitere Informationen zur Verwendung von Formatzeichenfolgen in breiten Ansichten finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e3c6d-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e3c6d-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e3c6d-124">Example</span></span>

<span data-ttu-id="e3c6d-125">Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="e3c6d-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="e3c6d-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e3c6d-126">See Also</span></span>

[<span data-ttu-id="e3c6d-127">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="e3c6d-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e3c6d-128">WideItem-Element für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e3c6d-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="e3c6d-129">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="e3c6d-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
