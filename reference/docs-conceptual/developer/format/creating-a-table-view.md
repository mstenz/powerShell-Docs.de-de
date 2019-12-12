---
title: Erstellen einer Tabellenansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363409"
---
# <a name="creating-a-table-view"></a>Erstellen einer Tabellenansicht

Eine Tabellen Sicht zeigt Daten in einer oder mehreren Spalten an. Jede Zeile in der Tabelle stellt ein .NET-Objekt dar, und jede Spalte der Tabelle stellt eine Eigenschaft des Objekts oder einen Skript Wert dar. Sie können eine Tabellen Sicht definieren, in der alle Eigenschaften eines Objekts oder eine Teilmenge der Eigenschaften eines Objekts angezeigt werden.

## <a name="a-table-view-display"></a>Anzeige der Tabellenansicht

Das folgende Beispiel zeigt, wie Windows PowerShell das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt anzeigt, das vom Cmdlet " [Get-Service](/powershell/module/microsoft.powershell.management/get-service) " zurückgegeben wird. Für dieses Objekt hat Windows PowerShell eine Tabellen Sicht definiert, in der die `Status`-Eigenschaft, die `Name`-Eigenschaft (diese Eigenschaft ist eine Alias Eigenschaft für die `ServiceName`-Eigenschaft) und die `DisplayName`-Eigenschaft angezeigt werden. Jede Zeile in der Tabelle stellt ein vom Cmdlet zurück gegebenes Objekt dar.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definieren der Tabellenansicht

Der folgende XML-Code zeigt das Tabellen Ansichts Schema zum Anzeigen von [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt. Sie müssen jede Eigenschaft angeben, die in der Tabellenansicht angezeigt werden soll.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

Die folgenden XML-Elemente werden verwendet, um eine Listenansicht zu definieren:

- Das [View](./view-element-format.md) -Element ist das übergeordnete Element der Tabellen Sicht. (Dies ist dasselbe übergeordnete Element für die Listen-, Wide-und Custom-Steuerelement Sichten.)

- Das [Name](./name-element-for-view-format.md) -Element gibt den Namen der Ansicht an. Dieses Element ist für alle Sichten erforderlich.

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht verwenden. Dieses Element ist erforderlich.

- Das [GroupBy](./groupby-element-for-view-format.md) -Element (in diesem Beispiel nicht gezeigt) definiert, wann eine neue Gruppe von Objekten angezeigt wird. Eine neue Gruppe wird immer dann gestartet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird. Dieses Element ist optional.

- Das [Controls](./controls-element-for-view-format.md) -Element (in diesem Beispiel nicht gezeigt) definiert die benutzerdefinierten Steuerelemente, die von der Tabellenansicht definiert werden. Steuerelemente geben Ihnen eine Möglichkeit, die Anzeige der Daten weiter anzugeben. Dieses Element ist optional. Eine Sicht kann eigene benutzerdefinierte Steuerelemente definieren, oder Sie kann allgemeine Steuerelemente verwenden, die von jeder Ansicht in der Formatierungs Datei verwendet werden können. Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

- Das [hidetableheaders](./hidetableheaders-element-format.md) -Element (in diesem Beispiel nicht angezeigt) gibt an, dass in der Tabelle keine Bezeichnungen am Anfang der Tabelle angezeigt werden. Dieses Element ist optional.

- Das [tablecontrol](./tablecontrol-element-format.md) -Element, das die Header-und Zeilen Informationen der Tabelle definiert. Ähnlich wie alle anderen Sichten kann eine Tabellenansicht die Werte der Objekteigenschaften oder von Skripts generierten Werte anzeigen.

## <a name="defining-column-headers"></a>Definieren von Spalten Headern

1. Das [tableHeaders](./tableheaders-element-format.md) -Element und seine untergeordneten Elemente definieren, was am oberen Rand der Tabelle angezeigt wird.

2. Das [tablecolumnheader](./tablecolumnheader-element-format.md) -Element definiert, was oben in einer Spalte der Tabelle angezeigt wird. Geben Sie diese Elemente in der Reihenfolge an, in der die Header angezeigt werden sollen.

   Es gibt keine Beschränkung für die Anzahl dieser Elemente, die Sie verwenden können, aber die Anzahl der [tablecolumnheader](./tablecolumnheader-element-format.md) -Elemente in der Tabellenansicht muss der Anzahl der [tablerowentry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) -Elemente entsprechen, die Sie verwenden.

3. Das [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt den Text an, der angezeigt wird. Dieses Element ist optional.

4. Das [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt die Breite (in Zeichen) der Spalte an. Dieses Element ist optional.

5. Das [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt an, wie die Bezeichnung angezeigt wird. Die Bezeichnung kann Links, rechts oder zentriert ausgerichtet werden. Dieses Element ist optional.

## <a name="defining-the-table-rows"></a>Definieren der Tabellenzeilen

Tabellen Sichten können eine oder mehrere Definitionen bereitstellen, die angeben, welche Daten in den Zeilen der Tabelle angezeigt werden, indem die untergeordneten Elemente des [tablerowentries](./tablerowentries-element-for-tablecontrol-format.md) -Elements verwendet werden. Beachten Sie, dass Sie mehrere Definitionen für die Zeilen der Tabelle angeben können, die Header für die Zeilen jedoch unverändert bleiben, unabhängig davon, welche Zeilen Definition verwendet wird. In der Regel enthält eine Tabelle nur eine Definition.

Im folgenden Beispiel stellt die Sicht eine einzelne Definition bereit, in der die Werte mehrerer Eigenschaften von [System. Diagnostics. Process angezeigt werden? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -Objekt. In einer Tabellen Sicht kann der Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel) in den Zeilen angezeigt werden.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

Die folgenden XML-Elemente können verwendet werden, um Definitionen für eine Zeile bereitzustellen:

- Das [tablerowentries](./tablerowentries-element-for-tablecontrol-format.md) -Element und seine untergeordneten Elemente definieren, was in den Zeilen der Tabelle angezeigt wird.

- Das [tablerowentry](./listentry-element-for-listcontrol-format.md) -Element stellt eine Definition der Zeile bereit. Mindestens ein [tablerowentry](./listentry-element-for-listcontrol-format.md) ist erforderlich. Es gibt jedoch keine maximale Beschränkung für die Anzahl der Elemente, die Sie hinzufügen können. In den meisten Fällen weist eine Ansicht nur eine Definition auf.

- Das [entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -Element gibt die Objekte an, die von einer bestimmten Definition angezeigt werden. Dieses Element ist optional und wird nur benötigt, wenn Sie mehrere [tablerowentry](./listentry-element-for-listcontrol-format.md) -Elemente definieren, die verschiedene-Objekte anzeigen.

- Das [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) -Element gibt an, dass der Text, der die Spaltenbreite überschreitet, in der nächsten Zeile angezeigt wird. Standardmäßig wird Text, der die Spaltenbreite überschreitet, abgeschnitten.

- Das [tablecolumnitems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -Element definiert die Eigenschaften oder Skripts, deren Werte in der Zeile angezeigt werden.

- Das [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird. Für jede Spalte der Zeile ist ein [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element erforderlich. Der erste Eintrag wird in der ersten Spalte angezeigt, der zweite Eintrag in der zweiten Spalte usw.

- Das [propertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt die-Eigenschaft an, deren Wert in der Zeile angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.

- Das [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

- Das Format [String](./label-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert angezeigt wird. Dieses Element ist optional.

- Das [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt an, wie der Wert der Eigenschaft oder des Skripts angezeigt wird. Der Wert kann Links, rechts oder zentriert ausgerichtet werden. Dieses Element ist optional.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definieren der Objekte, die die Tabellenansicht verwenden

Es gibt zwei Möglichkeiten, um zu definieren, welche .NET-Objekte die Tabellenansicht verwenden. Sie können das [viewselectedby](./viewselectedby-element-format.md) -Element verwenden, um die Objekte zu definieren, die von allen Definitionen der Sicht angezeigt werden können, oder Sie können das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element verwenden, um zu definieren, welche Objekte von einer bestimmten Definition der Sicht angezeigt werden. In den meisten Fällen verfügt eine Sicht nur über eine Definition, sodass Objekte normalerweise durch das [viewselectedby](./viewselectedby-element-format.md) -Element definiert werden.

Im folgenden Beispiel wird gezeigt, wie die Objekte definiert werden, die von der Tabellenansicht mithilfe der Elemente [viewselectedby](./viewselectedby-element-format.md) und [tygtame](./typename-element-for-viewselectedby-format.md) angezeigt werden. Es gibt keine Beschränkung für die Anzahl der [tyname](./typename-element-for-viewselectedby-format.md) -Elemente, die Sie angeben können, und ihre Reihenfolge ist nicht signifikant.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Tabellenansicht verwendet werden:

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Das [tykame](./typename-element-for-viewselectedby-format.md) -Element gibt das .NET-Objekt an, das von der Sicht angezeigt wird. Der voll qualifizierte .net-Typname ist erforderlich. Sie müssen mindestens einen Typ oder einen Auswahl Satz für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

Im folgenden Beispiel werden die Elemente [viewselectedby](./viewselectedby-element-format.md) und [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) verwendet. Verwenden Sie Auswahl Sätze, bei denen Sie über einen zugehörigen Satz von Objekten verfügen, die mithilfe mehrerer Sichten angezeigt werden, z. b. Wenn Sie eine Listenansicht und eine Tabellenansicht für dieselben Objekte definieren. Weitere Informationen zum Erstellen eines Auswahl Satzes finden Sie unter Definieren von [Auswahl Sätzen](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Listenansicht verwendet werden:

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element gibt eine Gruppe von-Objekten an, die von der Sicht angezeigt werden können. Sie müssen mindestens einen Auswahl Satz oder-Typ für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

Im folgenden Beispiel wird gezeigt, wie die Objekte, die durch eine bestimmte Definition der Tabellenansicht angezeigt werden, mithilfe des [entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -Elements definiert werden. Mit diesem Element können Sie den .NET-Typnamen des Objekts, einen Auswahl Satz von Objekten oder eine Auswahlbedingung angeben, die angibt, wann die Definition verwendet wird. Weitere Informationen zum Erstellen von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Wenn Sie mehrere Definitionen der Tabellenansicht erstellen, können Sie keine anderen Spaltenheader angeben. Sie können nur angeben, was in den Zeilen der Tabelle angezeigt wird, z. b. welche Objekte angezeigt werden.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von einer bestimmten Definition der Listenansicht verwendet werden:

- Das [entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) -Element definiert, welche Objekte von der Definition angezeigt werden.

- Das [tykame](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt das .NET-Objekt an, das von der Definition angezeigt wird. Wenn Sie dieses Element verwenden, ist der voll qualifizierte .net-Typname erforderlich. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

- Das [selectionsetname](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Gruppe von Objekten an, die von dieser Definition angezeigt werden können. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

- Das [selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Bedingung an, die vorhanden sein muss, damit diese Definition verwendet werden muss. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können. Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Using-Format

Formatierungs Zeichenfolgen können einer Ansicht hinzugefügt werden, um die Anzeige der Daten weiter zu definieren. Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Die folgenden XML-Elemente können verwendet werden, um ein Format Muster anzugeben:

- Das [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird. Für jede Spalte der Zeile ist ein [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element erforderlich. Der erste Eintrag wird in der ersten Spalte angezeigt, der zweite Eintrag in der zweiten Spalte usw.

- Das [propertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt die-Eigenschaft an, deren Wert in der Zeile angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.

- Das Format [String](./label-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert angezeigt wird.

Im folgenden Beispiel wird die `ToString`-Methode aufgerufen, um den Wert des Skripts zu formatieren. Skripts können beliebige Methoden eines Objekts aufzurufen. Wenn ein Objekt z. b. über eine-Methode verfügt, z. b. `ToString`, die über Formatierungs Parameter verfügt, kann das Skript diese Methode zum Formatieren des Ausgabe Werts des Skripts aufruft.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Das folgende XML-Element kann verwendet werden, um die `ToString`-Methode aufrufen:

- Das [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder das Skript, dessen Wert in der Spalte der Zeile angezeigt wird. Für jede Spalte der Zeile ist ein [tablecolumnitem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element erforderlich. Der erste Eintrag wird in der ersten Spalte angezeigt, der zweite Eintrag in der zweiten Spalte usw.

- Das [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
