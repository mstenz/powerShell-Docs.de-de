---
title: ScriptBlock-Element für wideitem für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362029"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="6e7b0-102">Element „ScriptBlock“ für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6e7b0-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="6e7b0-103">Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e7b0-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="6e7b0-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) wideitem-Element (Format) ScriptBlock-Element für wideitem (Format)</span><span class="sxs-lookup"><span data-stu-id="6e7b0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e7b0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e7b0-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e7b0-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="6e7b0-106">Attributes and Elements</span></span>

<span data-ttu-id="6e7b0-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6e7b0-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e7b0-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="6e7b0-108">Attributes</span></span>

<span data-ttu-id="6e7b0-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="6e7b0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e7b0-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6e7b0-110">Child Elements</span></span>

<span data-ttu-id="6e7b0-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="6e7b0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6e7b0-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="6e7b0-112">Parent Elements</span></span>

|<span data-ttu-id="6e7b0-113">Element</span><span class="sxs-lookup"><span data-stu-id="6e7b0-113">Element</span></span>|<span data-ttu-id="6e7b0-114">Description</span><span class="sxs-lookup"><span data-stu-id="6e7b0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6e7b0-115">Wideitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6e7b0-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="6e7b0-116">Definiert den Eigenschafts-oder Skriptblock, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e7b0-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6e7b0-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="6e7b0-117">Text Value</span></span>

<span data-ttu-id="6e7b0-118">Geben Sie das Skript an, dessen Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e7b0-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e7b0-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6e7b0-119">Remarks</span></span>

<span data-ttu-id="6e7b0-120">Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="6e7b0-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6e7b0-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6e7b0-121">Example</span></span>

<span data-ttu-id="6e7b0-122">Dieses Beispiel zeigt ein `WideItem`-Element, das ein Skript definiert, dessen Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6e7b0-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="6e7b0-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6e7b0-123">See Also</span></span>

[<span data-ttu-id="6e7b0-124">Wideitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="6e7b0-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="6e7b0-125">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="6e7b0-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6e7b0-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="6e7b0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
