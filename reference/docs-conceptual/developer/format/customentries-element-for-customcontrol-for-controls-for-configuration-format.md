---
title: Customentries-Element für CustomControl für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368819"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="4f3b0-102">Element „CustomEntries“ für CustomControl für Controls für Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="4f3b0-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4f3b0-103">Stellt die Definitionen eines allgemeinen Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="4f3b0-104">Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4f3b0-105">Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Ges</span><span class="sxs-lookup"><span data-stu-id="4f3b0-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4f3b0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4f3b0-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4f3b0-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="4f3b0-107">Attributes and Elements</span></span>

<span data-ttu-id="4f3b0-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomEntries`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="4f3b0-109">Sie müssen mindestens ein untergeordnetes Element angeben.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4f3b0-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="4f3b0-110">Attributes</span></span>

<span data-ttu-id="4f3b0-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4f3b0-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4f3b0-112">Child Elements</span></span>

|<span data-ttu-id="4f3b0-113">Element</span><span class="sxs-lookup"><span data-stu-id="4f3b0-113">Element</span></span>|<span data-ttu-id="4f3b0-114">Description</span><span class="sxs-lookup"><span data-stu-id="4f3b0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f3b0-115">Customentry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="4f3b0-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="4f3b0-116">Stellt eine Definition des allgemeinen Steuer Elements bereit.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4f3b0-117">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4f3b0-117">Parent Elements</span></span>

|<span data-ttu-id="4f3b0-118">Element</span><span class="sxs-lookup"><span data-stu-id="4f3b0-118">Element</span></span>|<span data-ttu-id="4f3b0-119">Description</span><span class="sxs-lookup"><span data-stu-id="4f3b0-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4f3b0-120">CustomControl-Element für das Steuer Element für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="4f3b0-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="4f3b0-121">Definiert ein gängiges Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4f3b0-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4f3b0-122">Remarks</span></span>

<span data-ttu-id="4f3b0-123">In den meisten Fällen verfügt ein Steuerelement nur über eine Definition, die in einem einzelnen `CustomEntry` Element definiert ist.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="4f3b0-124">Es ist jedoch möglich, mehrere Definitionen zu verwenden, wenn Sie das gleiche Steuerelement verwenden möchten, um unterschiedliche .NET-Objekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="4f3b0-125">In diesen Fällen können Sie ein `CustomEntry`-Element für jedes Objekt oder jede Gruppe von Objekten definieren.</span><span class="sxs-lookup"><span data-stu-id="4f3b0-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f3b0-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4f3b0-126">See Also</span></span>

[<span data-ttu-id="4f3b0-127">CustomControl-Element für das Steuer Element für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="4f3b0-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f3b0-128">Customentry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="4f3b0-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="4f3b0-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="4f3b0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
