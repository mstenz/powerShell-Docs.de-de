---
title: ScriptBlock-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229317"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="9bb89-102">Element „ScriptBlock“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb89-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="9bb89-103">Gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="9bb89-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="9bb89-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Ansicht (Format)-ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb89-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9bb89-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bb89-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9bb89-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9bb89-106">Attributes and Elements</span></span>

<span data-ttu-id="9bb89-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="9bb89-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9bb89-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="9bb89-108">Attributes</span></span>

<span data-ttu-id="9bb89-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="9bb89-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9bb89-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9bb89-110">Child Elements</span></span>

<span data-ttu-id="9bb89-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="9bb89-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9bb89-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9bb89-112">Parent Elements</span></span>

|<span data-ttu-id="9bb89-113">Element</span><span class="sxs-lookup"><span data-stu-id="9bb89-113">Element</span></span>|<span data-ttu-id="9bb89-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9bb89-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bb89-115">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb89-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="9bb89-116">Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9bb89-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9bb89-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="9bb89-117">Text Value</span></span>

<span data-ttu-id="9bb89-118">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="9bb89-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9bb89-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9bb89-119">Remarks</span></span>

<span data-ttu-id="9bb89-120">PowerShell startet eine neue Gruppe aus, wenn der Wert dieses Skript ändert.</span><span class="sxs-lookup"><span data-stu-id="9bb89-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="9bb89-121">Wenn dieses Element angegeben ist, können Sie nicht angeben der [PropertyName](propertyname-element-for-groupby-format.md) Element um eine neue Gruppe zu starten.</span><span class="sxs-lookup"><span data-stu-id="9bb89-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bb89-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9bb89-122">See Also</span></span>

[<span data-ttu-id="9bb89-123">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb89-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="9bb89-124">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9bb89-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="9bb89-125">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bb89-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
