---
title: Width-Element für TableColumnHeader für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083619"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Element „Width“ für TableColumnHeader für TableControl (Format)

Definiert die Breite einer Spalte (in Zeichen).

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders Konfigurationselement für TableControl (Format) TableColumnHeader Element TableHeaders für TableControl (Format)-Width-Element für TableColumnHeader für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Width` Element, das verwendet wird, wenn Spaltenheader zu definieren.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableColumnHeader-Element für TableHeaders für TableControl (Format)](./tablecolumnheader-element-format.md)|Definiert eine Bezeichnung, Breite und Ausrichtung der Daten für eine Spalte der Tabelle.|

## <a name="text-value"></a>Textwert

Geben Sie eine Breite (in Zeichen), die größer als die Länge der Eigenschaftswerte angezeigt wird, wenn bei der alle möglichen.

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `TableColumnHeader` Element, dessen Breite 16 Zeichen ist.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[TableColumnHeader-Element für TableHeader für TableControl (Format)](./tablecolumnheader-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
