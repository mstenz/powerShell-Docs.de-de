---
title: Alignment-Element für TableColumnHeader für TableControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853756"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Element „Alignment“ für TableColumnHeader für TableControl (Format)

Definiert, wie die Daten in einem Spaltenheader angezeigt werden.

(-Format)-Element ViewDefinitions-Element (Format) anzeigen (Format)-Element TableControl-Element (Format) TableHeaders-Element (Format) TableColumnHeader-Element (Format) Ausrichtung Konfigurationselement für TableColumnHeader (Format)

## <a name="syntax"></a>Syntax

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Alignment` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TableColumnHeader-Element (Format)](./tablecolumnheader-element-format.md)|Definiert eine Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte der Tabelle.|

## <a name="text-value"></a>Textwert

Geben Sie einen der folgenden Werte. Diese Werte sind nicht in der Groß-/Kleinschreibung beachtet.

Links Richtet die Daten in der Spalte auf der linken Seite angezeigt. ist dies die Standardeinstellung, wenn dieses Element nicht angegeben ist.

Rechts ausgerichtet werden, werden die Daten in der Spalte auf der rechten Seite angezeigt.

Center Rechenzentren, die Daten in der Spalte angezeigt.

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `TableColumnHeader` Element, dessen Daten werden auf der linken Seite ausgerichtet.

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
