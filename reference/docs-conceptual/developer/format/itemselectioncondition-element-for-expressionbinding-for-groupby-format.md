---
title: Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365289"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="a9073-102">Element „ItemSelectionCondition“ für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a9073-102">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="a9073-103">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="a9073-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="a9073-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die für ein Steuerelement angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="a9073-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="a9073-105">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a9073-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="a9073-106">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) ExpressionBinding-Element für customItem für GroupBy (Format) itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a9073-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9073-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a9073-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9073-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a9073-108">Attributes and Elements</span></span>

<span data-ttu-id="a9073-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ItemSelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a9073-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9073-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="a9073-110">Attributes</span></span>

<span data-ttu-id="a9073-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a9073-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9073-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a9073-112">Child Elements</span></span>

|<span data-ttu-id="a9073-113">Element</span><span class="sxs-lookup"><span data-stu-id="a9073-113">Element</span></span>|<span data-ttu-id="a9073-114">Description</span><span class="sxs-lookup"><span data-stu-id="a9073-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9073-115">PropertyName-Element für itemselectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a9073-115">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a9073-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a9073-116">Optional element.</span></span><br /><br /> <span data-ttu-id="a9073-117">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a9073-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="a9073-118">ScriptBlock-Element für itemselectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a9073-118">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|<span data-ttu-id="a9073-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="a9073-119">Optional element.</span></span><br /><br /> <span data-ttu-id="a9073-120">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="a9073-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a9073-121">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a9073-121">Parent Elements</span></span>

|<span data-ttu-id="a9073-122">Element</span><span class="sxs-lookup"><span data-stu-id="a9073-122">Element</span></span>|<span data-ttu-id="a9073-123">Description</span><span class="sxs-lookup"><span data-stu-id="a9073-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9073-124">ExpressionBinding-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a9073-124">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="a9073-125">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a9073-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9073-126">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a9073-126">Remarks</span></span>

<span data-ttu-id="a9073-127">Sie können einen Eigenschaftsnamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="a9073-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9073-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a9073-128">See Also</span></span>

[<span data-ttu-id="a9073-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a9073-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="a9073-130">ExpressionBinding-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a9073-130">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)
