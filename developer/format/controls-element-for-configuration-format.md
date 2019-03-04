---
title: Controls-Element für Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861176"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="437ce-102">Element „Controls“ für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="437ce-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="437ce-103">Definiert die allgemeinen Steuerelemente, die von allen Ansichten des die Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="437ce-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="437ce-104">Konfiguration-Element (Format)-Controls-Element (Format)-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="437ce-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="437ce-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="437ce-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="437ce-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="437ce-106">Attributes and Elements</span></span>

<span data-ttu-id="437ce-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Controls` Element.</span><span class="sxs-lookup"><span data-stu-id="437ce-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="437ce-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="437ce-108">Attributes</span></span>

<span data-ttu-id="437ce-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="437ce-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="437ce-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="437ce-110">Child Elements</span></span>

|<span data-ttu-id="437ce-111">Element</span><span class="sxs-lookup"><span data-stu-id="437ce-111">Element</span></span>|<span data-ttu-id="437ce-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="437ce-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="437ce-113">Control-Element für Controls für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="437ce-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="437ce-114">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="437ce-114">Required element.</span></span><br /><br /> <span data-ttu-id="437ce-115">Definiert ein allgemeines Steuerelement, das von allen Ansichten des die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="437ce-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="437ce-116">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="437ce-116">Parent Elements</span></span>

|<span data-ttu-id="437ce-117">Element</span><span class="sxs-lookup"><span data-stu-id="437ce-117">Element</span></span>|<span data-ttu-id="437ce-118">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="437ce-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="437ce-119">Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="437ce-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="437ce-120">Das Element das obersten Ebene eine Formatierungsdatei darstellt.</span><span class="sxs-lookup"><span data-stu-id="437ce-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="437ce-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="437ce-121">Remarks</span></span>

<span data-ttu-id="437ce-122">Sie können eine beliebige Anzahl von allgemeinen Steuerelementen erstellen.</span><span class="sxs-lookup"><span data-stu-id="437ce-122">You can create any number of common controls.</span></span> <span data-ttu-id="437ce-123">Für jedes Steuerelement müssen Sie den Namen angeben, der zum Verweisen auf das Steuerelement und die Komponenten des Steuerelements verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="437ce-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="437ce-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="437ce-124">See Also</span></span>

[<span data-ttu-id="437ce-125">Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="437ce-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="437ce-126">Control-Element für Controls für Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="437ce-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="437ce-127">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="437ce-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
