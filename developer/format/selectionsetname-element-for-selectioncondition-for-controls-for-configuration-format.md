---
title: SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064021"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a>Element „SelectionSetName“ für SelectionCondition für Controls für Configuration (Format)

Gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt mit diesem Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement-Element (Format)-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Steuerelemente für (-Format) CustomEntry Konfigurationselement für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für (Format) SelectionCondition Konfigurationselement für EntrySelectedBy für Steuerelemente für (-Format) SelectionSetName Konfigurationselement für SelectionCondition für Steuerelemente für die Konfiguration (Format)

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
|[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl.

## <a name="remarks"></a>Hinweise

Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert. Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

Die auswahlbedingung kann ein Auswahlsatz oder .NET Typ angeben, aber nicht beides angeben. Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[Auswahl definieren](./defining-selection-sets.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
