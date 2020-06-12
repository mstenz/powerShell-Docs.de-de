---
title: Skriptmodule
description: Skriptmodule sind eine einfache Möglichkeit, Skripts und Funktionen in einem wiederverwendbaren Tool zu verpacken.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438281"
---
# <a name="chapter-10---script-modules"></a><span data-ttu-id="46b9c-103">Kapitel 10: Skriptmodule</span><span class="sxs-lookup"><span data-stu-id="46b9c-103">Chapter 10 - Script modules</span></span>

<span data-ttu-id="46b9c-104">Die Umwandlung Ihrer Einzeiler und Skripts in PowerShell in wiederverwendbare Tools wird sogar noch wichtiger, wenn es sich um etwas handelt, das Sie häufig verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-104">Turning your one-liners and scripts in PowerShell into reusable tools becomes even more important if it's something that you're going to use frequently.</span></span> <span data-ttu-id="46b9c-105">Wenn Sie Ihre Funktionen in ein Skriptmodul packen, sieht dies professioneller aus, fühlt sich auch so an, und Sie können die Funktionen leichter teilen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-105">Packaging your functions in a script module makes them look and feel more professional and makes them easier to share.</span></span>

## <a name="dot-sourcing-functions"></a><span data-ttu-id="46b9c-106">Dot-Sourcing-Funktionen</span><span class="sxs-lookup"><span data-stu-id="46b9c-106">Dot-Sourcing Functions</span></span>

<span data-ttu-id="46b9c-107">Etwas, das wir im vorherigen Kapitel nicht besprochen haben, sind Dot-Sourcing-Funktionen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-107">Something that we didn't talk about in the previous chapter is dot-sourcing functions.</span></span> <span data-ttu-id="46b9c-108">Wenn eine Funktion in einem Skript nicht Teil eines Moduls ist, besteht die einzige Möglichkeit, sie in den Arbeitsspeicher zu laden, darin, ein Dot-Sourcing der Datei `.PS1` vorzunehmen, in der sie gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="46b9c-108">When a function in a script isn't part of a module, the only way to load it into memory is to dot-source the `.PS1` file that it's saved in.</span></span>

<span data-ttu-id="46b9c-109">Die folgende Funktion wurde als `Get-MrPSVersion.ps1` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="46b9c-109">The following function has been saved as `Get-MrPSVersion.ps1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

<span data-ttu-id="46b9c-110">Wenn Sie das Skript ausführen, geschieht nichts.</span><span class="sxs-lookup"><span data-stu-id="46b9c-110">When you run the script, nothing happens.</span></span>

```powershell
.\Get-MrPSVersion.ps1
```

<span data-ttu-id="46b9c-111">Wenn Sie versuchen, die-Funktion aufzurufen, wird eine Fehlermeldung generiert.</span><span class="sxs-lookup"><span data-stu-id="46b9c-111">If you try to call the function, it generates an error message.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

<span data-ttu-id="46b9c-112">Sie können bestimmen, ob Funktionen in den Arbeitsspeicher geladen wurden, indem Sie überprüfen, ob sie im PSDrive der **Funktion** vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="46b9c-112">You can determine if functions are loaded into memory by checking to see if they exist on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

<span data-ttu-id="46b9c-113">Das Problem beim Aufrufen des Skripts, das die Funktion enthält, besteht darin, dass die Funktionen in den Gültigkeitsbereich _Skript_ geladen werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-113">The problem with calling the script that contains the function is that the functions are loaded in the _Script_ scope.</span></span> <span data-ttu-id="46b9c-114">Wenn das Skript abgeschlossen ist, wird dieser Gültigkeitsbereich entfernt, und zusammen damit die Funktion.</span><span class="sxs-lookup"><span data-stu-id="46b9c-114">When the script completes, that scope is removed and the function is removed with it.</span></span>

<span data-ttu-id="46b9c-115">Die Funktion muss in den Gültigkeitsbereich _Global_ geladen werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-115">The function needs to be loaded into the _Global_ scope.</span></span> <span data-ttu-id="46b9c-116">Dies kann durch Dot-Sourcing des Skripts erreicht werden, das die Funktion enthält.</span><span class="sxs-lookup"><span data-stu-id="46b9c-116">That can be accomplished by dot-sourcing the script that contains the function.</span></span> <span data-ttu-id="46b9c-117">Der relative Pfad kann verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-117">The relative path can be used.</span></span>

```powershell
. .\Get-MrPSVersion.ps1
```

<span data-ttu-id="46b9c-118">Ebenso kann der vollqualifizierte Pfad verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-118">The fully qualified path can also be used.</span></span>

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

<span data-ttu-id="46b9c-119">Wenn ein Teil des Pfads in einer Variablen gespeichert ist, kann er mit dem Rest des Pfads kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-119">If a portion of the path is stored in a variable, it can be combined with the remainder of the path.</span></span>
<span data-ttu-id="46b9c-120">Es gibt keinen Grund, Zeichenfolgenverkettung zu verwenden, um die Variable mit dem Rest des Pfads zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="46b9c-120">There's no reason to use string concatenation to combine the variable together with the remainder of the path.</span></span>

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

<span data-ttu-id="46b9c-121">Wenn ich nun das PSDrive der **Funktion** überprüfe, ist die Funktion `Get-MrPSVersion` vorhanden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-121">Now when I check the **Function** PSDrive, the `Get-MrPSVersion` function exists.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a><span data-ttu-id="46b9c-122">Skriptmodule</span><span class="sxs-lookup"><span data-stu-id="46b9c-122">Script Modules</span></span>

<span data-ttu-id="46b9c-123">Ein Skriptmodul in PowerShell ist lediglich eine Datei, die eine oder mehrere Funktionen enthält, die als `.PSM1`-Datei gespeichert wurden, nicht als `.PS1`-Datei.</span><span class="sxs-lookup"><span data-stu-id="46b9c-123">A script module in PowerShell is simply a file containing one or more functions that's saved as a `.PSM1` file instead of a `.PS1` file.</span></span>

<span data-ttu-id="46b9c-124">Wie erstellen Sie ein Skriptmodul?</span><span class="sxs-lookup"><span data-stu-id="46b9c-124">How do you create a script module?</span></span> <span data-ttu-id="46b9c-125">Wahrscheinlich vermuten Sie schon mit einem Befehl, der ungefähr einen Namen wie `New-Module` trägt.</span><span class="sxs-lookup"><span data-stu-id="46b9c-125">You're probably guessing with a command named something like `New-Module`.</span></span> <span data-ttu-id="46b9c-126">Ihre Annahme wäre leider falsch.</span><span class="sxs-lookup"><span data-stu-id="46b9c-126">Your assumption would be wrong.</span></span> <span data-ttu-id="46b9c-127">Zwar gibt es einen Befehl namens `New-Module` in PowerShell, doch erstellt dieser Befehl ein dynamisches Modul, kein Skriptmodul.</span><span class="sxs-lookup"><span data-stu-id="46b9c-127">While there is a command in PowerShell named `New-Module`, that command creates a dynamic module, not a script module.</span></span> <span data-ttu-id="46b9c-128">Lesen Sie also immer unbedingt die Hilfe für einen Befehl, auch wenn Sie der Ansicht sind, dass Sie den benötigten Befehl gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="46b9c-128">Always be sure to read the help for a command even when you think you've found the command you need.</span></span>

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

<span data-ttu-id="46b9c-129">Im vorherigen Kapitel habe ich erwähnt, dass Funktionen genehmigte Verben verwenden sollten, da sie sonst eine Warnmeldung generieren, wenn das Modul importiert wird.</span><span class="sxs-lookup"><span data-stu-id="46b9c-129">In the previous chapter, I mentioned that functions should use approved verbs otherwise they'll generate a warning message when the module is imported.</span></span> <span data-ttu-id="46b9c-130">Der folgende Code verwendet das Cmdlet `New-Module`, um ein dynamisches Modul im Arbeitsspeicher zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-130">The following code uses the `New-Module` cmdlet to create a dynamic module in memory.</span></span> <span data-ttu-id="46b9c-131">Dieses Modul veranschaulicht die Warnung wegen nicht genehmigter Verben.</span><span class="sxs-lookup"><span data-stu-id="46b9c-131">This module demonstrates the unapproved verb warning.</span></span>

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

<span data-ttu-id="46b9c-132">Um dies noch mal zu wiederholen: Obwohl das Cmdlet `New-Module` im vorherigen Beispiel verwendet wurde, ist dies nicht der Befehl zum Erstellen von Skriptmodulen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46b9c-132">Just to reiterate, although the `New-Module` cmdlet was used in the previous example, that's not the command for creating script modules in PowerShell.</span></span>

<span data-ttu-id="46b9c-133">Speichern Sie die folgenden zwei Funktionen in einer Datei namens `MyScriptModule.psm1`.</span><span class="sxs-lookup"><span data-stu-id="46b9c-133">Save the following two functions in a file named `MyScriptModule.psm1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

<span data-ttu-id="46b9c-134">Versuchen Sie, eine der Funktionen aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-134">Try to call one of the functions.</span></span>

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="46b9c-135">Es wird eine Fehlermeldung generiert, die besagt, dass die Funktion nicht gefunden wurde.</span><span class="sxs-lookup"><span data-stu-id="46b9c-135">An error message is generated saying the function can't be found.</span></span> <span data-ttu-id="46b9c-136">Sie könnten auch das PSDrive der **Funktion** wie bereits zuvor überprüfen, und Sie werden feststellen, dass sie dort auch nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="46b9c-136">You could also check the **Function** PSDrive just like before and you'll find that it doesn't exist there either.</span></span>

<span data-ttu-id="46b9c-137">Sie könnten die Datei manuell mit dem Cmdlet `Import-Module` importieren.</span><span class="sxs-lookup"><span data-stu-id="46b9c-137">You could manually import the file with the `Import-Module` cmdlet.</span></span>

```powershell
Import-Module C:\MyScriptModule.psm1
```

<span data-ttu-id="46b9c-138">Die Funktion für das automatische Laden von Modulen wurde in PowerShell-Version 3 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="46b9c-138">The module autoloading feature was introduced in PowerShell version 3.</span></span> <span data-ttu-id="46b9c-139">Um das automatische Laden von Modulen zu nutzen, muss ein Skriptmodul in einem Ordner mit demselben Basisnamen wie die Datei `.PSM1` sowie an einem in `$env:PSModulePath` angegebenen Speicherort gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-139">To take advantage of module autoloading, a script module needs to be saved in a folder with the same base name as the `.PSM1` file and in a location specified in `$env:PSModulePath`.</span></span>

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="46b9c-140">Die Ergebnisse sind schwer zu lesen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-140">The results are difficult to read.</span></span> <span data-ttu-id="46b9c-141">Da die Pfade durch ein Semikolon getrennt sind, können Sie die Ergebnisse so aufteilen, dass jeder Pfad in einer separaten Zeile zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="46b9c-141">Since the paths are separated by a semicolon, you can split the results to return each path on a separate line.</span></span> <span data-ttu-id="46b9c-142">Dies vereinfacht das Lesen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-142">This makes them easier to read.</span></span>

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="46b9c-143">Die ersten drei Pfade in der Liste sind die Standardwerte.</span><span class="sxs-lookup"><span data-stu-id="46b9c-143">The first three paths in the list are the default.</span></span> <span data-ttu-id="46b9c-144">Wenn SQL Server Management Studio installiert ist, wurde der letzte Pfad davon hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="46b9c-144">When SQL Server Management Studio was installed, it added the last path.</span></span> <span data-ttu-id="46b9c-145">Damit das automatische Laden von Modulen funktioniert, muss sich die Datei `MyScriptModule.psm1` in einem Ordner namens `MyScriptModule` direkt innerhalb eines dieser Pfade befinden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-145">For module autoloading to work, the `MyScriptModule.psm1` file needs to be located in a folder named `MyScriptModule` directly inside one of those paths.</span></span>

<span data-ttu-id="46b9c-146">Nicht so schnell.</span><span class="sxs-lookup"><span data-stu-id="46b9c-146">Not so fast.</span></span> <span data-ttu-id="46b9c-147">Bei mir ist mein aktueller Benutzerpfad nicht der erste in der Liste.</span><span class="sxs-lookup"><span data-stu-id="46b9c-147">For me, my current user path isn't the first one in the list.</span></span> <span data-ttu-id="46b9c-148">Ich verwende diesen Pfad fast nie, da ich mich bei Windows mit einem anderen Benutzer anmelde als dem, den ich zum Ausführen von PowerShell verwende.</span><span class="sxs-lookup"><span data-stu-id="46b9c-148">I almost never use that path since I log into Windows with a different user than the one I use to run PowerShell.</span></span> <span data-ttu-id="46b9c-149">Dies bedeutet, dass er sich nicht in meinem normalen Ordner „Dokumente“ befindet.</span><span class="sxs-lookup"><span data-stu-id="46b9c-149">That means it's not located in my normal Documents folder.</span></span>

<span data-ttu-id="46b9c-150">Der zweite Pfad ist der Pfad **AllUsers**.</span><span class="sxs-lookup"><span data-stu-id="46b9c-150">The second path is the **AllUsers** path.</span></span> <span data-ttu-id="46b9c-151">Dies ist der Speicherort, an dem ich alle meine Module speichere.</span><span class="sxs-lookup"><span data-stu-id="46b9c-151">This is the location where I store all of my modules.</span></span>

<span data-ttu-id="46b9c-152">Der dritte Pfad befindet sich unter `C:\Windows\System32`.</span><span class="sxs-lookup"><span data-stu-id="46b9c-152">The third path is underneath `C:\Windows\System32`.</span></span> <span data-ttu-id="46b9c-153">Nur Microsoft sollte Module an diesem Speicherort speichern, da es sich im Betriebssystemordner befindet.</span><span class="sxs-lookup"><span data-stu-id="46b9c-153">Only Microsoft should be storing modules in that location since it resides within the operating systems folder.</span></span>

<span data-ttu-id="46b9c-154">Sobald sich die Datei `.PSM1` im richtigen Pfad befindet, wird das Modul automatisch geladen, wenn einer seiner Befehle aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="46b9c-154">Once the `.PSM1` file is located in the correct path, the module will load automatically when one of its commands is called.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="46b9c-155">Modulmanifeste</span><span class="sxs-lookup"><span data-stu-id="46b9c-155">Module Manifests</span></span>

<span data-ttu-id="46b9c-156">Alle Module sollten über ein Modulmanifest verfügen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-156">All modules should have a module manifest.</span></span> <span data-ttu-id="46b9c-157">Ein Modulmanifest enthält Metadaten zu Ihrem Modul.</span><span class="sxs-lookup"><span data-stu-id="46b9c-157">A module manifest contains metadata about your module.</span></span>
<span data-ttu-id="46b9c-158">Die Dateierweiterung für eine Modulmanifestdatei lautet `.PSD1`.</span><span class="sxs-lookup"><span data-stu-id="46b9c-158">The file extension for a module manifest file is `.PSD1`.</span></span> <span data-ttu-id="46b9c-159">Nicht alle Dateien mit einer `.PSD1`-Erweiterung sind Modulmanifeste.</span><span class="sxs-lookup"><span data-stu-id="46b9c-159">Not all files with a `.PSD1` extension are module manifests.</span></span> <span data-ttu-id="46b9c-160">Sie können auch für Dinge verwendet werden wie das Speichern des Umgebungsteils einer DSC-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="46b9c-160">They can also be used for things such as storing the environmental portion of a DSC configuration.</span></span> <span data-ttu-id="46b9c-161">`New-ModuleManifest` wird verwendet, um ein Modulmanifest zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-161">`New-ModuleManifest` is used to create a module manifest.</span></span> <span data-ttu-id="46b9c-162">**Path** ist der einzige erforderliche Wert.</span><span class="sxs-lookup"><span data-stu-id="46b9c-162">**Path** is the only value that's required.</span></span> <span data-ttu-id="46b9c-163">Das Modul funktioniert jedoch nicht, wenn **RootModule** nicht angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="46b9c-163">However, the module won't work if **RootModule** isn't specified.</span></span> <span data-ttu-id="46b9c-164">Es empfiehlt sich, **Author** und **Description** anzugeben für den Fall, dass Sie sich entschließen, das Modul mit „PowerShellGet“ in ein NuGet-Repository hochzuladen, da diese Werte in diesem Szenario erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="46b9c-164">It's a good idea to specify **Author** and **Description** in case you decide to upload your module to a NuGet repository with PowerShellGet since those values are required in that scenario.</span></span>

<span data-ttu-id="46b9c-165">Die Version eines Moduls ohne Manifest ist 0.0.</span><span class="sxs-lookup"><span data-stu-id="46b9c-165">The version of a module without a manifest is 0.0.</span></span> <span data-ttu-id="46b9c-166">Dies ist ein untrügliches Zeichen dafür, dass das Modul kein Manifest besitzt.</span><span class="sxs-lookup"><span data-stu-id="46b9c-166">This is a dead giveaway that the module doesn't have a manifest.</span></span>

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

<span data-ttu-id="46b9c-167">Das Modulmanifest kann mit allen empfohlenen Informationen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-167">The module manifest can be created with all of the recommended information.</span></span>

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

<span data-ttu-id="46b9c-168">Fehlt eine dieser Informationen bei der anfänglichen Erstellung des Modulmanifests, kann sie später mithilfe von `Update-ModuleManifest` hinzugefügt oder aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-168">If any of this information is missed during the initial creation of the module manifest, it can be added or updated later using `Update-ModuleManifest`.</span></span> <span data-ttu-id="46b9c-169">Erstellen Sie das Manifest nicht mit `New-ModuleManifest` neu, nachdem es bereits erstellt wurde, weil sich sonst die GUID ändert.</span><span class="sxs-lookup"><span data-stu-id="46b9c-169">Don't recreate the manifest using `New-ModuleManifest` once it's already created because the GUID will change.</span></span>

## <a name="defining-public-and-private-functions"></a><span data-ttu-id="46b9c-170">Definieren öffentlicher und privater Funktionen</span><span class="sxs-lookup"><span data-stu-id="46b9c-170">Defining Public and Private Functions</span></span>

<span data-ttu-id="46b9c-171">Möglicherweise verfügen Sie über Hilfsfunktionen, die privat sein sollen und auf die nur Funktionen innerhalb des Moduls zugreifen können sollen.</span><span class="sxs-lookup"><span data-stu-id="46b9c-171">You may have helper functions that you may want to be private and only accessible by other functions within the module.</span></span> <span data-ttu-id="46b9c-172">Benutzer Ihres Moduls sollen nicht darauf zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="46b9c-172">They are not intended to be accessible to users of your module.</span></span> <span data-ttu-id="46b9c-173">Dies kann auf unterschiedliche Arten erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-173">There are a couple of different ways to accomplish this.</span></span>

<span data-ttu-id="46b9c-174">Wenn Sie die bewährten Methoden nicht befolgen und nur eine `.PSM1`-Datei besitzen, besteht Ihre einzige Möglichkeit darin, das Cmdlet `Export-ModuleMember` zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-174">If you're not following the best practices and only have a `.PSM1` file, then your only option is to use the `Export-ModuleMember` cmdlet.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

<span data-ttu-id="46b9c-175">Im vorherigen Beispiel ist nur die Funktion `Get-MrPSVersion` für die Benutzer Ihres Moduls verfügbar, aber die Funktion `Get-MrComputerName` steht anderen Funktionen im Modul selbst zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="46b9c-175">In the previous example, only the `Get-MrPSVersion` function is available to the users of your module, but the `Get-MrComputerName` function is available to other functions within the module itself.</span></span>

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

<span data-ttu-id="46b9c-176">Wenn Sie Ihrem Modul ein Modulmanifest hinzugefügt haben (und dies sollten Sie), empfehle ich, die einzelnen Funktionen, die Sie exportieren möchten, im Abschnitt **FunctionsToExport** des Modulmanifests anzugeben.</span><span class="sxs-lookup"><span data-stu-id="46b9c-176">If you've added a module manifest to your module (and you should), then I recommend specifying the individual functions you want to export in the **FunctionsToExport** section of the module manifest.</span></span>

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

<span data-ttu-id="46b9c-177">Es ist nicht erforderlich, `Export-ModuleMember` sowohl in der `.PSM1`-Datei als auch im Abschnitt **FunctionsToExport** des Modulmanifests zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="46b9c-177">It's not necessary to use both `Export-ModuleMember` in the `.PSM1` file and the **FunctionsToExport** section of the module manifest.</span></span> <span data-ttu-id="46b9c-178">Das eine oder das andere ist ausreichend.</span><span class="sxs-lookup"><span data-stu-id="46b9c-178">One or the other is sufficient.</span></span>

## <a name="summary"></a><span data-ttu-id="46b9c-179">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="46b9c-179">Summary</span></span>

<span data-ttu-id="46b9c-180">In diesem Kapitel haben Sie erfahren, wie Sie Ihre Funktionen in ein Skriptmodul in PowerShell umwandeln.</span><span class="sxs-lookup"><span data-stu-id="46b9c-180">In this chapter you've learned how to turn your functions into a script module in PowerShell.</span></span> <span data-ttu-id="46b9c-181">Sie haben außerdem einige bewährte Methoden zum Erstellen von Skriptmodulen kennen gelernt, wie das Erstellen eines Modulmanifests für Ihr Skriptmodul.</span><span class="sxs-lookup"><span data-stu-id="46b9c-181">You've also leaned some of the best practices for creating script modules such as creating a module manifest for your script module.</span></span>

## <a name="review"></a><span data-ttu-id="46b9c-182">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="46b9c-182">Review</span></span>

1. <span data-ttu-id="46b9c-183">Wie erstellen Sie ein Skriptmodul in PowerShell?</span><span class="sxs-lookup"><span data-stu-id="46b9c-183">How do you create a script module in PowerShell?</span></span>
1. <span data-ttu-id="46b9c-184">Warum ist es wichtig, dass ihre Funktionen ein genehmigtes Verb verwenden?</span><span class="sxs-lookup"><span data-stu-id="46b9c-184">Why is it important for your functions to use an approved verb?</span></span>
1. <span data-ttu-id="46b9c-185">Wie erstellen Sie ein Modulmanifest in PowerShell?</span><span class="sxs-lookup"><span data-stu-id="46b9c-185">How do you create a module manifest in PowerShell?</span></span>
1. <span data-ttu-id="46b9c-186">Welche zwei Optionen sind zum Exportieren von nur bestimmten Funktionen aus Ihrem Modul verfügbar?</span><span class="sxs-lookup"><span data-stu-id="46b9c-186">What are the two options for exporting only certain functions from your module?</span></span>
1. <span data-ttu-id="46b9c-187">Was ist erforderlich, damit Ihre Module automatisch geladen werden, wenn ein Befehl aufgerufen wird?</span><span class="sxs-lookup"><span data-stu-id="46b9c-187">What is required for your modules to load automatically when a command is called?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="46b9c-188">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="46b9c-188">Recommended Reading</span></span>

- <span data-ttu-id="46b9c-189">[Erstellen von PowerShell-Skriptmodulen und Modulmanifesten][]</span><span class="sxs-lookup"><span data-stu-id="46b9c-189">[How to Create PowerShell Script Modules and Module Manifests][]</span></span>
- <span data-ttu-id="46b9c-190">[about_Modules][]</span><span class="sxs-lookup"><span data-stu-id="46b9c-190">[about_Modules][]</span></span>
- <span data-ttu-id="46b9c-191">[New-ModuleManifest][]</span><span class="sxs-lookup"><span data-stu-id="46b9c-191">[New-ModuleManifest][]</span></span>
- <span data-ttu-id="46b9c-192">[Export-ModuleMember][]</span><span class="sxs-lookup"><span data-stu-id="46b9c-192">[Export-ModuleMember][]</span></span>

<!-- link references -->
[Erstellen von PowerShell-Skriptmodulen und Modulmanifesten]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
