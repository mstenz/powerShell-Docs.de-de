---
title: SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855116"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>Element „SelectionSetName“ für SelectionCondition für Controls für View (Format)

Gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt wird mit diesem Steuerelement angezeigt. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für Steuerelemente für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für Steuerelemente für Ansicht) SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)-Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl.

## <a name="remarks"></a>Hinweise

Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert. Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).

Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben. Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[Auswahl definieren](./defining-selection-sets.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
