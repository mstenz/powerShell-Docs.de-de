---
title: Alignment-Element für tablecolumnheader für tablecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364379"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a>Element „Alignment“ für TableColumnHeader für TableControl (Format)

Definiert, wie die Daten in einem Spaltenheader angezeigt werden.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format) tableHeaders-Element (Format) tablecolumnheader-Element (Format) Alignment-Element für tablecolumnheader (Format)

## <a name="syntax"></a>Syntax

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `Alignment`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tablecolumnheader-Element (Format)](./tablecolumnheader-element-format.md)|Definiert eine Bezeichnung, die Breite und die Ausrichtung der Daten für eine Spalte der Tabelle.|

## <a name="text-value"></a>Textwert

Geben Sie einen der folgenden Werte an. Bei diesen Werten wird Groß-/Kleinschreibung nicht beachtet.

Links richtet die in der Spalte angezeigten Daten auf der linken Seite aus. Dies ist die Standardeinstellung, wenn dieses Element nicht angegeben ist.

Rechts richtet die in der Spalte auf der rechten Seite angezeigten Daten aus.

Zentrieren zentriert die in der Spalte angezeigten Daten.

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein `TableColumnHeader` Element, dessen Daten auf der linken Seite ausgerichtet werden.

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
