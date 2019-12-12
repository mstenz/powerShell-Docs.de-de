---
title: Customcontrolname-Element für ExpressionBinding für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368909"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="67cec-102">Element „CustomControlName“ für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="67cec-103">Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="67cec-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="67cec-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="67cec-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="67cec-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) ExpressionBinding-Element für customItem für GroupBy (Format) customcontrolname-Element für ExpressionBinding für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67cec-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="67cec-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67cec-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="67cec-107">Attributes and Elements</span></span>

<span data-ttu-id="67cec-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomControlName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="67cec-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67cec-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="67cec-109">Attributes</span></span>

<span data-ttu-id="67cec-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="67cec-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67cec-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="67cec-111">Child Elements</span></span>

<span data-ttu-id="67cec-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="67cec-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67cec-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="67cec-113">Parent Elements</span></span>

|<span data-ttu-id="67cec-114">Element</span><span class="sxs-lookup"><span data-stu-id="67cec-114">Element</span></span>|<span data-ttu-id="67cec-115">Description</span><span class="sxs-lookup"><span data-stu-id="67cec-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67cec-116">ExpressionBinding-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="67cec-117">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="67cec-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67cec-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="67cec-118">Text Value</span></span>

<span data-ttu-id="67cec-119">Geben Sie den Namen des Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="67cec-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="67cec-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="67cec-120">Remarks</span></span>

<span data-ttu-id="67cec-121">Sie können allgemeine Steuerelemente erstellen, die von allen Ansichten einer Formatierungs Datei verwendet werden können, und Sie können Ansichts Steuerelemente erstellen, die von einer bestimmten Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="67cec-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="67cec-122">Die folgenden Elemente geben die Namen dieser Steuerelemente an:</span><span class="sxs-lookup"><span data-stu-id="67cec-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="67cec-123">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="67cec-124">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="67cec-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="67cec-125">See Also</span></span>

[<span data-ttu-id="67cec-126">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="67cec-127">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="67cec-128">ExpressionBinding-Element für customItem für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="67cec-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="67cec-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="67cec-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
