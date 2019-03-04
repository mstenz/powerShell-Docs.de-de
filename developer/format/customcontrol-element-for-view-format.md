---
title: CustomControl-Element für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861256"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="c8e09-102">Element „CustomControl“ für View (Format)</span><span class="sxs-lookup"><span data-stu-id="c8e09-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="c8e09-103">Definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="c8e09-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="c8e09-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="c8e09-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8e09-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8e09-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8e09-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="c8e09-106">Attributes and Elements</span></span>

<span data-ttu-id="c8e09-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControl` Element.</span><span class="sxs-lookup"><span data-stu-id="c8e09-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="c8e09-108">Sie müssen ein untergeordnetes Element angeben.</span><span class="sxs-lookup"><span data-stu-id="c8e09-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8e09-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="c8e09-109">Attributes</span></span>

<span data-ttu-id="c8e09-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="c8e09-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8e09-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c8e09-111">Child Elements</span></span>

|<span data-ttu-id="c8e09-112">Element</span><span class="sxs-lookup"><span data-stu-id="c8e09-112">Element</span></span>|<span data-ttu-id="c8e09-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c8e09-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8e09-114">CustomEntries-Element für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c8e09-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="c8e09-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="c8e09-115">Required element.</span></span><br /><br /> <span data-ttu-id="c8e09-116">Enthält die Definitionen der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="c8e09-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c8e09-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c8e09-117">Parent Elements</span></span>

|<span data-ttu-id="c8e09-118">Element</span><span class="sxs-lookup"><span data-stu-id="c8e09-118">Element</span></span>|<span data-ttu-id="c8e09-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c8e09-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8e09-120">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c8e09-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c8e09-121">Definiert eine Ansicht, die verwendet wird, um eine oder mehrere .NET Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c8e09-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c8e09-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c8e09-122">Remarks</span></span>

<span data-ttu-id="c8e09-123">Klicken Sie in den meisten Fällen nur eine Definition für jede Ansicht des Steuerelement erforderlich ist, aber es ist möglich, mehrere Definitionen bereitstellen, sollten Sie die gleiche Ansicht zu verwenden, um verschiedene .NET Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c8e09-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="c8e09-124">In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c8e09-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8e09-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c8e09-125">See Also</span></span>

[<span data-ttu-id="c8e09-126">CustomEntries-Element für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c8e09-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c8e09-127">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c8e09-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c8e09-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8e09-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
