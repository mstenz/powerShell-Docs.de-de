---
title: Selectionsetname-Element für selectioncondition für entryselectedby für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361919"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a>Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für TableControl (Format)

Gibt den Satz von .NET-Typen an, die die Bedingung auslöst. Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt, und das Objekt wird mit dieser Definition der Tabellenansicht angezeigt.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element (Format) tablerowentry-Element (Format) entryselectedby-Element für tablerowentry (Format) Selectioncondition-Element für entryselectedby für tablerowentry (Format) selectionsetname-Element für selectioncondition für entryselectedby für tablerowentry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectioncondition-Element für entryselectedby für tablerowentry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Definiert die Bedingung, die für die Verwendung in dieser Definition der Tabellenansicht vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Auswahl Satzes an.

## <a name="remarks"></a>Hinweise

Die Auswahlbedingung kann einen Auswahl Satz oder einen .NET-Typ angeben, kann jedoch nicht beides angeben. Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird. Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).

Weitere Informationen zu anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md)

[Typname-Element für selectioncondition für entryselectedby für tablerowentry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[Selectioncondition-Element für entryselectedby für tablerowentry (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
