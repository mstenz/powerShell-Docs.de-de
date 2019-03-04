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
ms.openlocfilehash: a7ee550527ec1cb00b4ed83478992c7ab54dbdb6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861706"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="fc385-102">Element „Frame“ für CustomItem für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="fc385-102">Frame Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="fc385-103">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="fc385-103">Defines how the data is displayed, such as shifting the data to the left or right.</span></span> <span data-ttu-id="fc385-104">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fc385-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="fc385-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für CutomControlView (Format)-Frame-Element für CustomItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="fc385-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CutomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fc385-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc385-106">Syntax</span></span>

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc385-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fc385-107">Attributes and Elements</span></span>

<span data-ttu-id="fc385-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="fc385-108">The following sections describe attributes, child elements, and the parent element of the `Frame` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc385-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="fc385-109">Attributes</span></span>

<span data-ttu-id="fc385-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="fc385-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fc385-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fc385-111">Child Elements</span></span>

|<span data-ttu-id="fc385-112">Element</span><span class="sxs-lookup"><span data-stu-id="fc385-112">Element</span></span>|<span data-ttu-id="fc385-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fc385-113">Description</span></span>|
|-------------|-----------------|
|`CustomItem Element`|<span data-ttu-id="fc385-114">Erforderliches Element</span><span class="sxs-lookup"><span data-stu-id="fc385-114">Required Element</span></span>|
|[<span data-ttu-id="fc385-115">FirstLineHanging-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-115">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="fc385-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="fc385-116">Optional element.</span></span><br /><br /> <span data-ttu-id="fc385-117">Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="fc385-117">Specifies how many characters the first line of data is shifted to the left.</span></span>|
|[<span data-ttu-id="fc385-118">FirstLineIndent-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-118">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="fc385-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="fc385-119">Optional element.</span></span><br /><br /> <span data-ttu-id="fc385-120">Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="fc385-120">Specifies how many characters the first line of data is shifted to the right.</span></span>|
|[<span data-ttu-id="fc385-121">LeftIndent-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-121">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="fc385-122">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="fc385-122">Optional element.</span></span><br /><br /> <span data-ttu-id="fc385-123">Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="fc385-123">Specifies how many characters the data is shifted away from the left margin.</span></span>|
|[<span data-ttu-id="fc385-124">RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-124">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|<span data-ttu-id="fc385-125">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="fc385-125">Optional element.</span></span><br /><br /> <span data-ttu-id="fc385-126">Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="fc385-126">Specifies how many characters the data is shifted away from the right margin.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fc385-127">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fc385-127">Parent Elements</span></span>

|<span data-ttu-id="fc385-128">Element</span><span class="sxs-lookup"><span data-stu-id="fc385-128">Element</span></span>|<span data-ttu-id="fc385-129">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fc385-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fc385-130">CustomItem-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="fc385-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="fc385-131">Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fc385-131">Defines what data is displayed by the control and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fc385-132">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fc385-132">Remarks</span></span>

<span data-ttu-id="fc385-133">Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Elemente in der gleichen `Frame` Element.</span><span class="sxs-lookup"><span data-stu-id="fc385-133">You cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) and the [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) elements in the same `Frame` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc385-134">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fc385-134">See Also</span></span>

[<span data-ttu-id="fc385-135">FirstLineHanging-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-135">FirstLineHanging Element</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fc385-136">FirstLineIndent-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-136">FirstLineIndent Element</span></span>](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fc385-137">LeftIndent-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-137">LeftIndent Element</span></span>](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fc385-138">RightIndent-Element</span><span class="sxs-lookup"><span data-stu-id="fc385-138">RightIndent Element</span></span>](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fc385-139">CustomItem-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="fc385-139">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fc385-140">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="fc385-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
