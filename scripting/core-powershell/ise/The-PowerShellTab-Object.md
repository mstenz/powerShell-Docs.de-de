---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Das PowerShellTab-Objekt
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: d4e9374202d352a30b3eb46bcf1e4e40dea49822
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="e4256-103">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="e4256-103">The PowerShellTab Object</span></span>
  <span data-ttu-id="e4256-104">Das **PowerShellTab**-Objekt stellt eine Windows PowerShell-Laufzeitumgebung dar.</span><span class="sxs-lookup"><span data-stu-id="e4256-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="e4256-105">Methoden</span><span class="sxs-lookup"><span data-stu-id="e4256-105">Methods</span></span>

###  <span data-ttu-id="e4256-106"><a name="invoke"></a> Invoke\( Script \)</span><span class="sxs-lookup"><span data-stu-id="e4256-106"><a name="invoke"></a> Invoke\( Script \)</span></span>
  <span data-ttu-id="e4256-107">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-108">Führt das angegebene Skript auf der PowerShell-Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="e4256-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="e4256-109">Diese Methode kann nur für andere PowerShell-Registerkarten verwendet werden, nicht für die PowerShell-Registerkarte, auf der sie ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e4256-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="e4256-110">Sie gibt keine Objekte oder Werte zurück.</span><span class="sxs-lookup"><span data-stu-id="e4256-110">It does not return any object or value.</span></span> <span data-ttu-id="e4256-111">Wenn durch den Code eine Variable geändert wird, bleiben diese Änderungen auf der Registerkarte erhalten, für die der Befehl aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="e4256-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

 <span data-ttu-id="e4256-112">**Script**: System.Management.Automation.ScriptBlock oder Zeichenfolge – der auszuführende Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="e4256-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="e4256-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="e4256-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>
  <span data-ttu-id="e4256-114">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4256-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e4256-115">Führt das angegebene Skript auf der PowerShell-Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="e4256-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="e4256-116">Diese Methode kann nur für andere PowerShell-Registerkarten verwendet werden, nicht für die PowerShell-Registerkarte, auf der sie ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e4256-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="e4256-117">Der Skriptblock wird ausgeführt, und alle vom Skript zurückgegebenen Werte werden an die Laufzeitumgebung zurückgegeben, in der der Befehl aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="e4256-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="e4256-118">Wenn die Ausführung des Befehls länger dauert, als vom Wert **millesecondsTimeout** angegeben, tritt durch den Befehl ein Fehler mit folgender Ausnahme auf: „Timeout für Vorgang überschritten.“</span><span class="sxs-lookup"><span data-stu-id="e4256-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

 <span data-ttu-id="e4256-119">**Script**: System.Management.Automation.ScriptBlock oder Zeichenfolge – der auszuführende Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="e4256-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

 <span data-ttu-id="e4256-120">**\[useNewScope\]**: optionaler boolescher Wert mit Standardwert **$true**
. Bei Festlegung auf **$true** wird ein neuer Bereich erstellt, in dem der Befehl ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e4256-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true**
 If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="e4256-121">Die Laufzeitumgebung der vom Befehl angegebenen PowerShell-Registerkarte wird nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="e4256-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

 <span data-ttu-id="e4256-122">**\[millisecondsTimeout\]**: optionale ganze Zahl mit Standardwert **500**.</span><span class="sxs-lookup"><span data-stu-id="e4256-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="e4256-123">Wenn der Befehl nicht innerhalb der angegebenen Zeit abgeschlossen wird, generiert der Befehl eine **TimeoutException** mit der Meldung „Timeout für Vorgang überschritten“.</span><span class="sxs-lookup"><span data-stu-id="e4256-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type “$x” to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a><span data-ttu-id="e4256-124">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e4256-124">Properties</span></span>

###  <span data-ttu-id="e4256-125"><a name="AddOnsMenu"></a> AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="e4256-125"><a name="AddOnsMenu"></a> AddOnsMenu</span></span>
  <span data-ttu-id="e4256-126">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-127">Die schreibgeschützte Eigenschaft, die das Add-On-Menü für die PowerShell-Registerkarte abruft.</span><span class="sxs-lookup"><span data-stu-id="e4256-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

###  <span data-ttu-id="e4256-128"><a name="CanExecute"></a> CanInvoke</span><span class="sxs-lookup"><span data-stu-id="e4256-128"><a name="CanExecute"></a> CanInvoke</span></span>
  <span data-ttu-id="e4256-129">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-130">Die schreibgeschützte boolesche Eigenschaft, die den Wert **$true** zurückgibt, wenn ein Skript mit der [Invoke( Script )](#invoke)-Methode aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="e4256-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke) method.</span></span>

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

###  <span data-ttu-id="e4256-131"><a name="Commandpane"></a> Consolepane</span><span class="sxs-lookup"><span data-stu-id="e4256-131"><a name="Commandpane"></a> Consolepane</span></span>
  <span data-ttu-id="e4256-132">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4256-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="e4256-133">In Windows PowerShell ISE 2.0 lautete der Name hierfür **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="e4256-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

 <span data-ttu-id="e4256-134">Die schreibgeschützte Eigenschaft, die das [editor](../ise/The-ISEEditor-Object.md)-Objekt des Konsolenbereichs abruft.</span><span class="sxs-lookup"><span data-stu-id="e4256-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

###  <span data-ttu-id="e4256-135"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="e4256-135"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="e4256-136">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-137">Die Lese-/Schreibeigenschaft Eigenschaft, die den auf der PowerShell-Registerkarte angezeigten Text abruft oder festlegt.</span><span class="sxs-lookup"><span data-stu-id="e4256-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab.</span></span> <span data-ttu-id="e4256-138">Standardmäßig lautet der Name von Registerkarten „PowerShell #“, wobei # eine Zahl darstellt.</span><span class="sxs-lookup"><span data-stu-id="e4256-138">By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

###  <span data-ttu-id="e4256-139"><a name="ExpandedScript"></a> ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="e4256-139"><a name="ExpandedScript"></a> ExpandedScript</span></span>
  <span data-ttu-id="e4256-140">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-141">Die Lese-/Schreibeigenschaft, die bestimmt, ob der Skript-Bereich erweitert oder ausgeblendet wird.</span><span class="sxs-lookup"><span data-stu-id="e4256-141">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

###  <span data-ttu-id="e4256-142"><a name="Files"></a> Files</span><span class="sxs-lookup"><span data-stu-id="e4256-142"><a name="Files"></a> Files</span></span>
  <span data-ttu-id="e4256-143">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-144">Die schreibgeschützte Eigenschaft, die die [Sammlung von Skriptdateien](../ise/The-ISEFileCollection-Object.md) abruft, die auf der PowerShell-Registerkarte geöffnet sind.</span><span class="sxs-lookup"><span data-stu-id="e4256-144">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

###  <span data-ttu-id="e4256-145"><a name="Output"></a> Output</span><span class="sxs-lookup"><span data-stu-id="e4256-145"><a name="Output"></a> Output</span></span>
  <span data-ttu-id="e4256-146">Dieses Feature ist in Windows PowerShell ISE 2.0 enthalten, wurde in höheren Versionen von ISE aber entfernt oder umbenannt.</span><span class="sxs-lookup"><span data-stu-id="e4256-146">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="e4256-147">In höheren Versionen von Windows PowerShell ISE können Sie das **ConsolePane**-Objekt für den gleichen Zweck verwenden.</span><span class="sxs-lookup"><span data-stu-id="e4256-147">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

 <span data-ttu-id="e4256-148">Die schreibgeschützte Eigenschaft, die den Ausgabebereich des aktuellen [editor](../ise/The-ISEEditor-Object.md) abruft.</span><span class="sxs-lookup"><span data-stu-id="e4256-148">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

###  <span data-ttu-id="e4256-149"><a name="Prompt"></a> Prompt</span><span class="sxs-lookup"><span data-stu-id="e4256-149"><a name="Prompt"></a> Prompt</span></span>
  <span data-ttu-id="e4256-150">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-150">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-151">Die schreibgeschützte Eigenschaft, die den aktuellen Aufforderungstext abruft.</span><span class="sxs-lookup"><span data-stu-id="e4256-151">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="e4256-152">Hinweis: Die **Prompt**-Funktion kann durch das Profil des Benutzers überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="e4256-152">Note: the **Prompt** function can be overridden by the user’s profile.</span></span> <span data-ttu-id="e4256-153">Wenn das Ergebnis von einer einfachen Zeichenfolge abweicht, gibt diese Eigenschaft nichts zurück.</span><span class="sxs-lookup"><span data-stu-id="e4256-153">If the result is other than a simple string, then this property returns nothing.</span></span>

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

###  <span data-ttu-id="e4256-154"><a name="ShowCommands"></a> ShowCommands</span><span class="sxs-lookup"><span data-stu-id="e4256-154"><a name="ShowCommands"></a> ShowCommands</span></span>
  <span data-ttu-id="e4256-155">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4256-155">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e4256-156">Die Lese-/Schreibeigenschaft, die angibt, ob der Befehlsbereich derzeit angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e4256-156">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

###  <span data-ttu-id="e4256-157"><a name="StatusText"></a> StatusText</span><span class="sxs-lookup"><span data-stu-id="e4256-157"><a name="StatusText"></a> StatusText</span></span>
  <span data-ttu-id="e4256-158">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e4256-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="e4256-159">Die schreibgeschützte Eigenschaft, die den **PowerShellTab**-Statustext abruft.</span><span class="sxs-lookup"><span data-stu-id="e4256-159">The read-only property that gets the **PowerShellTab** status text.</span></span>

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

###  <span data-ttu-id="e4256-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="e4256-160"><a name="HorizontalAddOnToolsPaneOpened"></a> HorizontalAddOnToolsPaneOpened</span></span>
  <span data-ttu-id="e4256-161">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4256-161">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e4256-162">Die schreibgeschützte Eigenschaft, die angibt, ob der horizontale Add-On-Toolbereich derzeit geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="e4256-162">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

###  <span data-ttu-id="e4256-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span><span class="sxs-lookup"><span data-stu-id="e4256-163"><a name="VerticalAddOnToolsPaneOpened"></a> **VerticalAddOnToolsPaneOpened**</span></span>
  <span data-ttu-id="e4256-164">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="e4256-164">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="e4256-165">Die schreibgeschützte Eigenschaft, die angibt, ob der vertikale Add-On-Toolbereich derzeit geöffnet ist.</span><span class="sxs-lookup"><span data-stu-id="e4256-165">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="e4256-166">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e4256-166">See Also</span></span>
- [<span data-ttu-id="e4256-167">Das PowerShellTabCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="e4256-167">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md) 
- [<span data-ttu-id="e4256-168">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="e4256-168">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="e4256-169">Referenz zum Windows PowerShell ISE-Objektmodell</span><span class="sxs-lookup"><span data-stu-id="e4256-169">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="e4256-170">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="e4256-170">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
