---
title: CustomEntry-Element für CustomEntries für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861816"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="9b7c6-102">Element „CustomEntry“ für CustomEntries für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="9b7c6-103">Stellt eine Definition der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="9b7c6-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b7c6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b7c6-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b7c6-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9b7c6-106">Attributes and Elements</span></span>

<span data-ttu-id="9b7c6-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="9b7c6-108">Sie müssen die durch die Definition der angezeigten Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b7c6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9b7c6-109">Attributes</span></span>

<span data-ttu-id="9b7c6-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b7c6-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9b7c6-111">Child Elements</span></span>

|<span data-ttu-id="9b7c6-112">Element</span><span class="sxs-lookup"><span data-stu-id="9b7c6-112">Element</span></span>|<span data-ttu-id="9b7c6-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9b7c6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b7c6-114">EntrySelectedBy-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="9b7c6-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9b7c6-116">Definiert die Typen von .NET, mit denen die Definition der benutzerdefinierten Steuerelementansicht oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="9b7c6-117">CustomItem-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="9b7c6-118">Definiert ein Steuerelement für die Definition des benutzerdefinierten Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9b7c6-119">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9b7c6-119">Parent Elements</span></span>

|<span data-ttu-id="9b7c6-120">Element</span><span class="sxs-lookup"><span data-stu-id="9b7c6-120">Element</span></span>|<span data-ttu-id="9b7c6-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9b7c6-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b7c6-122">CustomEntries-Element für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="9b7c6-123">Enthält die Definitionen der benutzerdefinierten Steuerelements an.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="9b7c6-124">Die Ansicht benutzerdefiniertes Steuerelement muss eine oder mehrere Definitionen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9b7c6-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9b7c6-125">Remarks</span></span>

<span data-ttu-id="9b7c6-126">Klicken Sie in den meisten Fällen nur eine Definition für jede Ansicht benutzerdefiniertes Steuerelement erforderlich ist, aber es ist möglich, mehrere Definitionen zu besitzen, sollten Sie die gleiche Ansicht zu verwenden, um verschiedene .NET Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="9b7c6-127">In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b7c6-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9b7c6-128">See Also</span></span>

[<span data-ttu-id="9b7c6-129">CustomControl-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="9b7c6-130">CustomItem-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9b7c6-131">EntrySelectedBy-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="9b7c6-132">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="9b7c6-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
