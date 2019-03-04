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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861696"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="ce991-102">Element „CustomEntries“ für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="ce991-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="ce991-103">Enthält die Definitionen der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="ce991-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="ce991-104">Die Ansicht benutzerdefiniertes Steuerelement muss eine oder mehrere Definitionen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="ce991-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="ce991-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="ce991-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ce991-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce991-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ce991-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ce991-107">Attributes and Elements</span></span>

<span data-ttu-id="ce991-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControlEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="ce991-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="ce991-109">Sie müssen eine oder mehrere untergeordnete Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="ce991-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ce991-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="ce991-110">Attributes</span></span>

<span data-ttu-id="ce991-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="ce991-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ce991-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ce991-112">Child Elements</span></span>

|<span data-ttu-id="ce991-113">Element</span><span class="sxs-lookup"><span data-stu-id="ce991-113">Element</span></span>|<span data-ttu-id="ce991-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ce991-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce991-115">CustomEntry-Element für CustomEntries für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="ce991-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="ce991-116">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="ce991-116">Required element.</span></span><br /><br /> <span data-ttu-id="ce991-117">Stellt eine Definition der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="ce991-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ce991-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ce991-118">Parent Elements</span></span>

|<span data-ttu-id="ce991-119">Element</span><span class="sxs-lookup"><span data-stu-id="ce991-119">Element</span></span>|<span data-ttu-id="ce991-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ce991-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ce991-121">CustomControl-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="ce991-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="ce991-122">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="ce991-122">Required element.</span></span><br /><br /> <span data-ttu-id="ce991-123">Definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="ce991-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ce991-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ce991-124">Remarks</span></span>

<span data-ttu-id="ce991-125">In den meisten Fällen ein Steuerelement verfügt über nur eine Definition, die in einem einzelnen definiert ist `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="ce991-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="ce991-126">So ist es jedoch möglich, mehrere Definitionen zu besitzen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ce991-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="ce991-127">In diesen Fällen können Sie definieren eine `CustomEntry` -Element für jedes Objekt oder eine Gruppe von Objekten.</span><span class="sxs-lookup"><span data-stu-id="ce991-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce991-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ce991-128">See Also</span></span>

[<span data-ttu-id="ce991-129">CustomControl-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="ce991-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="ce991-130">CustomEntry-Element für CustomEntries für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="ce991-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ce991-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="ce991-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
