---
title: CustomControl-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368959"
---
# <a name="customcontrol-element-for-groupby-format"></a><span data-ttu-id="9b017-102">Element „CustomControl“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9b017-102">CustomControl Element for GroupBy (Format)</span></span>

<span data-ttu-id="9b017-103">Definiert das benutzerdefinierte Steuerelement, das die neue Gruppe anzeigt.</span><span class="sxs-lookup"><span data-stu-id="9b017-103">Defines the custom control that displays the new group.</span></span>

<span data-ttu-id="9b017-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9b017-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9b017-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b017-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b017-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9b017-106">Attributes and Elements</span></span>

<span data-ttu-id="9b017-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `CustomControl`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9b017-107">The following sections describe the attributes, child elements, and parent element of the `CustomControl` element.</span></span> <span data-ttu-id="9b017-108">Sie können beliebig viele untergeordnete Elemente angeben und in beliebiger Reihenfolge auflisten.</span><span class="sxs-lookup"><span data-stu-id="9b017-108">You can specify any number of child elements and list them in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b017-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9b017-109">Attributes</span></span>

<span data-ttu-id="9b017-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9b017-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9b017-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9b017-111">Child Elements</span></span>

|<span data-ttu-id="9b017-112">Element</span><span class="sxs-lookup"><span data-stu-id="9b017-112">Element</span></span>|<span data-ttu-id="9b017-113">Description</span><span class="sxs-lookup"><span data-stu-id="9b017-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b017-114">Customentries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9b017-114">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="9b017-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="9b017-115">Required element.</span></span><br /><br /> <span data-ttu-id="9b017-116">Stellt die Definitionen für das-Steuerelement bereit.</span><span class="sxs-lookup"><span data-stu-id="9b017-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9b017-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9b017-117">Parent Elements</span></span>

|<span data-ttu-id="9b017-118">Element</span><span class="sxs-lookup"><span data-stu-id="9b017-118">Element</span></span>|<span data-ttu-id="9b017-119">Description</span><span class="sxs-lookup"><span data-stu-id="9b017-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9b017-120">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b017-120">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="9b017-121">Definiert, wie Windows PowerShell eine neue Gruppe von Objekten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="9b017-121">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9b017-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9b017-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="9b017-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9b017-123">See Also</span></span>

[<span data-ttu-id="9b017-124">Customentries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9b017-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="9b017-125">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="9b017-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9b017-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="9b017-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
