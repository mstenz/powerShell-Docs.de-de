---
title: Wideentry-Element für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367899"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="7649c-102">Element „WideEntry“ für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="7649c-103">Stellt eine Definition der breiten Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="7649c-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="7649c-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7649c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7649c-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7649c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7649c-106">Attributes and Elements</span></span>

<span data-ttu-id="7649c-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `WideEntry`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7649c-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="7649c-108">Sie müssen ein einzelnes untergeordnetes `WideItem`-Element angeben.</span><span class="sxs-lookup"><span data-stu-id="7649c-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7649c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="7649c-109">Attributes</span></span>

<span data-ttu-id="7649c-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="7649c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7649c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7649c-111">Child Elements</span></span>

|<span data-ttu-id="7649c-112">Element</span><span class="sxs-lookup"><span data-stu-id="7649c-112">Element</span></span>|<span data-ttu-id="7649c-113">Description</span><span class="sxs-lookup"><span data-stu-id="7649c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7649c-114">Entryselectedby-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="7649c-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="7649c-115">Optional element.</span></span><br /><br /> <span data-ttu-id="7649c-116">Definiert die .NET-Typen, die diese Breite Eingabe Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="7649c-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="7649c-117">Wideitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="7649c-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="7649c-118">Required element.</span></span><br /><br /> <span data-ttu-id="7649c-119">Definiert die Eigenschaft oder das Skript, dessen Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7649c-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7649c-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7649c-120">Parent Elements</span></span>

|<span data-ttu-id="7649c-121">Element</span><span class="sxs-lookup"><span data-stu-id="7649c-121">Element</span></span>|<span data-ttu-id="7649c-122">Description</span><span class="sxs-lookup"><span data-stu-id="7649c-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7649c-123">Wideentries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="7649c-124">Stellt die Definitionen der breiten Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="7649c-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7649c-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7649c-125">Remarks</span></span>

<span data-ttu-id="7649c-126">Eine breite Ansicht ist ein Listenformat, in dem ein einzelner Eigenschafts Wert oder ein Skript Wert für jedes Objekt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7649c-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="7649c-127">Im Gegensatz zu anderen Sicht Typen können Sie für jede Sicht Definition nur ein Element Element angeben.</span><span class="sxs-lookup"><span data-stu-id="7649c-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="7649c-128">Weitere Informationen zu den anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7649c-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7649c-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7649c-129">Example</span></span>

<span data-ttu-id="7649c-130">Das folgende Beispiel zeigt ein `WideEntry`-Element, das ein einzelnes `WideItem`-Element definiert.</span><span class="sxs-lookup"><span data-stu-id="7649c-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="7649c-131">Das `WideItem`-Element definiert die-Eigenschaft, deren Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7649c-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="7649c-132">Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="7649c-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7649c-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7649c-133">See Also</span></span>

[<span data-ttu-id="7649c-134">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="7649c-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7649c-135">Selectioncondition-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7649c-136">Selectionsetname-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="7649c-137">Tyname-Element für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="7649c-138">Wideentries-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="7649c-139">Wideitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7649c-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="7649c-140">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="7649c-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
