---
title: TableColumnHeader-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858596"
---
# <a name="tablecolumnheader-element-format"></a>Element „TableColumnHeader“ (Format)

Definiert die Bezeichnung, die die Breite der Spalte und die Ausrichtung der Beschriftung für eine Spalte der Tabelle.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders Konfigurationselement für TableControl (Format) TableColumnHeader-Element für TableHeaders für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TableColumnHeader` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Label-Element für TableColumnHeader für TableControl (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bezeichnung, die am oberen Rand der Spalte angezeigt wird. Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft, deren Wert in den Zeilen angezeigt wird, verwendet.|
|[Width-Element für TableColumnHeader für TableControl (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Gibt die Breite (in Zeichen) der Spalte.|
|[Alignment-Element für TableColumbnHeader für TableControl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt an, wie die Bezeichnung der Spalte angezeigt wird. Wenn keine Ausrichtung angegeben wird, wird die Bezeichnung auf der linken Seite ausgerichtet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableHeaders-Element (Format)](./tableheaders-element-format.md)|Definiert die Spalten einer Tabelle-Sicht.|

## <a name="remarks"></a>Hinweise

Geben Sie einen Header für jede Spalte der Tabelle. Die Spalten werden angezeigt, in der Reihenfolge, in dem die `TableColumnHeader` Elemente definiert werden.

Eine Tabelle muss die gleiche Anzahl von besitzen `TableColumnHeader` Elemente wie `TableRowEntry` Elemente. Die Kopfzeile der Spalte definiert, wie der Text am oberen Rand der Tabelle angezeigt wird. Die Zeileneinträge definieren, welche Daten in den Zeilen der Tabelle angezeigt werden.

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [Tabellenansicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei `TableColumnHeader` Elemente. Das erste Element definiert eine Spalte, deren Bezeichnung ist "Spalte 1" hat eine Breite von 16 Zeichen lang und auf der linken Seite, deren Bezeichnung ausgerichtet ist. Das zweite Element definiert eine Spalte, deren Bezeichnung ist "Spalte 2" hat eine Breite von 10 Zeichen und, dessen Bezeichnung in der Spalte zentriert ist.

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

[Alignment-Element für TableColumnHeader für TableContrl (Format)](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Label-Element für TableColumnHeader für TableControl (Format)](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[TableHeaders-Element für TableControl (Format)](./tableheaders-element-format.md)

[Die Breite für TableColumnHeader für TableControl-Element (Format)](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
