---
title: Tyname-Element für entryselectedby für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361669"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="00c88-102">Element „TypeName“ für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="00c88-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="00c88-103">Gibt einen .NET-Typ an, der diese Definition des benutzerdefinierten Steuer Elements verwendet.</span><span class="sxs-lookup"><span data-stu-id="00c88-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="00c88-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="00c88-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="00c88-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format) tykename-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="00c88-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00c88-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="00c88-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="00c88-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="00c88-107">Attributes and Elements</span></span>

<span data-ttu-id="00c88-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="00c88-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00c88-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="00c88-109">Attributes</span></span>

<span data-ttu-id="00c88-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="00c88-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00c88-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="00c88-111">Child Elements</span></span>

<span data-ttu-id="00c88-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="00c88-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="00c88-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="00c88-113">Parent Elements</span></span>

|<span data-ttu-id="00c88-114">Element</span><span class="sxs-lookup"><span data-stu-id="00c88-114">Element</span></span>|<span data-ttu-id="00c88-115">Description</span><span class="sxs-lookup"><span data-stu-id="00c88-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00c88-116">Entryselectedby-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="00c88-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="00c88-117">Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="00c88-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="00c88-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="00c88-118">Text Value</span></span>

<span data-ttu-id="00c88-119">Geben Sie den voll qualifizierten Namen des .net-Typs an, z. b. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="00c88-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="00c88-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="00c88-120">Remarks</span></span>

<span data-ttu-id="00c88-121">Für jede Steuerelement Definition muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="00c88-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="00c88-122">Weitere Informationen zu den Komponenten einer benutzerdefinierten Steuerelement Ansicht finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="00c88-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00c88-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="00c88-123">See Also</span></span>

[<span data-ttu-id="00c88-124">Erstellen benutzerdefinierter Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="00c88-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="00c88-125">Entryselectedby-Element für customentry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="00c88-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="00c88-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="00c88-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
