---
title: Übersicht über die Formatierung von Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363689"
---
# <a name="formatting-file-overview"></a>Formatierungsdatei: Übersicht

Das Anzeige Format für die Objekte, die von Befehlen (Cmdlets, Funktionen und Skripts) zurückgegeben werden, wird mithilfe von Formatierungs Dateien (Format. ps1xml-Dateien) definiert. Einige dieser Dateien werden von PowerShell bereitgestellt, um das Anzeige Format für die Objekte zu definieren, die von von PowerShell bereitgestellten Befehlen zurückgegeben werden, z. b. das [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekt, das vom Cmdlet `Get-Process` zurückgegeben wird Sie können jedoch auch eigene benutzerdefinierte Formatierungs Dateien erstellen, um die Standard Anzeige Formate zu überschreiben, oder Sie können eine benutzerdefinierte Formatierungs Datei schreiben, um die Anzeige von Objekten zu definieren, die von ihren eigenen Befehlen zurückgegeben werden.

> [!IMPORTANT]
> Beim Formatieren von Dateien werden die Elemente eines Objekts, die an die Pipeline zurückgegeben werden, nicht bestimmt. Wenn ein Objekt an die Pipeline zurückgegeben wird, sind alle Member dieses Objekts verfügbar, auch wenn einige nicht angezeigt werden.

PowerShell verwendet die Daten in diesen Formatierungs Dateien, um zu bestimmen, was angezeigt wird und wie die angezeigten Daten formatiert werden. Die angezeigten Daten können die Eigenschaften eines Objekts oder den Wert eines Skripts enthalten. Skripts werden verwendet, wenn Sie einen Wert anzeigen möchten, der nicht direkt aus den Eigenschaften eines Objekts verfügbar ist, z. b. das Hinzufügen des Werts von zwei Eigenschaften eines Objekts und anschließendes Anzeigen der Summe als Datenelement. Die Formatierung der angezeigten Daten erfolgt durch Definieren von Sichten für die Objekte, die Sie anzeigen möchten. Sie können für jedes Objekt eine einzelne Ansicht definieren, Sie können eine einzelne Ansicht für mehrere Objekte definieren, oder Sie können mehrere Ansichten für dasselbe Objekt definieren. Es gibt keine Beschränkung für die Anzahl der Sichten, die Sie definieren können.

## <a name="common-features-of-formatting-files"></a>Allgemeine Funktionen zum Formatieren von Dateien

Jede Formatierungs Datei kann die folgenden Komponenten definieren, die für alle Ansichten freigegeben werden können, die in der Datei definiert sind:

- Standard Konfigurationseinstellung, z. b. ob die in den Zeilen der Tabellen angezeigten Daten in der nächsten Zeile angezeigt werden, wenn die Daten länger als die Spaltenbreite sind. Weitere Informationen zu diesen Einstellungen finden Sie unter [Definieren allgemeiner Konfigurationseinstellungen](./defining-common-configuration-features.md).

- Sätze von-Objekten, die von einer beliebigen Ansicht der Formatierungs Datei angezeigt werden können. Weitere Informationen zu diesen Sätzen (als *Auswahl Sätze*bezeichnet) finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).

- Allgemeine Steuerelemente, die von allen Ansichten der Formatierungs Datei verwendet werden können. Mit Steuerelementen können Sie besser steuern, wie Daten angezeigt werden. Weitere Informationen zu-Steuerelementen finden Sie unter [Definieren von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

## <a name="formatting-views"></a>Formatieren von Sichten

Durch das Formatieren von Sichten können Objekte in einem Tabellenformat, einem Listenformat, einem breiten Format und einem benutzerdefinierten Format angezeigt werden. In den meisten Fällen wird jede Formatierungs Definition durch eine Reihe von XML-Tags beschrieben, die die Sicht beschreiben. Jede Ansicht enthält den Namen der Ansicht, die Objekte, die die Sicht verwenden, und die Elemente der Ansicht, z. b. die Spalten-und Zeilen Informationen für eine Tabellen Sicht.

In der Tabellenansicht werden die Eigenschaften eines Objekts oder eines Skriptblock Werts in mindestens einer Spalte aufgelistet. Jede Spalte stellt eine einzelne Eigenschaft des Objekts oder einen Skript Wert dar. Sie können eine Tabellen Sicht definieren, in der alle Eigenschaften eines Objekts, eine Teilmenge der Eigenschaften eines Objekts oder eine Kombination von Eigenschaften und Skript Werten angezeigt werden. Jede Zeile der Tabelle stellt ein zurück gegebenes Objekt dar. Das Erstellen einer Tabellenansicht ist sehr ähnlich, wenn Sie ein Objekt an das `Format-Table`-Cmdlet weiterreichen. Weitere Informationen zu dieser Ansicht finden Sie unter [Tabellen Sicht](./creating-a-table-view.md).

In der Listenansicht werden die Eigenschaften eines Objekts oder eines Skript Werts in einer einzelnen Spalte aufgelistet. In jeder Zeile der Liste wird eine optionale Bezeichnung oder der Eigenschaftsname, gefolgt vom Wert der Eigenschaft oder des Skripts, angezeigt. Das Erstellen einer Listenansicht ähnelt der Weiterleitung eines Objekts an das `Format-List`-Cmdlet. Weitere Informationen zu dieser Ansicht finden Sie in der [Listenansicht](./creating-a-list-view.md).

Die Breite Ansicht Listet eine einzelne Eigenschaft eines Objekts oder einen Skript Wert in einer oder mehreren Spalten auf. Für diese Ansicht gibt es keine Bezeichnung oder einen Header. Das Erstellen einer breiten Ansicht ähnelt stark dem Übergeben eines Objekts an das `Format-Wide`-Cmdlet. Weitere Informationen zu dieser Ansicht finden Sie unter [Wide View](./creating-a-wide-view.md).

Die benutzerdefinierte Ansicht zeigt eine anpassbare Ansicht von Objekteigenschaften oder Skript Werten an, die nicht der festen Struktur von Tabellen Sichten, Listenansichten oder breiten Ansichten entspricht. Sie können eine eigenständige benutzerdefinierte Sicht definieren, oder Sie können eine benutzerdefinierte Ansicht definieren, die von einer anderen Ansicht verwendet wird, z. b. eine Tabellen-oder Listenansicht. Das Erstellen einer benutzerdefinierten Ansicht ähnelt der Weiterleitung eines Objekts an das `Format-Custom`-Cmdlet. Weitere Informationen zu dieser Ansicht finden Sie unter [benutzerdefinierte Ansicht](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Komponenten einer Ansicht

Die folgenden XML-Beispiele zeigen die grundlegenden XML-Komponenten einer Ansicht. Die einzelnen XML-Elemente variieren abhängig von der Sicht, die Sie erstellen möchten, aber die grundlegenden Komponenten der Sichten sind identisch.

Um mit zu beginnen, verfügt jede Ansicht über ein `Name`-Element, das einen benutzerfreundlichen Namen angibt, der zum Verweisen auf die Sicht verwendet wird. ein `ViewSelectedBy` Element, das definiert, welche .NET-Objekte von der Sicht angezeigt werden, und ein *Steuer* Element, das die Ansicht definiert.

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

Innerhalb des Control-Elements können Sie ein oder mehrere *Einstiegs* Elemente definieren. Wenn Sie mehrere Definitionen verwenden, müssen Sie angeben, welche .NET-Objekte die einzelnen Definitionen verwenden. In der Regel ist nur ein Eintrag mit nur einer Definition für jedes Steuerelement erforderlich.

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

In jedem Eintrags Element einer Ansicht geben Sie die *Element* Elemente an, die die .net-Eigenschaften oder-Skripts definieren, die von dieser Sicht angezeigt werden.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Wie in den vorherigen Beispielen gezeigt, kann die Formatierungs Datei mehrere Sichten enthalten, eine Sicht kann mehrere Definitionen enthalten, und jede Definition kann mehrere Elemente enthalten.

## <a name="example-of-a-table-view"></a>Beispiel für eine Tabellenansicht

Das folgende Beispiel zeigt die XML-Tags, mit denen eine Tabellen Sicht definiert wird, die zwei Spalten enthält. Das [viewdefinitions](./viewdefinitions-element-format.md) -Element ist das Containerelement für alle Sichten, die in der Formatierungs Datei definiert sind. Das [Ansichts](./view-element-format.md) Element definiert die spezifische Tabelle, die Liste, die Breite oder die benutzerdefinierte Sicht. Innerhalb jedes [Ansichts](./view-element-format.md) Elements gibt das [Name](./name-element-for-view-format.md) -Element den Namen der Ansicht an, das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht verwenden, und die verschiedenen Steuerelemente (wie z. b. das `TableControl`-Element, das im folgenden Beispiel gezeigt wird) definieren den Typ der Sicht.

```xml
<ViewDefinitions>
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

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Erstellen einer breiten Ansicht](./creating-a-wide-view.md)

[Erstellen benutzerdefinierter Steuerelemente](./creating-custom-controls.md)

[Schreiben einer PowerShell-Formatierungs-und-Typen Datei](./writing-a-powershell-formatting-file.md)
