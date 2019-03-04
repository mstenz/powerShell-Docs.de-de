---
title: CustomControlName-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860306"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="1fccd-102">Element „CustomControlName“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="1fccd-103">Gibt den Namen eines benutzerdefinierten Steuerelements, die verwendet wird, um die neue Gruppe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1fccd-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="1fccd-104">Dieses Element wird verwendet, bei der Definition einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1fccd-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="1fccd-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Anzeigeelement (Format) CustomControlName GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1fccd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1fccd-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1fccd-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="1fccd-107">Attributes and Elements</span></span>

<span data-ttu-id="1fccd-108">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Elemente von der `CustomControlName` Element.</span><span class="sxs-lookup"><span data-stu-id="1fccd-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1fccd-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1fccd-109">Attributes</span></span>

<span data-ttu-id="1fccd-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="1fccd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1fccd-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1fccd-111">Child Elements</span></span>

<span data-ttu-id="1fccd-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="1fccd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1fccd-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1fccd-113">Parent Elements</span></span>

|<span data-ttu-id="1fccd-114">Element</span><span class="sxs-lookup"><span data-stu-id="1fccd-114">Element</span></span>|<span data-ttu-id="1fccd-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1fccd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1fccd-116">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="1fccd-117">Definiert, wie Windows PowerShell eine neue Gruppe von Objekten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1fccd-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1fccd-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="1fccd-118">Text Value</span></span>

<span data-ttu-id="1fccd-119">Geben Sie den Namen des benutzerdefinierten Steuerelements, die verwendet wird, um eine neue Gruppe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1fccd-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fccd-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1fccd-120">Remarks</span></span>

<span data-ttu-id="1fccd-121">Sie können allgemeine Steuerelemente, die von allen Ansichten des eine Formatierungsdatei verwendet werden können erstellen und Sie können Steuerelemente, die von einer bestimmten Ansicht verwendet werden können erstellen.</span><span class="sxs-lookup"><span data-stu-id="1fccd-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1fccd-122">Die folgenden Elemente geben Sie die Namen dieser benutzerdefinierten Steuerelemente:</span><span class="sxs-lookup"><span data-stu-id="1fccd-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="1fccd-123">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1fccd-124">Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1fccd-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1fccd-125">See Also</span></span>

[<span data-ttu-id="1fccd-126">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="1fccd-127">Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1fccd-128">Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="1fccd-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1fccd-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="1fccd-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
