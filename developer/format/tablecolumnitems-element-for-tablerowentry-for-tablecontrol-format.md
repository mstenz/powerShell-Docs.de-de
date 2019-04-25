---
title: TableColumnItems-Element für TableRowEntry für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075391"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a>Element „TableColumnItems“ für TableRowEntry für TableControl (Format)

Definiert die Eigenschaften oder Skripts, die in einer Zeile, deren Werte angezeigt werden.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries Konfigurationselement für TableControl (Format) TableRowEntry-Element für TableRowEntries für TableControl (Format) TableColumnItems-Element für TableControlEntry für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableColumnItems` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableColumnItem-Element für TableColumnItems für TableControl (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Eigenschaft oder das Skript in einer Spalte der Zeile, deren Wert angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableRowEntry-Element für TableRowEntries für TableControl (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.|

## <a name="remarks"></a>Hinweise

Ein `TableColumnItem` Element ist erforderlich für jede Spalte der Zeile. Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `TableColumnItems` Element, das drei Eigenschaften definiert die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[TableColumnItem-Element (Format)](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[TableRowEntry-Element (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
