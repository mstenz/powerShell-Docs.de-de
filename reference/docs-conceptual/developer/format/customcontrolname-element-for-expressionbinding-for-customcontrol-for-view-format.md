---
title: Customcontrolname-Element für ExpressionBinding für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364109"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="74b82-102">Element „CustomControlName“ für ExpressionBinding für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="74b82-103">Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="74b82-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="74b82-104">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="74b82-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="74b82-105">Konfigurationselement (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element für View (Format) customentries-Element für CustomControl for View (Format) customentry-Element für customentries for View (Format) customItem -Element für customentry für das View (Format) ExpressionBinding-Element für das customItem (Format) customcontrolname-Element für die Ausdrucks Bindung für customItem (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74b82-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="74b82-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74b82-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="74b82-107">Attributes and Elements</span></span>

<span data-ttu-id="74b82-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomControlName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="74b82-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="74b82-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="74b82-109">Attributes</span></span>

<span data-ttu-id="74b82-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="74b82-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74b82-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="74b82-111">Child Elements</span></span>

<span data-ttu-id="74b82-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="74b82-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="74b82-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="74b82-113">Parent Elements</span></span>

|<span data-ttu-id="74b82-114">Element</span><span class="sxs-lookup"><span data-stu-id="74b82-114">Element</span></span>|<span data-ttu-id="74b82-115">Description</span><span class="sxs-lookup"><span data-stu-id="74b82-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74b82-116">ExpressionBinding-Element für customItem (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="74b82-117">Definiert die Daten, die vom-Steuerelement angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="74b82-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="74b82-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="74b82-118">Text Value</span></span>

<span data-ttu-id="74b82-119">Geben Sie den Namen des Steuer Elements an.</span><span class="sxs-lookup"><span data-stu-id="74b82-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="74b82-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="74b82-120">Remarks</span></span>

<span data-ttu-id="74b82-121">Sie können allgemeine Steuerelemente erstellen, die von allen Ansichten einer Formatierungs Datei verwendet werden können, und Sie können Ansichts Steuerelemente erstellen, die von einer bestimmten Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="74b82-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="74b82-122">Die Namen dieser Steuerelemente werden durch die folgenden Elemente angegeben.</span><span class="sxs-lookup"><span data-stu-id="74b82-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="74b82-123">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="74b82-124">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="74b82-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="74b82-125">See Also</span></span>

[<span data-ttu-id="74b82-126">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="74b82-127">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="74b82-128">ExpressionBinding-Element für customItem (Format)</span><span class="sxs-lookup"><span data-stu-id="74b82-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="74b82-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="74b82-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
