---
title: Functions
description: Mit PowerShell-Funktionen können Sie Tools erstellen, die in Skripts wiederverwendet werden können.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ca48f3020fa306f8a24328bd18648d5954c48a94
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438201"
---
# <a name="chapter-9---functions"></a><span data-ttu-id="3a4ef-103">Kapitel 9: Funktionen</span><span class="sxs-lookup"><span data-stu-id="3a4ef-103">Chapter 9 - Functions</span></span>

<span data-ttu-id="3a4ef-104">Wenn Sie PowerShell-Einzeiler oder -Skripts schreiben und diese häufig für verschiedene Szenarien ändern müssen, besteht die Möglichkeit, dass es sich dabei um einen guten Kandidaten handelt, um in eine Funktion umgewandelt zu werden, die wiederverwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-104">If you're writing PowerShell one-liners or scripts and find yourself often having to modify them for different scenarios, there's a good chance that it's a good candidate to be turned into a function that can be reused.</span></span>

<span data-ttu-id="3a4ef-105">Wann immer es möglich ist, ziehe ich es vor, Funktionen zu schreiben, da Sie wesentlich toolorientierter sind.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-105">Whenever possible, I prefer to write functions because they are more tool oriented.</span></span> <span data-ttu-id="3a4ef-106">Ich kann die Funktionen in einem Skriptmodul ablegen, dieses Modul in `$env:PSModulePath` platzieren und die Funktionen aufrufen, ohne physisch ihren Speicherort auffinden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-106">I can put the functions in a script module, put that module in the `$env:PSModulePath`, and call the functions without needing to physically locate where they're saved.</span></span> <span data-ttu-id="3a4ef-107">Mithilfe des PowerShellGet-Moduls lassen sich diese Module ganz einfach in einem NuGet-Repository freigeben.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-107">Using the PowerShellGet module, it's easy to share those modules in a NuGet repository.</span></span> <span data-ttu-id="3a4ef-108">„PowerShellGet“ ist im Lieferumfang von PowerShell, Version 5.0 und höher, enthalten.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-108">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="3a4ef-109">Es steht als getrennter Download für PowerShell, Version 3.0 und höher, zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-109">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="3a4ef-110">Machen Sie Dinge nicht komplizierter, als sie sind.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-110">Don't over complicate things.</span></span> <span data-ttu-id="3a4ef-111">Halten Sie es einfach, und verwenden Sie die direkteste Methode zum Ausführen einer Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-111">Keep it simple and use the most straight forward way to accomplish a task.</span></span> <span data-ttu-id="3a4ef-112">Vermeiden Sie Aliase und Positionsparameter in Code, den Sie wiederverwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-112">Avoid aliases and positional parameters in any code that you reuse.</span></span> <span data-ttu-id="3a4ef-113">Formatieren Sie Ihren Code für bessere Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-113">Format your code for readability.</span></span> <span data-ttu-id="3a4ef-114">Keine Hartcodierung von Parametern, verwenden Sie Parameter und Variablen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-114">Don't hardcode values; use parameters and variables.</span></span> <span data-ttu-id="3a4ef-115">Schreiben Sie keinen unnötigen Code, auch nicht, wenn dadurch nichts beeinträchtigt wird.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-115">Don't write unnecessary code even if it doesn't hurt anything.</span></span> <span data-ttu-id="3a4ef-116">Es erhöht die Komplexität unnötigerweise.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-116">It adds unnecessary complexity.</span></span> <span data-ttu-id="3a4ef-117">Details sind beim Schreiben von PowerShell-Code von großer Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-117">Attention to detail goes a long way when writing any PowerShell code.</span></span>

## <a name="naming"></a><span data-ttu-id="3a4ef-118">Benennung</span><span class="sxs-lookup"><span data-stu-id="3a4ef-118">Naming</span></span>

<span data-ttu-id="3a4ef-119">Wenn Sie Ihre Funktionen in PowerShell benennen, verwenden Sie einen [Pascal-Schreibweise][]-Namen mit einem genehmigten Verb und einem Nomen im Singular.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-119">When naming your functions in PowerShell, use a [Pascal case][] name with an approved verb and a singular noun.</span></span> <span data-ttu-id="3a4ef-120">Ich empfehle außerdem, dem Nomen ein Präfix voranzustellen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-120">I also recommend prefixing the noun.</span></span> <span data-ttu-id="3a4ef-121">Beispiel: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-121">For example: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span></span>

<span data-ttu-id="3a4ef-122">In PowerShell gibt es eine spezifische Liste mit genehmigten Verben, die Sie durch Ausführen von `Get-Verb` abrufen können.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-122">In PowerShell, there's a specific list of approved verbs that can be obtained by running `Get-Verb`.</span></span>

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

<span data-ttu-id="3a4ef-123">Im vorherigen Beispiel habe ich die Ergebnisse nach der Spalte **Verb** sortiert.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-123">In the previous example, I've sorted the results by the **Verb** column.</span></span> <span data-ttu-id="3a4ef-124">Die Spalte **Gruppe** vermittelt Ihnen eine Idee davon, wie diese Verben verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-124">The **Group** column gives you an idea of how these verbs are used.</span></span> <span data-ttu-id="3a4ef-125">Es ist wichtig, ein genehmigtes Verb in PowerShell auszuwählen, wenn Funktionen zu einem Modul hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-125">It's important to choose an approved verb in PowerShell when functions are added to a module.</span></span> <span data-ttu-id="3a4ef-126">Das Modul generiert eine Warnmeldung zur Ladezeit, wenn Sie ein nicht genehmigtes Verb auswählen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-126">The module generates a warning message at load time if you choose an unapproved verb.</span></span> <span data-ttu-id="3a4ef-127">Eine solche Warnmeldung lässt ihre Funktionen unprofessionell aussehen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-127">That warning message makes your functions look unprofessional.</span></span> <span data-ttu-id="3a4ef-128">Nicht genehmigte Verben schränken außerdem die Auffindbarkeit ihrer Funktionen ein.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-128">Unapproved verbs also limit the discoverability of your functions.</span></span>

## <a name="a-simple-function"></a><span data-ttu-id="3a4ef-129">Eine einfache Funktion</span><span class="sxs-lookup"><span data-stu-id="3a4ef-129">A simple function</span></span>

<span data-ttu-id="3a4ef-130">Eine Funktion in PowerShell wird mit dem Schlüsselwort „function“, gefolgt vom Funktionsnamen und einer geöffneten und einer schließenden geschweiften Klammer, deklariert.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-130">A function in PowerShell is declared with the function keyword followed by the function name and then an open and closing curly brace.</span></span> <span data-ttu-id="3a4ef-131">Der Code, der von der Funktion ausgeführt wird, steht in diesen geschweiften Klammern.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-131">The code that the function will execute is contained within those curly braces.</span></span>

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="3a4ef-132">Die gezeigte Funktion ist ein einfaches Beispiel, das die Version von PowerShell zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-132">The function shown is a simple example that returns the version of PowerShell.</span></span>

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="3a4ef-133">Es besteht eine hohe Wahrscheinlichkeit, dass Namenskonflikte mit ähnlich wie `Get-Version` benamten Funktionen, Standardbefehlen in PowerShell und Befehlen, die andere Benutzer möglicherweise schreiben, auftreten können.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-133">There's a good chance of name conflict with functions named something like `Get-Version` and default commands in PowerShell or commands that others may write.</span></span> <span data-ttu-id="3a4ef-134">Aus diesem Grund empfehle ich, dem Nomen-Teil Ihrer Funktionen ein Präfix voranzustellen, um Namenskonflikten vorzubeugen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-134">This is why I recommend prefixing the noun portion of your functions to help prevent naming conflicts.</span></span> <span data-ttu-id="3a4ef-135">Im folgenden Beispiel verwende ich das Präfix „PS“.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-135">In the following example, I'll use the prefix "PS".</span></span>

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="3a4ef-136">Mit Ausnahme des Namens ist diese Funktion mit der vorherigen identisch.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-136">Other than the name, this function is identical to the previous one.</span></span>

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="3a4ef-137">Selbst wenn Sie dem Nomen ein Präfix wie „PS“ voranstellen, besteht immer noch eine hohe Wahrscheinlichkeit, dass ein Namenskonflikt auftritt.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-137">Even when prefixing the noun with something like PS, there's still a good chance of having a name conflict.</span></span> <span data-ttu-id="3a4ef-138">Ich stelle meinen Funktions-Nomen normalerweise meine Initialen als Präfix voran.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-138">I typically prefix my function nouns with my initials.</span></span> <span data-ttu-id="3a4ef-139">Entwickeln Sie einen Standard, und halten Sie ihn ein.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-139">Develop a standard and stick to it.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="3a4ef-140">Diese Funktion unterscheidet sich von den beiden vorhergehenden nur durch die Verwendung eines sinnvolleren Namens, um Namenskonflikte mit anderen PowerShell-Befehlen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-140">This function is no different than the previous two other than using a more sensible name to try to prevent naming conflicts with other PowerShell commands.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="3a4ef-141">Nachdem Sie in den Arbeitsspeicher geladen wurde, können Sie Funktionen auf dem PSDrive **Function** sehen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-141">Once loaded into memory, you can see functions on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

<span data-ttu-id="3a4ef-142">Wenn Sie diese Funktionen aus Ihrer aktuellen Sitzung entfernen möchten, müssen Sie sie aus dem PSDrive **Function** entfernen oder PowerShell schließen und neu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-142">If you want to remove these functions from your current session, you'll have to remove them from the **Function** PSDrive or close and reopen PowerShell.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

<span data-ttu-id="3a4ef-143">Vergewissern Sie sich, dass die Funktionen tatsächlich entfernt wurden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-143">Verify that the functions were indeed removed.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

<span data-ttu-id="3a4ef-144">Wenn die Funktionen als Teil eines Moduls geladen wurden, kann das Modul entladen werden, um sie zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-144">If the functions were loaded as part of a module, the module can be unloaded to remove them.</span></span>

```powershell
Remove-Module -Name <ModuleName>
```

<span data-ttu-id="3a4ef-145">Das Cmdlet `Remove-Module` entfernt Module aus dem Arbeitsspeicher in Ihrer aktuellen PowerShell-Sitzung, entfernt sie aber nicht von Ihrem System oder vom Datenträger.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-145">The `Remove-Module` cmdlet removes modules from memory in your current PowerShell session, it doesn't remove them from your system or from disk.</span></span>

## <a name="parameters"></a><span data-ttu-id="3a4ef-146">Parameter</span><span class="sxs-lookup"><span data-stu-id="3a4ef-146">Parameters</span></span>

<span data-ttu-id="3a4ef-147">Weisen Sie keine Werte statisch zu!</span><span class="sxs-lookup"><span data-stu-id="3a4ef-147">Don't statically assign values!</span></span> <span data-ttu-id="3a4ef-148">Verwenden Sie Parameter und Variablen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-148">Use parameters and variables.</span></span> <span data-ttu-id="3a4ef-149">Wenn Sie Ihre Parameter benennen möchten, verwenden Sie dieselben Namen wie die Standard-Cmdlets für Ihre Parameternamen, wann immer dies möglich ist.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-149">When it comes to naming your parameters, use the same name as the default cmdlets for your parameter names whenever possible.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-150">Warum habe ich **ComputerName** und nicht **Computer**, **ServerName**oder **Host** als meinen Parameternamen verwendet?</span><span class="sxs-lookup"><span data-stu-id="3a4ef-150">Why did I use **ComputerName** and not **Computer**, **ServerName**, or **Host** for my parameter name?</span></span> <span data-ttu-id="3a4ef-151">Das liegt daran, dass meine Funktion so standardisiert wie die Standard-Cmdlets sein sollte.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-151">It's because I wanted my function standardized like the default cmdlets.</span></span>

<span data-ttu-id="3a4ef-152">Ich erstelle eine Funktion, um alle Befehle in einem System abzufragen und die Anzahl der Befehle zurückzugeben, die über bestimmte Parameternamen verfügen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-152">I'll create a function to query all of the commands on a system and return the number of them that have specific parameter names.</span></span>

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

<span data-ttu-id="3a4ef-153">Wie Sie in den unten gezeigten Ergebnissen sehen können, besitzen 39 Befehle einen Parameter **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-153">As you can see in the results shown below, 39 commands that have a **ComputerName** parameter.</span></span> <span data-ttu-id="3a4ef-154">Es gibt keine Cmdlets, die Parameter wie **Computer**, **ServerName**, **Host**oder **Machine** haben.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-154">There aren't any cmdlets that have parameters such as **Computer**, **ServerName**, **Host**, or **Machine**.</span></span>

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

<span data-ttu-id="3a4ef-155">Ich empfehle außerdem, dieselbe Groß-/Kleinschreibung für Ihre Parameternamen wie bei den Standard-Cmdlets zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-155">I also recommend using the same case for your parameter names as the default cmdlets.</span></span> <span data-ttu-id="3a4ef-156">Verwenden Sie `ComputerName`, nicht `computername`.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-156">Use `ComputerName`, not `computername`.</span></span> <span data-ttu-id="3a4ef-157">Dadurch sehen ihre Funktionen wie die Standard-Cmdlets aus und verhalten sich auch so.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-157">This makes your functions look and feel like the default cmdlets.</span></span> <span data-ttu-id="3a4ef-158">Personen, die bereits mit PowerShell vertraut sind, werden sich sofort wohlfühlen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-158">People who are already familiar with PowerShell will feel right at home.</span></span>

## <a name="advanced-functions"></a><span data-ttu-id="3a4ef-159">Erweiterte Funktionen</span><span class="sxs-lookup"><span data-stu-id="3a4ef-159">Advanced Functions</span></span>

<span data-ttu-id="3a4ef-160">Eine Funktion in PowerShell in eine erweiterte Funktion umzuwandeln, ist wirklich einfach.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-160">Turning a function in PowerShell into an advanced function is really simple.</span></span> <span data-ttu-id="3a4ef-161">Einer der Unterschiede zwischen einer Funktion und einer erweiterten Funktion besteht darin, dass erweiterte Funktionen über eine Reihe allgemeiner Parameter verfügen, die der Funktion automatisch hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-161">One of the differences between a function and an advanced function is that advanced functions have a number of common parameters that are added to the function automatically.</span></span> <span data-ttu-id="3a4ef-162">Zu diesen allgemeinen Parametern zählen Parameter wie **Verbose** und **Debug**.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-162">These common parameters include parameters such as **Verbose** and **Debug**.</span></span>

<span data-ttu-id="3a4ef-163">Ich beginne mit der `Test-MrParameter`-Funktion, die im vorherigen Abschnitt verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-163">I'll start out with the `Test-MrParameter` function that was used in the previous section.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-164">Beachten Sie hierbei, dass die `Test-MrParameter`-Funktion keine allgemeinen Parameter besitzt.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-164">What I want you to notice is that the `Test-MrParameter` function doesn't have any common parameters.</span></span> <span data-ttu-id="3a4ef-165">Es gibt eine Reihe unterschiedlicher Möglichkeiten, um die allgemeinen Parameter anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-165">There are a couple of different ways to see the common parameters.</span></span> <span data-ttu-id="3a4ef-166">Eine besteht darin, die Syntax mithilfe von `Get-Command` anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-166">One is by viewing the syntax using `Get-Command`.</span></span>

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

<span data-ttu-id="3a4ef-167">Eine andere besteht darin, mit `Get-Command` Detailinformationen zu den Parametern anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-167">Another is to drill down into the parameters with `Get-Command`.</span></span>

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

<span data-ttu-id="3a4ef-168">Fügen Sie `CmdletBinding` hinzu, um die Funktion in eine erweiterte Funktion umzuwandeln.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-168">Add `CmdletBinding` to turn the function into an advanced function.</span></span>

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-169">Beim Hinzufügen von `CmdletBinding` werden die allgemeinen Parameter automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-169">Adding `CmdletBinding` adds the common parameters automatically.</span></span> <span data-ttu-id="3a4ef-170">`CmdletBinding` erfordert einen `param`-Block, doch dieser `param`-Block kann leer sein.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-170">`CmdletBinding` requires a `param` block, but the `param` block can be empty.</span></span>

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

<span data-ttu-id="3a4ef-171">Beim Anzeigen von Detailinformationen zu den Parametern mithilfe von `Get-Command` werden die tatsächlichen Parameternamen angezeigt, einschließlich der allgemeinen Parameternamen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-171">Drilling down into the parameters with `Get-Command` shows the actual parameter names including the common ones.</span></span>

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="3a4ef-172">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="3a4ef-172">SupportsShouldProcess</span></span>

<span data-ttu-id="3a4ef-173">`SupportsShouldProcess` fügt die Parameter **WhatIf** und **Confirm** hinzu.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-173">`SupportsShouldProcess` adds **WhatIf** and **Confirm** parameters.</span></span> <span data-ttu-id="3a4ef-174">Diese werden nur für Befehle benötigt, die Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-174">These are only needed for commands that make changes.</span></span>

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-175">Beachten Sie, dass nun die Parameter **WhatIf** und **Confirm** vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-175">Notice that there are now **WhatIf** and **Confirm** parameters.</span></span>

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="3a4ef-176">Auch hier können Sie mit `Get-Command` eine Liste der tatsächlichen Parameternamen zurückgeben, einschließlich der allgemeinen Parameternamen zusammen mit „WhatIf“ und „Confirm“.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-176">Once again, you can also use `Get-Command` to return a list of the actual parameter names including the common ones along with WhatIf and Confirm.</span></span>

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a><span data-ttu-id="3a4ef-177">Parameterüberprüfung</span><span class="sxs-lookup"><span data-stu-id="3a4ef-177">Parameter Validation</span></span>

<span data-ttu-id="3a4ef-178">Überprüfen Sie Eingaben frühzeitig.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-178">Validate input early on.</span></span> <span data-ttu-id="3a4ef-179">Warum sollten Sie die Fortsetzung Ihres Codes auf einem Pfad zulassen, wenn er nicht ohne gültige Eingaben ausgeführt werden kann?</span><span class="sxs-lookup"><span data-stu-id="3a4ef-179">Why allow your code to continue on a path when it's not possible to run without valid input?</span></span>

<span data-ttu-id="3a4ef-180">Geben Sie immer die Variablen ein, die für Ihre Parameter verwendet werden (geben Sie einen Datentyp an).</span><span class="sxs-lookup"><span data-stu-id="3a4ef-180">Always type the variables that are being used for your parameters (specify a datatype).</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-181">Im vorherigen Beispiel habe ich **String** als Datentyp für den Parameter **ComputerName** angegeben.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-181">In the previous example, I've specified **String** as the datatype for the **ComputerName** parameter.</span></span> <span data-ttu-id="3a4ef-182">Dies bewirkt, dass nur ein einzelner Computername angegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-182">This causes it to allow only a single computer name to be specified.</span></span> <span data-ttu-id="3a4ef-183">Wird mehr als ein Computername über eine durch Trennzeichen getrennte Liste angegeben, wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-183">If more than one computer name is specified via a comma-separated list, an error is generated.</span></span>

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

<span data-ttu-id="3a4ef-184">Das Problem bei der aktuellen Definition besteht darin, dass es zulässig ist, den Wert des Parameters **ComputerName** auszulassen, wobei aber ein Wert erforderlich ist, damit die Funktion erfolgreich abgeschlossen werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-184">The problem with the current definition is that it's valid to omit the value of the **ComputerName** parameter, but a value is required for the function to complete successfully.</span></span> <span data-ttu-id="3a4ef-185">An dieser Stelle ist das Parameterattribut `Mandatory` äußerst praktisch.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-185">This is where the `Mandatory` parameter attribute comes in handy.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-186">Die im vorherigen Beispiel verwendete Syntax ist kompatibel mit PowerShell, Version 3.0 und höher.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-186">The syntax used in the previous example is PowerShell version 3.0 and higher compatible.</span></span>
<span data-ttu-id="3a4ef-187">`[Parameter(Mandatory=$true)]` könnte stattdessen angegeben werden, um die Funktion mit PowerShell, Version 2.0 und höher, kompatibel zu machen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-187">`[Parameter(Mandatory=$true)]` could be specified instead to make the function compatible with PowerShell version 2.0 and higher.</span></span> <span data-ttu-id="3a4ef-188">Nachdem der **ComputerName** nun erforderlich ist, fordert die Funktion zu seiner Eingabe auf, wenn keiner angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-188">Now that the **ComputerName** is required, if one isn't specified, the function will prompt for one.</span></span>

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

<span data-ttu-id="3a4ef-189">Wenn Sie mehr als einen Wert für den Parameter **ComputerName** zulassen möchten, verwenden Sie den Datentyp **String**, aber fügen Sie dem Datentyp öffnende und schließende eckige Klammern hinzu, um ein Array von Zeichenfolgen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-189">If you want to allow for more than one value for the **ComputerName** parameter, use the **String** datatype but add open and closed square brackets to the datatype to allow for an array of strings.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-190">Möglicherweise möchten Sie einen Standardwert für den Parameter **ComputerName** angeben, wenn kein Wert angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-190">Maybe you want to specify a default value for the **ComputerName** parameter if one isn't specified.</span></span>
<span data-ttu-id="3a4ef-191">Das Problem hierbei ist, dass Standardwerte nicht mit obligatorischen Parametern verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-191">The problem is that default values can't be used with mandatory parameters.</span></span> <span data-ttu-id="3a4ef-192">Stattdessen müssen Sie das Parameterüberprüfungsattribut `ValidateNotNullOrEmpty` mit einem Standardwert verwenden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-192">Instead, you'll need to use the `ValidateNotNullOrEmpty` parameter validation attribute with a default value.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3a4ef-193">Selbst wenn Sie einen Standardwert festlegen, versuchen Sie, keine statischen Werte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-193">Even when setting a default value, try not to use static values.</span></span> <span data-ttu-id="3a4ef-194">Im vorherigen Beispiel wird `$env:COMPUTERNAME` als Standardwert verwendet, der automatisch in den Namen des lokalen Computers übersetzt wird, wenn kein Wert angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-194">In the previous example, `$env:COMPUTERNAME` is used as the default value, which is automatically translated into the local computer name if a value is not provided.</span></span>

## <a name="verbose-output"></a><span data-ttu-id="3a4ef-195">Ausführliche Ausgabe (Verbose)</span><span class="sxs-lookup"><span data-stu-id="3a4ef-195">Verbose Output</span></span>

<span data-ttu-id="3a4ef-196">Inlinekommentare sind zwar nützlich, insbesondere, wenn Sie komplexen Code schreiben, doch der Benutzer bekommt sie nur zu Gesicht, wenn er sich den Code ansieht.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-196">While inline comments are useful, especially if you're writing some complex code, they never get seen by users unless they look into the code itself.</span></span>

<span data-ttu-id="3a4ef-197">Die im folgenden Beispiel gezeigte Funktion hat einen Inlinekommentar in der `foreach`-Schleife.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-197">The function shown in the following example has an inline comment in the `foreach` loop.</span></span> <span data-ttu-id="3a4ef-198">Dieser spezielle Kommentar mag nicht schwer aufzufinden sein, doch stellen Sie sich vor, dass die Funktion Hunderte von Codezeilen enthielte.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-198">While this particular comment may not be that difficult to locate, imagine if the function included hundreds of lines of code.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

<span data-ttu-id="3a4ef-199">Eine bessere Option ist die Verwendung von `Write-Verbose` anstelle von Inlinekommentaren.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-199">A better option is to use `Write-Verbose` instead of inline comments.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

<span data-ttu-id="3a4ef-200">Wenn die Funktion ohne den Parameter **Verbose** aufgerufen wird, wird die ausführliche Ausgabe nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-200">When the function is called without the **Verbose** parameter, the verbose output won't be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

<span data-ttu-id="3a4ef-201">Wenn sie mit dem Parameter **Verbose** aufgerufen wird, wird die ausführliche Ausgabe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-201">When it's called with the **Verbose** parameter, the verbose output will be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a><span data-ttu-id="3a4ef-202">Pipelineeingabe</span><span class="sxs-lookup"><span data-stu-id="3a4ef-202">Pipeline Input</span></span>

<span data-ttu-id="3a4ef-203">Wenn Sie möchten, dass ihre Funktion Pipelineeingaben akzeptiert, ist ein wenig zusätzliche Programmierung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-203">When you want your function to accept pipeline input, some additional coding is necessary.</span></span> <span data-ttu-id="3a4ef-204">Wie bereits in diesem Buch erwähnt, können Befehle Pipelineeingaben **als Wert** (als Typ) oder **als Eigenschaftsname** akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-204">As mentioned earlier in this book, commands can accept pipeline input **by value** (by type) or **by property name**.</span></span> <span data-ttu-id="3a4ef-205">Sie können ihre Funktionen genau wie die nativen Befehle schreiben, sodass Sie entweder einen oder beide dieser Eingabetypen akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-205">You can write your functions just like the native commands so that they accept either one or both of these types of input.</span></span>

<span data-ttu-id="3a4ef-206">Um die Pipelineeingabe **als Wert**zu akzeptieren, geben Sie das Parameterattribut `ValueFromPipeline` für diesen bestimmten Parameter an.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-206">To accept pipeline input **by value**, specified the `ValueFromPipeline` parameter attribute for that particular parameter.</span></span> <span data-ttu-id="3a4ef-207">Denken Sie daran, dass Sie Pipelineeingaben **als Wert** nur von einem des jeweiligen Datentyps akzeptieren können.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-207">Keep in mind that you can only accept pipeline input **by value** from one of each datatype.</span></span> <span data-ttu-id="3a4ef-208">Wenn Sie beispielsweise über zwei Parameter verfügen, die Zeichenfolgeneingaben (string) akzeptieren, kann nur einer davon Pipelineeingaben **als Wert** akzeptieren, denn wenn Sie dies für beide Zeichenfolgenparameter angeben würden, wüsste die Pipelineeingabe nicht, an welchen sie sich binden sollte.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-208">For example, if you have two parameters that accept string input, only one of those can accept pipeline input **by value** because if you specified it for both of the string parameters, the pipeline input wouldn't know which one to bind to.</span></span> <span data-ttu-id="3a4ef-209">Dies ist ein weiterer Grund, warum ich diese Art von Pipelineeingabe _als Typ_ anstelle von **als Wert** bezeichne.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-209">This is another reason I call this type of pipeline input _by type_ instead of **by value**.</span></span>

<span data-ttu-id="3a4ef-210">Pipelineeingaben gelangen gleichzeitig immer nur in ein Element, ähnlich der Art und Weise, wie Elemente in einer `foreach`-Schleife behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-210">Pipeline input comes in one item at a time similar to the way items are handled in a `foreach` loop.</span></span>
<span data-ttu-id="3a4ef-211">Es ist mindestens ein `process`-Block erforderlich, um jedes dieser Elemente zu verarbeiten, wenn Sie ein Array als Eingabe akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-211">At a minimum, a `process` block is required to process each of these items if you're accepting an array as input.</span></span> <span data-ttu-id="3a4ef-212">Wenn Sie nur einen einzelnen Wert als Eingabe akzeptieren, ist ein `process`-Block nicht erforderlich, aber ich empfehle dennoch, ihn aus Gründen der Konsistenz anzugeben.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-212">If you're only accepting a single value as input, a `process` block isn't necessary, but I still recommend specifying it for consistency.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

<span data-ttu-id="3a4ef-213">Das akzeptieren von Pipelineeingaben **als Eigenschaftsname** ist ähnlich, außer dass es mit dem Parameterattribut `ValueFromPipelineByPropertyName` angegeben wird und für eine beliebige Anzahl von Parametern, unabhängig vom Datentyp, angegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-213">Accepting pipeline input **by property name** is similar except it's specified with the `ValueFromPipelineByPropertyName` parameter attribute and it can be specified for any number of parameters regardless of datatype.</span></span> <span data-ttu-id="3a4ef-214">Der Schlüssel besteht darin, dass die Ausgabe des Befehls, der per Pipeline als Eingabe weitergeleitet wird, einen Eigenschaftsnamen besitzen muss, der mit dem Namen des Parameters oder einem Parameteralias Ihrer Funktion übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-214">The key is that the output of the command that's being piped in has to have a property name that matches the name of the parameter or a parameter alias of your function.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

<span data-ttu-id="3a4ef-215">`BEGIN`- und `END`-Blöcke sind optional.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-215">`BEGIN` and `END` blocks are optional.</span></span> <span data-ttu-id="3a4ef-216">`BEGIN` würde vor dem `PROCESS`-Block angegeben und wird verwendet, um alle anfänglichen Arbeiten durchzuführen, bevor die Elemente von der Pipeline empfangen werden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-216">`BEGIN` would be specified before the `PROCESS` block and is used to perform any initial work prior to the items being received from the pipeline.</span></span> <span data-ttu-id="3a4ef-217">Es ist wichtig, dies zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-217">This is important to understand.</span></span> <span data-ttu-id="3a4ef-218">Auf Werte, die per Pipeline als Eingabe weitergeleitet werden, kann im `BEGIN`-Block nicht zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-218">Values that are piped in are not accessible in the `BEGIN` block.</span></span> <span data-ttu-id="3a4ef-219">Der `END`-Block würde hinter dem `PROCESS`-Block angegeben und für die Bereinigung verwendet, nachdem alle Elemente, die per Pipeline als Eingabe weitergeleitet werden, verarbeitet wurden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-219">The `END` block would be specified after the `PROCESS` block and is used for cleanup once all of the items that are piped in have been processed.</span></span>

## <a name="error-handling"></a><span data-ttu-id="3a4ef-220">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="3a4ef-220">Error Handling</span></span>

<span data-ttu-id="3a4ef-221">Die im folgenden Beispiel gezeigte Funktion generiert eine nicht behandelte Ausnahme, wenn ein Computer nicht kontaktiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-221">The function shown in the following example generates an unhandled exception when a computer can't be contacted.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

<span data-ttu-id="3a4ef-222">Es gibt eine Reihe unterschiedlicher Methoden, um Fehler in PowerShell zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-222">There are a couple of different ways to handle errors in PowerShell.</span></span> <span data-ttu-id="3a4ef-223">`Try/Catch` ist die modernere Methode zum Behandeln von Fehlern.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-223">`Try/Catch` is the more modern way to handle errors.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="3a4ef-224">Obwohl die im vorherigen Beispiel gezeigte Funktion Fehlerbehandlung verwendet, generiert sie auch eine nicht behandelte Ausnahme, weil der Befehl keinen Fehler mit Abbruch generiert.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-224">Although the function shown in the previous example uses error handling, it also generates an unhandled exception because the command doesn't generate a terminating error.</span></span> <span data-ttu-id="3a4ef-225">Dies zu verstehen, ist ebenfalls wichtig.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-225">This is also important to understand.</span></span> <span data-ttu-id="3a4ef-226">Nur Fehler mit Abbruch können abgefangen werden.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-226">Only terminating errors are caught.</span></span> <span data-ttu-id="3a4ef-227">Geben Sie den Parameter **ErrorAction** mit **Stop** als Wert an, um einen Fehler ohne Abbruch in einen mit Abbruch zu verwandeln.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-227">Specify the **ErrorAction** parameter with **Stop** as the value to turn a non-terminating error into a terminating one.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="3a4ef-228">Ändern Sie die globale Variable `$ErrorActionPreference` nur, wenn dies unbedingt erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-228">Don't modify the global `$ErrorActionPreference` variable unless absolutely necessary.</span></span> <span data-ttu-id="3a4ef-229">Wenn Sie etwas wie .NET direkt aus ihrer PowerShell-Funktion heraus verwenden, können Sie die **ErrorAction** nicht mit dem Befehl selbst angeben.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-229">If you're using something like .NET directly from within your PowerShell function, you can't specify the **ErrorAction** on the command itself.</span></span> <span data-ttu-id="3a4ef-230">In diesem Szenario müssen Sie möglicherweise die globale Variable `$ErrorActionPreference` ändern, aber wenn Sie sie ändern, ändern Sie sie sofort nach dem Testen des Befehls wieder zurück.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-230">In that scenario, you might need to change the global `$ErrorActionPreference` variable, but if you do change it, change it back immediately after trying the command.</span></span>

## <a name="comment-based-help"></a><span data-ttu-id="3a4ef-231">Kommentarbasierte Hilfe</span><span class="sxs-lookup"><span data-stu-id="3a4ef-231">Comment-Based Help</span></span>

<span data-ttu-id="3a4ef-232">Es gilt als bewährte Methode, Ihren Funktionen kommentarbasierte Hilfe hinzuzufügen, damit die Personen, mit denen Sie sie teilen, wissen, wie Sie sie verwenden können.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-232">It's considered to be a best practice to add comment based help to your functions so the people you're sharing them with will know how to use them.</span></span>

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

<span data-ttu-id="3a4ef-233">Wenn Sie Ihren Funktionen kommentarbasierte Hilfe hinzufügen, lässt sich die Hilfe zu ihnen genau wie für die integrierten Standardbefehle abrufen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-233">When you add comment based help to your functions, help can be retrieved for them just like the default built-in commands.</span></span>

<span data-ttu-id="3a4ef-234">Die Gesamtheit der Syntax zum Schreiben einer Funktion in PowerShell kann überwältigend erscheinen, besonders für jemanden, der gerade erst damit begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-234">All of the syntax for writing a function in PowerShell can seem overwhelming especially for someone who is just getting started.</span></span> <span data-ttu-id="3a4ef-235">Wenn ich mich nicht mehr an die Syntax für etwas erinnern kann, öffne ich häufig eine zweite Kopie der ISE auf einem gesonderten Monitor und zeige bei der Eingabe des Codes für meine Funktion den Codeausschnitt „Cmdlet (erweiterte Funktion) – Vollständig“ an.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-235">Often times if I can't remember the syntax for something, I'll open a second copy of the ISE on a separate monitor and view the "Cmdlet (advanced function) - Complete" snippet while typing in the code for my function.</span></span> <span data-ttu-id="3a4ef-236">Auf Codeausschnitte können Sie in der PowerShell ISE mithilfe der Tastenkombination <kbd>STRG</kbd>+<kbd>J</kbd> zugreifen.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-236">Snippets can be accessed in the PowerShell ISE using the <kbd>Ctrl</kbd>+<kbd>J</kbd> key combination.</span></span>

## <a name="summary"></a><span data-ttu-id="3a4ef-237">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="3a4ef-237">Summary</span></span>

<span data-ttu-id="3a4ef-238">In diesem Kapitel haben Sie die Grundlagen zum Schreiben von Funktionen in PowerShell kennen gelernt, außerdem, wie Sie eine Funktion in eine erweiterte Funktion umwandeln, sowie einige der wichtigeren Elemente, die Sie beim Schreiben von PowerShell-Funktionen berücksichtigen sollten wie Parameterüberprüfung, ausführliche Ausgabe, Pipelineeingabe, Fehlerbehandlung und kommentarbasierte Hilfe.</span><span class="sxs-lookup"><span data-stu-id="3a4ef-238">In this chapter you've learned the basics of writing functions in PowerShell to include how to turn a function into an advanced function and some of the more important elements that you should consider when writing PowerShell functions such as parameter validation, verbose output, pipeline input, error handling, and comment based help.</span></span>

## <a name="review"></a><span data-ttu-id="3a4ef-239">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="3a4ef-239">Review</span></span>

1. <span data-ttu-id="3a4ef-240">Wie erhalten Sie eine Liste der genehmigten Verben in PowerShell?</span><span class="sxs-lookup"><span data-stu-id="3a4ef-240">How do you obtain a list of approved verbs in PowerShell?</span></span>
1. <span data-ttu-id="3a4ef-241">Wie wandeln Sie eine PowerShell-Funktion in eine erweiterte Funktion um?</span><span class="sxs-lookup"><span data-stu-id="3a4ef-241">How do you turn a PowerShell function into an advanced function?</span></span>
1. <span data-ttu-id="3a4ef-242">Wann sollten die Parameter **WhatIf** und **Confirm** Ihren PowerShell-Funktionen hinzugefügt werden?</span><span class="sxs-lookup"><span data-stu-id="3a4ef-242">When should **WhatIf** and **Confirm** parameters be added to your PowerShell functions?</span></span>
1. <span data-ttu-id="3a4ef-243">Wie wandeln Sie einen Fehler ohne Abbruch in einen Fehler mit Abbruch um?</span><span class="sxs-lookup"><span data-stu-id="3a4ef-243">How do you turn a non-terminating error into a terminating one?</span></span>
1. <span data-ttu-id="3a4ef-244">Warum sollten Sie Ihren Funktionen eine kommentarbasierte Hilfe hinzufügen?</span><span class="sxs-lookup"><span data-stu-id="3a4ef-244">Why should you add comment based help to your functions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="3a4ef-245">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="3a4ef-245">Recommended Reading</span></span>

- <span data-ttu-id="3a4ef-246">[about_Functions][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-246">[about_Functions][]</span></span>
- <span data-ttu-id="3a4ef-247">[about_Functions_Advanced_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-247">[about_Functions_Advanced_Parameters][]</span></span>
- <span data-ttu-id="3a4ef-248">[about_CommonParameters][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-248">[about_CommonParameters][]</span></span>
- <span data-ttu-id="3a4ef-249">[about_Functions_CmdletBindingAttribute][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-249">[about_Functions_CmdletBindingAttribute][]</span></span>
- <span data-ttu-id="3a4ef-250">[about_Functions_Advanced][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-250">[about_Functions_Advanced][]</span></span>
- <span data-ttu-id="3a4ef-251">[about_Try_Catch_Finally][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-251">[about_Try_Catch_Finally][]</span></span>
- <span data-ttu-id="3a4ef-252">[about_Comment_Based_Help][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-252">[about_Comment_Based_Help][]</span></span>
- <span data-ttu-id="3a4ef-253">[Video: PowerShell-Toolerstellung mit erweiterten Funktionen und Skriptmodulen][]</span><span class="sxs-lookup"><span data-stu-id="3a4ef-253">[Video: PowerShell Toolmaking with Advanced Functions and Script Modules][]</span></span>

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Video: PowerShell-Toolerstellung mit erweiterten Funktionen und Skriptmodulen]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [Pascal-Schreibweise]: /dotnet/standard/design-guidelines/capitalization-conventions
[Video: PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [Pascal case]: /dotnet/standard/design-guidelines/capitalization-conventionss
