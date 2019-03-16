---
title: EntrySelectedBy-Element für TableRowEntry für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058758"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a>Element „EntrySelectedBy“ für TableRowEntry für TableControl (Format)

Definiert .NET Typen, die dieser Definition der Tabellenansicht oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries-Element (Format) TableRowEntry-Element (Format) EntrySelectedBy Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die für diese Tabelle View Definition zu verwendende vorhanden sein muss.|
|[SelectionSetName-Element für EntrySelectedBy für TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, die diese Tabelle (Definition) Ansicht verwenden.|
|[TypeName-Element für EntrySelectedBy für TableControl (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der dieser Tabelle anzeigen (Definition) verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableRowEntry-Element für TableControl (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|Definiert die Daten, die in einer Zeile der Tabelle angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung für eine Tabelle (Definition) Ansicht angeben. Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der eine bestimmte Eigenschaft-Wert oder ein Skript ergibt, `true`. Weitere Informationen zu auswahlbedingungen, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `TableRowEntry` -Element, das verwendet wird, zum Anzeigen der Eigenschaften der ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[SelectionCondition-Element für EntrySelectedBy für TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[SelectionSetName-Element für EntrySelectedBy für TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[TableRowEntry-Element für TableControl (Format)](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[TypeName-Element für EntrySelectedBy für TableControl (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
