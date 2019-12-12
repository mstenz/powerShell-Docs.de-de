---
title: Tablerowentries-Element für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368149"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>Element „TableRowEntries“ für TableControl (Format)

Definiert die Zeilen der Tabelle.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element für tablecontrol (Format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `TableRowEntries`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablerowentry-Element für tablerowentries für tablecontrol (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Daten, die in einer Zeile der Tabelle angezeigt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablecontrol-Element (Format)](./tablecontrol-element-format.md)|Definiert ein Tabellenformat für eine Sicht.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens ein `TableRowEntry`-Element für die Tabellenansicht angeben. Es gibt keine maximale Beschränkung für die Anzahl der `TableRowEntry` Elemente, die hinzugefügt werden können, und deren Reihenfolge nicht signifikant ist.

Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `TableRowEntries` Element, das eine Zeile definiert, in der die Werte von zwei Eigenschaften des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts angezeigt werden.

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Tablecontrol-Element (Format)](./tablecontrol-element-format.md)

[Tablerowentry-Element (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
