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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066792"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="6cb35-102">Element „Control“ für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6cb35-103">Definiert ein allgemeines Steuerelement, das von allen Ansichten die Formatierungsdatei und den Namen, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="6cb35-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="6cb35-104">Konfigurationselement-Element (Format)-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6cb35-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6cb35-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6cb35-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6cb35-106">Attributes and Elements</span></span>

<span data-ttu-id="6cb35-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element für die `Control` Element.</span><span class="sxs-lookup"><span data-stu-id="6cb35-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="6cb35-108">Sie müssen nur eine jedes untergeordneten Elements angeben.</span><span class="sxs-lookup"><span data-stu-id="6cb35-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6cb35-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6cb35-109">Attributes</span></span>

<span data-ttu-id="6cb35-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6cb35-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6cb35-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6cb35-111">Child Elements</span></span>

|<span data-ttu-id="6cb35-112">Element</span><span class="sxs-lookup"><span data-stu-id="6cb35-112">Element</span></span>|<span data-ttu-id="6cb35-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6cb35-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cb35-114">CustomControl-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="6cb35-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="6cb35-115">Required element.</span></span><br /><br /> <span data-ttu-id="6cb35-116">Definiert das Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="6cb35-116">Defines the control.</span></span>|
|[<span data-ttu-id="6cb35-117">Name-Element für das Steuerelement für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="6cb35-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="6cb35-118">Required element.</span></span><br /><br /> <span data-ttu-id="6cb35-119">Gibt den Namen verwendet, um das Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="6cb35-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6cb35-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6cb35-120">Parent Elements</span></span>

|<span data-ttu-id="6cb35-121">Element</span><span class="sxs-lookup"><span data-stu-id="6cb35-121">Element</span></span>|<span data-ttu-id="6cb35-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6cb35-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6cb35-123">Controls-Element (Format)-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6cb35-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="6cb35-124">Definiert die allgemeinen Steuerelemente, die von allen Ansichten des die Formatierungsdatei oder von anderen Steuerelementen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="6cb35-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6cb35-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6cb35-125">Remarks</span></span>

<span data-ttu-id="6cb35-126">Der Name für dieses Steuerelement kann in den folgenden Elementen verwiesen werden:</span><span class="sxs-lookup"><span data-stu-id="6cb35-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="6cb35-127">ExpressionBinding-Element für CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="6cb35-128">GroupBy-Element für View(Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="6cb35-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6cb35-129">See Also</span></span>

[<span data-ttu-id="6cb35-130">Controls-Element (Format)-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6cb35-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="6cb35-131">CustomControl-Element für das Steuerelement für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6cb35-132">ExpressionBinding-Element für CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6cb35-133">GroupBy-Element für View(Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="6cb35-134">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6cb35-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6cb35-135">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="6cb35-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
