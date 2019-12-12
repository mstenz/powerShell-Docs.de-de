---
title: Customcontrolname-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368879"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="2679b-102">Element „CustomControlName“ für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="2679b-103">Gibt den Namen eines benutzerdefinierten Steuer Elements an, das zum Anzeigen der neuen Gruppe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2679b-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="2679b-104">Dieses Element wird verwendet, wenn eine Tabelle, eine Liste, eine Breite oder eine benutzerdefinierte Steuerelement Ansicht definiert wird.</span><span class="sxs-lookup"><span data-stu-id="2679b-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="2679b-105">Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) customcontrolname-Element von GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2679b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2679b-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2679b-107">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="2679b-107">Attributes and Elements</span></span>

<span data-ttu-id="2679b-108">In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und die übergeordneten Elemente des `CustomControlName`-Elements beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2679b-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2679b-109">Attributes</span><span class="sxs-lookup"><span data-stu-id="2679b-109">Attributes</span></span>

<span data-ttu-id="2679b-110">Keine.</span><span class="sxs-lookup"><span data-stu-id="2679b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2679b-111">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2679b-111">Child Elements</span></span>

<span data-ttu-id="2679b-112">Keine.</span><span class="sxs-lookup"><span data-stu-id="2679b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2679b-113">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="2679b-113">Parent Elements</span></span>

|<span data-ttu-id="2679b-114">Element</span><span class="sxs-lookup"><span data-stu-id="2679b-114">Element</span></span>|<span data-ttu-id="2679b-115">Description</span><span class="sxs-lookup"><span data-stu-id="2679b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2679b-116">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="2679b-117">Definiert, wie Windows PowerShell eine neue Gruppe von Objekten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="2679b-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2679b-118">Textwert</span><span class="sxs-lookup"><span data-stu-id="2679b-118">Text Value</span></span>

<span data-ttu-id="2679b-119">Geben Sie den Namen des benutzerdefinierten Steuer Elements an, das verwendet wird, um eine neue Gruppe anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2679b-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="2679b-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2679b-120">Remarks</span></span>

<span data-ttu-id="2679b-121">Sie können allgemeine Steuerelemente erstellen, die von allen Ansichten einer Formatierungs Datei verwendet werden können, und Sie können Ansichts Steuerelemente erstellen, die von einer bestimmten Ansicht verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="2679b-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="2679b-122">Die folgenden Elemente geben die Namen dieser benutzerdefinierten Steuerelemente an:</span><span class="sxs-lookup"><span data-stu-id="2679b-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="2679b-123">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="2679b-124">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="2679b-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2679b-125">See Also</span></span>

[<span data-ttu-id="2679b-126">GroupBy-Element für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="2679b-127">Name-Element für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="2679b-128">Name-Element für Steuerelemente für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="2679b-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="2679b-129">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="2679b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
