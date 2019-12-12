---
title: PropertyName-Element für wideitem für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364939"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="a84d9-102">Element „PropertyName“ für WideItem für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a84d9-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="a84d9-103">Gibt die-Eigenschaft des-Objekts an, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a84d9-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="a84d9-104">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) wideitem-Element (Format) propertyName-Element für wideitem (Format)</span><span class="sxs-lookup"><span data-stu-id="a84d9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a84d9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a84d9-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a84d9-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="a84d9-106">Attributes and Elements</span></span>

<span data-ttu-id="a84d9-107">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a84d9-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a84d9-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="a84d9-108">Attributes</span></span>

<span data-ttu-id="a84d9-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="a84d9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a84d9-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a84d9-110">Child Elements</span></span>

<span data-ttu-id="a84d9-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="a84d9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a84d9-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="a84d9-112">Parent Elements</span></span>

|<span data-ttu-id="a84d9-113">Element</span><span class="sxs-lookup"><span data-stu-id="a84d9-113">Element</span></span>|<span data-ttu-id="a84d9-114">Description</span><span class="sxs-lookup"><span data-stu-id="a84d9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a84d9-115">Wideitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a84d9-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="a84d9-116">Definiert die Eigenschaft oder das Skript, dessen Wert in der breiten Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a84d9-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a84d9-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="a84d9-117">Text Value</span></span>

<span data-ttu-id="a84d9-118">Geben Sie den Namen der Eigenschaft an, deren Wert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a84d9-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a84d9-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="a84d9-119">Remarks</span></span>

<span data-ttu-id="a84d9-120">Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="a84d9-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a84d9-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a84d9-121">Example</span></span>

<span data-ttu-id="a84d9-122">Dieses Beispiel zeigt eine breite Ansicht, in der der Wert der ProcessName-Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a84d9-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a84d9-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a84d9-123">See Also</span></span>

[<span data-ttu-id="a84d9-124">Wideitem-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="a84d9-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="a84d9-125">Erstellen einer breiten Ansicht</span><span class="sxs-lookup"><span data-stu-id="a84d9-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="a84d9-126">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="a84d9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
