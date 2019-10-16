---
title: GroupBy-Element für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363629"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="da055-102">Element „GroupBy“ für View (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="da055-103">Definiert, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="da055-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="da055-104">Dieses Element wird verwendet, wenn eine Tabelle, eine Liste, eine Breite oder eine benutzerdefinierte Steuerelement Ansicht definiert wird.</span><span class="sxs-lookup"><span data-stu-id="da055-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="da055-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="da055-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="da055-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="da055-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="da055-107">Attributes and Elements</span></span>

<span data-ttu-id="da055-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="da055-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="da055-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="da055-109">Attributes</span></span>

<span data-ttu-id="da055-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="da055-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="da055-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="da055-111">Child Elements</span></span>

|<span data-ttu-id="da055-112">Element</span><span class="sxs-lookup"><span data-stu-id="da055-112">Element</span></span>|<span data-ttu-id="da055-113">Description</span><span class="sxs-lookup"><span data-stu-id="da055-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="da055-114">CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="da055-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="da055-115">Optional element.</span></span><br /><br /> <span data-ttu-id="da055-116">Definiert das benutzerdefinierte Steuerelement, das neue Gruppen anzeigt.</span><span class="sxs-lookup"><span data-stu-id="da055-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="da055-117">Customcontrolname-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="da055-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="da055-118">Optional element.</span></span><br /><br /> <span data-ttu-id="da055-119">Gibt den Namen eines Steuer Elements an, das zum Anzeigen der neuen Gruppe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="da055-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="da055-120">Label-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="da055-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="da055-121">Optional element.</span></span><br /><br /> <span data-ttu-id="da055-122">Gibt eine Bezeichnung an, die beim Auftreten einer neuen Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="da055-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="da055-123">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="da055-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="da055-124">Optional element.</span></span><br /><br /> <span data-ttu-id="da055-125">Gibt an, dass die .net-Eigenschaft eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="da055-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="da055-126">ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="da055-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="da055-127">Optional element.</span></span><br /><br /> <span data-ttu-id="da055-128">Gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="da055-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="da055-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="da055-129">Parent Elements</span></span>

|<span data-ttu-id="da055-130">Element</span><span class="sxs-lookup"><span data-stu-id="da055-130">Element</span></span>|<span data-ttu-id="da055-131">Description</span><span class="sxs-lookup"><span data-stu-id="da055-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="da055-132">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="da055-133">Definiert eine Ansicht, in der ein oder mehrere .NET-Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="da055-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="da055-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="da055-134">Remarks</span></span>

<span data-ttu-id="da055-135">Wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird, müssen Sie die Eigenschaft oder das Skript angeben, mit der die neue Gruppe gestartet wird. Es ist jedoch nicht möglich, beides anzugeben.</span><span class="sxs-lookup"><span data-stu-id="da055-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="da055-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="da055-136">See Also</span></span>

[<span data-ttu-id="da055-137">Customcontrolname-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="da055-138">Label-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="da055-139">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="da055-140">ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="da055-141">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="da055-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="da055-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="da055-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
