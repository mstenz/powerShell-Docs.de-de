---
title: Control-Element für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369009"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="d7aac-102">Element „Control“ für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d7aac-103">Definiert ein gängiges Steuerelement, das von allen Ansichten der Formatierungs Datei und dem Namen, der zum Verweisen auf das Steuerelement verwendet wird, verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d7aac-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="d7aac-104">Configuration-Element (Format) Controls-Element des Configuration (Format)-Steuer Elements für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d7aac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7aac-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d7aac-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d7aac-106">Attributes and Elements</span></span>

<span data-ttu-id="d7aac-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete-Element für das `Control`-Element beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d7aac-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="d7aac-108">Sie müssen nur eines der einzelnen untergeordneten Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="d7aac-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d7aac-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d7aac-109">Attributes</span></span>

<span data-ttu-id="d7aac-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="d7aac-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d7aac-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d7aac-111">Child Elements</span></span>

|<span data-ttu-id="d7aac-112">Element</span><span class="sxs-lookup"><span data-stu-id="d7aac-112">Element</span></span>|<span data-ttu-id="d7aac-113">Description</span><span class="sxs-lookup"><span data-stu-id="d7aac-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7aac-114">CustomControl-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="d7aac-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="d7aac-115">Required element.</span></span><br /><br /> <span data-ttu-id="d7aac-116">Definiert das Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="d7aac-116">Defines the control.</span></span>|
|[<span data-ttu-id="d7aac-117">Name-Element für das Steuer Element für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="d7aac-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="d7aac-118">Required element.</span></span><br /><br /> <span data-ttu-id="d7aac-119">Gibt den Namen an, mit dem auf das Steuerelement verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="d7aac-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d7aac-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d7aac-120">Parent Elements</span></span>

|<span data-ttu-id="d7aac-121">Element</span><span class="sxs-lookup"><span data-stu-id="d7aac-121">Element</span></span>|<span data-ttu-id="d7aac-122">Description</span><span class="sxs-lookup"><span data-stu-id="d7aac-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d7aac-123">Controls-Element der Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="d7aac-124">Definiert die allgemeinen Steuerelemente, die von allen Ansichten der Formatierungs Datei oder von anderen Steuerelementen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d7aac-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d7aac-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d7aac-125">Remarks</span></span>

<span data-ttu-id="d7aac-126">Auf den Namen, den dieses Steuerelement erhält, kann in den folgenden Elementen verwiesen werden:</span><span class="sxs-lookup"><span data-stu-id="d7aac-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="d7aac-127">ExpressionBinding-Element für customItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d7aac-128">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d7aac-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d7aac-129">See Also</span></span>

[<span data-ttu-id="d7aac-130">Controls-Element der Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="d7aac-131">CustomControl-Element für das Steuerelement für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d7aac-132">ExpressionBinding-Element für customItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d7aac-133">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d7aac-134">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="d7aac-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d7aac-135">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="d7aac-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
