---
title: DefaultSettings-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363869"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="db560-102">Element „DefaultSettings“ (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="db560-103">Definiert allgemeine Einstellungen, die für alle Sichten der Formatierungs Datei gelten.</span><span class="sxs-lookup"><span data-stu-id="db560-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="db560-104">Zu den allgemeinen Einstellungen gehören das Anzeigen von Fehlern, das umschließen von Text in Tabellen, das Definieren der Erweiterung von Sammlungen und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="db560-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="db560-105">Configuration-Element (Format) DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db560-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="db560-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db560-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="db560-107">Attributes and Elements</span></span>

<span data-ttu-id="db560-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `DefaultSettings`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="db560-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db560-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="db560-109">Attributes</span></span>

<span data-ttu-id="db560-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="db560-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db560-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="db560-111">Child Elements</span></span>

|<span data-ttu-id="db560-112">Element</span><span class="sxs-lookup"><span data-stu-id="db560-112">Element</span></span>|<span data-ttu-id="db560-113">Description</span><span class="sxs-lookup"><span data-stu-id="db560-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db560-114">Display Error-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="db560-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="db560-115">Optional element.</span></span><br /><br /> <span data-ttu-id="db560-116">Gibt an, dass die Zeichenfolge #Err angezeigt wird, wenn ein Fehler auftritt, während ein Datenelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="db560-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="db560-117">Enumerableexpansions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="db560-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="db560-118">Optional element.</span></span><br /><br /> <span data-ttu-id="db560-119">Definiert die verschiedenen Möglichkeiten, wie .NET-Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="db560-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="db560-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="db560-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="db560-121">Optional element.</span></span><br /><br /> <span data-ttu-id="db560-122">Gibt die Mindestanzahl von Eigenschaften an, die ein Objekt besitzen muss, um das Objekt in einer Tabellenansicht anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="db560-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="db560-123">ShowError-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="db560-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="db560-124">Optional element.</span></span><br /><br /> <span data-ttu-id="db560-125">Gibt an, dass der vollständige Fehler Daten Satz angezeigt wird, wenn ein Fehler auftritt, während ein Datenelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="db560-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="db560-126">Wraptables-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="db560-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="db560-127">Optional element.</span></span><br /><br /> <span data-ttu-id="db560-128">Gibt an, dass Daten in einer Tabelle in die nächste Zeile verschoben werden, wenn Sie nicht in die Spaltenbreite passt.</span><span class="sxs-lookup"><span data-stu-id="db560-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db560-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="db560-129">Parent Elements</span></span>

|<span data-ttu-id="db560-130">Element</span><span class="sxs-lookup"><span data-stu-id="db560-130">Element</span></span>|<span data-ttu-id="db560-131">Description</span><span class="sxs-lookup"><span data-stu-id="db560-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db560-132">Configuration-Element</span><span class="sxs-lookup"><span data-stu-id="db560-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="db560-133">Stellt das Element der obersten Ebene einer Formatierungs Datei dar.</span><span class="sxs-lookup"><span data-stu-id="db560-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db560-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="db560-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="db560-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="db560-135">See Also</span></span>

[<span data-ttu-id="db560-136">Configuration-Element</span><span class="sxs-lookup"><span data-stu-id="db560-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="db560-137">Display Error-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="db560-138">Enumerableexpansions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="db560-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="db560-140">ShowError-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="db560-141">Wraptables-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="db560-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="db560-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="db560-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
