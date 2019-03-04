---
title: PropertyName-Element für WideItem für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860956"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="8be82-102">Element „PropertyName“ für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8be82-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="8be82-103">Gibt die Eigenschaft des Objekts, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8be82-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="8be82-104">Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) WideItem-Element (Format) PropertyName Konfigurationselement für WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="8be82-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8be82-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8be82-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8be82-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="8be82-106">Attributes and Elements</span></span>

<span data-ttu-id="8be82-107">Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `PropertyName` Element.</span><span class="sxs-lookup"><span data-stu-id="8be82-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8be82-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="8be82-108">Attributes</span></span>

<span data-ttu-id="8be82-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="8be82-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8be82-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8be82-110">Child Elements</span></span>

<span data-ttu-id="8be82-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="8be82-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8be82-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="8be82-112">Parent Elements</span></span>

|<span data-ttu-id="8be82-113">Element</span><span class="sxs-lookup"><span data-stu-id="8be82-113">Element</span></span>|<span data-ttu-id="8be82-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8be82-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8be82-115">WideItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8be82-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="8be82-116">Definiert die Eigenschaft oder ein Skript, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8be82-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8be82-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="8be82-117">Text Value</span></span>

<span data-ttu-id="8be82-118">Geben Sie den Namen der Eigenschaft, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8be82-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="8be82-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8be82-119">Remarks</span></span>

<span data-ttu-id="8be82-120">Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="8be82-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8be82-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8be82-121">Example</span></span>

<span data-ttu-id="8be82-122">Dieses Beispiel zeigt eine Breite Ansicht den Wert der ProcessName-Eigenschaft an die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.</span><span class="sxs-lookup"><span data-stu-id="8be82-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="8be82-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8be82-123">See Also</span></span>

[<span data-ttu-id="8be82-124">WideItem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8be82-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="8be82-125">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="8be82-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8be82-126">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="8be82-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
