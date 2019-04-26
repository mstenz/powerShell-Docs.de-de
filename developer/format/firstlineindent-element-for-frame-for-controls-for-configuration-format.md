---
title: FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065987"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="1eb1c-102">Element „FirstLineIndent“ für Frame für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb1c-102">FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1eb1c-103">Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-103">Specifies how many characters the first line of data is shifted to the right.</span></span> <span data-ttu-id="1eb1c-104">Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1eb1c-105">Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die Frame-Konfigurationselement für CustomItem für Steuerelemente für FirstLineIndent-Element für Konfiguration (Format) für Frame-Format) für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb1c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineIndent Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1eb1c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1eb1c-106">Syntax</span></span>

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1eb1c-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="1eb1c-107">Attributes and Elements</span></span>

<span data-ttu-id="1eb1c-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `FirstLineIndent` Element.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-108">The following sections describe attributes, child elements, and parent element of the `FirstLineIndent` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1eb1c-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1eb1c-109">Attributes</span></span>

<span data-ttu-id="1eb1c-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1eb1c-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1eb1c-111">Child Elements</span></span>

<span data-ttu-id="1eb1c-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1eb1c-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1eb1c-113">Parent Elements</span></span>

|<span data-ttu-id="1eb1c-114">Element</span><span class="sxs-lookup"><span data-stu-id="1eb1c-114">Element</span></span>|<span data-ttu-id="1eb1c-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1eb1c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1eb1c-116">Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb1c-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="1eb1c-117">Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1eb1c-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="1eb1c-118">Text Value</span></span>

<span data-ttu-id="1eb1c-119">Geben Sie die Anzahl der Zeichen, die die erste Zeile der Daten verschoben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="1eb1c-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1eb1c-120">Remarks</span></span>

<span data-ttu-id="1eb1c-121">Wenn dieses Element angegeben ist, Sie können nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) Element.</span><span class="sxs-lookup"><span data-stu-id="1eb1c-121">If this element is specified, you cannot specify the [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) element.</span></span>

## <a name="see-also"></a><span data-ttu-id="1eb1c-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1eb1c-122">See Also</span></span>

[<span data-ttu-id="1eb1c-123">FirstLineHanging-Element für Frame für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb1c-123">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[<span data-ttu-id="1eb1c-124">Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb1c-124">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="1eb1c-125">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="1eb1c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
