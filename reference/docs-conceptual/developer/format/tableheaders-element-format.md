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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361819"
---
# <a name="tableheaders-element-format"></a>Element „TableHeaders“ (Format)

Definiert die Header für die Spalten einer Tabelle.

Viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tableHeaders-Element für tablecontrol (Format)

## <a name="syntax"></a>Syntax

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und die übergeordneten Elemente des `TableHeaders`-Elements beschrieben. Es muss ein untergeordnetes-Element für jede Eigenschaft des Objekts vorhanden sein, das angezeigt werden soll. Die Spaltenheader Informationen werden in der Reihenfolge angezeigt, in der die untergeordneten Elemente angegeben werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablecolumnheader-Element (Format)](./tablecolumnheader-element-format.md)|Optionales Element.<br /><br /> Definiert die Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte einer Tabellen Sicht.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablecontrol-Element (Format)](./tablecontrol-element-format.md)|Definiert ein Tabellenformat für eine Sicht.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein `TableHeaders`-Element, das zwei Spaltenheader definiert.

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

[Tablecolumnheader-Element (Format)](./tablecolumnheader-element-format.md)

[Tablecontrol-Element (Format)](./tablecontrol-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
