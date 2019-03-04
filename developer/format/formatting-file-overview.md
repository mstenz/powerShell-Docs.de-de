---
title: Übersicht über die Datei Formatierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863296"
---
# <a name="formatting-file-overview"></a>Formatierungsdatei: Übersicht

Das Anzeigeformat für die Objekte, die durch Befehle (Cmdlets, Funktionen und Skripts) zurückgegeben werden, werden mithilfe von Formatierungsdateien (Format. ps1xml-Dateien) definiert. Einige dieser Dateien finden Sie PowerShell, um das Anzeigeformat für die bereitgestellte PowerShell-Befehle, wie z. B. zurückgegebenen Objekte definieren die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) zurückgegebenes Objekt der `Get-Process` Cmdlet. Allerdings können Sie auch eigene benutzerdefinierte Formatierungsdateien, um die Standardformate für die Anzeige zu überschreiben, erstellen, oder Sie können eine benutzerdefinierte Formatierung-Datei, um die Anzeige von Objekten zurückgegeben, die durch Ihre eigenen Befehle definieren, schreiben.

> [!IMPORTANT]
> Formatierungsdateien sind die Elemente eines Objekts nicht bestimmt werden, die an die Pipeline zurückgegeben werden. Wenn ein Objekt an die Pipeline zurückgegeben wird, sind alle Member des Objekts verfügbar, auch wenn einige nicht angezeigt werden.

PowerShell verwendet die Daten in diese Formatierungsdateien, um zu bestimmen, was angezeigt wird und wie die angezeigten Daten formatiert werden. Die angezeigten Daten können es sich um die Eigenschaften eines Objekts oder der Wert eines Skripts enthalten. Skripts werden verwendet, wenn einen Wert angezeigt werden sollen, nicht direkt über die Eigenschaften eines Objekts, z. B. den Wert von zwei Eigenschaften eines Objekts hinzufügen, und klicken Sie dann die Summe als ein Datenelement angezeigt werden sollen. Formatieren der angezeigten Daten erfolgt durch Definieren von Ansichten für die Objekte, die Sie anzeigen möchten. Sie können eine einzelne Ansicht für jedes Objekt definieren, können Sie eine einzelne Ansicht für mehrere Objekte definieren oder Sie können mehrere Ansichten für das gleiche Objekt definieren. Es gibt keine Beschränkung für die Anzahl der Aufrufe, die Sie definieren können.

## <a name="common-features-of-formatting-files"></a>Allgemeine Funktionen der Formatierungsdateien

Jede Formatierungsdatei kann die folgenden Komponenten definieren, die alle von der Datei definierten Sichten gemeinsam verwendet werden können:

- Standardeinstellung Konfiguration, z. B., ob die Daten angezeigt, die in den Zeilen der Tabellen in der nächsten Zeile angezeigt werden, wenn die Daten länger als die Breite der Spalte ist. Weitere Informationen zu diesen Einstellungen finden Sie unter [allgemeinen Konfigurationseinstellungen definieren](./defining-common-configuration-features.md).

- Legt fest, der Objekte, die von keiner der Ansichten der formatierungs-Datei angezeigt werden können. Weitere Informationen zu diesen Sätzen (bezeichnet als *Auswahl legt*), finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

- Allgemeine Steuerelemente, die von allen Ansichten der formatierungs-Datei verwendet werden können. Steuerelemente bieten Ihnen eine präzisere Kontrolle auf wie die Daten angezeigt werden. Weitere Informationen zu Steuerelementen, finden Sie unter [Definieren von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

## <a name="formatting-views"></a>Formatieren von Ansichten

Formatierung Ansichten können Objekte in ein Tabellenformat, Listenformat, Breiten Format und das benutzerdefinierte Format anzeigen. Zum größten Teil, wird jede formatierungsdefinition durch eine Reihe von XML-Tags beschrieben, die die Ansicht beschreiben. Jede Ansicht enthält den Namen der Ansicht der Objekte, die die Sicht und die Elemente in der Ansicht, z. B. die Spalten- und Informationen für eine Tabellenansicht verwenden.

Sehen Sie Listen die Eigenschaften eines Objekts oder einem Skript Block-Wert in einer oder mehreren Spalten der Tabelle. Jede Spalte stellt eine einzelne Eigenschaft eines Objekts oder einen Skriptwert dar. Sie können eine Tabellenansicht definieren, die alle Eigenschaften eines Objekts, das eine Teilmenge der Eigenschaften eines Objekts oder eine Kombination von Eigenschaften und Skriptwerte anzeigt. Jede Zeile der Tabelle stellt dar, ein zurückgegebenes Objekt. Erstellen eine Tabellenansicht ist sehr ähnlich, wenn Sie ein Objekt, das über die Pipeline die `Format-Table` Cmdlet. Weitere Informationen zu dieser Ansicht finden Sie unter [Tabellenansicht](./creating-a-table-view.md).

Liste Ansicht enthält die Eigenschaften eines Objekts oder einen Skriptwert in einer einzelnen Spalte an. Jede Zeile der Liste zeigt eine optionale Bezeichnung oder den Eigenschaftennamen, gefolgt von den Wert der Eigenschaft oder des Skripts. Erstellen einer Listenansicht ist sehr ähnlich, übergeben ein Objekt, das `Format-List` Cmdlet. Weitere Informationen zu dieser Ansicht finden Sie unter [Listenansicht](./creating-a-list-view.md).

Breite Ansicht enthält eine einzelne Eigenschaft eines Objekts oder ein Skriptwert in einer oder mehreren Spalten. Es gibt keine Bezeichnung oder Header für diese Sicht. Erstellen eine Breite Ansicht ist sehr ähnlich, übergeben ein Objekt, das `Format-Wide` Cmdlet. Weitere Informationen zu dieser Ansicht finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).

Benutzerdefinierte Ansicht zeigt eine anpassbare Ansicht der Objekteigenschaften oder Skriptwerte, die die starre Struktur der Tabellenansichten, Listenansichten oder breiten Ansichten nicht entspricht. Sie können eine eigenständige benutzerdefinierte Ansicht definieren, oder Sie können definieren, eine benutzerdefinierte Ansicht, die von einer anderen Ansicht, z. B. eine Tabelle oder Ansicht verwendet wird. Erstellen einer benutzerdefinierten Ansicht ist sehr ähnlich, übergeben ein Objekt, das `Format-Custom` Cmdlet. Weitere Informationen zu dieser Ansicht finden Sie unter [benutzerdefinierte Sicht](./creating-custom-controls.md).

## <a name="components-of-a-view"></a>Komponenten einer Ansicht

Die folgenden XML-Beispiele zeigen die grundlegenden XML-Komponenten einer Ansicht. Die einzelnen XML-Elemente variieren, je nachdem welche, die Ansicht Sie erstellen möchten, aber die grundlegenden Komponenten der Ansichten sind alle identisch.

Zu Beginn jeder Ansicht ist eine `Name` Element, das einen benutzerfreundlichen Namen, die verwendet wird angibt, um die Sicht verweisen. eine `ViewSelectedBy` Element, das definiert, welche .NET Objekte von der Ansicht angezeigt werden und ein *Steuerelement* -Element, das die Sicht definiert.

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

Sie können in das Steuerelement definieren, eine oder mehrere *Eintrag* Elemente. Wenn Sie mehrere Definitionen verwenden, müssen Sie angeben, welche Objekte .NET jede Definition verwenden. In der Regel wird nur ein Eintrag, mit der nur eine Definition für jedes Steuerelement benötigt.

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

Innerhalb jeder Entry-Element, einer Sicht werden soll, geben Sie die *Element* Elemente, die definieren, die Eigenschaften von .NET oder Skripts, die von dieser Sicht angezeigt werden.

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

Wie in den vorherigen Beispielen gezeigt, die Formatierungsdatei kann mehrere Sichten enthalten, eine Ansicht kann mehrere Definitionen enthalten, und jede Definition kann mehrere Elemente enthalten.

## <a name="example-of-a-table-view"></a>Beispiel für eine Tabellenansicht

Das folgende Beispiel zeigt die XML-Tags verwendet, um eine Tabellenansicht zu definieren, die zwei Spalten enthält. Die [ViewDefinitions](./viewdefinitions-element-format.md) Element ist das Containerelement für alle Ansichten in der Formatierungsdatei definiert. Die [Ansicht](./view-element-format.md) -Element definiert, die bestimmte Tabelle, Liste, Breite oder benutzerdefinierte Ansicht. In jedem [Ansicht](./view-element-format.md) -Element, die [Name](./name-element-for-view-format.md) Element gibt den Namen der Ansicht der [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht und die verschiedenen verwenden Elemente (z. B. die `TableControl` -Element wird im folgenden Beispiel gezeigt) definieren Sie den Typ der Ansicht.

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

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md)

[Schreiben eine PowerShell-Formatierung und Typendatei](./writing-a-powershell-formatting-file.md)
