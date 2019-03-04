---
title: SelectionSetName-Element für ViewSelectedBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858336"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="0fffd-102">Element „SelectionSetName“ für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0fffd-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="0fffd-103">Gibt einen Satz von .NET-Objekten, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0fffd-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="0fffd-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ViewSelectedBy-Element (Format) SelectionSetName Konfigurationselement für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="0fffd-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0fffd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0fffd-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0fffd-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="0fffd-106">Attributes and Elements</span></span>

<span data-ttu-id="0fffd-107">Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.</span><span class="sxs-lookup"><span data-stu-id="0fffd-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0fffd-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="0fffd-108">Attributes</span></span>

<span data-ttu-id="0fffd-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="0fffd-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0fffd-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0fffd-110">Child Elements</span></span>

<span data-ttu-id="0fffd-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="0fffd-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0fffd-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="0fffd-112">Parent Elements</span></span>

|<span data-ttu-id="0fffd-113">Element</span><span class="sxs-lookup"><span data-stu-id="0fffd-113">Element</span></span>|<span data-ttu-id="0fffd-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0fffd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fffd-115">ViewSelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0fffd-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="0fffd-116">Definiert die .NET Objekte, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0fffd-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0fffd-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="0fffd-117">Text Value</span></span>

<span data-ttu-id="0fffd-118">Geben Sie den Namen des Satzes Auswahl, die von definiert ist die `Name` -Element für den Auswahlsatz.</span><span class="sxs-lookup"><span data-stu-id="0fffd-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fffd-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0fffd-119">Remarks</span></span>

<span data-ttu-id="0fffd-120">Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten.</span><span class="sxs-lookup"><span data-stu-id="0fffd-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="0fffd-121">Weitere Informationen zum Definieren und verweisen auf die von Auswahlgruppen finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="0fffd-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="0fffd-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0fffd-122">Example</span></span>

<span data-ttu-id="0fffd-123">Das folgende Beispiel zeigt, wie Sie eine Auswahl, legen Sie für eine Listenansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="0fffd-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="0fffd-124">Das gleiche Schema wird für die Tabelle, Breite und benutzerdefinierte Ansichten verwendet.</span><span class="sxs-lookup"><span data-stu-id="0fffd-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="0fffd-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0fffd-125">See Also</span></span>

[<span data-ttu-id="0fffd-126">Auswahl definieren</span><span class="sxs-lookup"><span data-stu-id="0fffd-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="0fffd-127">ViewSelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0fffd-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="0fffd-128">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="0fffd-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
