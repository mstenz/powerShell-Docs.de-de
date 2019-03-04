---
title: TableRowEntry-Element für TableRowEntroes für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 001d46debde61f928c338b2f68112fb201f96216
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853586"
---
# <a name="tablerowentry-element-for-tablerowentroes-for-tablecontrol-format"></a>Element „TableRowEntry“ für TableRowEntries für TableControl (Format)

Definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries Konfigurationselement für TableControl (Format) TableRowEntry-Element für TableRowEntries für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableRowEntry` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für TableRowEntry für TableControl (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Objekte, deren Eigenschaftswerte in der Zeile angezeigt werden.|
|[TableColumnItems-Element für TableRowEntry für TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Eigenschaften oder Skripts, deren Werte angezeigt werden.|
|[Umschließen Sie Element für TableRowEntry für TableCntrol (Format)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)|Optionales Element.<br /><br /> Gibt an, dass Text, der die Spaltenbreite überschreitet, die in der nächsten Zeile angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableRowEntries-Element für TableControl (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Definiert die Zeilen der Tabelle an.|

## <a name="remarks"></a>Hinweise

Eine `TableColumnItems` -Element und ein `EntrySelectedBy` Element muss angegeben werden.

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `TableRowEntry` -Element, das eine Zeile definiert, die die Werte von zwei Eigenschaften des zeigt die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.

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

[EntrySelectedBy-Element für TableRowEntry für TableControl (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[TableColumnItems-Element für TableRowEntry für TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[TableRowEntries-Element für TableControl (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[TableRowEntry-Element für TableRowEntries für TableControl (Format)](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[Umschließen Sie Element für TableRowEntry für TableCntrol (Format)](./wrap-element-for-tablerowentry-for-tablecontrl-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
