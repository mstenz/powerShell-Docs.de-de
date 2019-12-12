---
title: Benutzerdefinierte Formatierungs Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369829"
---
# <a name="custom-formatting-files"></a>Benutzerdefinierte Formatierungsdateien

Das Anzeige Format für die von Cmdlets, Funktionen und Skripts zurückgegebenen Objekte wird mithilfe von Formatierungs Dateien (Format. ps1xml-Dateien) definiert. Einige dieser Dateien werden von Windows PowerShell bereitgestellt, um das Standard Anzeige Format für die von Windows PowerShell-Cmdlets zurückgegebenen Objekte zu definieren. Sie können jedoch auch eigene benutzerdefinierte Formatierungs Dateien erstellen, um die Standard Anzeige Formate zu überschreiben oder die Anzeige von Objekten zu definieren, die von ihren eigenen Befehlen zurückgegeben werden.

Windows PowerShell verwendet die Daten in diesen Formatierungs Dateien, um zu bestimmen, was angezeigt wird und wie die Daten formatiert werden. Die angezeigten Daten können die Eigenschaften eines Objekts oder den Wert eines Skript Blocks enthalten.  Skriptblöcke werden verwendet, wenn Sie einen Wert anzeigen möchten, der nicht direkt aus den Eigenschaften eines Objekts verfügbar ist. Beispielsweise können Sie den Wert von zwei Eigenschaften eines Objekts hinzufügen und die Summe als separates Datenelement anzeigen. Wenn Sie eine eigene Formatierungs Datei schreiben, müssen Sie *Sichten* für die Objekte definieren, die Sie anzeigen möchten. Sie können für jedes Objekt eine einzelne Ansicht definieren, Sie können eine einzelne Ansicht für mehrere Objekte definieren, oder Sie können mehrere Ansichten für dasselbe Objekt definieren. Es gibt keine Beschränkung für die Anzahl der Sichten, die Sie definieren können.

> [!IMPORTANT]
> Beim Formatieren von Dateien werden die Elemente eines Objekts, die an die Pipeline zurückgegeben werden, nicht bestimmt. Wenn ein Objekt an die Pipeline zurückgegeben wird, sind alle Member dieses Objekts verfügbar.

## <a name="format-views"></a>Formatieren von Sichten

Durch das Formatieren von Sichten können Objekte in einem Tabellenformat, einem Listenformat, einem breiten Format und einem benutzerdefinierten Format angezeigt werden. In den meisten Fällen wird jede Formatierungs Definition durch eine Reihe von XML-Tags beschrieben, die eine Sicht beschreiben. Jede Ansicht enthält den Namen der Ansicht, die Objekte, die die Sicht verwenden, und die Elemente der Ansicht, z. b. die Spalten-und Zeilen Informationen für eine Tabellen Sicht.

Die folgenden Ansichten sind verfügbar.

In der Tabellenansicht werden die Eigenschaften eines Objekts oder eines Skriptblock Werts in mindestens einer Spalte aufgelistet. Jede Spalte stellt eine Eigenschaft des Objekts oder eines Skriptblock Werts dar. Sie können eine Tabellen Sicht definieren, in der alle Eigenschaften eines Objekts, eine Teilmenge der Eigenschaften eines Objekts oder eine Kombination von Eigenschaften und Skriptblock Werten angezeigt werden. Jede Zeile der Tabelle stellt ein zurück gegebenes Objekt dar. Weitere Informationen zu dieser Ansicht finden Sie unter [Tabellen Sicht](../format/creating-a-table-view.md).

In der Listenansicht werden die Eigenschaften eines Objekts oder eines Skriptblock Werts in einer einzelnen Spalte aufgelistet. Jede Zeile der Liste zeigt eine optionale Bezeichnung oder den Eigenschaftsnamen gefolgt vom Wert der Eigenschaft oder des Skript Blocks an. Weitere Informationen zu dieser Ansicht finden Sie in der [Listenansicht](../format/creating-a-list-view.md).

Die Breite Ansicht Listet eine einzelne Eigenschaft eines Objekts oder einen Skriptblock Wert in einer oder mehreren Spalten auf. Für diese Ansicht gibt es keine Bezeichnung oder einen Header. Weitere Informationen zu dieser Ansicht finden Sie unter [Wide View](../format/creating-a-wide-view.md).

Die benutzerdefinierte Ansicht zeigt eine anpassbare Ansicht von Objekteigenschaften oder Skriptblock Werten an, die nicht der festen Struktur von Tabellen Sichten, Listenansichten oder breiten Ansichten entspricht. Sie können eine eigenständige benutzerdefinierte Ansicht definieren, oder Sie können eine benutzerdefinierte Ansicht definieren, die von einer anderen Ansicht verwendet wird, z. b. eine Tabellen-oder Listenansicht. Weitere Informationen zu dieser Ansicht finden Sie unter [benutzerdefinierte Ansicht](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Anzeigen von XML-Elementen

Das folgende Beispiel zeigt die XML-Tags, mit denen eine Tabellen Sicht definiert wird, die zwei Spalten enthält. Das [viewdefinitions](../format/viewdefinitions-element-format.md) -Element ist das Containerelement für alle Sichten, die in der Formatierungs Datei definiert sind. Das [Ansichts](../format/view-element-format.md) Element definiert die spezifische Tabelle, die Liste, die Breite oder die benutzerdefinierte Sicht. In jeder Ansicht gibt das [Name](../format/name-element-for-view-format.md) -Element den Namen der Ansicht an, das [viewselectedby](../format/viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht verwenden, und die verschiedenen Steuerelemente (z. b. das `TableControl`-Element) definieren das Format der Sicht.

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>Weitere Informationen

[Tabellenansicht](../format/creating-a-table-view.md)

[Listenansicht](../format/creating-a-list-view.md)

[Breite Ansicht](../format/creating-a-wide-view.md)

[Benutzerdefinierte Ansicht](../format/creating-custom-controls.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
