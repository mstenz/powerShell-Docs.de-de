---
title: ViewDefinitions-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862086"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="1397b-102">Element „ViewDefinitions“ (Format)</span><span class="sxs-lookup"><span data-stu-id="1397b-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="1397b-103">Definiert die Ansichten, die zum Anzeigen von .NET Objekten verwendet.</span><span class="sxs-lookup"><span data-stu-id="1397b-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="1397b-104">Diese Sichten können die Eigenschaften und das Skriptwerte eines Objekts in ein Tabellenformat, Listenformat, Breiten Format und Format des benutzerdefinierten Steuerelements anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1397b-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="1397b-105">ViewDefinitions (XML-Format) von Konfigurationselement-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1397b-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="1397b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1397b-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1397b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="1397b-107">Attributes and Elements</span></span>

<span data-ttu-id="1397b-108">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ViewDefinitions` Element.</span><span class="sxs-lookup"><span data-stu-id="1397b-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="1397b-109">Es gibt keine Beschränkung der Anzahl der Sichten, die in einer Formatierungsdatei definiert werden können, und sie können in beliebiger Reihenfolge hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="1397b-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="1397b-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="1397b-110">Attributes</span></span>

<span data-ttu-id="1397b-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="1397b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1397b-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1397b-112">Child Elements</span></span>

|<span data-ttu-id="1397b-113">Element</span><span class="sxs-lookup"><span data-stu-id="1397b-113">Element</span></span>|<span data-ttu-id="1397b-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1397b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1397b-115">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1397b-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="1397b-116">Definiert eine Ansicht, die verwendet wird, um eine oder mehrere .NET Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1397b-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1397b-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1397b-117">Parent Elements</span></span>

|<span data-ttu-id="1397b-118">Element</span><span class="sxs-lookup"><span data-stu-id="1397b-118">Element</span></span>|<span data-ttu-id="1397b-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1397b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1397b-120">Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="1397b-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="1397b-121">Das Element das obersten Ebene eine Formatierungsdatei darstellt.</span><span class="sxs-lookup"><span data-stu-id="1397b-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1397b-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1397b-122">Remarks</span></span>

<span data-ttu-id="1397b-123">Weitere Informationen zu den Komponenten der verschiedenen Typen von Sichten finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="1397b-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="1397b-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="1397b-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="1397b-125">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="1397b-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="1397b-126">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="1397b-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="1397b-127">Benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="1397b-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="1397b-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1397b-128">Example</span></span>

<span data-ttu-id="1397b-129">Dieses Beispiel zeigt eine `ViewDefinitions` Element, das die übergeordneten Elemente für eine Tabelle und einer Listenansicht enthält.</span><span class="sxs-lookup"><span data-stu-id="1397b-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="1397b-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1397b-130">See Also</span></span>

[<span data-ttu-id="1397b-131">Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="1397b-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="1397b-132">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="1397b-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="1397b-133">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="1397b-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1397b-134">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="1397b-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1397b-135">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="1397b-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1397b-136">Benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="1397b-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1397b-137">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="1397b-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
