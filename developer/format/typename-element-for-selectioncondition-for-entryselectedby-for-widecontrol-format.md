---
title: TypeName-Element für SelectionCondition für EntrySelectedBy für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083806"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a>Element „TypeName“ für SelectionCondition für EntrySelectedBy für WideControl (Format)

Gibt einen .NET-Typ, der die Bedingung auslöst. Wenn dieses Typs vorhanden ist, wird die Definition verwendet.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format) TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definiert die Bedingung, die für diesen wide Eintrag zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

Die auswahlbedingung kann einen .NET-Typ, ein angeben, oder eine Auswahl festgelegt, aber nicht beides angeben. Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
