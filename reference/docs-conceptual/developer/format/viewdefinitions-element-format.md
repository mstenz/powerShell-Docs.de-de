---
title: Viewdefinitions-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361419"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="cef0c-102">Element „ViewDefinitions“ (Format)</span><span class="sxs-lookup"><span data-stu-id="cef0c-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="cef0c-103">Definiert die Sichten, die zum Anzeigen von .NET-Objekten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cef0c-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="cef0c-104">Diese Sichten können die Eigenschaften und Skript Werte eines Objekts in einem Tabellenformat, einem Listenformat, einem breiten Format und einem benutzerdefinierten Steuerelement Format anzeigen.</span><span class="sxs-lookup"><span data-stu-id="cef0c-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="cef0c-105">Configuration-Element (Format) viewdefinitions (Format XML)-Element</span><span class="sxs-lookup"><span data-stu-id="cef0c-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="cef0c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cef0c-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cef0c-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="cef0c-107">Attributes and Elements</span></span>

<span data-ttu-id="cef0c-108">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `ViewDefinitions`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="cef0c-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="cef0c-109">Es gibt keine Beschränkung für die Anzahl der Sichten, die in einer Formatierungs Datei definiert werden können, und Sie können in beliebiger Reihenfolge hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="cef0c-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="cef0c-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="cef0c-110">Attributes</span></span>

<span data-ttu-id="cef0c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="cef0c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cef0c-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cef0c-112">Child Elements</span></span>

|<span data-ttu-id="cef0c-113">Element</span><span class="sxs-lookup"><span data-stu-id="cef0c-113">Element</span></span>|<span data-ttu-id="cef0c-114">Description</span><span class="sxs-lookup"><span data-stu-id="cef0c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cef0c-115">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cef0c-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="cef0c-116">Definiert eine Ansicht, die verwendet wird, um ein oder mehrere .NET-Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="cef0c-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cef0c-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="cef0c-117">Parent Elements</span></span>

|<span data-ttu-id="cef0c-118">Element</span><span class="sxs-lookup"><span data-stu-id="cef0c-118">Element</span></span>|<span data-ttu-id="cef0c-119">Description</span><span class="sxs-lookup"><span data-stu-id="cef0c-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cef0c-120">Configuration-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cef0c-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="cef0c-121">Stellt das Element der obersten Ebene einer Formatierungs Datei dar.</span><span class="sxs-lookup"><span data-stu-id="cef0c-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cef0c-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cef0c-122">Remarks</span></span>

<span data-ttu-id="cef0c-123">Weitere Informationen zu den Komponenten der verschiedenen Sicht Typen finden Sie in den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="cef0c-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="cef0c-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="cef0c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="cef0c-125">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="cef0c-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="cef0c-126">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="cef0c-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="cef0c-127">Benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="cef0c-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="cef0c-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="cef0c-128">Example</span></span>

<span data-ttu-id="cef0c-129">Dieses Beispiel zeigt ein `ViewDefinitions`-Element, das die übergeordneten Elemente für eine Tabellenansicht und eine Listenansicht enthält.</span><span class="sxs-lookup"><span data-stu-id="cef0c-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cef0c-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cef0c-130">See Also</span></span>

[<span data-ttu-id="cef0c-131">Configuration-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cef0c-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="cef0c-132">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cef0c-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="cef0c-133">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="cef0c-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="cef0c-134">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="cef0c-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cef0c-135">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="cef0c-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="cef0c-136">Benutzerdefinierte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="cef0c-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="cef0c-137">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="cef0c-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
