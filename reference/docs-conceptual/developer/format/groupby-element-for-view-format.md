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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363629"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="43262-102">Element „GroupBy“ für View (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="43262-103">Definiert, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="43262-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="43262-104">Dieses Element wird verwendet, wenn eine Tabelle, eine Liste, eine Breite oder eine benutzerdefinierte Steuerelement Ansicht definiert wird.</span><span class="sxs-lookup"><span data-stu-id="43262-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="43262-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43262-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="43262-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43262-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="43262-107">Attributes and Elements</span></span>

<span data-ttu-id="43262-108">In den folgenden Abschnitten werden die Attribute, untergeordneten und übergeordneten Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="43262-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="43262-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="43262-109">Attributes</span></span>

<span data-ttu-id="43262-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="43262-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43262-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="43262-111">Child Elements</span></span>

|<span data-ttu-id="43262-112">Element</span><span class="sxs-lookup"><span data-stu-id="43262-112">Element</span></span>|<span data-ttu-id="43262-113">Description</span><span class="sxs-lookup"><span data-stu-id="43262-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43262-114">CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="43262-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="43262-115">Optional element.</span></span><br /><br /> <span data-ttu-id="43262-116">Definiert das benutzerdefinierte Steuerelement, das neue Gruppen anzeigt.</span><span class="sxs-lookup"><span data-stu-id="43262-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="43262-117">Customcontrolname-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="43262-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="43262-118">Optional element.</span></span><br /><br /> <span data-ttu-id="43262-119">Gibt den Namen eines Steuer Elements an, das zum Anzeigen der neuen Gruppe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="43262-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="43262-120">Label-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="43262-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="43262-121">Optional element.</span></span><br /><br /> <span data-ttu-id="43262-122">Gibt eine Bezeichnung an, die beim Auftreten einer neuen Gruppe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="43262-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="43262-123">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="43262-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="43262-124">Optional element.</span></span><br /><br /> <span data-ttu-id="43262-125">Gibt an, dass die .net-Eigenschaft eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="43262-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="43262-126">ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="43262-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="43262-127">Optional element.</span></span><br /><br /> <span data-ttu-id="43262-128">Gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert.</span><span class="sxs-lookup"><span data-stu-id="43262-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="43262-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="43262-129">Parent Elements</span></span>

|<span data-ttu-id="43262-130">Element</span><span class="sxs-lookup"><span data-stu-id="43262-130">Element</span></span>|<span data-ttu-id="43262-131">Description</span><span class="sxs-lookup"><span data-stu-id="43262-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43262-132">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="43262-133">Definiert eine Ansicht, in der ein oder mehrere .NET-Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="43262-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43262-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="43262-134">Remarks</span></span>

<span data-ttu-id="43262-135">Wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird, müssen Sie die Eigenschaft oder das Skript angeben, mit der die neue Gruppe gestartet wird. Es ist jedoch nicht möglich, beides anzugeben.</span><span class="sxs-lookup"><span data-stu-id="43262-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="43262-136">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="43262-136">See Also</span></span>

[<span data-ttu-id="43262-137">Customcontrolname-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="43262-138">Label-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="43262-139">PropertyName-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="43262-140">ScriptBlock-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="43262-141">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="43262-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="43262-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="43262-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
