---
title: Wideitem-Element für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361399"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="f7892-102">Element „WideItem“ für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="f7892-103">Definiert die Eigenschaft oder das Skript, dessen Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f7892-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="f7892-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) wideitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7892-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7892-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7892-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f7892-106">Attributes and Elements</span></span>

<span data-ttu-id="f7892-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `WideItem`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="f7892-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="f7892-108">Das `FormatString`-Element ist optional.</span><span class="sxs-lookup"><span data-stu-id="f7892-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="f7892-109">Sie müssen jedoch ein `PropertyName`-oder `ScriptBlock`-Element angeben, aber Sie können nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="f7892-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7892-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="f7892-110">Attributes</span></span>

<span data-ttu-id="f7892-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="f7892-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7892-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f7892-112">Child Elements</span></span>

|<span data-ttu-id="f7892-113">Element</span><span class="sxs-lookup"><span data-stu-id="f7892-113">Element</span></span>|<span data-ttu-id="f7892-114">Description</span><span class="sxs-lookup"><span data-stu-id="f7892-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7892-115">FormatString-Element für wideitem für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="f7892-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="f7892-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f7892-117">Gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f7892-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="f7892-118">PropertyName-Element für wideitem (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="f7892-119">Gibt die-Eigenschaft des-Objekts an, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f7892-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="f7892-120">ScriptBlock-Element für wideitem (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="f7892-121">Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f7892-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7892-122">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f7892-122">Parent Elements</span></span>

|<span data-ttu-id="f7892-123">Element</span><span class="sxs-lookup"><span data-stu-id="f7892-123">Element</span></span>|<span data-ttu-id="f7892-124">Description</span><span class="sxs-lookup"><span data-stu-id="f7892-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7892-125">Wideentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="f7892-126">Stellt eine Definition der breiten Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="f7892-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7892-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f7892-127">Remarks</span></span>

<span data-ttu-id="f7892-128">Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f7892-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f7892-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f7892-129">Example</span></span>

<span data-ttu-id="f7892-130">Das folgende Beispiel zeigt ein `WideEntry`-Element, das ein einzelnes `WideItem`-Element definiert.</span><span class="sxs-lookup"><span data-stu-id="f7892-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="f7892-131">Das `WideItem`-Element definiert die Eigenschaft oder das Skript, dessen Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f7892-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="f7892-132">Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="f7892-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7892-133">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f7892-133">See Also</span></span>

[<span data-ttu-id="f7892-134">FormatString-Element für wideitem für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="f7892-135">PropertyName-Element für wideitem (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="f7892-136">ScriptBlock-Element für wideitem (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="f7892-137">Wideentry-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f7892-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="f7892-138">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="f7892-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
