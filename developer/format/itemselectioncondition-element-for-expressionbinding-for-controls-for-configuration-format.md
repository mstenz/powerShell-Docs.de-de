---
title: ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065508"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="91ae6-102">Element „ItemSelectionCondition“ für ExpressionBinding für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="91ae6-103">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="91ae6-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="91ae6-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="91ae6-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="91ae6-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die ExpressionBinding-Konfigurationselement für CustomItem für Steuerelemente für die Konfiguration (Format)-Format) ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="91ae6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="91ae6-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="91ae6-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="91ae6-107">Attributes and Elements</span></span>

<span data-ttu-id="91ae6-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ItemSelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="91ae6-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="91ae6-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="91ae6-109">Attributes</span></span>

<span data-ttu-id="91ae6-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="91ae6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="91ae6-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="91ae6-111">Child Elements</span></span>

|<span data-ttu-id="91ae6-112">Element</span><span class="sxs-lookup"><span data-stu-id="91ae6-112">Element</span></span>|<span data-ttu-id="91ae6-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91ae6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91ae6-114">PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="91ae6-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="91ae6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="91ae6-116">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="91ae6-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="91ae6-117">ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="91ae6-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="91ae6-118">Optional element.</span></span><br /><br /> <span data-ttu-id="91ae6-119">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="91ae6-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="91ae6-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="91ae6-120">Parent Elements</span></span>

|<span data-ttu-id="91ae6-121">Element</span><span class="sxs-lookup"><span data-stu-id="91ae6-121">Element</span></span>|<span data-ttu-id="91ae6-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="91ae6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91ae6-123">ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="91ae6-124">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="91ae6-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="91ae6-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="91ae6-125">Remarks</span></span>

<span data-ttu-id="91ae6-126">Sie können einen Eigenschaftennamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="91ae6-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="91ae6-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="91ae6-127">See Also</span></span>

[<span data-ttu-id="91ae6-128">PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="91ae6-129">ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="91ae6-130">ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="91ae6-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="91ae6-131">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="91ae6-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
