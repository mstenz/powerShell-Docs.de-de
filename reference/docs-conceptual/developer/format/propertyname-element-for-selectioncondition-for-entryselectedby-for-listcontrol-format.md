---
title: PropertyName-Element für selectioncondition für entryselectedby für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71c3f1f6-6fe2-42f1-8260-6974d3871748
caps.latest.revision: 11
ms.openlocfilehash: 7d526372cf80327b3fb9b79b6e83429c57780183
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362289"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Element „PropertyName“ für SelectionCondition für EntrySelectedBy für ListControl (Format)

Gibt die .net-Eigenschaft an, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder als `true` ausgewertet wird, wird die Bedingung erfüllt, und der Listeneintrag wird verwendet.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) entryselectedby-Element für ListEntry (Format) selectioncondition-Element für Entryselectedby für ListEntry (Format) propertyName-Element für selectioncondition für entryselectedby für ListEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectioncondition-Element für entryselectedby für ListEntry (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definiert die Bedingung, die für die Verwendung dieses Listen Eintrags vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .net-Eigenschaft an.

## <a name="remarks"></a>Hinweise

Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben. Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter Definieren von Bedingungen für den Fall, [dass ein Ansichts Eintrag oder Element verwendet wird](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu anderen Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md)

[ListEntry-Element (Format)](./listentry-element-for-listcontrol-format.md)

[ScriptBlock-Element für selectioncondition für entryselectedby für ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
