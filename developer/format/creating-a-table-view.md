---
title: Erstellen eine Tabellensicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 832527ea4b042812c39934cd7e124201c6dc2ea4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861496"
---
# <a name="creating-a-table-view"></a>Erstellen einer Tabellenansicht

Eine Tabellenansicht zeigt Daten in einer oder mehreren Spalten. Jede Zeile in der Tabelle darstellt, ein, und jede Spalte der Tabelle steht für eine Eigenschaft des Objekts oder ein Skriptwert. Sie können eine Tabellenansicht definieren, die alle Eigenschaften eines Objekts oder einer Teilmenge der Eigenschaften eines Objekts anzeigt.

## <a name="a-table-view-display"></a>Anzeige einer Tabelle

Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) von zurückgegebene Objekt der [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet. Für dieses Objekt wurde Windows PowerShell definiert eine Tabellenansicht, das anzeigt der `Status` -Eigenschaft, die `Name` Eigenschaft (diese Eigenschaft ist ein aliaseigenschaft für die `ServiceName` Eigenschaft), und die `DisplayName` Eigenschaft. Jede Zeile in der Tabelle stellt ein vom Cmdlet zurückgegebenes Objekt dar.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>Definieren der Tabellenansicht

Das folgende XML zeigt das Schema der Ansicht zum Anzeigen der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekt. Sie müssen jede Eigenschaft angeben, die in der Tabellenansicht angezeigt werden soll.

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

Die folgende XML-Elemente werden verwendet, um eine Ansicht zu definieren:

- Die [Ansicht](./view-element-format.md) Element ist das übergeordnete Element der Tabellenansicht. (Dies ist das über dasselbe übergeordnete Element der Liste, Breite und benutzerdefinierte Steuerelementansicht.)

- Die [Namen](./name-element-for-view-format.md) Element gibt den Namen der Ansicht. Dieses Element ist für alle Ansichten erforderlich.

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht zu verwenden. Dieses Element ist erforderlich.

- Die [GroupBy](./groupby-element-for-view-format.md) -Element (nicht in diesem Beispiel dargestellt) definiert, wenn eine neue Gruppe von Objekten angezeigt wird. Eine neue Gruppe wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts. Dieses Element ist optional.

- Die [Steuerelemente](./controls-element-for-view-format.md) -Element (nicht in diesem Beispiel dargestellt) definiert die benutzerdefinierten Steuerelemente, die von der Tabellenansicht definiert sind. Steuerelemente bieten Ihnen eine Möglichkeit, festzulegen, wie die Daten angezeigt werden. Dieses Element ist optional. Eine Ansicht kann eine eigene benutzerdefinierte Steuerelemente zu definieren, oder sie können allgemeine Steuerelemente, die von einer beliebigen Ansicht in der Formatierungsdatei verwendet werden können. Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

- Die [HideTableHeaders](./hidetableheaders-element-format.md) Element (nicht mehr anzeigen in diesem Beispiel) gibt an, dass die Tabelle keine Bezeichnungen am oberen Rand der Tabelle nicht angezeigt wird. Dieses Element ist optional.

- Die [TableControl](./tablecontrol-element-format.md) Element, das Informationen für den Kopf- und die Zeile der Tabelle definiert. Ähnlich wie bei allen anderen Ansichten, kann eine Tabellenansicht die Werte der Objekteigenschaften oder von Skripts generierte Werte anzeigen.

## <a name="defining-column-headers"></a>Definieren von Spaltenüberschriften

1. Die [TableHeaders](./tableheaders-element-format.md) -Element und seine untergeordneten Elemente definieren, was am oberen Rand der Tabelle angezeigt wird.

2. Die [TableColumnHeader](./tablecolumnheader-element-format.md) -Element definiert, was am oberen Rand einer Spalte der Tabelle angezeigt wird. Geben Sie diese Elemente in der Reihenfolge, in den Headern, die angezeigt werden sollen.

   Es gibt keine Beschränkung der Anzahl von diesen-Element, das Sie verwenden können, aber die Anzahl der [TableColumnHeader](./tablecolumnheader-element-format.md) Elemente in der Tabellenansicht müssen gleich der Anzahl der [TableRowEntry](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md) Elemente, die Sie verwenden.

3. Die [Bezeichnung](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) Element gibt den Text, der angezeigt wird. Dieses Element ist optional.

4. Die [Breite](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) Element gibt die Breite (in Zeichen) der Spalte an. Dieses Element ist optional.

5. Die [Ausrichtung](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) -Element gibt an, wie die Bezeichnung angezeigt wird. Die Bezeichnung kann auf der linken Seite nach rechts ausgerichtet werden oder zentriert. Dieses Element ist optional.

## <a name="defining-the-table-rows"></a>Definieren die Zeilen der Tabelle

Tabellenansichten bieten eine oder mehrere Definitionen an, die angeben, welche Daten in den Zeilen der Tabelle angezeigt werden, die untergeordneten Elemente mit den [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) Element. Beachten Sie, dass Sie können mehrere Definitionen für die Zeilen der Tabelle angeben, die Header für die Zeilen bleibt jedoch gleich, unabhängig davon, welche Zeilendefinition verwendet wird. In der Regel wird eine Tabelle nur eine Definition enthalten.

Im folgenden Beispiel die Ansicht bietet eine einzige Definition, die den Werten verschiedener Eigenschaften der an die ["System.Diagnostics.Process"? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) Objekt. Eine Tabellenansicht kann den Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel gezeigt) in seinen Zeilen anzeigen.

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

Die folgende XML-Elemente können verwendet werden, um Definitionen für eine Zeile bereitzustellen:

- Die [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) -Element und seine untergeordneten Elemente definieren, was in den Zeilen der Tabelle angezeigt wird.

- Die [TableRowEntry](./listentry-element-for-listcontrol-format.md) Element enthält eine Definition der Zeile. Mindestens ein [TableRowEntry](./listentry-element-for-listcontrol-format.md) ist erforderlich; Es ist jedoch nicht begrenzt auf die Anzahl der Elemente, die Sie hinzufügen können. In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.

- Die [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Element gibt an, die Objekte, die von einer bestimmten Definition angezeigt werden. Dieses Element ist optional und ist nur erforderlich, wenn Sie mehrere definieren [TableRowEntry](./listentry-element-for-listcontrol-format.md) Elemente, die verschiedene Objekte anzeigen.

- Die [umschließen](./wrap-element-for-tablerowentry-for-tablecontrl-format.md) Element gibt an, dass Text, der die Spaltenbreite überschreitet, die in der nächsten Zeile angezeigt wird. Standardmäßig wird Text, der die Spaltenbreite überschreitet, abgeschnitten.

- Die [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) -Element definiert die Eigenschaften oder Skripts, deren Werte werden in der Zeile angezeigt.

- Die [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird. Ein [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Element ist erforderlich für jede Spalte der Zeile. Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.

- Die [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt die Eigenschaft, deren Wert in der Zeile angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.

- Die ["scriptblock"](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

- Die [FormatString](./label-element-for-listitem-for-listcontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird. Dieses Element ist optional.

- Die [Ausrichtung](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) -Element gibt an, wie der Wert der Eigenschaft oder des Skripts angezeigt wird. Der Wert kann auf der linken Seite nach rechts ausgerichtet werden oder zentriert. Dieses Element ist optional.

## <a name="defining-the-objects-that-use-the-table-view"></a>Definieren die Objekte, mit denen die Tabellenansicht

Es gibt zwei Möglichkeiten, die definieren, welche .NET Objekte die Tabellenansicht verwenden. Können Sie die [ViewSelectedBy](./viewselectedby-element-format.md) Element, das die Objekte zu definieren, die durch alle Definitionen oder der Ansicht angezeigt werden können. die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element zum definieren, welche Objekte angezeigt werden ein spezifische Definition der Sicht. In den meisten Fällen eine Ansicht hat nur eine Definition, sodass Objekte in der Regel, indem definiert werden die [ViewSelectedBy](./viewselectedby-element-format.md) Element.

Das folgende Beispiel zeigt, wie Sie die Objekte zu definieren, die von der Ansicht mit Tabelle angezeigt werden die [ViewSelectedBy](./viewselectedby-element-format.md) und [TypeName](./typename-element-for-viewselectedby-format.md) Elemente. Es gibt keine Beschränkung der Anzahl der [TypeName](./typename-element-for-viewselectedby-format.md) Elementen, die Sie angeben können und ihre Reihenfolge ist nicht von Bedeutung.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Tabellenansicht verwendet werden:

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Die [TypeName](./typename-element-for-viewselectedby-format.md) -Element gibt an, das .NET-Objekt, das von der Ansicht angezeigt wird. Der vollqualifizierte Typname des .NET ist erforderlich. Geben Sie mindestens einen Typ oder Auswahl für die Ansicht festgelegt, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

Im folgenden Beispiel wird die [ViewSelectedBy](./viewselectedby-element-format.md) und [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Elemente. Verwenden Sie die Auswahl legt, haben eine zusammengehörige Gruppe von Objekten, die über mehrere Ansichten, z. B. Wenn Sie eine Listenansicht definieren und eine Tabellenansicht für diese Objekte angezeigt werden. Weitere Informationen dazu, wie Sie einen Auswahlsatz zu erstellen, finden Sie unter [definieren Auswahl legt](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Listenansicht verwendet werden:

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element gibt einen Satz von Objekten, die von der Ansicht angezeigt werden können. Geben Sie mindestens einen Auswahlsatz oder Typ, für die Sicht, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

Das folgende Beispiel zeigt, wie Sie die Objekte angezeigt, die von einer bestimmten Definition der Ansicht mit Tabelle definieren die [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Element. Verwenden dieses Element, können Sie den Namen des Objekts, einer Auswahlsatz von Objekten oder eine auswahlbedingung, die angibt, wenn die Definition verwendet wird angeben. Weitere Informationen dazu, wie Sie eine Auswahl Bedingungen zu erstellen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

> [!NOTE]
> Wenn Sie mehrere Definitionen der Tabellenansicht erstellen angeben nicht unterschiedliche Spaltenüberschriften. Sie können angeben, nur Anzeige in den Zeilen der Tabelle aus, wie z. B., welche Objekte angezeigt werden.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

Die folgende XML-Elemente können verwendet werden, die Objekte an, die von einer bestimmten Definition der Listenansicht verwendet werden:

- Die [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) Element definiert, welche Objekte durch die Definition angezeigt werden.

- Die [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt an, das .NET-Objekt, das durch die Definition angezeigt wird. Wenn Sie dieses Element zu verwenden, ist der vollqualifizierte Typname des .NET erforderlich. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

- Die [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt einen Satz von Objekten, die von dieser Definition angezeigt werden können. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

- Die [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt an, eine Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können. Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="using-format-strings"></a>Verwenden von Formatzeichenfolgen

Formatieren von Zeichenfolgen können hinzugefügt werden, zu einer Ansicht genauer definieren, wie die Daten angezeigt werden. Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

Die folgende XML-Elemente können verwendet werden, ein Formatmuster angeben:

- Die [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird. Ein [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Element ist erforderlich für jede Spalte der Zeile. Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.

- Die [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt die Eigenschaft, deren Wert in der Zeile angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.

- Die [FormatString](./label-element-for-listitem-for-listcontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird.

Im folgenden Beispiel die `ToString` aufgerufen, um den Wert des Skripts zu formatieren. Skripts können auf jede Methode eines Objekts aufrufen. Daher verfügt ein Objekt eine Methode, wie z. B. `ToString`über Formatierung Parameter verfügt, das Skript kann diese Methode zum Formatieren des Werts der Ausgabe des Skripts aufzurufen.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Das folgende XML-Element kann zum Aufrufen der `ToString` Methode:

- Die [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Spalte der Zeile angezeigt wird. Ein [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) Element ist erforderlich für jede Spalte der Zeile. Der erste Eintrag wird in der ersten Spalte und der zweite Eintrag in der zweiten Spalte und So weiter.

- Die ["scriptblock"](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
