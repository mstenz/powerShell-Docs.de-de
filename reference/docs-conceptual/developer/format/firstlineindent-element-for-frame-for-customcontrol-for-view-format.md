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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363059"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a><span data-ttu-id="91e60-102">Element „FirstLineIndent“ für Frame für CustomControl für View (Format)</span><span class="sxs-lookup"><span data-stu-id="91e60-102">FirstLineIndent Element for Frame for CustomControl for View (Format)</span></span>

<span data-ttu-id="91e60-103">Gibt an, wie viele Zeichen die erste Zeile der Daten nach rechts verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="91e60-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="91e60-104">Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="91e60-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="91e60-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für customcontrolview (Format) Frame-Element für customItem für CustomControl für View (Format) FirstLineIndent-Element</span><span class="sxs-lookup"><span data-stu-id="91e60-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for CustomControlView (Format) Frame Element for CustomItem for CustomControl for View (Format) FirstLineIndent Element</span></span>

## <a name="syntax"></a><span data-ttu-id="91e60-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="91e60-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="91e60-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="91e60-107">Attributes and Elements</span></span>

<span data-ttu-id="91e60-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `FirstLineIndent`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="91e60-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="91e60-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="91e60-109">Attributes</span></span>

<span data-ttu-id="91e60-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="91e60-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="91e60-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="91e60-111">Child Elements</span></span>

<span data-ttu-id="91e60-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="91e60-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="91e60-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="91e60-113">Parent Elements</span></span>

|<span data-ttu-id="91e60-114">Element</span><span class="sxs-lookup"><span data-stu-id="91e60-114">Element</span></span>|<span data-ttu-id="91e60-115">Description</span><span class="sxs-lookup"><span data-stu-id="91e60-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91e60-116">Frame-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="91e60-116">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="91e60-117">Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="91e60-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="91e60-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="91e60-118">Text Value</span></span>

<span data-ttu-id="91e60-119">Geben Sie die Anzahl der Zeichen an, die Sie in die erste Zeile der Daten verschieben möchten.</span><span class="sxs-lookup"><span data-stu-id="91e60-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="91e60-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="91e60-120">Remarks</span></span>

<span data-ttu-id="91e60-121">Wenn dieses Element angegeben ist, können Sie das [firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) -Element nicht angeben.</span><span class="sxs-lookup"><span data-stu-id="91e60-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="91e60-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="91e60-122">See Also</span></span>

[<span data-ttu-id="91e60-123">Firstlinehanging-Element für Frame für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="91e60-123">FirstLineHanging Element for Frame for CustomControl for View (Format)</span></span>](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[<span data-ttu-id="91e60-124">Frame-Element für customItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="91e60-124">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="91e60-125">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="91e60-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
