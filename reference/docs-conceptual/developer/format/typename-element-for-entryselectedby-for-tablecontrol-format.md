---
title: Tyname-Element für entryselectedby für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361629"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="54741-102">Element „TypeName“ für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="54741-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="54741-103">Gibt einen .NET-Typ an, der diesen Eintrag der Tabellenansicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="54741-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="54741-104">Es gibt keine Beschränkung für die Anzahl von Typen, die für einen Tabelleneintrag angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="54741-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="54741-105">Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element (Format) Typname-Element für entryselectedby für tablerowentry (Format)</span><span class="sxs-lookup"><span data-stu-id="54741-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54741-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="54741-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54741-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="54741-107">Attributes and Elements</span></span>

<span data-ttu-id="54741-108">In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="54741-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="54741-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="54741-109">Attributes</span></span>

<span data-ttu-id="54741-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="54741-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54741-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="54741-111">Child Elements</span></span>

<span data-ttu-id="54741-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="54741-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54741-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="54741-113">Parent Elements</span></span>

|<span data-ttu-id="54741-114">Element</span><span class="sxs-lookup"><span data-stu-id="54741-114">Element</span></span>|<span data-ttu-id="54741-115">Description</span><span class="sxs-lookup"><span data-stu-id="54741-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54741-116">Entryselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="54741-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="54741-117">Definiert die .NET-Typen, die diesen Eintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="54741-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="54741-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="54741-118">Text Value</span></span>

<span data-ttu-id="54741-119">Geben Sie den Namen des .net-Typs an.</span><span class="sxs-lookup"><span data-stu-id="54741-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="54741-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="54741-120">Remarks</span></span>

<span data-ttu-id="54741-121">Für jeden Listeneintrag muss mindestens ein Typname, ein Auswahl Satz oder eine Auswahlbedingung definiert sein.</span><span class="sxs-lookup"><span data-stu-id="54741-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="54741-122">Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="54741-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="54741-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="54741-123">See Also</span></span>

[<span data-ttu-id="54741-124">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="54741-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="54741-125">Entryselectedby-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="54741-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="54741-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="54741-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
