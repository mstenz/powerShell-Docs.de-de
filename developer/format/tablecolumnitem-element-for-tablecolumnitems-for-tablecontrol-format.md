---
title: TableColumnItem-Element für TableColumnItems für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063937"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a>Element „TableColumnItem“ für TableColumnItems für TableControl (Format)

Definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableRowEntries Konfigurationselement für TableControl (Format) TableRowEntry-Element für TableRowEntries für TableControl (Format) TableColumnItems-Element für TableControlEntry für TableControl (Format) TableColumnItem-Element für TableColumnItems für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableColumnItem` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Alignment-Element für TableColumnItem für TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Definiert, wie die Daten in einer Spalte der Zeile angezeigt werden.|
|[FormatString-Element für TableColumnItem für TableControl (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|Gibt ein Formatmuster, das zum Formatieren der Daten in der Spalte der Zeile verwendet wird.|
|[PropertyName-Element für TableColumnItem für TableControl (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt den Namen der Eigenschaft, deren Wert angezeigt wird.|
|[ScriptBlock-Element für TableColumnItem für TableControl (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert in der Spalte einer Zeile angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableColumnItems-Element für TableControlEntry für TableControl (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|Definiert die Eigenschaften oder Skripts, die in der Zeile, deren Werte angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie können eine Eigenschaft eines Objekts oder eines Skripts in jeder Spalte der Zeile angeben. Wenn keine untergeordneten Elemente angegeben sind, wird das Element ist ein Platzhalter, und keine Daten angezeigt.

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `TableColumnItem` -Element, das den Wert der `Status` Eigenschaft der ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Alignment-Element für TableColumnItem für TableControl (Format)](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[TableColumnItems-Element (Format)](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[FormatString-Element für TableColumnItem für TableControl (Format)](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[PropertyName-Element für TableColumnItem für TableControl (Format)](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[ScriptBlock-Element für TableColumnItem für TableControl (Format)](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
