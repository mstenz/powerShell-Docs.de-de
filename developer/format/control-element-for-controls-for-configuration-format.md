---
title: Control-Element für Konfiguration (Format) für Steuerelemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858886"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="6a83f-102">Element „Control“ für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6a83f-103">Definiert ein allgemeines Steuerelement, das von allen Ansichten die Formatierungsdatei und den Namen, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="6a83f-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="6a83f-104">Konfigurationselement-Element (Format)-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a83f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a83f-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a83f-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6a83f-106">Attributes and Elements</span></span>

<span data-ttu-id="6a83f-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element für die `Control` Element.</span><span class="sxs-lookup"><span data-stu-id="6a83f-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="6a83f-108">Sie müssen nur eine jedes untergeordneten Elements angeben.</span><span class="sxs-lookup"><span data-stu-id="6a83f-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a83f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6a83f-109">Attributes</span></span>

<span data-ttu-id="6a83f-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6a83f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a83f-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6a83f-111">Child Elements</span></span>

|<span data-ttu-id="6a83f-112">Element</span><span class="sxs-lookup"><span data-stu-id="6a83f-112">Element</span></span>|<span data-ttu-id="6a83f-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6a83f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a83f-114">CustomControl-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="6a83f-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="6a83f-115">Required element.</span></span><br /><br /> <span data-ttu-id="6a83f-116">Definiert das Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="6a83f-116">Defines the control.</span></span>|
|[<span data-ttu-id="6a83f-117">Name-Element für das Steuerelement für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="6a83f-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="6a83f-118">Required element.</span></span><br /><br /> <span data-ttu-id="6a83f-119">Gibt den Namen verwendet, um das Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="6a83f-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a83f-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6a83f-120">Parent Elements</span></span>

|<span data-ttu-id="6a83f-121">Element</span><span class="sxs-lookup"><span data-stu-id="6a83f-121">Element</span></span>|<span data-ttu-id="6a83f-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6a83f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a83f-123">Controls-Element (Format)-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6a83f-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="6a83f-124">Definiert die allgemeinen Steuerelemente, die von allen Ansichten des die Formatierungsdatei oder von anderen Steuerelementen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="6a83f-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a83f-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6a83f-125">Remarks</span></span>

<span data-ttu-id="6a83f-126">Der Name für dieses Steuerelement kann in den folgenden Elementen verwiesen werden:</span><span class="sxs-lookup"><span data-stu-id="6a83f-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="6a83f-127">ExpressionBinding-Element für CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="6a83f-128">GroupBy-Element für View(Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="6a83f-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6a83f-129">See Also</span></span>

[<span data-ttu-id="6a83f-130">Controls-Element (Format)-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6a83f-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="6a83f-131">CustomControl-Element für das Steuerelement für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6a83f-132">ExpressionBinding-Element für CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6a83f-133">GroupBy-Element für View(Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="6a83f-134">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6a83f-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6a83f-135">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a83f-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
