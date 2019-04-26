---
title: Versehen Sie Element für TableColumnHeader für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065749"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Element „Label“ für TableColumnHeader für TableControl (Format)

Definiert die Bezeichnung, die am oberen Rand einer Spalte angezeigt wird. Dieses Element wird verwendet, wenn Sie eine Tabellensicht definieren.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders Konfigurationselement für TableControl (Format) TableColumnHeader-Element für TableHeaders für TableControl (Format)-Label-Element für TableColumnHeader für TableControl (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Label` Element. Nur eine Bezeichnung ist für die einzelnen Spalten zulässig.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableColumnHeader-Element für TableHeaders für TableControl (Format)](./tablecolumnheader-element-format.md)|Definiert eine Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte der Tabelle.|

## <a name="text-value"></a>Textwert

Geben Sie den Text, der am oberen Rand der Spalte der Tabelle angezeigt wird. Es gibt keine eingeschränkten Zeichen für die Bezeichnung der Spalte.

## <a name="remarks"></a>Hinweise

Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft, deren Wert in den Zeilen angezeigt wird, verwendet.

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `TableColumnHeader` Element, dessen Bezeichnung ist "Spalte 1".

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[TableColumnHeader-Element (Format)](./tablecolumnheader-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
