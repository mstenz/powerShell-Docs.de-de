---
title: TypeName-Element für EntrySelectedBy für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861666"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="9988b-102">Element „TypeName“ für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9988b-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="9988b-103">Gibt einen .NET-Typ, ein, der dieser Definition des benutzerdefinierten Steuerelements verwendet.</span><span class="sxs-lookup"><span data-stu-id="9988b-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="9988b-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9988b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9988b-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) TypeName-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9988b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9988b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9988b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9988b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="9988b-107">Attributes and Elements</span></span>

<span data-ttu-id="9988b-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="9988b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9988b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="9988b-109">Attributes</span></span>

<span data-ttu-id="9988b-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="9988b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9988b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9988b-111">Child Elements</span></span>

<span data-ttu-id="9988b-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="9988b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9988b-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="9988b-113">Parent Elements</span></span>

|<span data-ttu-id="9988b-114">Element</span><span class="sxs-lookup"><span data-stu-id="9988b-114">Element</span></span>|<span data-ttu-id="9988b-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9988b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9988b-116">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9988b-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="9988b-117">Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9988b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9988b-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="9988b-118">Text Value</span></span>

<span data-ttu-id="9988b-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="9988b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9988b-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9988b-120">Remarks</span></span>

<span data-ttu-id="9988b-121">Jedes Steuerelement muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert aufweisen.</span><span class="sxs-lookup"><span data-stu-id="9988b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="9988b-122">Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9988b-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9988b-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9988b-123">See Also</span></span>

[<span data-ttu-id="9988b-124">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="9988b-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="9988b-125">EntrySelectedBy-Element für CustomEntry für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9988b-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="9988b-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="9988b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
