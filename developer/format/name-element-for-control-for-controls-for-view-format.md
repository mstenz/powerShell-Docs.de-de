---
title: Benennen Sie Element für das Steuerelement für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065100"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="c680b-102">Element „Name“ für Control für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="c680b-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="c680b-103">Gibt den Namen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="c680b-103">Specifies the name of the control.</span></span>

<span data-ttu-id="c680b-104">-Element (Format) ViewDefinitions-Element (Format) Ansicht Konfigurationselement (Format) steuert Elementen (-Format)-Steuerelement für Steuerelemente für die Name-Anzeigeelement (Format) für Steuerelement für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c680b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c680b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c680b-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c680b-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="c680b-106">Attributes and Elements</span></span>

<span data-ttu-id="c680b-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Name` Element.</span><span class="sxs-lookup"><span data-stu-id="c680b-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c680b-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="c680b-108">Attributes</span></span>

<span data-ttu-id="c680b-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="c680b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c680b-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c680b-110">Child Elements</span></span>

<span data-ttu-id="c680b-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="c680b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c680b-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c680b-112">Parent Elements</span></span>

|<span data-ttu-id="c680b-113">Element</span><span class="sxs-lookup"><span data-stu-id="c680b-113">Element</span></span>|<span data-ttu-id="c680b-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c680b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c680b-115">Control-Element für Controls für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c680b-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="c680b-116">Definiert ein Steuerelement, das von der Ansicht und der Name, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c680b-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c680b-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="c680b-117">Text Value</span></span>

<span data-ttu-id="c680b-118">Geben Sie den Namen, der verwendet wird, um das Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="c680b-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="c680b-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c680b-119">Remarks</span></span>

<span data-ttu-id="c680b-120">Der hier angegebene Name kann in den folgenden Elementen verwendet werden, um auf um dieses Steuerelement zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="c680b-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="c680b-121">Beim Erstellen einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen, kann das Steuerelement vom folgenden Element angegeben werden: [GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="c680b-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="c680b-122">Wenn Sie ein anderes Steuerelement erstellen, die von einer Ansicht verwendet werden kann, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="c680b-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="c680b-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c680b-123">See Also</span></span>

[<span data-ttu-id="c680b-124">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c680b-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c680b-125">ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c680b-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="c680b-126">Control-Element für Controls für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c680b-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="c680b-127">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="c680b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
