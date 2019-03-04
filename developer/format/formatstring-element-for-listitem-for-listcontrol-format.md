---
title: FormatString-Element für den ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860336"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="cc6d0-102">Element „FormatString“ für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cc6d0-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="cc6d0-103">Gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="cc6d0-104">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListControl (Format) ListItems-Element für ListControl (Format) ListItem-Element für ListControl (Format) FormatString-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="cc6d0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc6d0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cc6d0-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc6d0-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="cc6d0-106">Attributes and Elements</span></span>

<span data-ttu-id="cc6d0-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `FormatString` Element.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc6d0-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="cc6d0-108">Attributes</span></span>

<span data-ttu-id="cc6d0-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc6d0-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cc6d0-110">Child Elements</span></span>

<span data-ttu-id="cc6d0-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cc6d0-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cc6d0-112">Parent Elements</span></span>

|<span data-ttu-id="cc6d0-113">Element</span><span class="sxs-lookup"><span data-stu-id="cc6d0-113">Element</span></span>|<span data-ttu-id="cc6d0-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cc6d0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc6d0-115">ListItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cc6d0-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="cc6d0-116">Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cc6d0-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="cc6d0-117">Text Value</span></span>

<span data-ttu-id="cc6d0-118">Geben Sie das Muster, das zum Formatieren der Daten verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="cc6d0-119">Sie können z. B. dieses Muster verwenden, zum Formatieren des Werts einer Eigenschaft, die vom Typ [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: TT} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc6d0-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cc6d0-120">Remarks</span></span>

<span data-ttu-id="cc6d0-121">Formatzeichenfolgen können verwendet werden, wenn Sie Tabellenansichten, Listenansichten, Breiten Ansichten oder benutzerdefinierte Ansichten erstellen.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="cc6d0-122">Weitere Informationen zum Formatieren eines Wert in einer Ansicht angezeigt, finden Sie unter [Formatieren von angezeigten Daten](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d0-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="cc6d0-123">Weitere Informationen zur Verwendung von Formatzeichenfolgen in Listenansichten finden Sie unter [Listenansicht erstellen](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="cc6d0-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cc6d0-124">Beispiel</span><span class="sxs-lookup"><span data-stu-id="cc6d0-124">Example</span></span>

<span data-ttu-id="cc6d0-125">Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="cc6d0-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="cc6d0-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cc6d0-126">See Also</span></span>

[<span data-ttu-id="cc6d0-127">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="cc6d0-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cc6d0-128">ListItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cc6d0-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="cc6d0-129">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="cc6d0-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
