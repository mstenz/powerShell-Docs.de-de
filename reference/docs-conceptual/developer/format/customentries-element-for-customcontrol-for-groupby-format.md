---
title: Customentries-Element für CustomControl für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af83c0f6-7fdd-4aa0-af12-efc62f632974
caps.latest.revision: 7
ms.openlocfilehash: f073142bf836ae892f161cf8c36ed16c35e311f5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364089"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="3c8d6-102">Element „CustomEntries“ für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3c8d6-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="3c8d6-103">Stellt die Definitionen für das-Steuerelement bereit.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-103">Provides the definitions for the control.</span></span> <span data-ttu-id="3c8d6-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3c8d6-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3c8d6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c8d6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c8d6-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c8d6-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="3c8d6-107">Attributes and Elements</span></span>

<span data-ttu-id="3c8d6-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente des `CustomEntries`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="3c8d6-109">Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c8d6-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="3c8d6-110">Attributes</span></span>

<span data-ttu-id="3c8d6-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c8d6-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3c8d6-112">Child Elements</span></span>

|<span data-ttu-id="3c8d6-113">Element</span><span class="sxs-lookup"><span data-stu-id="3c8d6-113">Element</span></span>|<span data-ttu-id="3c8d6-114">Description</span><span class="sxs-lookup"><span data-stu-id="3c8d6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c8d6-115">Customentry-Element für CustomControl für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3c8d6-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="3c8d6-116">Erforderliches Element.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-116">Required element.</span></span><br /><br /> <span data-ttu-id="3c8d6-117">Stellt eine Definition des-Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c8d6-118">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="3c8d6-118">Parent Elements</span></span>

|<span data-ttu-id="3c8d6-119">Element</span><span class="sxs-lookup"><span data-stu-id="3c8d6-119">Element</span></span>|<span data-ttu-id="3c8d6-120">Description</span><span class="sxs-lookup"><span data-stu-id="3c8d6-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c8d6-121">CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3c8d6-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="3c8d6-122">Definiert das benutzerdefinierte Steuerelement, das die neue Gruppe anzeigt.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c8d6-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3c8d6-123">Remarks</span></span>

<span data-ttu-id="3c8d6-124">In den meisten Fällen verfügt ein Steuerelement nur über eine Definition, die in einem einzelnen `CustomEntry` Element angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="3c8d6-125">Es ist jedoch möglich, mehrere Definitionen bereitzustellen, wenn Sie das gleiche Steuerelement verwenden möchten, um unterschiedliche Gruppen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="3c8d6-126">In diesen Fällen können Sie ein `CustomEntry`-Element für eine Gruppe definieren.</span><span class="sxs-lookup"><span data-stu-id="3c8d6-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c8d6-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3c8d6-127">See Also</span></span>

[<span data-ttu-id="3c8d6-128">Customentry-Element für customentries für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="3c8d6-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="3c8d6-129">CustomControl-Element für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="3c8d6-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="3c8d6-130">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="3c8d6-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
