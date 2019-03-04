---
title: ListItem-Element für ListItems für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855156"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="d6adc-102">Element „ListItem“ für ListItems für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="d6adc-103">Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d6adc-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="d6adc-104">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListControl (Format) ListItems-Element für ListControl (Format) ListItem für ListControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d6adc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d6adc-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d6adc-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="d6adc-106">Attributes and Elements</span></span>

<span data-ttu-id="d6adc-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ListItem` Element.</span><span class="sxs-lookup"><span data-stu-id="d6adc-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="d6adc-108">Nur eine Eigenschaft oder ein Skript kann angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d6adc-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="d6adc-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="d6adc-109">Attributes</span></span>

<span data-ttu-id="d6adc-110">Keine</span><span class="sxs-lookup"><span data-stu-id="d6adc-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d6adc-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d6adc-111">Child Elements</span></span>

|<span data-ttu-id="d6adc-112">Element</span><span class="sxs-lookup"><span data-stu-id="d6adc-112">Element</span></span>|<span data-ttu-id="d6adc-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6adc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6adc-114">FormatString-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d6adc-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d6adc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="d6adc-116">Gibt eine Zeichenfolge, die definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d6adc-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="d6adc-117">ItemSelectionCondition-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d6adc-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d6adc-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d6adc-119">Definiert die Bedingung, die für dieses Listenelement zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="d6adc-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="d6adc-120">Label-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d6adc-121">Optionales element</span><span class="sxs-lookup"><span data-stu-id="d6adc-121">Optional element</span></span><br /><br /> <span data-ttu-id="d6adc-122">Gibt die Bezeichnung, die auf der linken Seite des Eigenschaft oder des Skripts in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d6adc-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="d6adc-123">PropertyName-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d6adc-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d6adc-124">Optional element.</span></span><br /><br /> <span data-ttu-id="d6adc-125">Gibt die .NET-Eigenschaft, deren Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d6adc-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="d6adc-126">ScriptBlock-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="d6adc-127">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="d6adc-127">Optional element.</span></span><br /><br /> <span data-ttu-id="d6adc-128">Gibt das Skript an, dessen Wert in der Zeile angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d6adc-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d6adc-129">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="d6adc-129">Parent Elements</span></span>

|<span data-ttu-id="d6adc-130">Element</span><span class="sxs-lookup"><span data-stu-id="d6adc-130">Element</span></span>|<span data-ttu-id="d6adc-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d6adc-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d6adc-132">ListItems-Element für das Listensteuerelement (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="d6adc-133">Definiert die Eigenschaften und Skripts, deren Werte in der Listenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d6adc-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d6adc-134">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d6adc-134">Remarks</span></span>

<span data-ttu-id="d6adc-135">Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d6adc-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d6adc-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d6adc-136">Example</span></span>

<span data-ttu-id="d6adc-137">Dieses Beispiel zeigt die XML-Elemente, die drei Zeilen der Listenansicht zu definieren.</span><span class="sxs-lookup"><span data-stu-id="d6adc-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="d6adc-138">Die ersten beiden Zeilen den Wert einer Eigenschaft für die .NET anzeigen, und die letzte Zeile zeigt einen Wert, der durch ein Skript generiert.</span><span class="sxs-lookup"><span data-stu-id="d6adc-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="d6adc-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d6adc-139">See Also</span></span>

[<span data-ttu-id="d6adc-140">ListItems-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="d6adc-141">FormatString-Element für den ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d6adc-142">Label-Element für den ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d6adc-143">PropertyName-Element für den ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d6adc-144">ScriptBlock-Element für den ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="d6adc-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="d6adc-145">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="d6adc-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d6adc-146">Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei</span><span class="sxs-lookup"><span data-stu-id="d6adc-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
