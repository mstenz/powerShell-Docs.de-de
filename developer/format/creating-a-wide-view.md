---
title: Erstellen eine Breite Ansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066718"
---
# <a name="creating-a-wide-view"></a>Erstellen einer breiten Ansicht

Eine Breite Ansicht zeigt einen einzelnen Wert für jedes Objekt, das angezeigt wird. Der angezeigte Wert möglich den Wert einer Objekteigenschaft .NET oder der Wert von einem Skript. Es wird standardmäßig keine Bezeichnung oder Header für diese Sicht.

## <a name="a-wide-view-display"></a>Eine Breite Ansicht anzeigen

Das folgende Beispiel zeigt, wie Windows PowerShell zeigt die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) -Objekt, das von zurückgegeben wird die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet aus, wenn die Ausgabe, um weitergeleitet werden die [ Format-Wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) Cmdlet. (Standardmäßig die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -Cmdlet wird eine Tabellenansicht zurückgegeben.) In diesem Beispiel werden die beiden Spalten verwendet, um den Namen des Prozesses für jedes zurückgegebene Objekt anzuzeigen. Der Name der Eigenschaft des Objekts nicht angezeigt wird, nur den Wert der Eigenschaft.

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

## <a name="defining-the-wide-view"></a>Definieren die Breite Ansicht

Das folgende XML zeigt das Schema Breite Ansicht, für die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.

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

Die folgende XML-Elemente werden verwendet, um eine Breite Ansicht zu definieren:

- Die [Ansicht](./view-element-format.md) Element ist das übergeordnete Element der breiten Ansicht. (Dies ist das über dasselbe übergeordnete Element für die Tabelle, eine Liste und ein benutzerdefiniertes Steuerelement Ansichten).

- Die [Namen](./name-element-for-view-format.md) Element gibt den Namen der Ansicht. Dieses Element ist für alle Ansichten erforderlich.

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element definiert die Objekte, die die Sicht zu verwenden. Dieses Element ist erforderlich.

- Die [GroupBy](./groupby-element-for-view-format.md) -Element definiert, wenn eine neue Gruppe von Objekten angezeigt wird. Eine neue Gruppe wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts. Dieses Element ist optional.

- Die [Steuerelemente](./controls-element-for-view-format.md) Elemente definiert, das die benutzerdefinierten Steuerelemente, die von der breiten Ansicht definiert sind. Steuerelemente bieten Ihnen eine Möglichkeit, festzulegen, wie die Daten angezeigt werden. Dieses Element ist optional. Eine Ansicht kann eine eigene benutzerdefinierte Steuerelemente zu definieren, oder sie können allgemeine Steuerelemente, die von einer beliebigen Ansicht in der Formatierungsdatei verwendet werden können. Weitere Informationen zu benutzerdefinierten Steuerelementen finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

- Die [WideControl](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird. Im vorherigen Beispiel dient zum Anzeigen die Ansicht der [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) Eigenschaft.

Ein Beispiel für eine vollständige Formatierung-Datei, die eine einfache Breite Ansicht definiert, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

## <a name="providing-definitions-for-your-wide-view"></a>Bereitstellen von Definitionen für die Breite Ansicht

Breite Ansichten können eine oder mehrere Definitionen bereitstellen, indem die untergeordneten Elemente des mithilfe der [WideControl](./widecontrol-element-format.md) Element. Eine Sicht wird in der Regel nur eine Definition verfügen. Im folgenden Beispiel ist die Ansicht bietet eine einzige Definition, die den Wert der [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) Eigenschaft. Eine Breite Ansicht kann es sich um den Wert einer Eigenschaft oder der Wert eines Skripts (nicht im Beispiel gezeigt) angezeigt.

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

Die folgende XML-Elemente können verwendet werden, um Definitionen für eine Breite Ansicht bereitzustellen:

- Die [WideControl](./widecontrol-element-format.md) -Element und seine untergeordneten Elemente definieren, was in der Ansicht angezeigt wird.

- Die [AutoSize](./autosize-element-for-widecontrol-format.md) Element gibt an, ob die Größe der Spalte und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden. Dieses Element ist optional.

- Die [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) Element gibt die Anzahl der Spalten in der breiten Ansicht angezeigt. Dieses Element ist optional.

- Die [WideEntries](./wideentries-element-for-widecontrol-format.md) Element enthält die Definitionen der Ansicht. In den meisten Fällen wird eine Ansicht nur eine Definition verfügen. Dieses Element ist erforderlich.

- Die [WideEntry](./wideentry-element-for-widecontrol-format.md) Element enthält eine Definition der Sicht. Mindestens ein [WideEntry](./wideentry-element-for-widecontrol-format.md) ist erforderlich; Es ist jedoch nicht begrenzt auf die Anzahl der Elemente, die Sie hinzufügen können. In den meisten Fällen wird eine Ansicht nur eine Definition verfügen.

- Die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) Element gibt an, die Objekte, die von einer bestimmten Definition angezeigt werden. Dieses Element ist optional und ist nur erforderlich, wenn Sie mehrere definieren [WideEntry](./wideentry-element-for-widecontrol-format.md) Elemente, die verschiedene Objekte anzeigen.

- Die [WideItem](./wideitem-element-for-widecontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden. Im Gegensatz zu anderen Ansichten kann ein Breite-Steuerelement nur ein Element anzeigen.

- Die [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) Element gibt die Eigenschaft, deren Wert wird von der Sicht angezeigt. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.

- Die ["scriptblock"](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Element gibt das Skript an, deren Wert wird von der Sicht angezeigt. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

- Die [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) Element gibt ein Muster, das zum Anzeigen der Daten verwendet wird. Dieses Element ist optional.

Ein Beispiel für eine vollständige Formatierung-Datei, die eine Breite Ansichtsdefinition definiert, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

## <a name="defining-the-objects-that-use-the-wide-view"></a>Definieren die Objekte, die die Breite Ansicht verwenden.

Es gibt zwei Möglichkeiten, die definieren, welche .NET Objekte auf die Breite Ansicht verwenden. Können Sie die [ViewSelectedBy](./viewselectedby-element-format.md) Element, das die Objekte zu definieren, die durch alle Definitionen oder der Ansicht angezeigt werden können. die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) -Element zum definieren, welche Objekte angezeigt werden ein spezifische Definition der Sicht. In den meisten Fällen eine Ansicht hat nur eine Definition, sodass Objekte in der Regel, indem definiert werden die [ViewSelectedBy](./viewselectedby-element-format.md) Element.

Das folgende Beispiel zeigt, wie Sie die Objekte zu definieren, die mithilfe der Breite Ansicht angezeigt werden die [ViewSelectedBy](./viewselectedby-element-format.md) und [TypeName](./typename-element-for-viewselectedby-format.md) Elemente. Es gibt keine Beschränkung der Anzahl der [TypeName](./typename-element-for-viewselectedby-format.md) Elementen, die Sie angeben können und ihre Reihenfolge ist nicht von Bedeutung.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte angeben, die von der breiten Ansicht verwendet werden:

- Die [ViewSelectedBy](./viewselectedby-element-format.md) Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.

- Die [TypeName](./typename-element-for-viewselectedby-format.md) Element gibt an, die .NET, die von der Ansicht angezeigt wird. Der vollqualifizierte Typname des .NET ist erforderlich. Geben Sie mindestens einen Typ oder Auswahl für die Ansicht festgelegt, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

Ein Beispiel für eine vollständige Formatierungsdatei, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

Im folgenden Beispiel wird die [ViewSelectedBy](./viewselectedby-element-format.md) und [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Elemente. Verwenden Sie die Auswahl legt, haben eine zusammengehörige Gruppe von Objekten, die über mehrere Ansichten, z. B. Wenn Sie eine Breite Ansicht definieren und eine Tabellenansicht für diese Objekte angezeigt werden. Weitere Informationen dazu, wie Sie einen Auswahlsatz zu erstellen, finden Sie unter [definieren Auswahl legt](./defining-selection-sets.md).

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

Die folgenden XML-Elemente können verwendet werden, um die Objekte angeben, die von der breiten Ansicht verwendet werden:

- Die [ViewSelectedBy](./viewselectedby-element-format.md) Element definiert, welche Objekte von der breiten Ansicht angezeigt werden.

- Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element gibt einen Satz von Objekten, die von der Ansicht angezeigt werden können. Geben Sie mindestens einen Auswahlsatz oder Typ, für die Sicht, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

Das folgende Beispiel zeigt, wie die Objekte angezeigt, die von der breiten Ansicht mithilfe einer bestimmten Definition definiert die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) Element. Verwenden dieses Element, können Sie den Namen des Objekts, einer Auswahlsatz von Objekten oder eine auswahlbedingung, die angibt, wenn die Definition verwendet wird angeben. Weitere Informationen dazu, wie Sie eine Auswahl Bedingungen zu erstellen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

Die folgende XML-Elemente können verwendet werden, die Objekte an, die von einer bestimmten Definition der breiten Ansicht verwendet werden:

- Die [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) Element definiert, welche Objekte durch die Definition angezeigt werden.

- Die [TypeName](./typename-element-for-viewselectedby-format.md) Element gibt an, die .NET, die durch die Definition angezeigt wird. Bei Verwendung dieses Elements ist der vollqualifizierte Typname des .NET erforderlich. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

- Die [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) Element (nicht dargestellt) gibt einen Satz von Objekten, die von dieser Definition angezeigt werden können. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können.

- Die [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) Element (nicht dargestellt) gibt an, eine Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition angeben, aber es ist keine maximale Anzahl von Elementen, die angegeben werden können. Weitere Informationen zum Definieren von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>Anzeigen von Gruppen von Objekten in eine Breite Ansicht

Sie können die Objekte trennen, die von der breiten Ansicht in Gruppen angezeigt werden. Dies bedeutet nicht, dass Sie eine Gruppe definieren nur die eine neue Gruppe, die Windows PowerShell wird gestartet, Änderung des Werts, der eine bestimmte Eigenschaft oder des Skripts. Im folgenden Beispiel wird eine neue Gruppe gestartet Wenn der Wert des der [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) eigenschaftenänderungen.

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

Ein Beispiel für eine vollständige Formatierung-Datei, die Gruppen definiert, finden Sie unter [Breite Ansicht (-GroupBy)](./wide-view-groupby.md).

## <a name="using-format-strings"></a>Verwenden von Formatzeichenfolgen

Formatieren von Zeichenfolgen können hinzugefügt werden, um eine Breite Ansicht genauer definieren, wie die Daten angezeigt werden. Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

Die folgende XML-Elemente können verwendet werden, ein Formatmuster angeben:

- Die [WideItem](./wideitem-element-for-widecontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.

- Die [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) Element gibt die Eigenschaft, deren Wert wird von der Sicht angezeigt. Sie müssen entweder eine Eigenschaft oder ein Skript angeben, aber nicht beides angeben.

- Die [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) Element gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird

- Die ["scriptblock"](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

Im folgenden Beispiel die `ToString` aufgerufen, um den Wert des Skripts zu formatieren. Skripts können auf jede Methode eines Objekts aufrufen. Daher verfügt ein Objekt eine Methode, wie z. B. `ToString`über Formatierung Parameter verfügt, das Skript kann diese Methode zum Formatieren des Werts der Ausgabe des Skripts aufzurufen.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

Das folgende XML-Element kann zum Aufrufen der `ToString` Methode:

- Die [WideItem](./wideitem-element-for-widecontrol-format.md) Element gibt an, die Daten, die von der Ansicht angezeigt werden.

- Die ["scriptblock"](./scriptblock-element-for-wideitem-for-widecontrol-format.md) Element (nicht dargestellt) gibt das Skript an, deren Wert wird von der Sicht angezeigt. Sie müssen entweder ein Skript oder eine Eigenschaft angeben, aber nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Breite Ansicht (Basic)](./wide-view-basic.md)

[Breite Ansicht (-GroupBy)](./wide-view-groupby.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
