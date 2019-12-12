---
title: Tablerowentry-Element für tablerowentries für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361799"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a>Element „TableRowEntry“ für TableRowEntries für TableControl (Format)

Definiert die Daten, die in einer Zeile der Tabelle angezeigt werden.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element für tablecontrol (Format) tablerowentry-Element für tablerowentries für tablecontrol (Format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TableRowEntry`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Entryselectedby-Element für tablerowentry für tablecontrol (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Objekte, deren Eigenschaftswerte in der Zeile angezeigt werden.|
|[Tablecolumnitems-Element für tablerowentry für tablecontrol (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Eigenschaften oder Skripts, deren Werte angezeigt werden.|
|[Wrap-Element für tablerowentry für tablecontrol (Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt an, dass der Text, der die Spaltenbreite überschreitet, in der nächsten Zeile angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablerowentries-Element für tablecontrol (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Definiert die Zeilen der Tabelle.|

## <a name="remarks"></a>Hinweise

Ein `TableColumnItems` Element und ein `EntrySelectedBy` Element müssen angegeben werden.

Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `TableRowEntry` Element, das eine Zeile definiert, in der die Werte von zwei Eigenschaften des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts angezeigt werden.

```xml
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
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Entryselectedby-Element für tablerowentry für tablecontrol (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[Tablecolumnitems-Element für tablerowentry für tablecontrol (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[Tablerowentries-Element für tablecontrol (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Wrap-Element für tablerowentry für tablecontrol (Format)](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
