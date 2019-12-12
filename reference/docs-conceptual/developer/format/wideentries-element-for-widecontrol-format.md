---
title: Wideentries-Element für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361429"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="a44cc-102">Element „WideEntries“ für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a44cc-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="a44cc-103">Stellt die Definitionen der breiten Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="a44cc-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="a44cc-104">In der breiten Ansicht muss mindestens eine Definition angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a44cc-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="a44cc-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) widecontrol-Element (Format) wideentries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a44cc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a44cc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a44cc-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a44cc-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a44cc-107">Attributes and Elements</span></span>

<span data-ttu-id="a44cc-108">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `WideEntries`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a44cc-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="a44cc-109">Es muss mindestens ein untergeordnetes Element angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a44cc-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="a44cc-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="a44cc-110">Attributes</span></span>

<span data-ttu-id="a44cc-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a44cc-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a44cc-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a44cc-112">Child Elements</span></span>

|<span data-ttu-id="a44cc-113">Element</span><span class="sxs-lookup"><span data-stu-id="a44cc-113">Element</span></span>|<span data-ttu-id="a44cc-114">Description</span><span class="sxs-lookup"><span data-stu-id="a44cc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a44cc-115">Wideentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a44cc-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="a44cc-116">Stellt eine Definition der breiten Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="a44cc-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a44cc-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a44cc-117">Parent Elements</span></span>

|<span data-ttu-id="a44cc-118">Element</span><span class="sxs-lookup"><span data-stu-id="a44cc-118">Element</span></span>|<span data-ttu-id="a44cc-119">Description</span><span class="sxs-lookup"><span data-stu-id="a44cc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a44cc-120">Widecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a44cc-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="a44cc-121">Definiert ein breites Listenformat (Einzelwert) für die Sicht.</span><span class="sxs-lookup"><span data-stu-id="a44cc-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a44cc-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a44cc-122">Remarks</span></span>

<span data-ttu-id="a44cc-123">Eine breite Ansicht ist ein Listenformat, in dem ein einzelner Eigenschafts Wert oder ein Skript Wert für jedes Objekt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a44cc-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="a44cc-124">Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Wide View Components](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a44cc-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a44cc-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a44cc-125">Example</span></span>

<span data-ttu-id="a44cc-126">Das folgende Beispiel zeigt ein `WideEntries`-Element, das ein einzelnes `WideEntry` Element definiert.</span><span class="sxs-lookup"><span data-stu-id="a44cc-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="a44cc-127">Das `WideEntry`-Element enthält ein einzelnes `WideItem` Element, das definiert, welcher Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a44cc-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="a44cc-128">Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="a44cc-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a44cc-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a44cc-129">See Also</span></span>

[<span data-ttu-id="a44cc-130">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="a44cc-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a44cc-131">Widecontrol-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a44cc-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="a44cc-132">Wideentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a44cc-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="a44cc-133">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a44cc-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
