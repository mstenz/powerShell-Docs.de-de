---
title: CustomEntries-Element für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066514"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="22e39-102">Element „CustomEntries“ für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="22e39-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="22e39-103">Enthält die Definitionen der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="22e39-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="22e39-104">Die Ansicht benutzerdefiniertes Steuerelement muss eine oder mehrere Definitionen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="22e39-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="22e39-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22e39-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="22e39-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="22e39-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="22e39-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="22e39-107">Attributes and Elements</span></span>

<span data-ttu-id="22e39-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControlEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="22e39-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="22e39-109">Sie müssen eine oder mehrere untergeordnete Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="22e39-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="22e39-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="22e39-110">Attributes</span></span>

<span data-ttu-id="22e39-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="22e39-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="22e39-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="22e39-112">Child Elements</span></span>

|<span data-ttu-id="22e39-113">Element</span><span class="sxs-lookup"><span data-stu-id="22e39-113">Element</span></span>|<span data-ttu-id="22e39-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="22e39-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22e39-115">CustomEntry-Element für CustomEntries für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22e39-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="22e39-116">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="22e39-116">Required element.</span></span><br /><br /> <span data-ttu-id="22e39-117">Stellt eine Definition der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="22e39-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="22e39-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="22e39-118">Parent Elements</span></span>

|<span data-ttu-id="22e39-119">Element</span><span class="sxs-lookup"><span data-stu-id="22e39-119">Element</span></span>|<span data-ttu-id="22e39-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="22e39-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="22e39-121">CustomControl-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22e39-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="22e39-122">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="22e39-122">Required element.</span></span><br /><br /> <span data-ttu-id="22e39-123">Definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="22e39-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="22e39-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="22e39-124">Remarks</span></span>

<span data-ttu-id="22e39-125">In den meisten Fällen ein Steuerelement verfügt über nur eine Definition, die in einem einzelnen definiert ist `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="22e39-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="22e39-126">So ist es jedoch möglich, mehrere Definitionen zu besitzen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="22e39-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="22e39-127">In diesen Fällen können Sie definieren eine `CustomEntry` -Element für jedes Objekt oder eine Gruppe von Objekten.</span><span class="sxs-lookup"><span data-stu-id="22e39-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="22e39-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="22e39-128">See Also</span></span>

[<span data-ttu-id="22e39-129">CustomControl-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22e39-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="22e39-130">CustomEntry-Element für CustomEntries für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="22e39-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="22e39-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="22e39-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
