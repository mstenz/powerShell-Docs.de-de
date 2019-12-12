---
title: Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369149"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="74217-102">Element „CustomControlName“ für ExpressionBinding für Controls für View (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="74217-103">Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="74217-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="74217-104">Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="74217-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="74217-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für das View (Format) ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format) customcontrolname -Element für expressionbindine für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74217-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="74217-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74217-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="74217-107">Attributes and Elements</span></span>

<span data-ttu-id="74217-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomControlName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="74217-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="74217-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="74217-109">Attributes</span></span>

<span data-ttu-id="74217-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="74217-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74217-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="74217-111">Child Elements</span></span>

<span data-ttu-id="74217-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="74217-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="74217-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="74217-113">Parent Elements</span></span>

|<span data-ttu-id="74217-114">Element</span><span class="sxs-lookup"><span data-stu-id="74217-114">Element</span></span>|<span data-ttu-id="74217-115">Description</span><span class="sxs-lookup"><span data-stu-id="74217-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74217-116">ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="74217-117">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="74217-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="74217-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="74217-118">Text Value</span></span>

<span data-ttu-id="74217-119">Geben Sie den Namen des Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="74217-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="74217-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="74217-120">Remarks</span></span>

<span data-ttu-id="74217-121">Sie können allgemeine Steuerelemente erstellen, die von allen Ansichten einer Formatierungs Datei verwendet werden können, und Sie können Ansichts Steuerelemente erstellen, die von einer bestimmten Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="74217-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="74217-122">Die folgenden Elemente geben die Namen dieser Steuerelemente an:</span><span class="sxs-lookup"><span data-stu-id="74217-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="74217-123">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="74217-124">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="74217-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="74217-125">See Also</span></span>

[<span data-ttu-id="74217-126">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="74217-127">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="74217-128">ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="74217-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="74217-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="74217-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
