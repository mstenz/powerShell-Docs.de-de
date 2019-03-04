---
title: Benennen Sie Element für das Steuerelement für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860086"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="2a6bc-102">Element „Name“ für Control für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2a6bc-103">Gibt den Namen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-103">Specifies the name of the control.</span></span> <span data-ttu-id="2a6bc-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2a6bc-105">Konfigurationselement-Element (Format)-Steuerelemente des Steuerelements für Konfiguration (Format) für die Steuerelemente für die Konfiguration (Format)-Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a6bc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a6bc-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a6bc-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2a6bc-107">Attributes and Elements</span></span>

<span data-ttu-id="2a6bc-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Name` Element.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a6bc-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2a6bc-109">Attributes</span></span>

<span data-ttu-id="2a6bc-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a6bc-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2a6bc-111">Child Elements</span></span>

<span data-ttu-id="2a6bc-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a6bc-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2a6bc-113">Parent Elements</span></span>

|<span data-ttu-id="2a6bc-114">Element</span><span class="sxs-lookup"><span data-stu-id="2a6bc-114">Element</span></span>|<span data-ttu-id="2a6bc-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a6bc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a6bc-116">Control-Element für Controls für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="2a6bc-117">Definiert ein allgemeines Steuerelement, das von allen Ansichten die Formatierungsdatei und den Namen, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2a6bc-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="2a6bc-118">Text Value</span></span>

<span data-ttu-id="2a6bc-119">Geben Sie den Namen, der verwendet wird, um auf dieses Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a6bc-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2a6bc-120">Remarks</span></span>

<span data-ttu-id="2a6bc-121">Der hier angegebene Name kann in den folgenden Elementen verwendet werden, um auf um dieses Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="2a6bc-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="2a6bc-122">Beim Erstellen einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen, kann das Steuerelement vom folgenden Element angegeben werden: [GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="2a6bc-123">Wenn Sie einen anderen allgemeinen Steuerelements erstellen zu können, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="2a6bc-124">Beim Erstellen eines Steuerelements, die von einer Ansicht verwendet werden kann, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="2a6bc-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2a6bc-125">See Also</span></span>

[<span data-ttu-id="2a6bc-126">Control-Element für Controls für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="2a6bc-127">ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="2a6bc-128">ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="2a6bc-129">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2a6bc-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2a6bc-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="2a6bc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
