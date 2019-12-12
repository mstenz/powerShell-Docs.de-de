---
title: Erstellen einer breiten Ansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368949"
---
# <a name="creating-a-wide-view"></a>Erstellen einer breiten Ansicht

Eine breite Ansicht zeigt einen einzelnen Wert für jedes angezeigte Objekt an. Der angezeigte Wert kann der Wert einer .NET-Objekt Eigenschaft oder der Wert eines Skripts sein. Standardmäßig gibt es für diese Ansicht keine Bezeichnung oder einen Header.

## <a name="a-wide-view-display"></a>Eine breite Anzeige Ansicht

Das folgende Beispiel zeigt, wie Windows PowerShell das [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekt anzeigt, das vom Cmdlet " [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) " zurückgegeben wird, wenn die Ausgabe an das Cmdlet " [Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) " weitergeleitet wird. (Standardmäßig gibt das [Get-Process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet eine Tabellenansicht zurück.) In diesem Beispiel werden die beiden Spalten verwendet, um den Namen des Prozesses für jedes zurückgegebene Objekt anzuzeigen. Der Name der Eigenschaft des Objekts wird nicht angezeigt, sondern nur der Wert der Eigenschaft.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>Definieren der breiten Ansicht

Der folgende XML-Code zeigt das breite Ansichts Schema für das [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekt.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

Die folgenden XML-Elemente werden zum Definieren einer breiten Ansicht verwendet:

- Das [View](./view-element-format.md) -Element ist das übergeordnete Element der breiten Ansicht. (Dies ist dasselbe übergeordnete Element für die Tabellen-, Listen-und benutzerdefinierten Steuerelement Sichten.)

- Das [Name](./name-element-for-view-format.md) -Element gibt den Namen der Ansicht an. Dieses Element ist für alle Sichten erforderlich.

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht verwenden. Dieses Element ist erforderlich.

- Das [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wann eine neue Gruppe von Objekten angezeigt wird. Eine neue Gruppe wird immer dann gestartet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird. Dieses Element ist optional.

- Die [Steuerelemente der](./controls-element-for-view-format.md) Steuerelemente definieren die benutzerdefinierten Steuerelemente, die von der breiten Ansicht definiert werden. Steuerelemente geben Ihnen eine Möglichkeit, die Anzeige der Daten weiter anzugeben. Dieses Element ist optional. Eine Sicht kann eigene benutzerdefinierte Steuerelemente definieren, oder Sie kann allgemeine Steuerelemente verwenden, die von jeder Ansicht in der Formatierungs Datei verwendet werden können. Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

- Das [widecontrol](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird. Im vorherigen Beispiel wurde die-Sicht entworfen, um die [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) -Eigenschaft anzuzeigen.

Ein Beispiel für eine komplette Formatierungs Datei, die eine einfache Breite Ansicht definiert, finden Sie unter [Wide View (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Bereitstellen von Definitionen für Ihre breite Ansicht

Breite Ansichten können mithilfe der untergeordneten Elemente des [widecontrol](./widecontrol-element-format.md) -Elements eine oder mehrere Definitionen bereitstellen. In der Regel hat eine Ansicht nur eine Definition. Im folgenden Beispiel stellt die Sicht eine einzelne Definition bereit, in der der Wert der [System. Diagnostics. Process. ProcessName](/dotnet/api/System.Diagnostics.Process.ProcessName) -Eigenschaft angezeigt wird. In einer breiten Ansicht kann der Wert einer Eigenschaft oder der Wert eines Skripts angezeigt werden (nicht im Beispiel dargestellt).

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

Die folgenden XML-Elemente können verwendet werden, um Definitionen für eine breite Ansicht bereitzustellen:

- Das [widecontrol](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.

- Das [AutoSize](./autosize-element-for-widecontrol-format.md) -Element gibt an, ob die Spaltengröße und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden. Dieses Element ist optional.

- Das [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) -Element gibt die Anzahl der Spalten an, die in der breiten Ansicht angezeigt werden. Dieses Element ist optional.

- Das [wideentries](./wideentries-element-for-widecontrol-format.md) -Element stellt die Definitionen der Sicht bereit. In den meisten Fällen weist eine Ansicht nur eine Definition auf. Dieses Element ist erforderlich.

- Das [wideentry](./wideentry-element-for-widecontrol-format.md) -Element stellt eine Definition der Sicht bereit. Mindestens ein " [wideentry](./wideentry-element-for-widecontrol-format.md) " ist erforderlich. Es gibt jedoch keine maximale Beschränkung für die Anzahl der Elemente, die Sie hinzufügen können. In den meisten Fällen weist eine Ansicht nur eine Definition auf.

- Das [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Element gibt die Objekte an, die von einer bestimmten Definition angezeigt werden. Dieses Element ist optional und nur erforderlich, wenn Sie mehrere [wideentry](./wideentry-element-for-widecontrol-format.md) -Elemente definieren, die verschiedene-Objekte anzeigen.

- Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden. Im Gegensatz zu anderen Sicht Typen kann ein breites Steuerelement nur ein Element anzeigen.

- Das [propertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) -Element gibt die Eigenschaft an, deren Wert von der Sicht angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.

- Das [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -Element gibt das Skript an, dessen Wert von der Sicht angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

- Das [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) -Element gibt ein Muster an, das zum Anzeigen der Daten verwendet wird. Dieses Element ist optional.

Ein Beispiel für eine komplette Formatierungs Datei, die eine breite Sicht Definition definiert, finden Sie unter [Wide View (Basic)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definieren der Objekte, die die Breite Ansicht verwenden

Es gibt zwei Möglichkeiten, um zu definieren, welche .NET-Objekte die Breite Ansicht verwenden. Sie können das [viewselectedby](./viewselectedby-element-format.md) -Element verwenden, um die Objekte zu definieren, die von allen Definitionen der Sicht angezeigt werden können, oder Sie können das [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Element verwenden, um zu definieren, welche Objekte von einer bestimmten Definition der Sicht angezeigt werden. In den meisten Fällen verfügt eine Sicht nur über eine Definition, sodass Objekte normalerweise durch das [viewselectedby](./viewselectedby-element-format.md) -Element definiert werden.

Im folgenden Beispiel wird gezeigt, wie die-Objekte definiert werden, die von der breiten Ansicht mithilfe der Elemente [viewselectedby](./viewselectedby-element-format.md) und [tygtame](./typename-element-for-viewselectedby-format.md) angezeigt werden. Es gibt keine Beschränkung für die Anzahl der [tyname](./typename-element-for-viewselectedby-format.md) -Elemente, die Sie angeben können, und ihre Reihenfolge ist nicht signifikant.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der breiten Ansicht verwendet werden:

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.

- Das [tygtame](./typename-element-for-viewselectedby-format.md) -Element gibt das von der Sicht angezeigte .net an. Der voll qualifizierte .net-Typname ist erforderlich. Sie müssen mindestens einen Typ oder einen Auswahl Satz für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

Ein Beispiel für eine komplette Formatierungs Datei finden Sie unter [Wide View (Basic)](./wide-view-basic.md).

Im folgenden Beispiel werden die Elemente [viewselectedby](./viewselectedby-element-format.md) und [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) verwendet. Verwenden Sie Auswahl Sätze, bei denen Sie über einen zugehörigen Satz von Objekten verfügen, die mithilfe mehrerer Sichten angezeigt werden, z. b. Wenn Sie eine breite Ansicht und eine Tabellenansicht für dieselben Objekte definieren. Weitere Informationen zum Erstellen eines Auswahl Satzes finden Sie unter Definieren von [Auswahl Sätzen](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der breiten Ansicht verwendet werden:

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.

- Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element gibt eine Gruppe von-Objekten an, die von der Sicht angezeigt werden können. Sie müssen mindestens einen Auswahl Satz oder-Typ für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

Im folgenden Beispiel wird gezeigt, wie die-Objekte, die durch eine bestimmte Definition der breiten Ansicht angezeigt werden, mithilfe des [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Elements definiert werden. Mit diesem Element können Sie den .NET-Typnamen des Objekts, einen Auswahl Satz von Objekten oder eine Auswahlbedingung angeben, die angibt, wann die Definition verwendet wird. Weitere Informationen zum Erstellen von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von einer bestimmten Definition der breiten Ansicht verwendet werden:

- Das [entryselectedby](./entryselectedby-element-for-wideentry-format.md) -Element definiert, welche Objekte von der Definition angezeigt werden.

- Das [tykame](./typename-element-for-viewselectedby-format.md) -Element gibt das .net an, das von der Definition angezeigt wird. Wenn Sie dieses Element verwenden, ist der voll qualifizierte .net-Typname erforderlich. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

- Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element (nicht angezeigt) gibt eine Gruppe von Objekten an, die von dieser Definition angezeigt werden können. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

- Das [selectioncondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) -Element (nicht angezeigt) gibt eine Bedingung an, die vorhanden sein muss, damit diese Definition verwendet werden muss. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können. Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Anzeigen von Gruppen von Objekten in einer breiten Ansicht

Sie können die Objekte, die von der breiten Ansicht angezeigt werden, in Gruppen aufteilen. Dies bedeutet nicht, dass Sie eine Gruppe definieren, sondern nur, dass Windows PowerShell eine neue Gruppe startet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird. Im folgenden Beispiel wird eine neue Gruppe immer dann gestartet, wenn sich der Wert der [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) -Eigenschaft ändert.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Die folgenden XML-Elemente werden verwendet, um zu definieren, wann eine Gruppe gestartet wird:

- Das [GroupBy](./groupby-element-for-view-format.md) -Element definiert die Eigenschaft oder das Skript, das die neue Gruppe startet und definiert, wie die Gruppe angezeigt wird.

- Das [propertyName](./propertyname-element-for-groupby-format.md) -Element gibt die Eigenschaft an, die eine neue Gruppe startet, wenn sich der Wert ändert. Sie müssen eine Eigenschaft oder ein Skript angeben, um die Gruppe zu starten, aber Sie können nicht beides angeben.

- Das [ScriptBlock](./scriptblock-element-for-groupby-format.md) -Element gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert. Sie müssen ein Skript oder eine Eigenschaft angeben, um die Gruppe zu starten, aber Sie können nicht beides angeben.

- Das [Label](./label-element-for-groupby-format.md) -Element definiert eine Bezeichnung, die am Anfang jeder Gruppe angezeigt wird. Zusätzlich zu dem Text, der von diesem Element angegeben wird, zeigt Windows PowerShell den Wert an, der die neue Gruppe ausgelöst hat, und fügt vor und nach der Bezeichnung eine leere Zeile hinzu. Dieses Element ist optional.

- Das [CustomControl](./customcontrol-element-for-groupby-format.md) -Element definiert ein Steuerelement, das zum Anzeigen der Daten verwendet wird. Dieses Element ist optional.

- Das [customcontrolname](./customcontrolname-element-for-groupby-format.md) -Element gibt ein Common-oder View-Steuerelement an, das zum Anzeigen der Daten verwendet wird. Dieses Element ist optional.

Ein Beispiel für eine komplette Formatierungs Datei, die Gruppen definiert, finden Sie unter [Wide View (GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Using-Format

Formatierungs Zeichenfolgen können einer breiten Ansicht hinzugefügt werden, um die Anzeige der Daten weiter zu definieren. Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Die folgenden XML-Elemente können verwendet werden, um ein Format Muster anzugeben:

- Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.

- Das [propertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) -Element gibt die Eigenschaft an, deren Wert von der Sicht angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.

- Das Format [String](./formatstring-element-for-wideitem-for-widecontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.

- Das [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

Im folgenden Beispiel wird die `ToString`-Methode aufgerufen, um den Wert des Skripts zu formatieren. Skripts können beliebige Methoden eines Objekts aufzurufen. Wenn ein Objekt z. b. über eine-Methode verfügt, z. b. `ToString`, die über Formatierungs Parameter verfügt, kann das Skript diese Methode zum Formatieren des Ausgabe Werts des Skripts aufruft.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

Das folgende XML-Element kann verwendet werden, um die `ToString`-Methode aufrufen:

- Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.

- Das [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Breite Ansicht (Basic)](./wide-view-basic.md)

[Breite Ansicht (GroupBy)](./wide-view-groupby.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
