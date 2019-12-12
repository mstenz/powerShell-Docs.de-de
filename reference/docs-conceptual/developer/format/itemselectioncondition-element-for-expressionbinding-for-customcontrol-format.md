---
title: Itemselectioncondition-Element für ExpressionBinding für CustomControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362909"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="07c1d-102">Element „ItemSelectionCondition“ für ExpressionBinding für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="07c1d-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="07c1d-103">Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="07c1d-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="07c1d-104">Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die für ein Steuerelement angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="07c1d-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="07c1d-105">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="07c1d-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="07c1d-106">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für das View (Format)-ExpressionBinding-Element für customItem für CustomControl für View (Format) itemselectioncondition-Element für die Ausdrucks Bindung von CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="07c1d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="07c1d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="07c1d-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07c1d-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="07c1d-108">Attributes and Elements</span></span>

<span data-ttu-id="07c1d-109">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ItemSelectionCondition`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="07c1d-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="07c1d-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="07c1d-110">Attributes</span></span>

<span data-ttu-id="07c1d-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="07c1d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07c1d-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="07c1d-112">Child Elements</span></span>

|<span data-ttu-id="07c1d-113">Element</span><span class="sxs-lookup"><span data-stu-id="07c1d-113">Element</span></span>|<span data-ttu-id="07c1d-114">Description</span><span class="sxs-lookup"><span data-stu-id="07c1d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07c1d-115">PropertyName-Element für itemselectioncondition für CustomControl für View (Format</span><span class="sxs-lookup"><span data-stu-id="07c1d-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="07c1d-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="07c1d-116">Optional element.</span></span><br /><br /> <span data-ttu-id="07c1d-117">Gibt die .net-Eigenschaft an, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="07c1d-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="07c1d-118">ScriptBlock-Element für itemselectioncondition für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="07c1d-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="07c1d-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="07c1d-119">Optional element.</span></span><br /><br /> <span data-ttu-id="07c1d-120">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="07c1d-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07c1d-121">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="07c1d-121">Parent Elements</span></span>

|<span data-ttu-id="07c1d-122">Element</span><span class="sxs-lookup"><span data-stu-id="07c1d-122">Element</span></span>|<span data-ttu-id="07c1d-123">Description</span><span class="sxs-lookup"><span data-stu-id="07c1d-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07c1d-124">ExpressionBinding-Element für customItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="07c1d-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="07c1d-125">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="07c1d-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07c1d-126">Hinweise</span><span class="sxs-lookup"><span data-stu-id="07c1d-126">Remarks</span></span>

<span data-ttu-id="07c1d-127">Sie können einen Eigenschaftsnamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="07c1d-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="07c1d-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="07c1d-128">See Also</span></span>

[<span data-ttu-id="07c1d-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="07c1d-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="07c1d-130">ExpressionBinding-Element für customItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="07c1d-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
