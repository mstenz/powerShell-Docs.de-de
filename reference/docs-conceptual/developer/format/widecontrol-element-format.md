---
title: Widecontrol-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367989"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="a713e-102">Element „WideControl“ (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-102">WideControl Element (Format)</span></span>

<span data-ttu-id="a713e-103">Definiert ein breites Listenformat (Einzelwert) für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="a713e-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="a713e-104">Diese Ansicht zeigt einen einzelnen Eigenschafts Wert oder einen Skript Wert für jedes Objekt an.</span><span class="sxs-lookup"><span data-stu-id="a713e-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="a713e-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) widecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a713e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a713e-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a713e-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a713e-107">Attributes and Elements</span></span>

<span data-ttu-id="a713e-108">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `WideControl`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a713e-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="a713e-109">Sie können die Elemente `AutoSize` und `ColumnNumber` nicht gleichzeitig angeben.</span><span class="sxs-lookup"><span data-stu-id="a713e-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="a713e-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="a713e-110">Attributes</span></span>

<span data-ttu-id="a713e-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a713e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a713e-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a713e-112">Child Elements</span></span>

|<span data-ttu-id="a713e-113">Element</span><span class="sxs-lookup"><span data-stu-id="a713e-113">Element</span></span>|<span data-ttu-id="a713e-114">Description</span><span class="sxs-lookup"><span data-stu-id="a713e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a713e-115">AutoSize-Element für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="a713e-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a713e-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a713e-117">Gibt an, ob die Spaltengröße und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="a713e-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="a713e-118">ColumnNumber-Element für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="a713e-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a713e-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a713e-120">Gibt die Anzahl der Spalten an, die in der breiten Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a713e-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="a713e-121">Wideentries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="a713e-122">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="a713e-122">Required element.</span></span><br /><br /> <span data-ttu-id="a713e-123">Stellt die Definitionen der breiten Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="a713e-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a713e-124">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a713e-124">Parent Elements</span></span>

|<span data-ttu-id="a713e-125">Element</span><span class="sxs-lookup"><span data-stu-id="a713e-125">Element</span></span>|<span data-ttu-id="a713e-126">Description</span><span class="sxs-lookup"><span data-stu-id="a713e-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a713e-127">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="a713e-128">Definiert eine Ansicht, die verwendet wird, um ein oder mehrere .NET-Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a713e-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a713e-129">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a713e-129">Remarks</span></span>

<span data-ttu-id="a713e-130">Wenn Sie eine breite Sicht definieren, können Sie das `AutoSize`-Element oder den `ColumnNumber` hinzufügen, aber Sie können nicht beides hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a713e-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="a713e-131">In den meisten Fällen ist nur eine Definition für jede Breite Ansicht erforderlich, aber es ist möglich, mehrere Definitionen zu verwenden, wenn Sie dieselbe Ansicht verwenden möchten, um unterschiedliche .NET-Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a713e-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="a713e-132">In diesen Fällen können Sie eine separate Definition für jedes Objekt oder jede Gruppe von Objekten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a713e-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="a713e-133">Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Wide View Components](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a713e-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a713e-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a713e-134">Example</span></span>

<span data-ttu-id="a713e-135">Das folgende Beispiel zeigt ein `WideControl`-Element, das verwendet wird, um eine Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a713e-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="a713e-136">Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a713e-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a713e-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a713e-137">See Also</span></span>

[<span data-ttu-id="a713e-138">AutoSize-Element für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="a713e-139">ColumnNumber-Element für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="a713e-140">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="a713e-141">Wideentries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a713e-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="a713e-142">Breite Ansicht (Basic)</span><span class="sxs-lookup"><span data-stu-id="a713e-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="a713e-143">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="a713e-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a713e-144">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a713e-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
