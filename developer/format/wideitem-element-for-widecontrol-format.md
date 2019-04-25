---
title: WideItem-Element für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083636"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="d318c-102">Element „WideItem“ für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="d318c-103">Definiert die Eigenschaft oder ein Skript, dessen Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d318c-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="d318c-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) WideItem Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d318c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d318c-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d318c-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d318c-106">Attributes and Elements</span></span>

<span data-ttu-id="d318c-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `WideItem` Element.</span><span class="sxs-lookup"><span data-stu-id="d318c-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="d318c-108">Die `FormatString` Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="d318c-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="d318c-109">Allerdings müssen Sie angeben einer `PropertyName` oder `ScriptBlock` -Element, aber Sie können nicht beide angeben.</span><span class="sxs-lookup"><span data-stu-id="d318c-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="d318c-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="d318c-110">Attributes</span></span>

<span data-ttu-id="d318c-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="d318c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d318c-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d318c-112">Child Elements</span></span>

|<span data-ttu-id="d318c-113">Element</span><span class="sxs-lookup"><span data-stu-id="d318c-113">Element</span></span>|<span data-ttu-id="d318c-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d318c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d318c-115">FormatString-Element für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="d318c-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d318c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="d318c-117">Gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d318c-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="d318c-118">PropertyName-Element für WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="d318c-119">Gibt die Eigenschaft des Objekts, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d318c-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="d318c-120">ScriptBlock-Element für WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="d318c-121">Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d318c-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d318c-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d318c-122">Parent Elements</span></span>

|<span data-ttu-id="d318c-123">Element</span><span class="sxs-lookup"><span data-stu-id="d318c-123">Element</span></span>|<span data-ttu-id="d318c-124">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d318c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d318c-125">WideEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="d318c-126">Stellt eine Definition der breiten Ansicht.</span><span class="sxs-lookup"><span data-stu-id="d318c-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d318c-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d318c-127">Remarks</span></span>

<span data-ttu-id="d318c-128">Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d318c-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d318c-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d318c-129">Example</span></span>

<span data-ttu-id="d318c-130">Das folgende Beispiel zeigt eine `WideEntry` Element, das ein einzelnes definiert `WideItem` Element.</span><span class="sxs-lookup"><span data-stu-id="d318c-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="d318c-131">Die `WideItem` -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d318c-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="d318c-132">Ein vollständiges Beispiel eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="d318c-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d318c-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d318c-133">See Also</span></span>

[<span data-ttu-id="d318c-134">FormatString-Element für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="d318c-135">PropertyName-Element für WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="d318c-136">ScriptBlock-Element für WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="d318c-137">WideEntry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d318c-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="d318c-138">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="d318c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
