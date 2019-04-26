---
title: Benutzerdefinierte Formatierung von Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068299"
---
# <a name="custom-formatting-files"></a>Benutzerdefinierte Formatierungsdateien

Das Anzeigeformat für die von Cmdlets, Funktionen und Skripts zurückgegebenen Objekte werden mithilfe von Formatierungsdateien (Format. ps1xml-Dateien) definiert. Einige dieser Dateien werden von Windows PowerShell zum Definieren von des Standardanzeigeformat für diejenigen Objekte zurückgegeben, die von Windows PowerShell-Cmdlets bereitgestellt. Sie können jedoch auch eigene benutzerdefinierte Formatierungsdateien die Standardformate für die Anzeige überschrieben oder die Anzeige von Objekten zurückgegeben, die durch Ihre eigenen Befehle definieren, erstellen.

Windows PowerShell verwendet die Daten in diese Formatierungsdateien, um zu bestimmen, was angezeigt wird und wie die Daten formatiert werden. Die angezeigten Daten zählen die Eigenschaften eines Objekts oder der Wert eines Skriptblocks.  Skriptblöcke werden verwendet, wenn einen Wert, der nicht direkt über die Eigenschaften eines Objekts verfügbar ist, angezeigt werden soll. Beispielsweise empfiehlt es sich, fügen Sie den Wert von zwei Eigenschaften eines Objekts und die Summe wird als ein separater Teil der Daten angezeigt. Wenn Sie eine eigene Formatierung-Datei schreiben, müssen Sie definieren *Ansichten* für die Objekte, die Sie anzeigen möchten. Sie können eine einzelne Ansicht für jedes Objekt definieren, können Sie eine einzelne Ansicht für mehrere Objekte definieren oder Sie können mehrere Ansichten für das gleiche Objekt definieren. Es gibt keine Beschränkung für die Anzahl der Aufrufe, die Sie definieren können.

> [!IMPORTANT]
> Formatierungsdateien sind die Elemente eines Objekts nicht bestimmt werden, die an die Pipeline zurückgegeben werden. Wenn ein Objekt an die Pipeline zurückgegeben wird, sind alle Member des Objekts verfügbar.

## <a name="format-views"></a>Formatieren von Ansichten

Formatierung Ansichten können Objekte in ein Tabellenformat, einer Liste an, einen breiten Format und ein benutzerdefiniertes Format anzeigen. Zum größten Teil, wird jede formatierungsdefinition durch eine Reihe von XML-Tags beschrieben, die eine Ansicht zu beschreiben. Jede Ansicht enthält den Namen der Ansicht der Objekte, die die Sicht und die Elemente in der Ansicht, z. B. die Spalten- und Informationen für eine Tabellenansicht verwenden.

Die folgenden Ansichten sind verfügbar.

Tabellenansicht werden die Eigenschaften eines Objekts oder einem Skript Block-Wert in einer oder mehreren Spalten aufgelistet. Jede Spalte stellt eine Eigenschaft des Objekts oder einen scriptblockwert Skript dar. Sie können eine Tabellenansicht definieren, die alle Eigenschaften eines Objekts, das eine Teilmenge der Eigenschaften eines Objekts oder eine Kombination von Eigenschaften und Werte der Skript-Block wird angezeigt. Jede Zeile der Tabelle stellt dar, ein zurückgegebenes Objekt. Weitere Informationen zu dieser Ansicht finden Sie unter [Tabellenansicht](../format/creating-a-table-view.md).

Listenansicht sind die Eigenschaften eines Objekts oder einer Skript-Block-Wert in einer einzelnen Spalte aufgelistet. Jede Zeile der Liste zeigt eine optionale Bezeichnung oder den Eigenschaftennamen, gefolgt von den Wert des Blocks-Eigenschaft oder ein Skript. Weitere Informationen zu dieser Ansicht finden Sie unter [Listenansicht](../format/creating-a-list-view.md).

Breite Ansicht enthält eine einzelne Eigenschaft eines Objekts oder einem Skript Block-Wert in einer oder mehreren Spalten. Es gibt keine Bezeichnung oder Header für diese Sicht. Weitere Informationen zu dieser Ansicht finden Sie unter [Breite Ansicht](../format/creating-a-wide-view.md).

Benutzerdefinierte Ansicht zeigt eine anpassbare Ansicht der Objekteigenschaften oder Skriptwerte-Block, die die starre Struktur der Tabellenansichten, Listenansichten oder breiten Ansichten nicht entspricht. Sie können eine eigenständige benutzerdefinierte Ansicht definieren, oder Sie können definieren, eine benutzerdefinierte Ansicht, die von einer anderen Ansicht, z. B. eine Tabelle oder Ansicht verwendet wird. Weitere Informationen zu dieser Ansicht finden Sie unter [benutzerdefinierte Sicht](../format/creating-custom-controls.md).

## <a name="view-xml-elements"></a>Die XML-Elemente anzeigen

Das folgende Beispiel zeigt die XML-Tags verwendet, um eine Tabellenansicht zu definieren, die zwei Spalten enthält. Die [ViewDefinitions](../format/viewdefinitions-element-format.md) Element ist das Containerelement für alle Ansichten in der Formatierungsdatei definiert. Die [Ansicht](../format/view-element-format.md) -Element definiert, die bestimmte Tabelle, Liste, Breite oder benutzerdefinierte Ansicht. In jeder Ansicht der [Namen](../format/name-element-for-view-format.md) Element gibt den Namen der Ansicht der [ViewSelectedBy](../format/viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht und die verschiedenen Steuerelemente verwenden (z. B. die `TableControl` -Element) definieren Sie das Format der Ansicht.

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
