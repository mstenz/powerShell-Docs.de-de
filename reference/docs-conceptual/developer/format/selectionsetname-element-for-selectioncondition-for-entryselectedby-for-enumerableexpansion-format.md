---
title: Selectionsetname-Element für selectioncondition für entryselectedby für enumerableweiterung (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361989"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)

Gibt den Satz von .NET-Typen an, die die Bedingung auslöst. Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt.

Configuration-Element DefaultSettings-Element (Format) enumerableerweiterungs-Element (Format) enumerableerweiterungs-Element (Format) entryselectedby-Element für enumerableexpansion (Format) selectioncondition-Element für entryselectedby Enumerableexpansion (Format) selectionsetname-Element für selectioncondition für entryselectedby für enumerableexpansion (Format)

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
|[Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definiert die Bedingung, die vorhanden sein muss, um die Auflistungs Objekte dieser Definition zu erweitern.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Auswahl Satzes an.

## <a name="remarks"></a>Hinweise

Die Auswahlbedingung kann einen Auswahl Satz oder einen .NET-Typ angeben, kann jedoch nicht beides angeben. Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird. Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).

## <a name="see-also"></a>Weitere Informationen

[Definieren von Auswahl Sätzen](./defining-selection-sets.md)

[Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
