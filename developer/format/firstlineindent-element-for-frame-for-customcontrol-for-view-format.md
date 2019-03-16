---
title: FirstLineIndent-Element für Frame für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054848"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="3ee07-102">Element „FirstLineIndent“ für Frame für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="3ee07-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="3ee07-103">Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="3ee07-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="3ee07-104">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3ee07-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3ee07-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für Frame-Element für CustomItem für CustomControl für Ansichtselement (Format) FirstLineIndent CustomControlView (Format)</span><span class="sxs-lookup"><span data-stu-id="3ee07-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="3ee07-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ee07-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ee07-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3ee07-107">Attributes and Elements</span></span>

<span data-ttu-id="3ee07-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `FirstLineIndent` Element.</span><span class="sxs-lookup"><span data-stu-id="3ee07-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ee07-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="3ee07-109">Attributes</span></span>

<span data-ttu-id="3ee07-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="3ee07-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ee07-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3ee07-111">Child Elements</span></span>

<span data-ttu-id="3ee07-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="3ee07-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3ee07-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3ee07-113">Parent Elements</span></span>

|<span data-ttu-id="3ee07-114">Element</span><span class="sxs-lookup"><span data-stu-id="3ee07-114">Element</span></span>|<span data-ttu-id="3ee07-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3ee07-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ee07-116">Frame-Element für CustomItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3ee07-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3ee07-117">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="3ee07-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3ee07-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="3ee07-118">Text Value</span></span>

<span data-ttu-id="3ee07-119">Geben Sie die Anzahl der Zeichen, die die erste Zeile der Daten verschoben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="3ee07-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ee07-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3ee07-120">Remarks</span></span>

<span data-ttu-id="3ee07-121">Wenn dieses Element angegeben ist, Sie können nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="3ee07-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ee07-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3ee07-122">See Also</span></span>

[<span data-ttu-id="3ee07-123">FirstLineHanging-Element für Frame für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3ee07-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3ee07-124">Frame-Element für CustomItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3ee07-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3ee07-125">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ee07-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
