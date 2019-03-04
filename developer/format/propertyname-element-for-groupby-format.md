---
title: PropertyName-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863266"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="f4fee-102">Element „PropertyName“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f4fee-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="f4fee-103">Gibt die .NET-Eigenschaft, die eine neue Gruppe beginnt, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="f4fee-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="f4fee-104">Configuration Element (Format) ViewDefinitions-Element (Format) GroupBy Ansichtselement Element (Format) für Ansicht (Format)-PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f4fee-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4fee-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4fee-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4fee-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f4fee-106">Attributes and Elements</span></span>

<span data-ttu-id="f4fee-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="f4fee-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4fee-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="f4fee-108">Attributes</span></span>

<span data-ttu-id="f4fee-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="f4fee-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4fee-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f4fee-110">Child Elements</span></span>

<span data-ttu-id="f4fee-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="f4fee-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f4fee-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f4fee-112">Parent Elements</span></span>

|<span data-ttu-id="f4fee-113">Element</span><span class="sxs-lookup"><span data-stu-id="f4fee-113">Element</span></span>|<span data-ttu-id="f4fee-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f4fee-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4fee-115">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f4fee-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="f4fee-116">Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f4fee-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f4fee-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="f4fee-117">Text Value</span></span>

<span data-ttu-id="f4fee-118">Geben Sie den Namen der .NET-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f4fee-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4fee-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f4fee-119">Remarks</span></span>

<span data-ttu-id="f4fee-120">Windows PowerShell startet eine neue Gruppe aus, wenn der Wert dieser Eigenschaft geändert wird.</span><span class="sxs-lookup"><span data-stu-id="f4fee-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="f4fee-121">Wenn dieses Element angegeben ist, können Sie nicht angeben der ["scriptblock"](./scriptblock-element-for-groupby-format.md) Element um eine neue Gruppe zu starten.</span><span class="sxs-lookup"><span data-stu-id="f4fee-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="f4fee-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f4fee-122">Example</span></span>

<span data-ttu-id="f4fee-123">Das folgende Beispiel zeigt, wie Sie eine neue Gruppe zu starten, wenn der Wert einer Eigenschaft geändert wird.</span><span class="sxs-lookup"><span data-stu-id="f4fee-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="f4fee-124">Ein Beispiel für eine vollständige Formatierung-Datei, die dieses Element enthält, finden Sie unter [Breite Ansicht (-GroupBy)](./wide-view-groupby.md).</span><span class="sxs-lookup"><span data-stu-id="f4fee-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4fee-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f4fee-125">See Also</span></span>

[<span data-ttu-id="f4fee-126">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f4fee-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="f4fee-127">ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f4fee-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="f4fee-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4fee-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
