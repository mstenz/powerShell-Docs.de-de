---
title: TypeName-Element für EntrySelectedBy für CustomEntry für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083976"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="f100f-102">Element „TypeName“ für EntrySelectedBy für CustomEntry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="f100f-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="f100f-103">Gibt einen .NET-Typ, ein, der dieser Definition der Sicht benutzerdefiniertes Steuerelement verwendet.</span><span class="sxs-lookup"><span data-stu-id="f100f-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="f100f-104">Es gibt keine Beschränkung der Anzahl von Typen, die für eine Definition angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="f100f-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="f100f-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) EntrySelectedBy -Element für CustomEntry für Ansicht (Format) TypeName-Element für EntrySelectedBy für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f100f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f100f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f100f-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f100f-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="f100f-107">Attributes and Elements</span></span>

<span data-ttu-id="f100f-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="f100f-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f100f-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="f100f-109">Attributes</span></span>

<span data-ttu-id="f100f-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="f100f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f100f-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f100f-111">Child Elements</span></span>

<span data-ttu-id="f100f-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="f100f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f100f-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="f100f-113">Parent Elements</span></span>

|<span data-ttu-id="f100f-114">Element</span><span class="sxs-lookup"><span data-stu-id="f100f-114">Element</span></span>|<span data-ttu-id="f100f-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f100f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f100f-116">EntrySelectedBy-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f100f-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="f100f-117">Definiert .NET Typen, die dieser Definition des benutzerdefinierten Steuerelements anzeigen oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f100f-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f100f-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="f100f-118">Text Value</span></span>

<span data-ttu-id="f100f-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="f100f-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f100f-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f100f-120">Remarks</span></span>

<span data-ttu-id="f100f-121">Jede Definition des benutzerdefinierten Steuerelements anzeigen muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.</span><span class="sxs-lookup"><span data-stu-id="f100f-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f100f-122">Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f100f-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f100f-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f100f-123">See Also</span></span>

[<span data-ttu-id="f100f-124">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="f100f-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="f100f-125">EntrySelectedBy-Element für CustomEntry für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="f100f-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="f100f-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="f100f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
