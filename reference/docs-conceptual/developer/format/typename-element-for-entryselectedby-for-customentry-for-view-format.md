---
title: Typname-Element für entryselectedby für customentry für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368069"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="0e827-102">Element „TypeName“ für EntrySelectedBy für CustomEntry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e827-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="0e827-103">Gibt einen .NET-Typ an, der diese Definition der benutzerdefinierten Steuerelement Ansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="0e827-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="0e827-104">Es gibt keine Beschränkung für die Anzahl von Typen, die für eine Definition angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="0e827-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="0e827-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries for View (Format) entryselectedby Element für customentry für View (Format) tykename-Element für entryselectedby für customentry for View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e827-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e827-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e827-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e827-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0e827-107">Attributes and Elements</span></span>

<span data-ttu-id="0e827-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0e827-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e827-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="0e827-109">Attributes</span></span>

<span data-ttu-id="0e827-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="0e827-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e827-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0e827-111">Child Elements</span></span>

<span data-ttu-id="0e827-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="0e827-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0e827-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0e827-113">Parent Elements</span></span>

|<span data-ttu-id="0e827-114">Element</span><span class="sxs-lookup"><span data-stu-id="0e827-114">Element</span></span>|<span data-ttu-id="0e827-115">Description</span><span class="sxs-lookup"><span data-stu-id="0e827-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e827-116">Entryselectedby-Element für customentry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e827-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="0e827-117">Definiert die .NET-Typen, die diese Definition für die benutzerdefinierte Steuerelement Ansicht oder die Bedingung verwenden, die für die Verwendung dieser Definition vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="0e827-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0e827-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="0e827-118">Text Value</span></span>

<span data-ttu-id="0e827-119">Geben Sie den voll qualifizierten Namen des .net-Typs an, z. b. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="0e827-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e827-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0e827-120">Remarks</span></span>

<span data-ttu-id="0e827-121">Für jede Definition einer benutzerdefinierten Steuerelement Ansicht muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="0e827-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0e827-122">Weitere Informationen zu den Komponenten einer benutzerdefinierten Steuerelement Ansicht finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="0e827-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0e827-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0e827-123">See Also</span></span>

[<span data-ttu-id="0e827-124">Erstellen benutzerdefinierter Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="0e827-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="0e827-125">Entryselectedby-Element für customentry für View (Format)</span><span class="sxs-lookup"><span data-stu-id="0e827-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="0e827-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="0e827-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
