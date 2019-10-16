---
title: Erstellen einer Listenansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c7a40ca-1786-46f0-bab5-6ce229daa7ee
caps.latest.revision: 14
ms.openlocfilehash: 25d24063501196d44e0f806a55bb699c82f771ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368979"
---
# <a name="creating-a-list-view"></a>Erstellen einer Listenansicht

Eine Listenansicht zeigt Daten in einer einzelnen Spalte (in sequenzieller Reihenfolge) an. Bei den in der Liste angezeigten Daten kann es sich um den Wert einer .net-Eigenschaft oder den Wert eines Skripts handeln.

## <a name="a-list-view-display"></a>Eine Listen Ansichts Anzeige

Die folgende Ausgabe zeigt, wie die Eigenschaften von [System. ServiceProcess. ServiceController in Windows PowerShell angezeigt werden. Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, die vom Cmdlet " [Get-Service](/powershell/module/microsoft.powershell.management/get-service) " zurückgegeben werden. In diesem Beispiel wurden drei Objekte zurückgegeben, wobei jedes Objekt durch eine leere Zeile vom vorangehenden Objekt getrennt wurde.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>Definieren der Listenansicht

Der folgende XML-Code zeigt das Listen Ansichts Schema zum Anzeigen verschiedener Eigenschaften von [System. ServiceProcess. ServiceController? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt. Sie müssen jede Eigenschaft angeben, die in der Listenansicht angezeigt werden soll.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

Die folgenden XML-Elemente werden verwendet, um eine Listenansicht zu definieren:

- Das [View](./view-element-format.md) -Element ist das übergeordnete Element der Listenansicht. (Dies ist dasselbe übergeordnete Element für die Tabellen-, Wide-und Custom-Steuerelement Sichten.)

- Das [Name](./name-element-for-view-format.md) -Element gibt den Namen der Ansicht an. Dieses Element ist für alle Sichten erforderlich.

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Ansicht verwenden. Dieses Element ist erforderlich.

- Das [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wann eine neue Gruppe von Objekten angezeigt wird. Eine neue Gruppe wird immer dann gestartet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird. Dieses Element ist optional.

- Das [Controls](./controls-element-for-view-format.md) -Element definiert die benutzerdefinierten Steuerelemente, die von der Listenansicht definiert werden. Steuerelemente geben Ihnen eine Möglichkeit, die Anzeige der Daten weiter anzugeben. Dieses Element ist optional. Eine Sicht kann eigene benutzerdefinierte Steuerelemente definieren, oder Sie kann allgemeine Steuerelemente verwenden, die von jeder Ansicht in der Formatierungs Datei verwendet werden können. Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

- Das [ListControl](./listcontrol-element-format.md) -Element definiert, was in der Ansicht angezeigt wird und wie es formatiert wird. Ähnlich wie bei allen anderen Ansichten können in einer Listenansicht die Werte der Objekteigenschaften oder Werte angezeigt werden, die vom Skript generiert werden.

Ein Beispiel für eine komplette Formatierungs Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Bereitstellen von Definitionen für die Listenansicht

Listenansichten können mithilfe der untergeordneten Elemente des [ListControl](./listcontrol-element-format.md) -Elements eine oder mehrere Definitionen bereitstellen. In der Regel hat eine Ansicht nur eine Definition. Im folgenden Beispiel stellt die Sicht eine einzelne Definition bereit, die mehrere Eigenschaften von [System. Diagnostics. Process anzeigt? Displayproperty = FullName](/dotnet/api/System.Diagnostics.Process) -Objekt. In einer Listenansicht kann der Wert einer Eigenschaft oder der Wert eines Skripts angezeigt werden (nicht im Beispiel dargestellt).

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

Die folgenden XML-Elemente können verwendet werden, um Definitionen für eine Listenansicht bereitzustellen:

- Das [ListControl](./listcontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.

- Das [ListEntries](./listentries-element-for-listcontrol-format.md) -Element stellt die Definitionen der Sicht bereit. In den meisten Fällen weist eine Ansicht nur eine Definition auf. Dieses Element ist erforderlich.

- Das [ListEntry](./listentry-element-for-listcontrol-format.md) -Element stellt eine Definition der Sicht bereit. Mindestens ein [ListEntry](./listentry-element-for-listcontrol-format.md) ist erforderlich. Es gibt jedoch keine maximale Beschränkung für die Anzahl der Elemente, die Sie hinzufügen können. In den meisten Fällen weist eine Ansicht nur eine Definition auf.

- Das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element gibt die Objekte an, die von einer bestimmten Definition angezeigt werden. Dieses Element ist optional und wird nur benötigt, wenn Sie mehrere [ListEntry](./listentry-element-for-listcontrol-format.md) -Elemente definieren, die verschiedene-Objekte anzeigen.

- Das [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) -Element gibt die Eigenschaften und Skripts an, deren Werte in den Zeilen der Listenansicht angezeigt werden.

- Das [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) -Element gibt eine Eigenschaft oder ein Skript an, dessen Wert in einer Zeile der Listenansicht angezeigt wird. In einer Listenansicht muss mindestens eine Eigenschaft oder ein Skript angegeben werden. Es gibt keine maximale Beschränkung für die Anzahl der Zeilen, die angegeben werden können.

- Das [propertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element gibt die-Eigenschaft an, deren Wert in der Zeile angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.

- Das [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) -Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

- Das [Label](./label-element-for-listitem-for-listcontrol-format.md) -Element gibt die Bezeichnung an, die auf der linken Seite des Eigenschafts-oder Skript Werts in der Zeile angezeigt wird. Dieses Element ist optional. Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft oder des Skripts angezeigt. Ein umfassendes Beispiel finden Sie unter [Listenansicht (Bezeichnungen)](./list-view-labels.md).

- Das [itemselectioncondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) -Element gibt eine Bedingung an, die vorhanden sein muss, damit die Zeile angezeigt wird. Weitere Informationen zum Hinzufügen von Bedingungen zur Listenansicht finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md). Dieses Element ist optional.

- Das [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Muster an, das verwendet wird, um den Wert der Eigenschaft oder des Skripts anzuzeigen. Dieses Element ist optional.

Ein Beispiel für eine komplette Formatierungs Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definieren der Objekte, die die Listenansicht verwenden

Es gibt zwei Möglichkeiten, um zu definieren, welche .NET-Objekte die Listenansicht verwenden. Sie können das [viewselectedby](./viewselectedby-element-format.md) -Element verwenden, um die Objekte zu definieren, die von allen Definitionen der Sicht angezeigt werden können, oder Sie können das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element verwenden, um zu definieren, welche Objekte von einer bestimmten Definition der Sicht angezeigt werden. In den meisten Fällen verfügt eine Sicht nur über eine Definition, sodass Objekte normalerweise durch das [viewselectedby](./viewselectedby-element-format.md) -Element definiert werden.

Im folgenden Beispiel wird gezeigt, wie die Objekte definiert werden, die in der Listenansicht mithilfe der Elemente [viewselectedby](./viewselectedby-element-format.md) und [tygtame](./typename-element-for-viewselectedby-format.md) angezeigt werden. Es gibt keine Beschränkung für die Anzahl der [tyname](./typename-element-for-viewselectedby-format.md) -Elemente, die Sie angeben können, und ihre Reihenfolge ist nicht signifikant.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Listenansicht verwendet werden:

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Das [tykame](./typename-element-for-viewselectedby-format.md) -Element gibt das .NET-Objekt an, das von der Sicht angezeigt wird. Der voll qualifizierte .net-Typname ist erforderlich. Sie müssen mindestens einen Typ oder einen Auswahl Satz für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

Ein Beispiel für eine komplette Formatierungs Datei finden Sie in der [Listenansicht (Basic)](./list-view-basic.md).

Im folgenden Beispiel werden die Elemente [viewselectedby](./viewselectedby-element-format.md) und [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) verwendet. Verwenden Sie Auswahl Sätze, bei denen Sie über einen zugehörigen Satz von Objekten verfügen, die mithilfe mehrerer Sichten angezeigt werden, z. b. Wenn Sie eine Listenansicht und eine Tabellenansicht für dieselben Objekte definieren. Weitere Informationen zum Erstellen eines Auswahl Satzes finden Sie unter Definieren von [Auswahl Sätzen](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von der Listenansicht verwendet werden:

- Das [viewselectedby](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Das [selectionsetname](./selectionsetname-element-for-viewselectedby-format.md) -Element gibt eine Gruppe von-Objekten an, die von der Sicht angezeigt werden können. Sie müssen mindestens einen Auswahl Satz oder-Typ für die Sicht angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

Im folgenden Beispiel wird gezeigt, wie die-Objekte, die durch eine bestimmte Definition der Listenansicht angezeigt werden, mit dem [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element definiert werden. Mit diesem Element können Sie den .NET-Typnamen des Objekts, einen Auswahl Satz von Objekten oder eine Auswahlbedingung angeben, die angibt, wann die Definition verwendet wird. Weitere Informationen zum Erstellen von Auswahl Bedingungen finden Sie unter Definieren von [Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte anzugeben, die von einer bestimmten Definition der Listenansicht verwendet werden:

- Das [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element definiert, welche Objekte von der Definition angezeigt werden.

- Das [tykame](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt das .NET-Objekt an, das von der Definition angezeigt wird. Wenn Sie dieses Element verwenden, ist der voll qualifizierte .net-Typname erforderlich. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

- Das [selectionsetname](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Gruppe von Objekten an, die von dieser Definition angezeigt werden können. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können.

- Das [selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) -Element (nicht angezeigt) gibt eine Bedingung an, die vorhanden sein muss, damit diese Definition verwendet werden muss. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für die Definition angeben, es gibt jedoch keine maximale Anzahl von Elementen, die angegeben werden können. Weitere Informationen zum Definieren von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Anzeigen von Gruppen von Objekten in einer Listenansicht

Sie können die Objekte, die von der Listenansicht angezeigt werden, in Gruppen aufteilen. Dies bedeutet nicht, dass Sie eine Gruppe definieren, sondern nur, dass Windows PowerShell eine neue Gruppe startet, wenn der Wert einer bestimmten Eigenschaft oder eines Skripts geändert wird. Im folgenden Beispiel wird eine neue Gruppe immer dann gestartet, wenn sich der Wert der [System. ServiceProcess. ServiceController. ServiceType](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) -Eigenschaft ändert.

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

Ein Beispiel für eine komplette Formatierungs Datei, die Gruppen definiert, finden Sie unter [Listenansicht (GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Using-Format

Formatierungs Zeichenfolgen können einer Ansicht hinzugefügt werden, um die Anzeige der Daten weiter zu definieren. Im folgenden Beispiel wird gezeigt, wie eine Formatierungs Zeichenfolge für den Wert der `StartTime`-Eigenschaft definiert wird.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Die folgenden XML-Elemente können verwendet werden, um ein Format Muster anzugeben:

- Das [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.

- Das [propertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element gibt die Eigenschaft an, deren Wert von der Sicht angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber Sie können nicht beides angeben.

- Das Format [String](./formatstring-element-for-listitem-for-listcontrol-format.md) -Element gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.

- Das [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

Im folgenden Beispiel wird die `ToString`-Methode aufgerufen, um den Wert des Skripts zu formatieren. Skripts können beliebige Methoden eines Objekts aufzurufen. Wenn ein Objekt über eine-Methode verfügt, z. b. `ToString`, die Formatierungs Parameter hat, kann das Skript daher diese Methode zum Formatieren des Ausgabe Werts des Skripts aufruft.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Das folgende XML-Element kann verwendet werden, um die `ToString`-Methode aufrufen:

- Das [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -Element gibt die Daten an, die von der Sicht angezeigt werden.

- Das [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) -Element (nicht angezeigt) gibt das Skript an, dessen Wert von der Sicht angezeigt wird. Sie müssen entweder ein-Skript oder eine-Eigenschaft angeben, aber Sie können nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md)
