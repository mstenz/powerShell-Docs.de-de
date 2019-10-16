---
title: Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363889"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Element „EntrySelectedBy“ für CustomEntry für Controls für View (Format)

Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine Definition angeben. Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.|
|[Selectionsetname-Element für entryselectedby für Steuerelemente für View (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen an, die diese Definition des-Steuer Elements verwenden.|
|[Typname-Element für entryselectedby für Steuerelemente für View (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der diese Definition des-Steuer Elements verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für customentries für Steuerelemente für Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Stellt eine Definition des-Steuer Elements bereit.|

## <a name="remarks"></a>Hinweise

Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt eine bestimmte Eigenschaft hat oder wenn ein bestimmter Eigenschafts Wert oder ein Skript zu `true` ausgewertet wird. Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[Customentry-Element für customentries für Steuerelemente für Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
