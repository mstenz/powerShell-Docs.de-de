---
title: Typname-Element für selectioncondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361479"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="6b702-102">Element „TypeName“ für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6b702-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="6b702-103">Gibt einen .NET-Typ an, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="6b702-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="6b702-104">Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6b702-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6b702-105">Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format) selectioncondition-Element für entryselectedby für GroupBy (Format) Typname-Element für selectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6b702-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b702-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b702-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b702-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6b702-107">Attributes and Elements</span></span>

<span data-ttu-id="6b702-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6b702-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b702-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="6b702-109">Attributes</span></span>

<span data-ttu-id="6b702-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="6b702-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b702-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6b702-111">Child Elements</span></span>

<span data-ttu-id="6b702-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="6b702-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6b702-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6b702-113">Parent Elements</span></span>

|<span data-ttu-id="6b702-114">Element</span><span class="sxs-lookup"><span data-stu-id="6b702-114">Element</span></span>|<span data-ttu-id="6b702-115">Description</span><span class="sxs-lookup"><span data-stu-id="6b702-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b702-116">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6b702-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="6b702-117">Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="6b702-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6b702-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="6b702-118">Text Value</span></span>

<span data-ttu-id="6b702-119">Geben Sie den voll qualifizierten Namen des .net-Typs an, z. b. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="6b702-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b702-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6b702-120">Remarks</span></span>

<span data-ttu-id="6b702-121">Wenn dieses Element angegeben ist, können Sie das `SelectionSetName`-Element nicht angeben.</span><span class="sxs-lookup"><span data-stu-id="6b702-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="6b702-122">Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6b702-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b702-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6b702-123">See Also</span></span>

[<span data-ttu-id="6b702-124">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6b702-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="6b702-125">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="6b702-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
