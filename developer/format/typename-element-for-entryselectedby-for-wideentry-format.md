---
title: TypeName-Element für EntrySelectedBy für WideEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862646"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="4956b-102">Element „TypeName“ für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4956b-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="4956b-103">Gibt einen Typ .NET für die Definition.</span><span class="sxs-lookup"><span data-stu-id="4956b-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="4956b-104">Die Definition wird verwendet, wenn dieses Objekt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4956b-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="4956b-105">Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für TypeName-Element für WideEntry (WideEntry (Format) -Format)</span><span class="sxs-lookup"><span data-stu-id="4956b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4956b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4956b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4956b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="4956b-107">Attributes and Elements</span></span>

<span data-ttu-id="4956b-108">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="4956b-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4956b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="4956b-109">Attributes</span></span>

<span data-ttu-id="4956b-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="4956b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4956b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4956b-111">Child Elements</span></span>

<span data-ttu-id="4956b-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="4956b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4956b-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4956b-113">Parent Elements</span></span>

|<span data-ttu-id="4956b-114">Element</span><span class="sxs-lookup"><span data-stu-id="4956b-114">Element</span></span>|<span data-ttu-id="4956b-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4956b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4956b-116">EntrySelectedBy-Element für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4956b-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="4956b-117">Definiert die .NET-Typen, die dieser breiten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="4956b-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4956b-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="4956b-118">Text Value</span></span>

<span data-ttu-id="4956b-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="4956b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4956b-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4956b-120">Remarks</span></span>

<span data-ttu-id="4956b-121">Jeder Eintrag Breite muss angeben, einen oder mehrere Typen von .NET, einen Auswahlsatz oder die auswahlbedingung, die die Definition der zu verwendenden vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="4956b-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="4956b-122">Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4956b-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4956b-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4956b-123">See Also</span></span>

[<span data-ttu-id="4956b-124">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="4956b-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4956b-125">EntrySelectedBy-Element für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="4956b-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="4956b-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="4956b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
