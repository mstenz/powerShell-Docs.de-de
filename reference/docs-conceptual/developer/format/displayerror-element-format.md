---
title: Display Error-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363989"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="4d720-102">Element „DisplayError“ (Format)</span><span class="sxs-lookup"><span data-stu-id="4d720-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="4d720-103">Gibt an, dass die Zeichenfolge #Err angezeigt wird, wenn ein Fehler beim Anzeigen eines Daten Abschnitts auftritt.</span><span class="sxs-lookup"><span data-stu-id="4d720-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="4d720-104">Configuration-Element (Format) DefaultSettings-Element (Format) Display Error-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4d720-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4d720-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4d720-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d720-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="4d720-106">Attributes and Elements</span></span>

<span data-ttu-id="4d720-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `DisplayError`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4d720-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4d720-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="4d720-108">Attributes</span></span>

<span data-ttu-id="4d720-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="4d720-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4d720-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4d720-110">Child Elements</span></span>

<span data-ttu-id="4d720-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="4d720-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4d720-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4d720-112">Parent Elements</span></span>

|<span data-ttu-id="4d720-113">Element</span><span class="sxs-lookup"><span data-stu-id="4d720-113">Element</span></span>|<span data-ttu-id="4d720-114">Description</span><span class="sxs-lookup"><span data-stu-id="4d720-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4d720-115">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4d720-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="4d720-116">Definiert allgemeine Einstellungen, die für alle Sichten der Formatierungs Datei gelten.</span><span class="sxs-lookup"><span data-stu-id="4d720-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4d720-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4d720-117">Remarks</span></span>

<span data-ttu-id="4d720-118">Wenn ein Fehler auftritt, während versucht wird, ein Datenelement anzuzeigen, wird der Speicherort der Datenstandard mäßig leer gelassen.</span><span class="sxs-lookup"><span data-stu-id="4d720-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="4d720-119">Wenn dieses Element auf true festgelegt ist, wird die #Err Zeichenfolge angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4d720-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d720-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4d720-120">See Also</span></span>

[<span data-ttu-id="4d720-121">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4d720-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="4d720-122">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="4d720-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
