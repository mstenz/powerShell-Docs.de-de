---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das PowerShellTab-Objekt
ms.openlocfilehash: bfa11b553f97b7b27b974855ff4e8f1a48c33fea
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028906"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="347cb-103">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="347cb-103">The PowerShellTab Object</span></span>

<span data-ttu-id="347cb-104">Das **PowerShellTab**-Objekt stellt eine Windows PowerShell-Laufzeitumgebung dar.</span><span class="sxs-lookup"><span data-stu-id="347cb-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="347cb-105">Methoden</span><span class="sxs-lookup"><span data-stu-id="347cb-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="347cb-106">Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="347cb-106">Invoke\( Script \)</span></span>

<span data-ttu-id="347cb-107">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-108">Führt das angegebene Skript auf der PowerShell-Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="347cb-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="347cb-109">Diese Methode kann nur für andere PowerShell-Registerkarten verwendet werden, nicht für die PowerShell-Registerkarte, auf der sie ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="347cb-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="347cb-110">Sie gibt keine Objekte oder Werte zurück.</span><span class="sxs-lookup"><span data-stu-id="347cb-110">It does not return any object or value.</span></span> <span data-ttu-id="347cb-111">Wenn durch den Code eine Variable geändert wird, bleiben diese Änderungen auf der Registerkarte erhalten, für die der Befehl aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="347cb-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="347cb-112">**Script**: System.Management.Automation.ScriptBlock oder Zeichenfolge – der auszuführende Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="347cb-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="347cb-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="347cb-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="347cb-114">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="347cb-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="347cb-115">Führt das angegebene Skript auf der PowerShell-Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="347cb-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="347cb-116">Diese Methode kann nur für andere PowerShell-Registerkarten verwendet werden, nicht für die PowerShell-Registerkarte, auf der sie ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="347cb-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="347cb-117">Der Skriptblock wird ausgeführt, und alle vom Skript zurückgegebenen Werte werden an die Laufzeitumgebung zurückgegeben, in der der Befehl aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="347cb-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="347cb-118">Wenn die Ausführung des Befehls länger dauert, als vom Wert **millesecondsTimeout** angegeben, tritt durch den Befehl ein Fehler mit folgender Ausnahme auf: „Timeout bei Vorgang.“.</span><span class="sxs-lookup"><span data-stu-id="347cb-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="347cb-119">**Script**: System.Management.Automation.ScriptBlock oder Zeichenfolge – der auszuführende Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="347cb-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="347cb-120">**\[useNewScope\]** : optionaler boolescher Wert mit Standardwert **$true**. Bei Festlegung auf **$true** wird ein neuer Bereich erstellt, in dem der Befehl ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="347cb-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="347cb-121">Die Laufzeitumgebung der vom Befehl angegebenen PowerShell-Registerkarte wird nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="347cb-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="347cb-122">**\[millisecondsTimeout\]** : optionale ganze Zahl mit Standardwert **500**.</span><span class="sxs-lookup"><span data-stu-id="347cb-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="347cb-123">Wenn der Befehl nicht innerhalb der angegebenen Zeit abgeschlossen wird, generiert der Befehl eine **TimeoutException** mit der Meldung „Timeout für Vorgang überschritten“.</span><span class="sxs-lookup"><span data-stu-id="347cb-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="347cb-124">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="347cb-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="347cb-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="347cb-125">AddOnsMenu</span></span>

<span data-ttu-id="347cb-126">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-127">Die schreibgeschützte Eigenschaft, die das Add-On-Menü für die PowerShell-Registerkarte abruft.</span><span class="sxs-lookup"><span data-stu-id="347cb-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="347cb-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="347cb-128">CanInvoke</span></span>

<span data-ttu-id="347cb-129">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-130">Die schreibgeschützte boolesche Eigenschaft, die den Wert **$true** zurückgibt, wenn ein Skript mit der [Invoke( Script )](#invoke-script-)-Methode aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="347cb-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="347cb-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="347cb-131">Consolepane</span></span>

<span data-ttu-id="347cb-132">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="347cb-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="347cb-133">In Windows PowerShell ISE 2.0 lautete der Name hierfür **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="347cb-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="347cb-134">Die schreibgeschützte Eigenschaft, die das [editor](The-ISEEditor-Object.md)-Objekt des Konsolenbereichs abruft.</span><span class="sxs-lookup"><span data-stu-id="347cb-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="347cb-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="347cb-135">DisplayName</span></span>

<span data-ttu-id="347cb-136">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-137">Die Lese-/Schreibeigenschaft Eigenschaft, die den auf der PowerShell-Registerkarte angezeigten Text abruft oder festlegt. Standardmäßig lautet der Name von Registerkarten „PowerShell #“, wobei # eine Zahl darstellt.</span><span class="sxs-lookup"><span data-stu-id="347cb-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="347cb-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="347cb-138">ExpandedScript</span></span>

<span data-ttu-id="347cb-139">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-140">Die Lese-/Schreibeigenschaft, die bestimmt, ob der Skript-Bereich erweitert oder ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="347cb-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="347cb-141">Dateien</span><span class="sxs-lookup"><span data-stu-id="347cb-141">Files</span></span>

<span data-ttu-id="347cb-142">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-143">Die schreibgeschützte Eigenschaft, die die [Sammlung von Skriptdateien](The-ISEFileCollection-Object.md) abruft, die auf der PowerShell-Registerkarte geöffnet sind.</span><span class="sxs-lookup"><span data-stu-id="347cb-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="347cb-144">Ausgabe</span><span class="sxs-lookup"><span data-stu-id="347cb-144">Output</span></span>

<span data-ttu-id="347cb-145">Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt.</span><span class="sxs-lookup"><span data-stu-id="347cb-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="347cb-146">In höheren Versionen von Windows PowerShell ISE können Sie das **ConsolePane**-Objekt für den gleichen Zweck verwenden.</span><span class="sxs-lookup"><span data-stu-id="347cb-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="347cb-147">Die schreibgeschützte Eigenschaft, die den Ausgabebereich des aktuellen [editor](The-ISEEditor-Object.md) abruft.</span><span class="sxs-lookup"><span data-stu-id="347cb-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="347cb-148">Auffordern</span><span class="sxs-lookup"><span data-stu-id="347cb-148">Prompt</span></span>

<span data-ttu-id="347cb-149">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-150">Die schreibgeschützte Eigenschaft, die den aktuellen Aufforderungstext abruft.</span><span class="sxs-lookup"><span data-stu-id="347cb-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="347cb-151">Hinweis: Die **Prompt**-Funktion kann durch das Profil des Benutzers überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="347cb-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="347cb-152">Wenn das Ergebnis von einer einfachen Zeichenfolge abweicht, gibt diese Eigenschaft nichts zurück.</span><span class="sxs-lookup"><span data-stu-id="347cb-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="347cb-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="347cb-153">ShowCommands</span></span>

<span data-ttu-id="347cb-154">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="347cb-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="347cb-155">Die Lese-/Schreibeigenschaft, die angibt, ob der Befehlsbereich derzeit angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="347cb-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="347cb-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="347cb-156">StatusText</span></span>

<span data-ttu-id="347cb-157">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="347cb-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="347cb-158">Die schreibgeschützte Eigenschaft, die den **PowerShellTab**-Statustext abruft.</span><span class="sxs-lookup"><span data-stu-id="347cb-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="347cb-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="347cb-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="347cb-160">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="347cb-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="347cb-161">Die schreibgeschützte Eigenschaft, die angibt, ob der horizontale Add-On-Toolbereich derzeit geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="347cb-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="347cb-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="347cb-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="347cb-163">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="347cb-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="347cb-164">Die schreibgeschützte Eigenschaft, die angibt, ob der vertikale Add-On-Toolbereich derzeit geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="347cb-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="347cb-165">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="347cb-165">See Also</span></span>

- [<span data-ttu-id="347cb-166">Das PowerShellTabCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="347cb-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="347cb-167">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="347cb-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="347cb-168">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="347cb-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
