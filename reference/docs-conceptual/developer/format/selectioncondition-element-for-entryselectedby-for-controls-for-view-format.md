---
title: Selectioncondition-Element für entryselectedby für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362049"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Element „SelectionCondition“ für EntrySelectedBy für Controls für View (Format)

Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für das View (Format) customentry-Element für customentries für Steuerelemente für das View (Format) entryselectedby-Element für customentry für Steuerelemente für das View (Format) selectioncondition-Element für entryselectedby für Steuerelemente für View ( Ges

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[PropertyName-Element für selectioncondition für Steuerelemente für View (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt eine .net-Eigenschaft an, die die Bedingung auslöst.|
|[ScriptBlock-Element für selectioncondition für Steuerelemente für View (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.|
|[Typname-Element für selectioncondition für Steuerelemente für View (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.|

## <a name="remarks"></a>Hinweise

Wenn Sie eine Auswahlbedingung definieren, gelten die folgenden Anforderungen:

- Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.

- Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.

Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für selectioncondition für Steuerelemente für View (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[ScriptBlock-Element für selectioncondition für Steuerelemente für View (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[Typname-Element für selectioncondition für Steuerelemente für View (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[Entryselectedby-Element für customentry für Steuerelemente für Ansicht (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
