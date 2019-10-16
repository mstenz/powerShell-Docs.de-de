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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368999"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="86f89-102">Element „Controls“ für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="86f89-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="86f89-103">Definiert die allgemeinen Steuerelemente, die von allen Ansichten der Formatierungs Datei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="86f89-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="86f89-104">Configuration-Element (Format) steuert Element der Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="86f89-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86f89-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="86f89-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86f89-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="86f89-106">Attributes and Elements</span></span>

<span data-ttu-id="86f89-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Controls`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="86f89-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86f89-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="86f89-108">Attributes</span></span>

<span data-ttu-id="86f89-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="86f89-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86f89-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="86f89-110">Child Elements</span></span>

|<span data-ttu-id="86f89-111">Element</span><span class="sxs-lookup"><span data-stu-id="86f89-111">Element</span></span>|<span data-ttu-id="86f89-112">Description</span><span class="sxs-lookup"><span data-stu-id="86f89-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86f89-113">Control-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="86f89-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="86f89-114">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="86f89-114">Required element.</span></span><br /><br /> <span data-ttu-id="86f89-115">Definiert ein gängiges Steuerelement, das von allen Ansichten der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="86f89-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86f89-116">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="86f89-116">Parent Elements</span></span>

|<span data-ttu-id="86f89-117">Element</span><span class="sxs-lookup"><span data-stu-id="86f89-117">Element</span></span>|<span data-ttu-id="86f89-118">Description</span><span class="sxs-lookup"><span data-stu-id="86f89-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86f89-119">Configuration-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="86f89-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="86f89-120">Stellt das Element der obersten Ebene einer Formatierungs Datei dar.</span><span class="sxs-lookup"><span data-stu-id="86f89-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86f89-121">Hinweise</span><span class="sxs-lookup"><span data-stu-id="86f89-121">Remarks</span></span>

<span data-ttu-id="86f89-122">Sie können eine beliebige Anzahl von allgemeinen Steuerelementen erstellen.</span><span class="sxs-lookup"><span data-stu-id="86f89-122">You can create any number of common controls.</span></span> <span data-ttu-id="86f89-123">Für jedes Steuerelement müssen Sie den Namen angeben, der zum Verweisen auf das Steuerelement und die Komponenten des Steuer Elements verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="86f89-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="86f89-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="86f89-124">See Also</span></span>

[<span data-ttu-id="86f89-125">Configuration-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="86f89-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="86f89-126">Control-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="86f89-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="86f89-127">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="86f89-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
