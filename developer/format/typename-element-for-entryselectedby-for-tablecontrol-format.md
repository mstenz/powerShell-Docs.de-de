---
title: TypeName-Element für EntrySelectedBy für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855726"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a>Element „TypeName“ für EntrySelectedBy für TableControl (Format)

Gibt einen .NET-Typ, der dieser Eintrag der Tabellenansicht verwendet. Es gibt keine Beschränkung der Anzahl von Typen, die für einen Tabelleneintrag angegeben werden können.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy-Element (Format) TypeName Konfigurationselement für EntrySelectedBy für TableRowEntry (Format)

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
|[EntrySelectedBy-Element (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definiert die .NET-Typen, die diesen Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des .NET-Typs.

## <a name="remarks"></a>Hinweise

Jeder Listeneintrag muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[EntrySelectedBy-Element (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
