---
title: ScriptBlock-Element für WideItem für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858026"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="8a946-102">Element „ScriptBlock“ für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8a946-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="8a946-103">Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a946-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="8a946-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) WideItem-Element (Format) "scriptblock" Konfigurationselement für WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="8a946-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8a946-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8a946-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8a946-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8a946-106">Attributes and Elements</span></span>

<span data-ttu-id="8a946-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ScriptBlock` Element.</span><span class="sxs-lookup"><span data-stu-id="8a946-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8a946-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="8a946-108">Attributes</span></span>

<span data-ttu-id="8a946-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="8a946-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8a946-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8a946-110">Child Elements</span></span>

<span data-ttu-id="8a946-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="8a946-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8a946-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8a946-112">Parent Elements</span></span>

|<span data-ttu-id="8a946-113">Element</span><span class="sxs-lookup"><span data-stu-id="8a946-113">Element</span></span>|<span data-ttu-id="8a946-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a946-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8a946-115">WideItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8a946-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="8a946-116">Definiert die Eigenschaft oder ein Skript-Block, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a946-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8a946-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="8a946-117">Text Value</span></span>

<span data-ttu-id="8a946-118">Geben Sie das Skript, dessen Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a946-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a946-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8a946-119">Remarks</span></span>

<span data-ttu-id="8a946-120">Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8a946-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8a946-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8a946-121">Example</span></span>

<span data-ttu-id="8a946-122">Dieses Beispiel zeigt eine `WideItem` Element, das ein Skript definiert, deren Wert in der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a946-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="8a946-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8a946-123">See Also</span></span>

[<span data-ttu-id="8a946-124">WideItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8a946-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="8a946-125">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="8a946-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8a946-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a946-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
