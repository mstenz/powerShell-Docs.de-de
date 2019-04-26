---
title: TypeName-Element für ViewSelectedBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083755"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="4b830-102">Element „TypeName“ für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4b830-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="4b830-103">Gibt ein .NET-Objekt, das von der Ansicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4b830-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="4b830-104">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ViewSelectedBy-Element (Format) TypeName Konfigurationselement für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4b830-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b830-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b830-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b830-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="4b830-106">Attributes and Elements</span></span>

<span data-ttu-id="4b830-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `TypeName` Element.</span><span class="sxs-lookup"><span data-stu-id="4b830-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b830-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="4b830-108">Attributes</span></span>

<span data-ttu-id="4b830-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="4b830-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b830-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4b830-110">Child Elements</span></span>

<span data-ttu-id="4b830-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="4b830-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4b830-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="4b830-112">Parent Elements</span></span>

|<span data-ttu-id="4b830-113">Element</span><span class="sxs-lookup"><span data-stu-id="4b830-113">Element</span></span>|<span data-ttu-id="4b830-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4b830-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b830-115">ViewSelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4b830-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="4b830-116">Definiert die .NET Objekte, die von der Ansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="4b830-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4b830-117">Textwert</span><span class="sxs-lookup"><span data-stu-id="4b830-117">Text Value</span></span>

<span data-ttu-id="4b830-118">Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="4b830-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b830-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4b830-119">Remarks</span></span>

<span data-ttu-id="4b830-120">Weitere Informationen zur Verwendung dieses Elements in verschiedenen Ansichten finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md), [Erstellen einer Listenansicht](./creating-a-list-view.md), [erstellen eine Breite Ansicht](./creating-a-wide-view.md), und [ Benutzerdefinierte Ansichtskomponenten](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4b830-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="4b830-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4b830-121">Example</span></span>

<span data-ttu-id="4b830-122">Das folgende Beispiel zeigt, wie die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt für eine Listenansicht.</span><span class="sxs-lookup"><span data-stu-id="4b830-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="4b830-123">Das gleiche Schema wird für die Tabelle, Breite und benutzerdefinierte Ansichten verwendet.</span><span class="sxs-lookup"><span data-stu-id="4b830-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="4b830-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4b830-124">See Also</span></span>

[<span data-ttu-id="4b830-125">Erstellen einer Listenansicht</span><span class="sxs-lookup"><span data-stu-id="4b830-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4b830-126">Erstellen einer Tabellenansicht</span><span class="sxs-lookup"><span data-stu-id="4b830-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4b830-127">Erstellen eine Breite Ansicht</span><span class="sxs-lookup"><span data-stu-id="4b830-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4b830-128">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="4b830-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4b830-129">ViewSelectedBy-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4b830-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="4b830-130">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="4b830-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
