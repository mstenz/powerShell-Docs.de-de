---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das PowerShellTab-Objekt
ms.openlocfilehash: 55e3678a8285f0ec7e8131d98c87478216c26f37
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736929"
---
# <a name="the-powershelltab-object"></a>Das PowerShellTab-Objekt

Das **PowerShellTab**-Objekt stellt eine Windows PowerShell-Laufzeitumgebung dar.

## <a name="methods"></a>Methoden

### <a name="invoke-script-"></a>Invoke\( Script \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Führt das angegebene Skript auf der PowerShell-Registerkarte aus.

> [!NOTE]
> Diese Methode kann nur für andere PowerShell-Registerkarten verwendet werden, nicht für die PowerShell-Registerkarte, auf der sie ausgeführt wird. Sie gibt keine Objekte oder Werte zurück. Wenn durch den Code eine Variable geändert wird, bleiben diese Änderungen auf der Registerkarte erhalten, für die der Befehl aufgerufen wurde.

**Script**: System.Management.Automation.ScriptBlock oder Zeichenfolge – der auszuführende Skriptblock.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Führt das angegebene Skript auf der PowerShell-Registerkarte aus.

> [!NOTE]
> Diese Methode kann nur für andere PowerShell-Registerkarten verwendet werden, nicht für die PowerShell-Registerkarte, auf der sie ausgeführt wird. Der Skriptblock wird ausgeführt, und alle vom Skript zurückgegebenen Werte werden an die Laufzeitumgebung zurückgegeben, in der der Befehl aufgerufen wurde. Wenn die Ausführung des Befehls länger dauert, als vom Wert **millesecondsTimeout** angegeben, tritt durch den Befehl ein Fehler mit folgender Ausnahme auf: „Timeout bei Vorgang.“.

**Script**: System.Management.Automation.ScriptBlock oder Zeichenfolge – der auszuführende Skriptblock.

**\[useNewScope\]** : optionaler boolescher Wert mit Standardwert `$true`. Bei Festlegung auf `$true` wird ein neuer Bereich erstellt, in dem der Befehl ausgeführt werden soll. Die Laufzeitumgebung der vom Befehl angegebenen PowerShell-Registerkarte wird nicht geändert.

**\[millisecondsTimeout\]** : optionale ganze Zahl mit Standardwert **500**.
Wenn der Befehl nicht innerhalb der angegebenen Zeit abgeschlossen wird, generiert der Befehl eine **TimeoutException** mit der Meldung „Timeout für Vorgang überschritten“.

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a>Eigenschaften

### <a name="addonsmenu"></a>AddOnsMenu

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die das Add-On-Menü für die PowerShell-Registerkarte abruft.

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte boolesche Eigenschaft, die den Wert `$true` zurückgibt, wenn ein Skript mit der [Invoke( Script )](#invoke-script-)-Methode aufgerufen werden kann.

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a>ConsolePane

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. In Windows PowerShell ISE 2.0 lautete der Name hierfür **CommandPane**.

Die schreibgeschützte Eigenschaft, die das [editor](The-ISEEditor-Object.md)-Objekt des Konsolenbereichs abruft.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die Lese-/Schreibeigenschaft Eigenschaft, die den auf der PowerShell-Registerkarte angezeigten Text abruft oder festlegt. Standardmäßig lautet der Name von Registerkarten „PowerShell #“, wobei # eine Zahl darstellt.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die Lese-/Schreibeigenschaft, die bestimmt, ob der Skript-Bereich erweitert oder ausgeblendet wird.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Dateien

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die [Sammlung von Skriptdateien](The-ISEFileCollection-Object.md) abruft, die auf der PowerShell-Registerkarte geöffnet sind.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Output

Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt. In höheren Versionen von Windows PowerShell ISE können Sie das **ConsolePane**-Objekt für den gleichen Zweck verwenden.

Die schreibgeschützte Eigenschaft, die den Ausgabebereich des aktuellen [editor](The-ISEEditor-Object.md) abruft.

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Prompt

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die den aktuellen Aufforderungstext abruft. Hinweis: Die **Prompt**-Funktion kann durch das Profil des Benutzers überschrieben werden. Wenn das Ergebnis von einer einfachen Zeichenfolge abweicht, gibt diese Eigenschaft nichts zurück.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die Lese-/Schreibeigenschaft, die angibt, ob der Befehlsbereich derzeit angezeigt wird.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die den **PowerShellTab**-Statustext abruft.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die schreibgeschützte Eigenschaft, die angibt, ob der horizontale Add-On-Toolbereich derzeit geöffnet ist.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die schreibgeschützte Eigenschaft, die angibt, ob der vertikale Add-On-Toolbereich derzeit geöffnet ist.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Weitere Informationen

- [Das PowerShellTabCollection-Objekt](The-PowerShellTabCollection-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
