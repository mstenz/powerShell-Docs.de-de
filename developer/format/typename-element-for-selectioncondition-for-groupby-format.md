---
title: TypeName-Element für SelectionCondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083772"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="2b0da-102">Element „TypeName“ für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2b0da-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="2b0da-103">Gibt einen .NET-Typ, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="2b0da-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="2b0da-104">Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2b0da-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2b0da-105">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionCondition-Element für EntrySelectedBy für GroupBy (Format) TypeName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2b0da-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b0da-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b0da-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b0da-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2b0da-107">Attributes and Elements</span></span>

<span data-ttu-id="2b0da-108">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="2b0da-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b0da-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2b0da-109">Attributes</span></span>

<span data-ttu-id="2b0da-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="2b0da-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2b0da-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b0da-111">Child Elements</span></span>

<span data-ttu-id="2b0da-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="2b0da-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b0da-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2b0da-113">Parent Elements</span></span>

|<span data-ttu-id="2b0da-114">Element</span><span class="sxs-lookup"><span data-stu-id="2b0da-114">Element</span></span>|<span data-ttu-id="2b0da-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2b0da-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2b0da-116">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2b0da-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="2b0da-117">Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2b0da-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2b0da-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="2b0da-118">Text Value</span></span>

<span data-ttu-id="2b0da-119">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="2b0da-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b0da-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2b0da-120">Remarks</span></span>

<span data-ttu-id="2b0da-121">Wenn dieses Element angegeben ist, können Sie nicht angeben der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="2b0da-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="2b0da-122">Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2b0da-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b0da-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2b0da-123">See Also</span></span>

[<span data-ttu-id="2b0da-124">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2b0da-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="2b0da-125">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b0da-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
