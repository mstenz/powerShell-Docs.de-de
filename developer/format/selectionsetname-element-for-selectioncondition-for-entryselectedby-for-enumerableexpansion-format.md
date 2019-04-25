---
title: SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063859"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>Element „SelectionSetName“ für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)

Gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, wird die Bedingung erfüllt.

Element DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansions-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format) SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format) SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `SelectionSetName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl.

## <a name="remarks"></a>Hinweise

Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben. Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert. Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).

## <a name="see-also"></a>Weitere Informationen

[Auswahl definieren](./defining-selection-sets.md)

[SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
