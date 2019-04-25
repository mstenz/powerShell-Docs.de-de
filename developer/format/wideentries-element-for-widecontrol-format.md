---
title: WideEntries-Element für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083687"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="37774-102">Element „WideEntries“ für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="37774-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="37774-103">Enthält die Definitionen der breiten Ansicht an.</span><span class="sxs-lookup"><span data-stu-id="37774-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="37774-104">Die Breite Ansicht muss eine oder mehrere Definitionen angeben.</span><span class="sxs-lookup"><span data-stu-id="37774-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="37774-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="37774-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="37774-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="37774-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="37774-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="37774-107">Attributes and Elements</span></span>

<span data-ttu-id="37774-108">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `WideEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="37774-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="37774-109">Mindestens ein untergeordnetes Element muss angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="37774-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="37774-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="37774-110">Attributes</span></span>

<span data-ttu-id="37774-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="37774-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="37774-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="37774-112">Child Elements</span></span>

|<span data-ttu-id="37774-113">Element</span><span class="sxs-lookup"><span data-stu-id="37774-113">Element</span></span>|<span data-ttu-id="37774-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="37774-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37774-115">WideEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="37774-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="37774-116">Stellt eine Definition der breiten Ansicht.</span><span class="sxs-lookup"><span data-stu-id="37774-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="37774-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="37774-117">Parent Elements</span></span>

|<span data-ttu-id="37774-118">Element</span><span class="sxs-lookup"><span data-stu-id="37774-118">Element</span></span>|<span data-ttu-id="37774-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="37774-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="37774-120">WideControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="37774-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="37774-121">Definiert eine Vielzahl (Einzelwert) Listenformat für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="37774-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37774-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="37774-122">Remarks</span></span>

<span data-ttu-id="37774-123">Eine Breite Ansicht ist einer Liste an, in dem eine einzelne Eigenschaft-Wert oder die Skriptwert für jedes Objekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="37774-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="37774-124">Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [Wide Ansichtskomponenten](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="37774-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="37774-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="37774-125">Example</span></span>

<span data-ttu-id="37774-126">Das folgende Beispiel zeigt eine `WideEntries` Element, das ein einzelnes definiert `WideEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="37774-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="37774-127">Die `WideEntry` -Element enthält ein einzelnes `WideItem` Element, das definiert, welche Eigenschaft oder ein Skript-Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="37774-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="37774-128">Ein vollständiges Beispiel eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="37774-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37774-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="37774-129">See Also</span></span>

[<span data-ttu-id="37774-130">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="37774-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="37774-131">WideControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="37774-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="37774-132">WideEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="37774-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="37774-133">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="37774-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
