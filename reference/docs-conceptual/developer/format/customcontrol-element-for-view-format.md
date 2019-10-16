---
title: CustomControl-Element für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363359"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="eeb20-102">Element „CustomControl“ für View (Format)</span><span class="sxs-lookup"><span data-stu-id="eeb20-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="eeb20-103">Definiert ein benutzerdefiniertes Steuerelement Format für die Ansicht.</span><span class="sxs-lookup"><span data-stu-id="eeb20-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="eeb20-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="eeb20-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="eeb20-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="eeb20-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="eeb20-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="eeb20-106">Attributes and Elements</span></span>

<span data-ttu-id="eeb20-107">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomControl`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="eeb20-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="eeb20-108">Sie müssen ein untergeordnetes Element angeben.</span><span class="sxs-lookup"><span data-stu-id="eeb20-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="eeb20-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="eeb20-109">Attributes</span></span>

<span data-ttu-id="eeb20-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="eeb20-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="eeb20-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="eeb20-111">Child Elements</span></span>

|<span data-ttu-id="eeb20-112">Element</span><span class="sxs-lookup"><span data-stu-id="eeb20-112">Element</span></span>|<span data-ttu-id="eeb20-113">Description</span><span class="sxs-lookup"><span data-stu-id="eeb20-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eeb20-114">Customentries-Element für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="eeb20-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="eeb20-115">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="eeb20-115">Required element.</span></span><br /><br /> <span data-ttu-id="eeb20-116">Stellt die Definitionen der benutzerdefinierten Steuerelement Ansicht bereit.</span><span class="sxs-lookup"><span data-stu-id="eeb20-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="eeb20-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="eeb20-117">Parent Elements</span></span>

|<span data-ttu-id="eeb20-118">Element</span><span class="sxs-lookup"><span data-stu-id="eeb20-118">Element</span></span>|<span data-ttu-id="eeb20-119">Description</span><span class="sxs-lookup"><span data-stu-id="eeb20-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="eeb20-120">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="eeb20-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="eeb20-121">Definiert eine Ansicht, die verwendet wird, um ein oder mehrere .NET-Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="eeb20-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="eeb20-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="eeb20-122">Remarks</span></span>

<span data-ttu-id="eeb20-123">In den meisten Fällen ist nur eine Definition für jede Steuerelement Ansicht erforderlich, aber es ist möglich, mehrere Definitionen bereitzustellen, wenn Sie die gleiche Ansicht verwenden möchten, um unterschiedliche .NET-Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="eeb20-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="eeb20-124">In diesen Fällen können Sie eine separate Definition für jedes Objekt oder jede Gruppe von Objekten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="eeb20-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="eeb20-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="eeb20-125">See Also</span></span>

[<span data-ttu-id="eeb20-126">Customentries-Element für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="eeb20-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="eeb20-127">View-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="eeb20-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="eeb20-128">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="eeb20-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
