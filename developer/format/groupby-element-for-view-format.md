---
title: GroupBy-Element für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859526"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="025d9-102">Element „GroupBy“ für View (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="025d9-103">Definiert, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="025d9-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="025d9-104">Dieses Element wird verwendet, bei der Definition einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen.</span><span class="sxs-lookup"><span data-stu-id="025d9-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="025d9-105">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="025d9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="025d9-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="025d9-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="025d9-107">Attributes and Elements</span></span>

<span data-ttu-id="025d9-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="025d9-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="025d9-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="025d9-109">Attributes</span></span>

<span data-ttu-id="025d9-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="025d9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="025d9-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="025d9-111">Child Elements</span></span>

|<span data-ttu-id="025d9-112">Element</span><span class="sxs-lookup"><span data-stu-id="025d9-112">Element</span></span>|<span data-ttu-id="025d9-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="025d9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="025d9-114">CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="025d9-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="025d9-115">Optional element.</span></span><br /><br /> <span data-ttu-id="025d9-116">Definiert das benutzerdefinierte Steuerelement, in denen neue Gruppen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="025d9-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="025d9-117">CustomControlName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="025d9-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="025d9-118">Optional element.</span></span><br /><br /> <span data-ttu-id="025d9-119">Gibt den Namen eines Steuerelements, die verwendet wird, um die neue Gruppe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="025d9-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="025d9-120">Label-Element für die GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="025d9-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="025d9-121">Optional element.</span></span><br /><br /> <span data-ttu-id="025d9-122">Gibt eine Bezeichnung, die angezeigt wird, wenn eine neue Gruppe gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="025d9-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="025d9-123">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="025d9-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="025d9-124">Optional element.</span></span><br /><br /> <span data-ttu-id="025d9-125">Gibt an, die .NET-Eigenschaft der beginnt eine neue Gruppe, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="025d9-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="025d9-126">ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="025d9-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="025d9-127">Optional element.</span></span><br /><br /> <span data-ttu-id="025d9-128">Gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="025d9-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="025d9-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="025d9-129">Parent Elements</span></span>

|<span data-ttu-id="025d9-130">Element</span><span class="sxs-lookup"><span data-stu-id="025d9-130">Element</span></span>|<span data-ttu-id="025d9-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="025d9-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="025d9-132">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="025d9-133">Definiert eine Ansicht, in dem ein oder mehrere .NET Objekte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="025d9-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="025d9-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="025d9-134">Remarks</span></span>

<span data-ttu-id="025d9-135">Wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird, müssen Sie angeben, die Eigenschaft oder ein Skript, das die neue Gruppe gestartet wird; Sie können nicht jedoch beides angeben.</span><span class="sxs-lookup"><span data-stu-id="025d9-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="025d9-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="025d9-136">See Also</span></span>

[<span data-ttu-id="025d9-137">CustomControlName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="025d9-138">Label-Element für die GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="025d9-139">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="025d9-140">ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="025d9-141">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="025d9-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="025d9-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="025d9-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
