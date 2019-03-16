---
title: Frame-Element für CustomItem für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054780"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="187e8-102">Element „Frame“ für CustomItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="187e8-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="187e8-103">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="187e8-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="187e8-104">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="187e8-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="187e8-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für CustomControlView (Format)-Frame-Element für CustomItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="187e8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="187e8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="187e8-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="187e8-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="187e8-107">Attributes and Elements</span></span>

<span data-ttu-id="187e8-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="187e8-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="187e8-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="187e8-109">Attributes</span></span>

<span data-ttu-id="187e8-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="187e8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="187e8-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="187e8-111">Child Elements</span></span>

|<span data-ttu-id="187e8-112">Element</span><span class="sxs-lookup"><span data-stu-id="187e8-112">Element</span></span>|<span data-ttu-id="187e8-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="187e8-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="187e8-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="187e8-114">Required Element</span></span>|
|[<span data-ttu-id="187e8-115">FirstLineHanging-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="187e8-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="187e8-116">Optional element.</span></span><br /><br /> <span data-ttu-id="187e8-117">Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="187e8-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="187e8-118">FirstLineIndent-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="187e8-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="187e8-119">Optional element.</span></span><br /><br /> <span data-ttu-id="187e8-120">Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="187e8-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="187e8-121">LeftIndent-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="187e8-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="187e8-122">Optional element.</span></span><br /><br /> <span data-ttu-id="187e8-123">Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="187e8-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="187e8-124">RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="187e8-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="187e8-125">Optional element.</span></span><br /><br /> <span data-ttu-id="187e8-126">Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="187e8-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="187e8-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="187e8-127">Parent Elements</span></span>

|<span data-ttu-id="187e8-128">Element</span><span class="sxs-lookup"><span data-stu-id="187e8-128">Element</span></span>|<span data-ttu-id="187e8-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="187e8-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="187e8-130">CustomItem-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="187e8-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="187e8-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="187e8-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="187e8-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="187e8-132">Remarks</span></span>

<span data-ttu-id="187e8-133">Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Elemente in der gleichen `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="187e8-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="187e8-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="187e8-134">See Also</span></span>

[<span data-ttu-id="187e8-135">FirstLineHanging-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="187e8-136">FirstLineIndent-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="187e8-137">LeftIndent-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="187e8-138">RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="187e8-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="187e8-139">CustomItem-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="187e8-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="187e8-140">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="187e8-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
