---
title: Label-Element für tablecolumnheader für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365169"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a>Element „Label“ für TableColumnHeader für TableControl (Format)

Definiert die Bezeichnung, die oben in einer Spalte angezeigt wird. Dieses Element wird verwendet, wenn eine Tabellen Sicht definiert wird.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tableHeaders-Element für tablecontrol (Format) tablecolumnheader-Element für tableHeaders für tablecontrol (Format) Label-Element für Tablecolumnheader für tablecontrol (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Label`-Elements beschrieben. Für jede Spalte ist nur eine Bezeichnung zulässig.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablecolumnheader-Element für tableHeaders für tablecontrol (Format)](./tablecolumnheader-element-format.md)|Definiert eine Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte der Tabelle.|

## <a name="text-value"></a>Textwert

Geben Sie den Text an, der oben in der Spalte der Tabelle angezeigt wird. Es sind keine eingeschränkten Zeichen für die Spalten Bezeichnung vorhanden.

## <a name="remarks"></a>Hinweise

Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft verwendet, deren Wert in den Zeilen angezeigt wird.

Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein `TableColumnHeader`-Element, dessen Bezeichnung "Column 1" ist.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Tablecolumnheader-Element (Format)](./tablecolumnheader-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
