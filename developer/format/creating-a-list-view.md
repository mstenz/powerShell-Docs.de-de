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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066854"
---
# <a name="creating-a-list-view"></a>Erstellen einer Listenansicht

Eine Listenansicht zeigt Daten in eine einzelne Spalte (in sequenzieller Reihenfolge). In der Liste angezeigten Daten möglich den Wert einer Eigenschaft .NET oder der Wert eines Skripts.

## <a name="a-list-view-display"></a>Anzeige einer Liste

Die folgende Ausgabe zeigt, wie die Eigenschaften der von Windows PowerShell zeigt [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte, die von zurückgegeben werden die [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet. In diesem Beispiel wurden drei Objekte zurückgegeben, mit jedem Objekt, das aus dem vorherigen Objekt durch eine leere Zeile getrennt.

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

Das folgende XML zeigt das Schema Liste angezeigt, für die Anzeige von mehreren Eigenschaften der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekt. Sie müssen jede Eigenschaft angeben, die in der Listenansicht angezeigt werden soll.

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

Die folgende XML-Elemente werden verwendet, um eine Ansicht zu definieren:

- Die [Ansicht](./view-element-format.md) Element ist das übergeordnete Element der Listenansicht angezeigt. (Dies ist der dasselbe übergeordnete Element für die Tabelle, Breite und benutzerdefinierte Steuerelementansicht.)

- Die [Namen](./name-element-for-view-format.md) Element gibt den Namen der Ansicht. Dieses Element ist für alle Ansichten erforderlich.

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht zu verwenden. Dieses Element ist erforderlich.

- Die [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wenn eine neue Gruppe von Objekten angezeigt wird. Eine neue Gruppe wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts. Dieses Element ist optional.

- Die [Steuerelemente](./controls-element-for-view-format.md) -Element definiert die benutzerdefinierten Steuerelemente, die von der Listenansicht definiert sind. Steuerelemente bieten Ihnen eine Möglichkeit, festzulegen, wie die Daten angezeigt werden. Dieses Element ist optional. Eine Ansicht kann eine eigene benutzerdefinierte Steuerelemente zu definieren, oder sie können allgemeine Steuerelemente, die von einer beliebigen Ansicht in der Formatierungsdatei verwendet werden können. Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

- Die [ListControl](./listcontrol-element-format.md) -Element definiert, was in der Ansicht angezeigt wird und wie es formatiert ist. Ähnlich wie bei allen anderen Ansichten, kann eine Listenansicht die Werte der Objekteigenschaften oder Werte, die vom Skript generiert anzeigen.

Ein Beispiel für eine vollständige Formatierung-Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).

## <a name="providing-definitions-for-your-list-view"></a>Bereitstellen von Definitionen für Ihre Listenansicht

Listenansichten können eine oder mehrere Definitionen bereitstellen, indem die untergeordneten Elemente des mithilfe der [ListControl](./listcontrol-element-format.md) Element. Eine Sicht wird in der Regel nur eine Definition verfügen. Im folgenden Beispiel die Ansicht bietet eine einzige Definition, die mehrere Eigenschaften der zeigt die ["System.Diagnostics.Process"? Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) Objekt. Eine Listenansicht kann den Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel gezeigt) anzeigen.

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

Die folgende XML-Elemente können verwendet werden, um Definitionen für eine Listenansicht bereitzustellen:

- Die [ListControl](./listcontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.

- Die [ListEntries](./listentries-element-for-listcontrol-format.md) Element enthält die Definitionen der Ansicht. In den meisten Fällen wird eine Ansicht nur eine Definition verfügen. Dieses Element ist erforderlich.

- Die [ListEntry](./listentry-element-for-listcontrol-format.md) Element enthält eine Definition der Sicht. Mindestens ein [ListEntry](./listentry-element-for-listcontrol-format.md) ist erforderlich; Es ist jedoch nicht begrenzt auf die Anzahl der Elemente, die Sie hinzufügen können. In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.

- Die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Element gibt an, die Objekte, die von einer bestimmten Definition angezeigt werden. Dieses Element ist optional und ist nur erforderlich, wenn Sie mehrere definieren [ListEntry](./listentry-element-for-listcontrol-format.md) Elemente, die verschiedene Objekte anzeigen.

- Die [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) Element gibt die Eigenschaften und Skripts, deren Werte werden in den Zeilen der Listenansicht angezeigt.

- Die [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) Element gibt an, eine Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird. Eine Listenansicht muss mindestens eine Eigenschaft oder ein Skript angeben. Es gibt keine Obergrenze, die Anzahl der Zeilen, die angegeben werden können.

- Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) Element gibt die Eigenschaft, deren Wert in der Zeile angezeigt wird. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.

- Die ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element gibt das Skript an, dessen Wert in der Zeile angezeigt wird. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

- Die [Bezeichnung](./label-element-for-listitem-for-listcontrol-format.md) Element gibt die Bezeichnung, die auf der linken Seite des Eigenschaft oder des Skripts in der Zeile angezeigt wird. Dieses Element ist optional. Wenn eine Bezeichnung nicht angegeben ist, wird der Name der Eigenschaft oder des Skripts angezeigt. Ein vollständiges Beispiel finden Sie unter [Listenansicht (Bezeichnungen)](./list-view-labels.md).

- Die [ItemSelectionCondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) Element gibt eine Bedingung, die vorhanden sein muss, für die Zeile, die angezeigt werden. Weitere Informationen zum Hinzufügen von Bedingungen zur Listenansicht wechseln, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md). Dieses Element ist optional.

- Die [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) Element gibt ein Muster, das verwendet wird, um den Wert der Eigenschaft oder des Skripts anzuzeigen. Dieses Element ist optional.

Ein Beispiel für eine vollständige Formatierung-Datei, die eine einfache Listenansicht definiert, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).

## <a name="defining-the-objects-that-use-the-list-view"></a>Definieren die Objekte, die der Listenansicht

Es gibt zwei Möglichkeiten, die definieren, welche .NET Objekte der Listenansicht angezeigt. Können Sie die [ViewSelectedBy](./viewselectedby-element-format.md) Element, das die Objekte zu definieren, die durch alle Definitionen oder der Ansicht angezeigt werden können. die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) -Element zum definieren, welche Objekte angezeigt werden ein spezifische Definition der Sicht. In den meisten Fällen eine Ansicht hat nur eine Definition, sodass Objekte in der Regel, indem definiert werden die [ViewSelectedBy](./viewselectedby-element-format.md) Element.

Das folgende Beispiel zeigt, wie Sie die Objekte zu definieren, die mithilfe der Liste Ansicht angezeigt werden die [ViewSelectedBy](./viewselectedby-element-format.md) und [TypeName](./typename-element-for-viewselectedby-format.md) Elemente. Es gibt keine Beschränkung der Anzahl der [TypeName](./typename-element-for-viewselectedby-format.md) Elementen, die Sie angeben können und ihre Reihenfolge ist nicht von Bedeutung.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Listenansicht verwendet werden:

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Die [TypeName](./typename-element-for-viewselectedby-format.md) -Element gibt an, das .NET-Objekt, das von der Ansicht angezeigt wird. Der vollqualifizierte Typname des .NET ist erforderlich. Geben Sie mindestens einen Typ oder Auswahl für die Ansicht festgelegt, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

Ein Beispiel für eine vollständige Formatierungsdatei, finden Sie unter [Listenansicht (Basic)](./list-view-basic.md).

Im folgenden Beispiel wird die [ViewSelectedBy](./viewselectedby-element-format.md) und [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Elemente. Verwenden Sie die Auswahl legt, haben eine zusammengehörige Gruppe von Objekten, die über mehrere Ansichten, z. B. Wenn Sie eine Listenansicht definieren und eine Tabellenansicht für diese Objekte angezeigt werden. Weitere Informationen dazu, wie Sie einen Auswahlsatz zu erstellen, finden Sie unter [definieren Auswahl legt](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

Die folgende XML-Elemente können verwendet werden, die Objekte an, die von der Listenansicht verwendet werden:

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert, welche Objekte von der Listenansicht angezeigt werden.

- Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element gibt einen Satz von Objekten, die von der Ansicht angezeigt werden können. Geben Sie mindestens einen Auswahlsatz oder Typ, für die Sicht, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

Das folgende Beispiel zeigt, wie Sie definieren die Objekte angezeigt, die von einer bestimmten Definition der Liste Ansicht mithilfe der [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Element. Verwenden dieses Element, können Sie den Namen des Objekts, einer Auswahlsatz von Objekten oder eine auswahlbedingung, die angibt, wenn die Definition verwendet wird angeben. Weitere Informationen dazu, wie Sie eine Auswahl Bedingungen zu erstellen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

Die folgende XML-Elemente können verwendet werden, die Objekte an, die von einer bestimmten Definition der Listenansicht verwendet werden:

- Die [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) Element definiert, welche Objekte durch die Definition angezeigt werden.

- Die [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) -Element gibt an, das .NET-Objekt, das durch die Definition angezeigt wird. Wenn Sie dieses Element zu verwenden, ist der vollqualifizierte Typname des .NET erforderlich. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

- Die [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt einen Satz von Objekten, die von dieser Definition angezeigt werden können. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

- Die [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) Element (nicht dargestellt) gibt an, eine Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können. Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-list-view"></a>Anzeigen von Gruppen von Objekten in einer Listenansicht

Sie können die Objekte trennen, die von der Listenansicht in Gruppen angezeigt werden. Dies bedeutet nicht, dass Sie eine Gruppe definieren nur die eine neue Gruppe, die Windows PowerShell wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts. Im folgenden Beispiel wird eine neue Gruppe gestartet Wenn der Wert des der [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) eigenschaftenänderungen.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Die folgende XML-Elemente werden zum definieren, wenn Sie eine Gruppe gestartet wird:

- Die [GroupBy](./groupby-element-for-view-format.md) -Element definiert die Eigenschaft oder ein Skript, das die neue Gruppe gestartet und definiert, wie die Gruppe angezeigt wird.

- Die [PropertyName](./propertyname-element-for-groupby-format.md) Element gibt die Eigenschaft, die eine neue Gruppe wird gestartet, wenn sich der Wert ändert. Sie müssen eine Eigenschaft oder ein Skript zum Starten der Gruppe angeben, aber nicht beides angeben.

- Die ["scriptblock"](./scriptblock-element-for-groupby-format.md) Element gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert. Sie müssen angeben, ein Skript oder eine Eigenschaft, um die Gruppe zu starten, aber nicht beides angeben.

- Die [Bezeichnung](./label-element-for-groupby-format.md) -Element definiert eine Bezeichnung, die am Anfang der Gruppe "Jeder" angezeigt wird. Zusätzlich zu den Text, der von diesem Element angegeben wird wird der Wert, der die neue Gruppe ausgelöst und fügt eine leere Zeile vor und nach der die Bezeichnung von Windows PowerShell angezeigt. Dieses Element ist optional.

- Die [CustomControl](./customcontrol-element-for-groupby-format.md) -Element definiert ein Steuerelement, das zum Anzeigen der Daten verwendet wird. Dieses Element ist optional.

- Die [CustomControlName](./customcontrolname-element-for-groupby-format.md) Element gibt einen allgemeinen oder Steuerelements, die zum Anzeigen der Daten verwendet wird. Dieses Element ist optional.

Ein Beispiel für eine vollständige Formatierung-Datei, die Gruppen definiert, finden Sie unter [Listenansicht (-GroupBy)](./list-view-groupby.md).

## <a name="using-format-strings"></a>Verwenden von Formatzeichenfolgen

Formatieren von Zeichenfolgen können hinzugefügt werden, zu einer Ansicht genauer definieren, wie die Daten angezeigt werden. Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

Die folgende XML-Elemente können verwendet werden, ein Formatmuster angeben:

- Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.

- Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) Element gibt die Eigenschaft, deren Wert wird von der Sicht angezeigt. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.

- Die [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird.

- Die ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

Im folgenden Beispiel die `ToString` aufgerufen, um den Wert des Skripts zu formatieren. Skripts können auf jede Methode eines Objekts aufrufen. Daher verfügt ein Objekt eine Methode, wie z. B. `ToString`über Formatierung Parameter verfügt, das Skript kann diese Methode zum Formatieren des Werts der Ausgabe des Skripts aufzurufen.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

Das folgende XML-Element kann zum Aufrufen der `ToString` Methode:

- Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.

- Die ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md)
