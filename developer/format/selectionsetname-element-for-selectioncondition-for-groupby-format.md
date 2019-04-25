---
title: SelectionSetName-Element für SelectionCondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b9a4912-d755-42f3-8058-53c0797e28e4
caps.latest.revision: 6
ms.openlocfilehash: 371913eda2b09ff6788494b68738f2ad53ccb115
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063765"
---
# <a name="selectionsetname-element-for-selectioncondition-for-groupby-format"></a>Element „SelectionSetName“ für SelectionCondition für GroupBy (Format)

Gibt den Satz von .NET-Typen, die die Bedingung auslösen. Wenn alle Typen in dieser Gruppe vorhanden sind, die Bedingung ist erfüllt, und das Objekt mit diesem Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionCondition-Element für EntrySelectedBy für GroupBy (Format) SelectionSetName-Element für SelectionCondition für GroupBy (Format)

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
|[SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl.

## <a name="remarks"></a>Hinweise

Auswahl sind allgemeine Gruppen von .NET-Objekten, die von einer beliebigen Ansicht verwendet werden können, die die Formatierungsdatei definiert. Weitere Informationen zum Erstellen von und verweisen auf diese Auswahl legt finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).

Wenn dieses Element angegeben ist, können Sie nicht angeben der [TypeName](./typename-element-for-selectioncondition-for-groupby-format.md) Element. Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[TypeName-Element für SelectionCondition für GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[Auswahl definieren](./defining-selection-sets.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
