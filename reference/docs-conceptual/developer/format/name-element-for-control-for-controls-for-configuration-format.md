---
title: Name-Element für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362709"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="54a73-102">Element „Name“ für Control für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="54a73-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="54a73-103">Gibt den Namen des Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="54a73-103">Specifies the name of the control.</span></span> <span data-ttu-id="54a73-104">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="54a73-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="54a73-105">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Configuration (Format) Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54a73-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54a73-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="54a73-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="54a73-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="54a73-107">Attributes and Elements</span></span>

<span data-ttu-id="54a73-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Name`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="54a73-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54a73-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="54a73-109">Attributes</span></span>

<span data-ttu-id="54a73-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="54a73-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54a73-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="54a73-111">Child Elements</span></span>

<span data-ttu-id="54a73-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="54a73-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54a73-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="54a73-113">Parent Elements</span></span>

|<span data-ttu-id="54a73-114">Element</span><span class="sxs-lookup"><span data-stu-id="54a73-114">Element</span></span>|<span data-ttu-id="54a73-115">Description</span><span class="sxs-lookup"><span data-stu-id="54a73-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54a73-116">Control-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54a73-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="54a73-117">Definiert ein gängiges Steuerelement, das von allen Ansichten der Formatierungs Datei und dem Namen, der zum Verweisen auf das Steuerelement verwendet wird, verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="54a73-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="54a73-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="54a73-118">Text Value</span></span>

<span data-ttu-id="54a73-119">Geben Sie den Namen an, der zum Verweisen auf dieses Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="54a73-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="54a73-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="54a73-120">Remarks</span></span>

<span data-ttu-id="54a73-121">Der hier angegebene Name kann in den folgenden Elementen verwendet werden, um auf dieses Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="54a73-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="54a73-122">Beim Erstellen einer Tabelle, einer Liste, einer breiten oder einer benutzerdefinierten Steuerelement Ansicht kann das Steuerelement vom folgenden Element angegeben werden: [GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="54a73-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="54a73-123">Wenn Sie ein weiteres gängiges Steuerelement erstellen, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="54a73-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="54a73-124">Wenn Sie ein Steuerelement erstellen, das von einer Ansicht verwendet werden kann, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für customItem für Steuerelemente für View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="54a73-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="54a73-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="54a73-125">See Also</span></span>

[<span data-ttu-id="54a73-126">Control-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54a73-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="54a73-127">ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="54a73-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="54a73-128">ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="54a73-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="54a73-129">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="54a73-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="54a73-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="54a73-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
