---
title: Frame-Element für customItem für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363639"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="63d4a-102">Element „Frame“ für CustomItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="63d4a-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="63d4a-103">Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="63d4a-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="63d4a-104">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="63d4a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="63d4a-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für customcontrolview (Format) Frame-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="63d4a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="63d4a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="63d4a-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63d4a-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="63d4a-107">Attributes and Elements</span></span>

<span data-ttu-id="63d4a-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Frame`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="63d4a-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="63d4a-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="63d4a-109">Attributes</span></span>

<span data-ttu-id="63d4a-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="63d4a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="63d4a-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="63d4a-111">Child Elements</span></span>

|<span data-ttu-id="63d4a-112">Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-112">Element</span></span>|<span data-ttu-id="63d4a-113">Description</span><span class="sxs-lookup"><span data-stu-id="63d4a-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="63d4a-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-114">Required Element</span></span>|
|[<span data-ttu-id="63d4a-115">Firstlinehanging-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="63d4a-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63d4a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="63d4a-117">Gibt an, wie viele Zeichen die erste Zeile der Daten nach links verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="63d4a-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="63d4a-118">Firstlineingedent-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="63d4a-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63d4a-119">Optional element.</span></span><br /><br /> <span data-ttu-id="63d4a-120">Gibt an, wie viele Zeichen die erste Zeile der Daten nach rechts verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="63d4a-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="63d4a-121">LeftIndent-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="63d4a-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63d4a-122">Optional element.</span></span><br /><br /> <span data-ttu-id="63d4a-123">Gibt an, wie viele Zeichen die Daten vom linken Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="63d4a-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="63d4a-124">RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="63d4a-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="63d4a-125">Optional element.</span></span><br /><br /> <span data-ttu-id="63d4a-126">Gibt an, wie viele Zeichen die Daten vom rechten Rand entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="63d4a-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="63d4a-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="63d4a-127">Parent Elements</span></span>

|<span data-ttu-id="63d4a-128">Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-128">Element</span></span>|<span data-ttu-id="63d4a-129">Description</span><span class="sxs-lookup"><span data-stu-id="63d4a-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="63d4a-130">CustomItem-Element für customentry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="63d4a-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="63d4a-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="63d4a-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63d4a-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="63d4a-132">Remarks</span></span>

<span data-ttu-id="63d4a-133">Sie können die Elemente [firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) nicht im selben `Frame`-Element angeben.</span><span class="sxs-lookup"><span data-stu-id="63d4a-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="63d4a-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="63d4a-134">See Also</span></span>

[<span data-ttu-id="63d4a-135">Firstlinehanging-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="63d4a-136">Firstlineingedent-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="63d4a-137">LeftIndent-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="63d4a-138">RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="63d4a-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="63d4a-139">CustomItem-Element für customentry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="63d4a-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="63d4a-140">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="63d4a-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
