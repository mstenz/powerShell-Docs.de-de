---
title: Selectionsetname-Element für viewselectedby (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368259"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="15c6f-102">Element „SelectionSetName“ für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="15c6f-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="15c6f-103">Gibt einen Satz von .NET-Objekten an, die von der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="15c6f-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="15c6f-104">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) viewselectedby-Element (Format) selectionsetname-Element für viewselectedby (Format)</span><span class="sxs-lookup"><span data-stu-id="15c6f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15c6f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="15c6f-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15c6f-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="15c6f-106">Attributes and Elements</span></span>

<span data-ttu-id="15c6f-107">In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="15c6f-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15c6f-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="15c6f-108">Attributes</span></span>

<span data-ttu-id="15c6f-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="15c6f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15c6f-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="15c6f-110">Child Elements</span></span>

<span data-ttu-id="15c6f-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="15c6f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15c6f-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="15c6f-112">Parent Elements</span></span>

|<span data-ttu-id="15c6f-113">Element</span><span class="sxs-lookup"><span data-stu-id="15c6f-113">Element</span></span>|<span data-ttu-id="15c6f-114">Description</span><span class="sxs-lookup"><span data-stu-id="15c6f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15c6f-115">Viewselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="15c6f-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="15c6f-116">Definiert die .NET-Objekte, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="15c6f-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="15c6f-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="15c6f-117">Text Value</span></span>

<span data-ttu-id="15c6f-118">Geben Sie den Namen des Auswahl Satzes an, der vom `Name`-Element für den Auswahl Satz definiert wird.</span><span class="sxs-lookup"><span data-stu-id="15c6f-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="15c6f-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="15c6f-119">Remarks</span></span>

<span data-ttu-id="15c6f-120">Sie können Auswahl Sätze verwenden, wenn Sie über einen Satz verwandter Objekte verfügen, auf die Sie verweisen möchten, indem Sie einen einzelnen Namen verwenden, z. b. eine Gruppe von Objekten, die durch Vererbung verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="15c6f-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="15c6f-121">Weitere Informationen zum Definieren und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="15c6f-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="15c6f-122">Beispiel</span><span class="sxs-lookup"><span data-stu-id="15c6f-122">Example</span></span>

<span data-ttu-id="15c6f-123">Im folgenden Beispiel wird gezeigt, wie Sie einen Auswahl Satz für eine Listenansicht angeben.</span><span class="sxs-lookup"><span data-stu-id="15c6f-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="15c6f-124">Das gleiche Schema wird für Tabellen-, breiten-und benutzerdefinierte Sichten verwendet.</span><span class="sxs-lookup"><span data-stu-id="15c6f-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="15c6f-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="15c6f-125">See Also</span></span>

[<span data-ttu-id="15c6f-126">Definieren von Auswahl Sätzen</span><span class="sxs-lookup"><span data-stu-id="15c6f-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="15c6f-127">Viewselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="15c6f-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="15c6f-128">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="15c6f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
