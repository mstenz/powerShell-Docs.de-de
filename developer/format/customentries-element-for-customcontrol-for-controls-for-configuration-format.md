---
title: CustomEntries-Element für CustomControl für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856306"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="be8b7-102">Element „CustomEntries“ für CustomControl für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="be8b7-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="be8b7-103">Enthält die Definitionen von einem allgemeinen Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="be8b7-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="be8b7-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="be8b7-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="be8b7-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( -Format)</span><span class="sxs-lookup"><span data-stu-id="be8b7-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="be8b7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="be8b7-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="be8b7-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="be8b7-107">Attributes and Elements</span></span>

<span data-ttu-id="be8b7-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomEntries` Element.</span><span class="sxs-lookup"><span data-stu-id="be8b7-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="be8b7-109">Sie müssen eine oder mehrere untergeordnete Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="be8b7-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="be8b7-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="be8b7-110">Attributes</span></span>

<span data-ttu-id="be8b7-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="be8b7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="be8b7-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="be8b7-112">Child Elements</span></span>

|<span data-ttu-id="be8b7-113">Element</span><span class="sxs-lookup"><span data-stu-id="be8b7-113">Element</span></span>|<span data-ttu-id="be8b7-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be8b7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be8b7-115">CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="be8b7-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="be8b7-116">Stellt eine Definition des allgemeinen-Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="be8b7-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="be8b7-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="be8b7-117">Parent Elements</span></span>

|<span data-ttu-id="be8b7-118">Element</span><span class="sxs-lookup"><span data-stu-id="be8b7-118">Element</span></span>|<span data-ttu-id="be8b7-119">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="be8b7-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be8b7-120">CustomControl-Element für das Steuerelement für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="be8b7-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="be8b7-121">Das allgemeine Steuerelement definiert.</span><span class="sxs-lookup"><span data-stu-id="be8b7-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="be8b7-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="be8b7-122">Remarks</span></span>

<span data-ttu-id="be8b7-123">In den meisten Fällen ein Steuerelement verfügt über nur eine Definition, die in einem einzelnen definiert ist `CustomEntry` Element.</span><span class="sxs-lookup"><span data-stu-id="be8b7-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="be8b7-124">So ist es jedoch möglich, mehrere Definitionen zu besitzen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="be8b7-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="be8b7-125">In diesen Fällen können Sie definieren eine `CustomEntry` -Element für jedes Objekt oder eine Gruppe von Objekten.</span><span class="sxs-lookup"><span data-stu-id="be8b7-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="be8b7-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="be8b7-126">See Also</span></span>

[<span data-ttu-id="be8b7-127">CustomControl-Element für das Steuerelement für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="be8b7-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="be8b7-128">CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="be8b7-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="be8b7-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="be8b7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
