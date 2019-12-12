---
title: Customentry-Element für CustomControl für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364059"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="1545e-102">Element „CustomEntry“ für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="1545e-103">Stellt eine Definition des-Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="1545e-103">Provides a definition of the control.</span></span> <span data-ttu-id="1545e-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1545e-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1545e-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1545e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1545e-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1545e-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="1545e-107">Attributes and Elements</span></span>

<span data-ttu-id="1545e-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente des `CustomEntry`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1545e-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1545e-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="1545e-109">Attributes</span></span>

<span data-ttu-id="1545e-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="1545e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1545e-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1545e-111">Child Elements</span></span>

|<span data-ttu-id="1545e-112">Element</span><span class="sxs-lookup"><span data-stu-id="1545e-112">Element</span></span>|<span data-ttu-id="1545e-113">Description</span><span class="sxs-lookup"><span data-stu-id="1545e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1545e-114">Entryselectedby-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="1545e-115">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="1545e-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1545e-116">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="1545e-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="1545e-117">CustomItem-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="1545e-118">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="1545e-118">Required element.</span></span><br /><br /> <span data-ttu-id="1545e-119">Definiert, wie das-Steuerelement die Daten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="1545e-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1545e-120">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="1545e-120">Parent Elements</span></span>

|<span data-ttu-id="1545e-121">Element</span><span class="sxs-lookup"><span data-stu-id="1545e-121">Element</span></span>|<span data-ttu-id="1545e-122">Description</span><span class="sxs-lookup"><span data-stu-id="1545e-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1545e-123">Customentries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="1545e-124">Stellt die Definitionen für das-Steuerelement bereit.</span><span class="sxs-lookup"><span data-stu-id="1545e-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1545e-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1545e-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="1545e-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1545e-126">See Also</span></span>

[<span data-ttu-id="1545e-127">Entryselectedby-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="1545e-128">CustomItem-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="1545e-129">Customentries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1545e-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="1545e-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="1545e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
