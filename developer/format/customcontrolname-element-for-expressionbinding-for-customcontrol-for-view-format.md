---
title: CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066616"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="248a9-102">Element „CustomControlName“ für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="248a9-103">Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="248a9-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="248a9-104">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="248a9-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="248a9-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem -Element für CustomEntry für Ansicht (Format) ExpressionBinding-Element für CustomItem (Format) CustomControlName-Element für Ausdrucksbindung für CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="248a9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="248a9-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="248a9-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="248a9-107">Attributes and Elements</span></span>

<span data-ttu-id="248a9-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControlName` Element.</span><span class="sxs-lookup"><span data-stu-id="248a9-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="248a9-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="248a9-109">Attributes</span></span>

<span data-ttu-id="248a9-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="248a9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="248a9-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="248a9-111">Child Elements</span></span>

<span data-ttu-id="248a9-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="248a9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="248a9-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="248a9-113">Parent Elements</span></span>

|<span data-ttu-id="248a9-114">Element</span><span class="sxs-lookup"><span data-stu-id="248a9-114">Element</span></span>|<span data-ttu-id="248a9-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="248a9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="248a9-116">ExpressionBinding-Element für CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="248a9-117">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="248a9-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="248a9-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="248a9-118">Text Value</span></span>

<span data-ttu-id="248a9-119">Geben Sie den Namen des Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="248a9-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="248a9-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="248a9-120">Remarks</span></span>

<span data-ttu-id="248a9-121">Sie können allgemeine Steuerelemente, die von allen Ansichten des eine Formatierungsdatei verwendet werden können erstellen aus, und Sie können Steuerelemente, die von einer bestimmten Ansicht verwendet werden können erstellen.</span><span class="sxs-lookup"><span data-stu-id="248a9-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="248a9-122">Die Namen dieser Steuerelemente werden durch die folgenden Elemente angegeben.</span><span class="sxs-lookup"><span data-stu-id="248a9-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="248a9-123">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="248a9-124">Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="248a9-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="248a9-125">See Also</span></span>

[<span data-ttu-id="248a9-126">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="248a9-127">Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="248a9-128">ExpressionBinding-Element für CustomItem (Format)</span><span class="sxs-lookup"><span data-stu-id="248a9-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="248a9-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="248a9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
