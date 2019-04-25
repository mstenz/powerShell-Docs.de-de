---
title: TableHeaders-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075408"
---
# <a name="tableheaders-element-format"></a>Element „TableHeaders“ (Format)

Definiert die Header für die Spalten einer Tabelle an.

ViewDefinitions-Element (Format) Element (Format) TableControl-Element (Format) TableHeaders Ansichtselement für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Elemente von der `TableHeaders` Element. Es muss ein untergeordnetes Element für jede Eigenschaft des Objekts, das angezeigt werden soll. Die Headerinformationen für die Spalte wird in der Reihenfolge angezeigt, dass die untergeordneten Elemente angegeben werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableColumnHeader-Element (Format)](./tablecolumnheader-element-format.md)|Optionales Element.<br /><br /> Definiert die Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte mit einer Tabellenansicht.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableControl-Element (Format)](./tablecontrol-element-format.md)|Definiert ein Table-Format für eine Sicht.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `TableHeaders` Element, das zwei Spaltenüberschriften definiert.

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[TableColumnHeader-Element (Format)](./tablecolumnheader-element-format.md)

[TableControl-Element (Format)](./tablecontrol-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
