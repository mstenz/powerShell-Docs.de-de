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
ms.openlocfilehash: 41a6aaa24e5850bd390c8e3b6505cc88fc80b7b5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856206"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="c4e00-102">Element „ScriptBlock“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c4e00-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="c4e00-103">Gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="c4e00-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="c4e00-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Ansicht (Format)-ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c4e00-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c4e00-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4e00-105">Syntax</span></span>

```xml
<ScriptBolck>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c4e00-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="c4e00-106">Attributes and Elements</span></span>

<span data-ttu-id="c4e00-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="c4e00-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c4e00-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="c4e00-108">Attributes</span></span>

<span data-ttu-id="c4e00-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="c4e00-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c4e00-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c4e00-110">Child Elements</span></span>

<span data-ttu-id="c4e00-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="c4e00-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c4e00-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="c4e00-112">Parent Elements</span></span>

|<span data-ttu-id="c4e00-113">Element</span><span class="sxs-lookup"><span data-stu-id="c4e00-113">Element</span></span>|<span data-ttu-id="c4e00-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c4e00-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c4e00-115">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c4e00-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="c4e00-116">Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c4e00-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c4e00-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="c4e00-117">Text Value</span></span>

<span data-ttu-id="c4e00-118">Geben Sie das Skript aus, das ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="c4e00-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4e00-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c4e00-119">Remarks</span></span>

<span data-ttu-id="c4e00-120">Windows PowerShell startet eine neue Gruppe aus, wenn der Wert dieses Skript ändert.</span><span class="sxs-lookup"><span data-stu-id="c4e00-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="c4e00-121">Wenn dieses Element angegeben ist, können Sie nicht angeben der [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) Element um eine neue Gruppe zu starten.</span><span class="sxs-lookup"><span data-stu-id="c4e00-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4e00-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c4e00-122">See Also</span></span>

[<span data-ttu-id="c4e00-123">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="c4e00-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="c4e00-124">GroupBy-Element für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="c4e00-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="c4e00-125">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4e00-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
