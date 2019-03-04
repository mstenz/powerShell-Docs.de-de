---
title: DisplayError-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854916"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="fe010-102">Element „DisplayError“ (Format)</span><span class="sxs-lookup"><span data-stu-id="fe010-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="fe010-103">Gibt an, dass die Zeichenfolge #ERR angezeigt wird, wenn ein Fehler auftritt, Anzeigen von Daten.</span><span class="sxs-lookup"><span data-stu-id="fe010-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="fe010-104">-Element (Format) DefaultSettings-Element (Format) DisplayError Konfigurationselement (Frmat)</span><span class="sxs-lookup"><span data-stu-id="fe010-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Frmat)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe010-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fe010-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe010-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="fe010-106">Attributes and Elements</span></span>

<span data-ttu-id="fe010-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `DisplayError` Element.</span><span class="sxs-lookup"><span data-stu-id="fe010-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe010-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="fe010-108">Attributes</span></span>

<span data-ttu-id="fe010-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="fe010-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe010-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fe010-110">Child Elements</span></span>

<span data-ttu-id="fe010-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="fe010-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe010-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="fe010-112">Parent Elements</span></span>

|<span data-ttu-id="fe010-113">Element</span><span class="sxs-lookup"><span data-stu-id="fe010-113">Element</span></span>|<span data-ttu-id="fe010-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fe010-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe010-115">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fe010-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="fe010-116">Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.</span><span class="sxs-lookup"><span data-stu-id="fe010-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fe010-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fe010-117">Remarks</span></span>

<span data-ttu-id="fe010-118">Standardmäßig tritt ein Fehler beim Versuch, ein Datenelement, angezeigt wird der Speicherort der Daten leer gelassen.</span><span class="sxs-lookup"><span data-stu-id="fe010-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="fe010-119">Wenn dieses Element die #ERR-Zeichenfolge "true" festgelegt ist, wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fe010-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe010-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fe010-120">See Also</span></span>

[<span data-ttu-id="fe010-121">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="fe010-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="fe010-122">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe010-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
