---
title: TableRowEntries-Element für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055732"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a>Element „TableRowEntries“ für TableControl (Format)

Definiert die Zeilen der Tabelle an.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries Konfigurationselement für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableRowEntries` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableRowEntry-Element für TableRowEntries für TableControl (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableControl-Element (Format)](./tablecontrol-element-format.md)|Definiert ein Table-Format für eine Sicht.|

## <a name="remarks"></a>Hinweise

Sie müssen angeben, eine oder mehrere `TableRowEntry` Elemente für die Tabelle an. Es gibt keine maximale Beschränkung der Anzahl der `TableRowEntry` Elemente, die hinzugefügt werden können, noch ist die Reihenfolge von Bedeutung.

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `TableRowEntries` -Element, das eine Zeile definiert, die die Werte von zwei Eigenschaften des zeigt die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.

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

[TableControl-Element (Format)](./tablecontrol-element-format.md)

[TableRowEntry-Element (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
