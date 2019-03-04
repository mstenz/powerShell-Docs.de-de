---
title: WideControl-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859826"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="e2641-102">Element „WideControl“ (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-102">WideControl Element (Format)</span></span>

<span data-ttu-id="e2641-103">Definiert eine Vielzahl (Einzelwert) Listenformat für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="e2641-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="e2641-104">Diese Ansicht zeigt eine einzelne Eigenschaft-Wert oder die Skriptwert für jedes Objekt.</span><span class="sxs-lookup"><span data-stu-id="e2641-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="e2641-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2641-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2641-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2641-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="e2641-107">Attributes and Elements</span></span>

<span data-ttu-id="e2641-108">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `WideControl` Element.</span><span class="sxs-lookup"><span data-stu-id="e2641-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="e2641-109">Sie können nicht angeben, die `AutoSize` und `ColumnNumber` Elemente zur gleichen Zeit.</span><span class="sxs-lookup"><span data-stu-id="e2641-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2641-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="e2641-110">Attributes</span></span>

<span data-ttu-id="e2641-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="e2641-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2641-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e2641-112">Child Elements</span></span>

|<span data-ttu-id="e2641-113">Element</span><span class="sxs-lookup"><span data-stu-id="e2641-113">Element</span></span>|<span data-ttu-id="e2641-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e2641-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2641-115">AutoSize-Element für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="e2641-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e2641-116">Optional element.</span></span><br /><br /> <span data-ttu-id="e2641-117">Gibt an, ob die Größe der Spalte und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="e2641-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="e2641-118">ColumnNumber-Element für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="e2641-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="e2641-119">Optional element.</span></span><br /><br /> <span data-ttu-id="e2641-120">Gibt die Anzahl der Spalten in der breiten Ansicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e2641-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="e2641-121">WideEntries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="e2641-122">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="e2641-122">Required element.</span></span><br /><br /> <span data-ttu-id="e2641-123">Enthält die Definitionen der breiten Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="e2641-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2641-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="e2641-124">Parent Elements</span></span>

|<span data-ttu-id="e2641-125">Element</span><span class="sxs-lookup"><span data-stu-id="e2641-125">Element</span></span>|<span data-ttu-id="e2641-126">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e2641-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2641-127">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e2641-128">Definiert eine Ansicht, die verwendet wird, um eine oder mehrere .NET Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e2641-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2641-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e2641-129">Remarks</span></span>

<span data-ttu-id="e2641-130">Wenn Sie eine Breite Ansicht definieren zu können, können Sie Hinzufügen der `AutoSize` Element oder die `ColumnNumber` jedoch beide kann nicht hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e2641-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="e2641-131">Klicken Sie in den meisten Fällen nur eine Definition für die einzelnen Breiten Ansichten erforderlich ist, aber es ist möglich, mehrere Definitionen zu besitzen, sollten Sie die gleiche Ansicht zu verwenden, um verschiedene .NET Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e2641-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="e2641-132">In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e2641-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="e2641-133">Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [Wide Ansichtskomponenten](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e2641-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e2641-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e2641-134">Example</span></span>

<span data-ttu-id="e2641-135">Das folgende Beispiel zeigt eine `WideControl` -Element, das verwendet wird, eine Eigenschaft der an die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="e2641-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="e2641-136">Ein vollständiges Beispiel eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="e2641-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2641-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e2641-137">See Also</span></span>

[<span data-ttu-id="e2641-138">AutoSize-Element für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="e2641-139">ColumnNumber-Element für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="e2641-140">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e2641-141">WideEntries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e2641-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="e2641-142">Breite Ansicht (Basic)</span><span class="sxs-lookup"><span data-stu-id="e2641-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="e2641-143">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="e2641-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e2641-144">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2641-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
