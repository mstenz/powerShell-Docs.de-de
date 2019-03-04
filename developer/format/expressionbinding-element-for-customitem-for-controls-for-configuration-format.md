---
title: ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855136"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="bdbfe-102">Element „ExpressionBinding“ für CustomItem für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="bdbfe-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bdbfe-103">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="bdbfe-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bdbfe-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die ExpressionBinding-Konfigurationselement für CustomItem für Steuerelemente für die Konfiguration (Format)-Format)</span><span class="sxs-lookup"><span data-stu-id="bdbfe-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdbfe-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bdbfe-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdbfe-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="bdbfe-107">Attributes and Elements</span></span>

<span data-ttu-id="bdbfe-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ExpressionBinding` Element.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdbfe-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="bdbfe-109">Attributes</span></span>

<span data-ttu-id="bdbfe-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdbfe-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bdbfe-111">Child Elements</span></span>

|<span data-ttu-id="bdbfe-112">Element</span><span class="sxs-lookup"><span data-stu-id="bdbfe-112">Element</span></span>|<span data-ttu-id="bdbfe-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bdbfe-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="bdbfe-114">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-114">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbfe-115">Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="bdbfe-116">CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="bdbfe-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bdbfe-117">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-117">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbfe-118">Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="bdbfe-119">EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="bdbfe-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bdbfe-120">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-120">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbfe-121">Angegeben, dass die Elemente der Auflistungen, die vom Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="bdbfe-122">ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="bdbfe-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bdbfe-123">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-123">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbfe-124">Definiert die Bedingung, die für dieses allgemeinen Steuerelement zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="bdbfe-125">PropertyName-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="bdbfe-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bdbfe-126">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-126">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbfe-127">Gibt die .NET-Eigenschaft, deren Wert durch das allgemeine Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="bdbfe-128">ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="bdbfe-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="bdbfe-129">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-129">Optional element.</span></span><br /><br /> <span data-ttu-id="bdbfe-130">Gibt das Skript an, dessen Wert durch das allgemeine Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bdbfe-131">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="bdbfe-131">Parent Elements</span></span>

|<span data-ttu-id="bdbfe-132">Element</span><span class="sxs-lookup"><span data-stu-id="bdbfe-132">Element</span></span>|<span data-ttu-id="bdbfe-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bdbfe-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdbfe-134">CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="bdbfe-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="bdbfe-135">Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bdbfe-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bdbfe-136">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bdbfe-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="bdbfe-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bdbfe-137">See Also</span></span>

[<span data-ttu-id="bdbfe-138">CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration</span><span class="sxs-lookup"><span data-stu-id="bdbfe-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="bdbfe-139">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="bdbfe-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
