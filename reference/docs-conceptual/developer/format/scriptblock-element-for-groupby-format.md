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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364929"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="7b123-102">Element „ScriptBlock“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b123-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="7b123-103">Gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="7b123-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="7b123-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b123-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b123-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7b123-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b123-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7b123-106">Attributes and Elements</span></span>

<span data-ttu-id="7b123-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7b123-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b123-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7b123-108">Attributes</span></span>

<span data-ttu-id="7b123-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="7b123-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b123-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7b123-110">Child Elements</span></span>

<span data-ttu-id="7b123-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="7b123-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b123-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7b123-112">Parent Elements</span></span>

|<span data-ttu-id="7b123-113">Element</span><span class="sxs-lookup"><span data-stu-id="7b123-113">Element</span></span>|<span data-ttu-id="7b123-114">Description</span><span class="sxs-lookup"><span data-stu-id="7b123-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b123-115">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="7b123-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7b123-116">Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7b123-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b123-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="7b123-117">Text Value</span></span>

<span data-ttu-id="7b123-118">Geben Sie das auszuwertende Skript an.</span><span class="sxs-lookup"><span data-stu-id="7b123-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b123-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7b123-119">Remarks</span></span>

<span data-ttu-id="7b123-120">PowerShell startet immer dann eine neue Gruppe, wenn der Wert dieses Skripts geändert wird.</span><span class="sxs-lookup"><span data-stu-id="7b123-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="7b123-121">Wenn dieses Element angegeben ist, können Sie das [propertyName](propertyname-element-for-groupby-format.md) -Element nicht angeben, um eine neue Gruppe zu starten.</span><span class="sxs-lookup"><span data-stu-id="7b123-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b123-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7b123-122">See Also</span></span>

[<span data-ttu-id="7b123-123">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7b123-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="7b123-124">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="7b123-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="7b123-125">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="7b123-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
