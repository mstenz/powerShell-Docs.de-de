---
title: Konfigurationselement (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066820"
---
# <a name="configuration-element-format"></a><span data-ttu-id="33915-102">Element „Configuration“ (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-102">Configuration Element (Format)</span></span>

<span data-ttu-id="33915-103">Das Element das obersten Ebene eine Formatierungsdatei darstellt.</span><span class="sxs-lookup"><span data-stu-id="33915-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="33915-104">Konfigurationselement</span><span class="sxs-lookup"><span data-stu-id="33915-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="33915-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="33915-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="33915-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="33915-106">Attributes and Elements</span></span>

<span data-ttu-id="33915-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Configuration` Element.</span><span class="sxs-lookup"><span data-stu-id="33915-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="33915-108">Dieses Element muss das Stammelement für jede Formatierungsdatei, und dieses Element muss mindestens ein untergeordnetes Element enthalten.</span><span class="sxs-lookup"><span data-stu-id="33915-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33915-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="33915-109">Attributes</span></span>

<span data-ttu-id="33915-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="33915-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33915-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="33915-111">Child Elements</span></span>

|<span data-ttu-id="33915-112">Element</span><span class="sxs-lookup"><span data-stu-id="33915-112">Element</span></span>|<span data-ttu-id="33915-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33915-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33915-114">Controls-Element für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="33915-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="33915-115">Optional element.</span></span><br /><br /> <span data-ttu-id="33915-116">Definiert die allgemeinen Steuerelemente, die von allen Ansichten des die Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="33915-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="33915-117">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="33915-118">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="33915-118">Optional element.</span></span><br /><br /> <span data-ttu-id="33915-119">Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.</span><span class="sxs-lookup"><span data-stu-id="33915-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="33915-120">Format des SelectionSets</span><span class="sxs-lookup"><span data-stu-id="33915-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="33915-121">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="33915-121">Optional element.</span></span><br /><br /> <span data-ttu-id="33915-122">Definiert die allgemeine Sätze von .NET-Objekten, die von allen Ansichten des die Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="33915-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="33915-123">ViewDefinitions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="33915-124">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="33915-124">Optional element.</span></span><br /><br /> <span data-ttu-id="33915-125">Definiert die Ansichten verwendet, um die Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="33915-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="33915-126">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="33915-126">Parent Elements</span></span>

<span data-ttu-id="33915-127">Keine.</span><span class="sxs-lookup"><span data-stu-id="33915-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="33915-128">Hinweise</span><span class="sxs-lookup"><span data-stu-id="33915-128">Remarks</span></span>

<span data-ttu-id="33915-129">Formatierungsdateien definieren, wie die Objekte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="33915-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="33915-130">In den meisten Fällen dieses Root-Element enthält eine [ViewDefinitions](./viewdefinitions-element-format.md) Element, das die Tabelle, Liste und Breiten Ansichten der formatierungs-Datei definiert.</span><span class="sxs-lookup"><span data-stu-id="33915-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="33915-131">Zusätzlich zu den Definitionen anzeigen kann die Formatierungsdatei definieren, allgemeine Auswahl legt, Einstellungen und Steuerelemente, die diese Sichten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="33915-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="33915-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="33915-132">See Also</span></span>

[<span data-ttu-id="33915-133">Controls-Element für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="33915-134">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="33915-135">SelectionSets-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="33915-136">ViewDefinitions-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="33915-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="33915-137">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="33915-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
