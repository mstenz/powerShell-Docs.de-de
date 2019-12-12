---
title: Tablecolumnitem-Element für tablecolumnitems für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 9e6cffc7476ef01124d95ecbf287d9788b0324c9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368229"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Element „TableColumnItem“ für TableColumnItems für TableControl (Format)

Definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tablerowentries-Element für tablecontrol (Format) tablerowentry-Element für tablerowentries für tablecontrol (Format) Tablecolumnitems-Element für tablecontrolentry für tablecontrol (Format) tablecolumnitem-Element für tablecolumnitems für tablecontrol (Format)

## <a name="syntax"></a>Syntax

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `TableColumnItem`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Alignment-Element für tablecolumnitem für tablecontrol (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Definiert, wie die Daten in einer Spalte der Zeile angezeigt werden.|
|[FormatString-Element für tablecolumnitem für tablecontrol (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Gibt ein Format Muster an, das zum Formatieren der Daten in der Spalte der Zeile verwendet wird.|
|[PropertyName-Element für tablecolumnitem für tablecontrol (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt den Namen der Eigenschaft an, deren Wert angezeigt wird.|
|[ScriptBlock-Element für tablecolumnitem für tablecontrol (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert in der Spalte einer Zeile angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablecolumnitems-Element für tablecontrolentry für tablecontrol (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definiert die Eigenschaften oder Skripts, deren Werte in der Zeile angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie können in jeder Spalte der Zeile eine Eigenschaft eines Objekts oder eines Skripts angeben. Wenn keine untergeordneten Elemente angegeben werden, ist das Element ein Platzhalter, und es werden keine Daten angezeigt.

Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein `TableColumnItem`-Element, das den Wert der `Status`-Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts anzeigt.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Alignment-Element für tablecolumnitem für tablecontrol (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Tablecolumnitems-Element (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString-Element für tablecolumnitem für tablecontrol (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName-Element für tablecolumnitem für tablecontrol (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[ScriptBlock-Element für tablecolumnitem für tablecontrol (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
