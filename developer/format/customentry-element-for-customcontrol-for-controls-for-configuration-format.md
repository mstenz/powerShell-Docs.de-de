---
title: CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859806"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="58511-102">Element „CustomEntry“ für CustomControl für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="58511-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="58511-103">Stellt eine Definition des allgemeinen-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="58511-103">Provides a definition of the common control.</span></span> <span data-ttu-id="58511-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="58511-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="58511-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="58511-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="58511-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="58511-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="58511-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="58511-107">Attributes and Elements</span></span>

<span data-ttu-id="58511-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="58511-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="58511-109">Sie müssen die durch die Definition der angezeigten Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="58511-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="58511-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="58511-110">Attributes</span></span>

<span data-ttu-id="58511-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="58511-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="58511-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="58511-112">Child Elements</span></span>

|<span data-ttu-id="58511-113">Element</span><span class="sxs-lookup"><span data-stu-id="58511-113">Element</span></span>|<span data-ttu-id="58511-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="58511-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58511-115">EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="58511-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="58511-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="58511-116">Optional element.</span></span><br /><br /> <span data-ttu-id="58511-117">Definiert die Typen von .NET, mit denen die Definition eines allgemeinen Steuerelement oder die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="58511-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="58511-118">CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58511-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="58511-119">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="58511-119">Required element.</span></span><br /><br /> <span data-ttu-id="58511-120">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="58511-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="58511-121">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="58511-121">Parent Elements</span></span>

|<span data-ttu-id="58511-122">Element</span><span class="sxs-lookup"><span data-stu-id="58511-122">Element</span></span>|<span data-ttu-id="58511-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="58511-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58511-124">CustomEntries-Element für CustomControl für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="58511-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="58511-125">Enthält die Definitionen des allgemeinen-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="58511-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="58511-126">Hinweise</span><span class="sxs-lookup"><span data-stu-id="58511-126">Remarks</span></span>

<span data-ttu-id="58511-127">Klicken Sie in den meisten Fällen nur eine Definition für die einzelnen common benutzerdefinierten Steuerelemente erforderlich ist, aber es ist möglich, mehrere Definitionen zu besitzen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="58511-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="58511-128">In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="58511-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="58511-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="58511-129">See Also</span></span>

[<span data-ttu-id="58511-130">CustomEntries-Element für CustomControl für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="58511-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="58511-131">CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58511-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="58511-132">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="58511-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
