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
ms.openlocfilehash: 59cc0514087cc52438e0d1271b8b77a7799eb32c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855666"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="63b7b-102">Element „DefaultSettings“ (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="63b7b-103">Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.</span><span class="sxs-lookup"><span data-stu-id="63b7b-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="63b7b-104">Allgemeine Einstellungen umfassen das Anzeigen von Fehlern, Umbrechen von Text in Tabellen, die definieren, wie Sammlungen erweitert werden, und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="63b7b-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="63b7b-105">-Element (Format) DefaultSettings Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63b7b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="63b7b-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63b7b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="63b7b-107">Attributes and Elements</span></span>

<span data-ttu-id="63b7b-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `DefaultSettings` Element.</span><span class="sxs-lookup"><span data-stu-id="63b7b-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63b7b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="63b7b-109">Attributes</span></span>

<span data-ttu-id="63b7b-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="63b7b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63b7b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="63b7b-111">Child Elements</span></span>

|<span data-ttu-id="63b7b-112">Element</span><span class="sxs-lookup"><span data-stu-id="63b7b-112">Element</span></span>|<span data-ttu-id="63b7b-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="63b7b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63b7b-114">DisplayError-Element (Frmat)</span><span class="sxs-lookup"><span data-stu-id="63b7b-114">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="63b7b-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63b7b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="63b7b-116">Gibt an, dass die Zeichenfolge #ERR angezeigt wird, tritt ein Fehler beim Anzeigen eines Datenelements.</span><span class="sxs-lookup"><span data-stu-id="63b7b-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="63b7b-117">EnumerableExpansions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="63b7b-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63b7b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="63b7b-119">Definiert die verschiedenen Möglichkeiten, in der .NET Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="63b7b-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="63b7b-120">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="63b7b-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63b7b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="63b7b-122">Gibt die minimale Anzahl von Eigenschaften, die ein Objekt benötigen, um das Objekt in einer Tabellenansicht anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="63b7b-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="63b7b-123">ShowError-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="63b7b-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63b7b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="63b7b-125">Gibt an, dass es sich bei der vollständigen Fehlerdatensatz angezeigt wird, tritt ein Fehler beim Anzeigen eines Datenelements.</span><span class="sxs-lookup"><span data-stu-id="63b7b-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="63b7b-126">WrapTables-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="63b7b-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63b7b-127">Optional element.</span></span><br /><br /> <span data-ttu-id="63b7b-128">Gibt an, dass die Daten in einer Tabelle in der nächsten Zeile verschoben werden, wenn es sich nicht in die Breite der Spalte passt.</span><span class="sxs-lookup"><span data-stu-id="63b7b-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63b7b-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="63b7b-129">Parent Elements</span></span>

|<span data-ttu-id="63b7b-130">Element</span><span class="sxs-lookup"><span data-stu-id="63b7b-130">Element</span></span>|<span data-ttu-id="63b7b-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="63b7b-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63b7b-132">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="63b7b-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="63b7b-133">Das Element das obersten Ebene eine Formatierungsdatei darstellt.</span><span class="sxs-lookup"><span data-stu-id="63b7b-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63b7b-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="63b7b-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="63b7b-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="63b7b-135">See Also</span></span>

[<span data-ttu-id="63b7b-136">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="63b7b-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="63b7b-137">DisplayError-Element (Frmat)</span><span class="sxs-lookup"><span data-stu-id="63b7b-137">DisplayError Element (Frmat)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="63b7b-138">EnumerableExpansions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="63b7b-139">PropertyCountForTable (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="63b7b-140">ShowError-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="63b7b-141">WrapTables-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="63b7b-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="63b7b-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="63b7b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
