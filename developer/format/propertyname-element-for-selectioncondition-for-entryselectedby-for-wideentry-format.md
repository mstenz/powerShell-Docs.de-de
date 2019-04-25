---
title: PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 340abb12-6df1-42f4-bdae-b0509c90952c
caps.latest.revision: 11
ms.openlocfilehash: 196877b97db9ed0592e357486c1318dc1e7efd31
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064678"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a>Element „PropertyName“ für SelectionCondition für EntrySelectedBy für WideEntry (Format)

Gibt die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Definition verwendet.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)-PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .NET-Eigenschaft.

## <a name="remarks"></a>Hinweise

Die auswahlbedingung muss angeben, über mindestens einen Eigenschaftennamen oder ein Skript zu evaluieren, aber nicht beide angeben. Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
