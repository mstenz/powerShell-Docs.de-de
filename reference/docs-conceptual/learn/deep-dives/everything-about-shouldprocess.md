---
title: Alles, was Sie schon immer über ShouldProcess wissen wollten
description: ShouldProcess ist ein wichtiges Feature, das oft übersehen wird. Mit den WhatIf- und Confirm-Parametern können Sie Ihre Funktionen einfach erweitern.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1d9110302a191b90bd11bdf742f77704a8c9d6f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149483"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a><span data-ttu-id="b0bc1-104">Alles, was Sie schon immer über ShouldProcess wissen wollten</span><span class="sxs-lookup"><span data-stu-id="b0bc1-104">Everything you wanted to know about ShouldProcess</span></span>

<span data-ttu-id="b0bc1-105">PowerShell-Funktionen verfügen über mehrere Features, die die Interaktion der Benutzer mit ihnen erheblich verbessern.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-105">PowerShell functions have several features that greatly improve the way users interact with them.</span></span>
<span data-ttu-id="b0bc1-106">Ein wichtiges Feature, das oft übersehen wird, ist die Unterstützung von `-WhatIf` und `-Confirm`. Diese kann ganz einfach zu Ihren Funktionen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-106">One important feature that is often overlooked is `-WhatIf` and `-Confirm` support and it's easy to add to your functions.</span></span> <span data-ttu-id="b0bc1-107">In diesem Artikel wird ausführlich erläutert, wie dieses Feature implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-107">In this article, we dive deep into how to implement this feature.</span></span>

> [!NOTE]
> <span data-ttu-id="b0bc1-108">Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="b0bc1-109">Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="b0bc1-110">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="b0bc1-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

<span data-ttu-id="b0bc1-111">Dies ist ein einfaches Feature, das Sie in Ihren Funktionen aktivieren können, um ein Sicherheitsnetz für die Benutzer bereitzustellen, die es benötigen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-111">This is a simple feature you can enable in your functions to provide a safety net for the users that need it.</span></span> <span data-ttu-id="b0bc1-112">Es gibt nichts Schlimmeres, zum ersten Mal einen Befehl auszuführen, von dem man weiß, dass er gefährlich sein kann.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-112">There's nothing scarier than running a command that you know can be dangerous for the first time.</span></span> <span data-ttu-id="b0bc1-113">Die Option, ihn mit `-WhatIf` auszuführen, kann einen großen Unterschied ausmachen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-113">The option to run it with `-WhatIf` can make a big difference.</span></span>

## <a name="commonparameters"></a><span data-ttu-id="b0bc1-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0bc1-114">CommonParameters</span></span>

<span data-ttu-id="b0bc1-115">Bevor wir uns mit der Implementierung dieser [Allgemeine Parameter][] befassen, möchte ich kurz darauf eingehen, wie sie verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-115">Before we look at implementing these [common parameters][], I want to take a quick look at how they're used.</span></span>

## <a name="using--whatif"></a><span data-ttu-id="b0bc1-116">Verwenden von -WhatIf</span><span class="sxs-lookup"><span data-stu-id="b0bc1-116">Using -WhatIf</span></span>

<span data-ttu-id="b0bc1-117">Wenn ein Befehl den `-WhatIf`-Parameter unterstützt, können Sie sehen, was der Befehl getan hätte, anstatt Änderungen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-117">When a command supports the `-WhatIf` parameter, it allows you to see what the command would have done instead of making changes.</span></span> <span data-ttu-id="b0bc1-118">Das ist eine gute Möglichkeit, die Auswirkungen eines Befehls zu testen, vor allem, bevor Sie etwas machen, was zerstörerische Folgen haben könnte.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-118">it's a good way to test out the impact of a command, especially before you do something destructive.</span></span>

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="b0bc1-119">Wenn der Befehl `ShouldProcess` ordnungsgemäß implementiert, sollte er Ihnen alle Änderungen zeigen, die er vorgenommen hätte.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-119">If the command correctly implements `ShouldProcess`, it should show you all the changes that it would have made.</span></span> <span data-ttu-id="b0bc1-120">Hier ist ein Beispiel für die Verwendung eines Platzhalters zum Löschen mehrerer Dateien.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-120">Here is an example using a wildcard to delete multiple files.</span></span>

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a><span data-ttu-id="b0bc1-121">Verwenden von -Confirm</span><span class="sxs-lookup"><span data-stu-id="b0bc1-121">Using -Confirm</span></span>

<span data-ttu-id="b0bc1-122">Befehle, die `-WhatIf` unterstützen, unterstützen auch `-Confirm`.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-122">Commands that support `-WhatIf` also support `-Confirm`.</span></span> <span data-ttu-id="b0bc1-123">Dadurch haben Sie die Möglichkeit, eine Aktion zu bestätigen, bevor Sie sie ausführen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-123">This gives you a chance confirm an action before performing it.</span></span>

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="b0bc1-124">In diesem Fall haben Sie mehrere Optionen, mit denen Sie fortfahren, eine Änderung überspringen oder das Skript anhalten können.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-124">In this case, you have multiple options that allow you to continue, skip a change, or stop the script.</span></span> <span data-ttu-id="b0bc1-125">In der Hilfeanzeige werden die einzelnen Optionen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-125">The help prompt describes each of those options like this.</span></span>

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a><span data-ttu-id="b0bc1-126">Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="b0bc1-126">Localization</span></span>

<span data-ttu-id="b0bc1-127">Diese Eingabeaufforderung ist in PowerShell lokalisiert, sodass sich die Sprache basierend auf der Sprache Ihres Betriebssystems ändert.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-127">This prompt is localized in PowerShell so the language changes based on the language of your operating system.</span></span> <span data-ttu-id="b0bc1-128">Dies ist ein weiterer Punkt, den PowerShell für Sie übernimmt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-128">This is one more thing that PowerShell manages for you.</span></span>

### <a name="switch-parameters"></a><span data-ttu-id="b0bc1-129">Switch-Parameter</span><span class="sxs-lookup"><span data-stu-id="b0bc1-129">Switch parameters</span></span>

<span data-ttu-id="b0bc1-130">Schauen wir uns kurz an, wie Sie einen Wert an einen Switch-Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-130">Let's take quick moment to look at ways to pass a value to a switch parameter.</span></span> <span data-ttu-id="b0bc1-131">Der Hauptgrund, warum ich dies ausspreche, ist, dass Sie oft Parameterwerte an von Ihnen aufgerufene Funktionen übergeben wollen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-131">The main reason I call this out is that you often want to pass parameter values to functions you call.</span></span>

<span data-ttu-id="b0bc1-132">Der erste Ansatz ist eine spezifische Parametersyntax, die zwar für alle Parameter verwendet werden kann, aber meistens für Switch-Parameter eingesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-132">The first approach is a specific parameter syntax that can be used for all parameters but you mostly see it used for switch parameters.</span></span> <span data-ttu-id="b0bc1-133">Sie geben einen Doppelpunkt an, um einen Wert an den Parameter anzufügen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-133">You specify a colon to attach a value to the parameter.</span></span>

```powershell
Remove-Item -Path:* -WhatIf:$true
```

<span data-ttu-id="b0bc1-134">Dasselbe können Sie mit einer Variablen machen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-134">You can do the same with a variable.</span></span>

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

<span data-ttu-id="b0bc1-135">Der zweite Ansatz ist, eine Hashtabelle zum Verteilen des Werts zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-135">The second approach is to use a hashtable to splat the value.</span></span>

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

<span data-ttu-id="b0bc1-136">Wenn Sie noch nicht mit Hashtabellen oder dem Verteilen vertraut sind, lesen Sie den Artikel [Alles, was Sie schon immer über Hashtabellen wissen wollten][].</span><span class="sxs-lookup"><span data-stu-id="b0bc1-136">If you're new to hashtables or splatting, I have another article on that covers [everything you wanted to know about hashtables][].</span></span>

## <a name="supportsshouldprocess"></a><span data-ttu-id="b0bc1-137">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="b0bc1-137">SupportsShouldProcess</span></span>

<span data-ttu-id="b0bc1-138">Der erste Schritt zum Aktivieren der `-WhatIf`- und `-Confirm`-Unterstützung besteht darin, `SupportsShouldProcess` in `CmdletBinding` der Funktion anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-138">The first step to enable `-WhatIf` and `-Confirm` support is to specify `SupportsShouldProcess` in the `CmdletBinding` of your function.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

<span data-ttu-id="b0bc1-139">Wenn Sie `SupportsShouldProcess` so angeben, können wir die Funktion mit `-WhatIf` (oder `-Confirm`) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-139">By specifying `SupportsShouldProcess` in this way, we can now call our function with `-WhatIf` (or `-Confirm`).</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="b0bc1-140">Beachten Sie, dass ich keinen Parameter namens `-WhatIf` erstellt habe.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-140">Notice that I did not create a parameter called `-WhatIf`.</span></span> <span data-ttu-id="b0bc1-141">Durch das Angeben von `SupportsShouldProcess` wird dieser automatisch für uns erstellt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-141">Specifying `SupportsShouldProcess` automatically creates it for us.</span></span> <span data-ttu-id="b0bc1-142">Wenn wir den `-WhatIf`-Parameter in `Test-ShouldProcess` angeben, führen einige Funktionen, die wir aufrufen, auch eine `-WhatIf`-Verarbeitung aus.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-142">When we specify the `-WhatIf` parameter on `Test-ShouldProcess`, some things we call also perform `-WhatIf` processing.</span></span>

### <a name="trust-but-verify"></a><span data-ttu-id="b0bc1-143">Vertrauen ist gut – Kontrolle ist besser</span><span class="sxs-lookup"><span data-stu-id="b0bc1-143">Trust but verify</span></span>

<span data-ttu-id="b0bc1-144">Hier besteht eine gewisse Gefahr, wenn man darauf vertraut, dass jeder Befehl, der aufgerufen wird, `-WhatIf`-Werte übernimmt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-144">There's some danger here trusting that everything you call inherits `-WhatIf` values.</span></span> <span data-ttu-id="b0bc1-145">Bei den weiteren Beispielen gehe ich davon aus, dass es nicht funktioniert, und werde bei Aufrufen anderer Befehle sehr explizit sein.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-145">For the rest of the examples, I'm going to assume that it doesn't work and be very explicit when making calls to other commands.</span></span> <span data-ttu-id="b0bc1-146">Ich empfehle, dass Sie das auch machen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-146">I recommend that you do the same.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

<span data-ttu-id="b0bc1-147">Ich werde auf die Besonderheiten später noch einmal zurückkommen, wenn Sie alle beteiligten Aspekte besser kennen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-147">I will revisit the nuances much later once you have a better understanding of all the pieces in play.</span></span>

## <a name="pscmdletshouldprocess"></a><span data-ttu-id="b0bc1-148">$PSCmdlet.ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="b0bc1-148">$PSCmdlet.ShouldProcess</span></span>

<span data-ttu-id="b0bc1-149">Mit dieser Methode können Sie `SupportsShouldProcess` in `$PSCmdlet.ShouldProcess` implementieren.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-149">The method that allows you to implement `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess`.</span></span> <span data-ttu-id="b0bc1-150">Sie rufen `$PSCmdlet.ShouldProcess(...)` auf, um festzustellen, ob Sie etwas Logik verarbeiten müssen, und PowerShell kümmert sich um den Rest.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-150">You call `$PSCmdlet.ShouldProcess(...)` to see if you should process some logic and PowerShell takes care of the rest.</span></span> <span data-ttu-id="b0bc1-151">Beginnen wir mit einem Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b0bc1-151">Let's start with an example:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

<span data-ttu-id="b0bc1-152">Durch den Aufruf von `$PSCmdlet.ShouldProcess($file.name)` wir überprüft, ob `-WhatIf` (und der `-Confirm`-Parameter) vorhanden ist, und verarbeitet ihn dann entsprechend.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-152">The call to `$PSCmdlet.ShouldProcess($file.name)` checks for the `-WhatIf` (and `-Confirm` parameter) then handles it accordingly.</span></span> <span data-ttu-id="b0bc1-153">Durch `-WhatIf` gibt `ShouldProcess` eine Beschreibung der Änderung aus und gibt `$false` zurück:</span><span class="sxs-lookup"><span data-stu-id="b0bc1-153">The `-WhatIf` causes `ShouldProcess` to output a description of the change and return `$false`:</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

<span data-ttu-id="b0bc1-154">Ein Aufruf mit `-Confirm` hält das Skript an und zeigt dem Benutzer die Option zum Fortfahren an.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-154">A call using `-Confirm` pauses the script and prompts the user with the option to continue.</span></span> <span data-ttu-id="b0bc1-155">Wenn der Benutzer `Y` ausgewählt hat, wird `$true` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-155">It returns `$true` if the user selected `Y`.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="b0bc1-156">Ein tolles Feature von `$PSCmdlet.ShouldProcess` ist, dass es gleichzeitig eine ausführliche Ausgabe darstellt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-156">An awesome feature of `$PSCmdlet.ShouldProcess` is that it doubles as verbose output.</span></span> <span data-ttu-id="b0bc1-157">Darauf bin ich beim Implementieren von `ShouldProcess` oft angewiesen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-157">I depend on this often when implementing `ShouldProcess`.</span></span>

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a><span data-ttu-id="b0bc1-158">Überladungen</span><span class="sxs-lookup"><span data-stu-id="b0bc1-158">Overloads</span></span>

<span data-ttu-id="b0bc1-159">Es gibt einige verschiedene Überladungen für `$PSCmdlet.ShouldProcess` mit unterschiedlichen Parametern zum Anpassen des Messaging.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-159">There are a few different overloads for `$PSCmdlet.ShouldProcess` with different parameters for customizing the messaging.</span></span> <span data-ttu-id="b0bc1-160">Die erste haben wir bereits im obigen Beispiel gesehen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-160">We already saw the first one in the example above.</span></span> <span data-ttu-id="b0bc1-161">Schauen wir uns das genauer an.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-161">Let's take a closer look at it.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

<span data-ttu-id="b0bc1-162">Dadurch wird sowohl der Funktionsname als auch das Ziel (Wert des Parameters) ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-162">This produces output that includes both the function name and the target (value of the parameter).</span></span>

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

<span data-ttu-id="b0bc1-163">Geben Sie einen zweiten Parameter an, da der Vorgang den Vorgangswert anstelle des Funktionsnamens in der Nachricht verwendet.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-163">Specifying a second parameter as the operation uses the operation value instead of the function name in the message.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

<span data-ttu-id="b0bc1-164">Die nächste Option besteht darin, drei Parameter anzugeben, um die Nachricht vollständig anzupassen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-164">The next option is to specify three parameters to fully customize the message.</span></span> <span data-ttu-id="b0bc1-165">Wenn drei Parameter verwendet werden, ist der erste die gesamte Nachricht.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-165">When three parameters are used, the first one is the entire message.</span></span> <span data-ttu-id="b0bc1-166">Die nächsten beiden Parameter werden weiterhin in der Meldungsausgabe von `-Confirm` verwendet.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-166">The second two parameters are still used in the `-Confirm` message output.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a><span data-ttu-id="b0bc1-167">Schneller Parameterverweis</span><span class="sxs-lookup"><span data-stu-id="b0bc1-167">Quick parameter reference</span></span>

<span data-ttu-id="b0bc1-168">Wenn Sie diesen Artikel nur lesen, um herauszufinden, welche Parameter Sie verwenden sollten, finden Sie hier einen kurzen Verweis darauf, wie die Parameter die Nachricht in den verschiedenen `-WhatIf`-Szenarien verändern.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-168">Just in case you came here only to figure out what parameters you should use, here is a quick reference showing how the parameters change the message in the different `-WhatIf` scenarios.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

<span data-ttu-id="b0bc1-169">Ich verwende in der Regel die Variante mit zwei Parametern.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-169">I tend to use the one with two parameters.</span></span>

### <a name="shouldprocessreason"></a><span data-ttu-id="b0bc1-170">ShouldProcessReason</span><span class="sxs-lookup"><span data-stu-id="b0bc1-170">ShouldProcessReason</span></span>

<span data-ttu-id="b0bc1-171">Wir haben eine vierte Überladung, die ausgereifter ist als die anderen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-171">We have a fourth overload that's more advanced than the others.</span></span> <span data-ttu-id="b0bc1-172">Diese ermöglicht es Ihnen, den Grund für die Ausführung `ShouldProcess` abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-172">It allows you to get the reason `ShouldProcess` was executed.</span></span> <span data-ttu-id="b0bc1-173">Ich führe dies hier nur der Vollständigkeit halber an, weil wir einfach prüfen können, ob `$WhatIf` stattdessen `$true` ist.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-173">I'm only adding this here for completeness because we can just check if `$WhatIf` is `$true` instead.</span></span>

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

<span data-ttu-id="b0bc1-174">Wir müssen die `$reason`-Variable als Verweisvariable mit `[ref]` an den vierten Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-174">We have to pass the `$reason` variable into the fourth parameter as a reference variable with `[ref]`.</span></span> <span data-ttu-id="b0bc1-175">`ShouldProcess` füllt `$reason` mit dem Wert `None` oder `WhatIf` auf.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-175">`ShouldProcess` populates `$reason` with the value `None` or `WhatIf`.</span></span> <span data-ttu-id="b0bc1-176">Ich habe nicht gesagt, dass dies nützlich ist, und es gab für mich bisher auch noch keinen Grund, das so zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-176">I didn't say this was useful and I have had no reason to ever use it.</span></span>

### <a name="where-to-place-it"></a><span data-ttu-id="b0bc1-177">Die richtige Position</span><span class="sxs-lookup"><span data-stu-id="b0bc1-177">Where to place it</span></span>

<span data-ttu-id="b0bc1-178">Mit `ShouldProcess` können Sie Skripts sicherer gestalten.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-178">You use `ShouldProcess` to make your scripts safer.</span></span> <span data-ttu-id="b0bc1-179">Sie verwenden es also, wenn Ihre Skripts Änderungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-179">So you use it when your scripts are making changes.</span></span> <span data-ttu-id="b0bc1-180">Ich füge den `$PSCmdlet.ShouldProcess`-Aufruf gern so nah wie möglich an der Änderung ein.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-180">I like to place the `$PSCmdlet.ShouldProcess` call as close to the change as possible.</span></span>

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

<span data-ttu-id="b0bc1-181">Wenn ich eine Auflistung von Elementen ausführe, rufe ich es für jedes Element auf.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-181">If I'm processing a collection of items, I call it for each item.</span></span> <span data-ttu-id="b0bc1-182">Der Aufruf wird also in der ForEach-Schleife eingefügt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-182">So the call gets placed inside the foreach loop.</span></span>

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

<span data-ttu-id="b0bc1-183">Ich füge `ShouldProcess` eng um die Änderung herum ein, da ich möchte, dass so viel Code wie möglich ausgeführt wird, wenn `-WhatIf` angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-183">The reason why I place `ShouldProcess` tightly around the change, is that I want as much code to execute as possible when `-WhatIf` is specified.</span></span> <span data-ttu-id="b0bc1-184">Ich möchte, dass Setup und Validierung ausgeführt werden, falls möglich, damit der Benutzer diese Fehler sehen kann.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-184">I want the setup and validation to run if possible so the user gets to see those errors.</span></span>

<span data-ttu-id="b0bc1-185">Ich verwende das auch gern in meinen Pester-Tests, mit denen meine Projekte validiert werden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-185">I also like to use this in my Pester tests that validate my projects.</span></span> <span data-ttu-id="b0bc1-186">Wenn ich eine Logik verwende, die in Pester schwer zu simulieren ist, kann ich sie häufig in `ShouldProcess` umschließen und mit `-WhatIf` in meinen Tests aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-186">If I have a piece of logic that is hard to mock in pester, I can often wrap it in `ShouldProcess` and call it with `-WhatIf` in my tests.</span></span> <span data-ttu-id="b0bc1-187">Es ist besser, einen Teil Ihres Codes zu testen, als keinen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-187">It's better to test some of your code than none of it.</span></span>

### <a name="whatifpreference"></a><span data-ttu-id="b0bc1-188">$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="b0bc1-188">$WhatIfPreference</span></span>

<span data-ttu-id="b0bc1-189">Unsere erste Einstellungsvariable ist `$WhatIfPreference`.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-189">The first preference variable we have is `$WhatIfPreference`.</span></span> <span data-ttu-id="b0bc1-190">Diese ist standardmäßig auf `$false` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-190">This is `$false` by default.</span></span> <span data-ttu-id="b0bc1-191">Wenn Sie sie auf `$true` festlegen, wird die Funktion so ausgeführt, als ob Sie `-WhatIf` angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-191">If you set it to `$true` then your function executes as if you specified `-WhatIf`.</span></span> <span data-ttu-id="b0bc1-192">Wenn Sie dies in Ihrer Sitzung festlegen, führen alle Befehle eine `-WhatIf`-Ausführung aus.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-192">If you set this in your session, all commands perform `-WhatIf` execution.</span></span>

<span data-ttu-id="b0bc1-193">Wenn Sie eine Funktion mit `-WhatIf` aufzurufen, wird der Wert von `$WhatIfPreference` innerhalb des Gültigkeitsbereichs der Funktion auf `$true` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-193">When you call a function with `-WhatIf`, the value of `$WhatIfPreference` gets set to `$true` inside the scope of your function.</span></span>

## <a name="confirmimpact"></a><span data-ttu-id="b0bc1-194">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="b0bc1-194">ConfirmImpact</span></span>

<span data-ttu-id="b0bc1-195">Die meisten meiner Beispiele beziehen sich auf `-WhatIf`, sie funktionieren aber auch mit `-Confirm`, um dem Benutzer eine Eingabeaufforderung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-195">Most of my examples are for `-WhatIf` but everything so far also works with `-Confirm` to prompt the user.</span></span> <span data-ttu-id="b0bc1-196">Sie können den `ConfirmImpact`-Parameter der Funktion auf „Hoch“ festlegen, und der Benutzer wird eine Eingabeaufforderung angezeigt, als ob der Aufruf mit `-Confirm` erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-196">You can set the `ConfirmImpact` of the function to high and it prompts the user as if it was called with `-Confirm`.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="b0bc1-197">Da `High` festgelegt wurde, führt der Aufruf von `Test-ShouldProcess` die `-Confirm`-Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-197">This call to `Test-ShouldProcess` is performing the `-Confirm` action because of the `High` impact.</span></span>

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

<span data-ttu-id="b0bc1-198">Das offensichtliche Problem besteht darin, dass es jetzt schwieriger ist, das in anderen Skripten zu verwenden, ohne eine Eingabeaufforderung für den Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-198">The obvious issue is that now it's harder to use in other scripts without prompting the user.</span></span> <span data-ttu-id="b0bc1-199">In diesem Fall können wir ein `$false` an `-Confirm` übergeben, um die Eingabeaufforderung zu unterdrücken.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-199">In this case, we can pass a `$false` to `-Confirm` to suppress the prompt.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

<span data-ttu-id="b0bc1-200">In einem späteren Abschnitt werde ich erläutern, wie die `-Force`-Unterstützung hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-200">I'll cover how to add `-Force` support in a later section.</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="b0bc1-201">$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="b0bc1-201">$ConfirmPreference</span></span>

<span data-ttu-id="b0bc1-202">`$ConfirmPreference` ist eine automatische Variable, die steuert, wann `ConfirmImpact` Sie zur Bestätigung der Ausführung auffordert.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-202">`$ConfirmPreference` is an automatic variable that controls when `ConfirmImpact` asks you to confirm execution.</span></span> <span data-ttu-id="b0bc1-203">Hier sind die möglichen Werte für sowohl `$ConfirmPreference` als auch `ConfirmImpact`.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-203">Here are the possible values for both `$ConfirmPreference` and `ConfirmImpact`.</span></span>

- `High`
- `Medium`
- `Low`
- `None`

<span data-ttu-id="b0bc1-204">Mit diesen Werten können Sie für jede Funktion unterschiedliche Auswirkungsstufen angeben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-204">With these values, you can specify different levels of impact for each function.</span></span> <span data-ttu-id="b0bc1-205">Wenn Sie `$ConfirmPreference` auf einen höheren Wert als `ConfirmImpact` festgelegt haben, werden Sie nicht aufgefordert, die Ausführung zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-205">If you have `$ConfirmPreference` set to a value higher than `ConfirmImpact`, then you aren't prompted to confirm execution.</span></span>

<span data-ttu-id="b0bc1-206">Standardmäßig ist `$ConfirmPreference` auf `High` und `ConfirmImpact` auf `Medium` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-206">By default, `$ConfirmPreference` is set to `High` and `ConfirmImpact` is `Medium`.</span></span> <span data-ttu-id="b0bc1-207">Wenn Sie möchten, dass die Funktion dem Benutzer automatisch Eingabeaufforderung anzeigt, legen Sie für `ConfirmImpact` `High`fest.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-207">If you want your function to automatically prompt the user, set your `ConfirmImpact` to `High`.</span></span> <span data-ttu-id="b0bc1-208">Legen Sie andernfalls `Medium` fest, wenn die Funktion destruktiv ist, und verwenden Sie `Low`, wenn der Befehl immer sicher in der Produktion ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-208">Otherwise set it to `Medium` if its destructive and use `Low` if the command is always safe run in production.</span></span> <span data-ttu-id="b0bc1-209">Wenn Sie diesen Wert auf `none` festlegen, wird auch dann keine Eingabeaufforderung angezeigt, wenn `-Confirm` angegeben wurde (`-WhatIf` wird jedoch unterstützt).</span><span class="sxs-lookup"><span data-stu-id="b0bc1-209">If you set it to `none`, it doesn't prompt even if `-Confirm` was specified (but it still gives you `-WhatIf` support).</span></span>

<span data-ttu-id="b0bc1-210">Wenn Sie eine Funktion mit `-Confirm` aufzurufen, wird der Wert von `$ConfirmPreference` innerhalb des Gültigkeitsbereichs der Funktion auf `Low` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-210">When calling a function with `-Confirm`, the value of `$ConfirmPreference` gets set to `Low` inside the scope of your function.</span></span>

### <a name="suppressing-nested-confirm-prompts"></a><span data-ttu-id="b0bc1-211">Unterdrücken von geschachtelten Confirm-Eingabeaufforderungen</span><span class="sxs-lookup"><span data-stu-id="b0bc1-211">Suppressing nested confirm prompts</span></span>

<span data-ttu-id="b0bc1-212">`$ConfirmPreference` kann von Funktionen übernommen werden, die Sie aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-212">The `$ConfirmPreference` can get picked up by functions that you call.</span></span> <span data-ttu-id="b0bc1-213">Dadurch entstehen Szenarios, in denen Sie eine Confirm-Eingabeaufforderung hinzufügen und die von Ihnen aufgerufene Funktion den Benutzer ebenfalls auffordert.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-213">This can create scenarios where you add a confirm prompt and the function you call also prompts the user.</span></span>

<span data-ttu-id="b0bc1-214">Ich gebe in der Regel `-Confirm:$false` bei den Befehlen an, die ich aufrufe, wenn ich die Eingabeaufforderung bereits bearbeitet habe.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-214">What I tend to do is specify `-Confirm:$false` on the commands that I call when I have already handled the prompting.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

<span data-ttu-id="b0bc1-215">Damit kommen wir zurück zu einer früheren Warnung: Es gibt Besonderheiten, wann `-WhatIf` nicht an eine Funktion übergeben wird und wann `-Confirm` an eine Funktion übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-215">This brings us back to an earlier warning: There are nuances as to when `-WhatIf` is not passed to a function and when `-Confirm` passes to a function.</span></span> <span data-ttu-id="b0bc1-216">Ich werde später noch einmal darauf zurückkommen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-216">I promise I'll get back to this later.</span></span>

## <a name="pscmdletshouldcontinue"></a><span data-ttu-id="b0bc1-217">$PSCmdlet.ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="b0bc1-217">$PSCmdlet.ShouldContinue</span></span>

<span data-ttu-id="b0bc1-218">Wenn Sie mehr Kontrolle benötigen, als `ShouldProcess` Ihnen ermöglicht, können Sie die Eingabeaufforderung direkt mit `ShouldContinue` auslösen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-218">If you need more control than `ShouldProcess` provides, you can trigger the prompt directly with `ShouldContinue`.</span></span> <span data-ttu-id="b0bc1-219">`ShouldContinue` ignoriert `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference` und `-WhatIf`, da bei jeder Ausführung eine Eingabeaufforderung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-219">`ShouldContinue` ignores `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, and `-WhatIf` because it prompts every time it's executed.</span></span>

<span data-ttu-id="b0bc1-220">Auf den ersten Blick können `ShouldProcess` und `ShouldContinue` leicht verwechselt werden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-220">At a quick glance, it's easy to confuse `ShouldProcess` and `ShouldContinue`.</span></span> <span data-ttu-id="b0bc1-221">Ich erinnere mich daran, eher `ShouldProcess` zu verwenden, da der Parameter in `CmdletBinding` als `SupportsShouldProcess` bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-221">I tend to remember to use `ShouldProcess` because the parameter is called `SupportsShouldProcess` in the `CmdletBinding`.</span></span>
<span data-ttu-id="b0bc1-222">Sie sollten in fast jedem Szenario `ShouldProcess` verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-222">You should use `ShouldProcess` in almost every scenario.</span></span> <span data-ttu-id="b0bc1-223">Aus diesem Grund habe ich diese Methode zuerst erläutert.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-223">That is why I covered that method first.</span></span>

<span data-ttu-id="b0bc1-224">Schauen wir uns `ShouldContinue` in Aktion an.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-224">Let's take a look at `ShouldContinue` in action.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="b0bc1-225">Damit wird eine vereinfachte Eingabeaufforderung mit weniger Optionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-225">This provides us a simpler prompt with fewer options.</span></span>

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="b0bc1-226">Das größte Problem bei `ShouldContinue` besteht darin, dass es vom Benutzer interaktiv ausgeführt muss, da dem Benutzer immer eine Eingabeaufforderung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-226">The biggest issue with `ShouldContinue` is that it requires the user to run it interactively because it always prompts the user.</span></span> <span data-ttu-id="b0bc1-227">Sie sollten immer Tools zusammenstellen, die von anderen Skripts verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-227">You should always be building tools that can be used by other scripts.</span></span> <span data-ttu-id="b0bc1-228">Dafür können Sie `-Force`implementiert.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-228">The way you do this is by implementing `-Force`.</span></span> <span data-ttu-id="b0bc1-229">Ich komme auf diesen Punkt später noch einmal zurück.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-229">I'll revisit this idea later.</span></span>

### <a name="yes-to-all"></a><span data-ttu-id="b0bc1-230">Ja zu allem</span><span class="sxs-lookup"><span data-stu-id="b0bc1-230">Yes to all</span></span>

<span data-ttu-id="b0bc1-231">Dies wird automatisch mit `ShouldProcess` bearbeitet, aber für `ShouldContinue` müssen wir etwas mehr Arbeit leisten.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-231">This is automatically handled with `ShouldProcess` but we have to do a little more work for `ShouldContinue`.</span></span> <span data-ttu-id="b0bc1-232">Es gibt eine zweite Methodenüberladung, bei der wir ein paar Werte per Verweis übergeben müssen, um die Logik zu steuern.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-232">There's a second method overload where we have to pass in a few values by reference to control the logic.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

<span data-ttu-id="b0bc1-233">Ich habe eine `foreach`-Schleife und eine Auflistung hinzugefügt, um das in Aktion anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-233">I added a `foreach` loop and a collection to show it in action.</span></span> <span data-ttu-id="b0bc1-234">Ich habe den `ShouldContinue`-Befehl aus der `if`-Anweisung abgerufen, um die Lesbarkeit zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-234">I pulled the `ShouldContinue` call out of the `if` statement to make it easier to read.</span></span> <span data-ttu-id="b0bc1-235">Der Aufruf einer Methode mit vier Parametern wird langsam etwas unschön, aber ich habe versucht, es so übersichtlich wie möglich zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-235">Calling a method with four parameters starts to get a little ugly, but I tried to make it look as clean as I could.</span></span>

## <a name="implementing--force"></a><span data-ttu-id="b0bc1-236">Implementieren von -Force</span><span class="sxs-lookup"><span data-stu-id="b0bc1-236">Implementing -Force</span></span>

<span data-ttu-id="b0bc1-237">`ShouldProcess` und `ShouldContinue` müssen `-Force` unterschiedlich implementieren.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-237">`ShouldProcess` and `ShouldContinue` need to implement `-Force` in different ways.</span></span> <span data-ttu-id="b0bc1-238">Der Trick bei dieser Implementierungen ist, dass `ShouldProcess` immer ausgeführt werden sollte, aber `ShouldContinue` sollte nicht ausgeführt werden, wenn `-Force` angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-238">The trick to these implementations is that `ShouldProcess` should always get executed, but `ShouldContinue` should not get executed if `-Force` is specified.</span></span>

### <a name="shouldprocess--force"></a><span data-ttu-id="b0bc1-239">ShouldProcess -Force</span><span class="sxs-lookup"><span data-stu-id="b0bc1-239">ShouldProcess -Force</span></span>

<span data-ttu-id="b0bc1-240">Wenn Sie `ConfirmImpact` auf `high` festlegen, wird der Benutzer zunächst versuchen, das mit `-Force` zu unterdrücken.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-240">If you set your `ConfirmImpact` to `high`, the first thing your users are going to try is to suppress it with `-Force`.</span></span> <span data-ttu-id="b0bc1-241">Das ist sowieso das erste, was ich mache.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-241">That's the first thing I do anyway.</span></span>

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

<span data-ttu-id="b0bc1-242">Wie Sie aus dem Abschnitt `ConfirmImpact` wissen, müssen Sie ihn wie folgt bezeichnen:</span><span class="sxs-lookup"><span data-stu-id="b0bc1-242">If you recall from the `ConfirmImpact` section, they actually need to call it like this:</span></span>

```powershell
Test-ShouldProcess -Confirm:$false
```

<span data-ttu-id="b0bc1-243">Nicht allen ist klar, dass das notwendig ist, und `-Confirm:$false` nicht `ShouldContinue` unterdrückt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-243">Not everyone realizes they need to do that and `-Confirm:$false` doesn't suppress `ShouldContinue`.</span></span>
<span data-ttu-id="b0bc1-244">Daher sollten wir `-Force` für die Benutzerfreundlichkeit implementieren.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-244">So we should implement `-Force` for the sanity of our users.</span></span> <span data-ttu-id="b0bc1-245">Schauen wir uns hier dieses vollständige Beispiel an:</span><span class="sxs-lookup"><span data-stu-id="b0bc1-245">Take a look at this full example here:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="b0bc1-246">Wir fügen unseren eigenen `-Force`-Switch als Parameter hinzu und verwenden den automatischen `$Confirm`-Parameter, der beim Hinzufügen von `SupportsShouldProcess` in `CmdletBinding` verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-246">We add our own `-Force` switch as a parameter and use the `$Confirm` automatic parameter that is available when adding `SupportsShouldProcess` in the `CmdletBinding`.</span></span>

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

<span data-ttu-id="b0bc1-247">Hier konzentrieren wir uns auf die `-Force`-Logik:</span><span class="sxs-lookup"><span data-stu-id="b0bc1-247">Focusing in on the `-Force` logic here:</span></span>

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

<span data-ttu-id="b0bc1-248">Wenn der Benutzer `-Force` angibt, möchten wir die Confirm-Eingabeaufforderung unterdrücken, es sei denn, es wird auf `-Confirm` angegeben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-248">If the user specifies `-Force`, we want to suppress the confirm prompt unless they also specify `-Confirm`.</span></span> <span data-ttu-id="b0bc1-249">Dadurch kann ein Benutzer eine Änderung erzwingen, die Änderung aber dennoch bestätigen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-249">This allows a user to force a change but still confirm the change.</span></span> <span data-ttu-id="b0bc1-250">Anschließend legen wir `$ConfirmPreference` im lokalen Bereich fest, in dem der Wert durch den Aufruf von `ShouldProcess` ermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-250">Then we set `$ConfirmPreference` in the local scope where our call to `ShouldProcess` discoverers it.</span></span>

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

<span data-ttu-id="b0bc1-251">Wenn sowohl `-Force` als auch `-WhatIf`angegeben werden, muss `-WhatIf` Priorität haben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-251">If someone specifies both `-Force` and `-WhatIf`, then `-WhatIf` needs to take priority.</span></span> <span data-ttu-id="b0bc1-252">Dieser Ansatz behält die `-WhatIf`-Verarbeitung bei, da `ShouldProcess` immer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-252">This approach preserves `-WhatIf` processing because `ShouldProcess` always gets executed.</span></span>

<span data-ttu-id="b0bc1-253">Fügen Sie in der if-Anweisung mit `ShouldProcess` keine Überprüfung auf den `$Force` Wert hinzu.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-253">Do not add a check for the `$Force` value inside the if statement with the `ShouldProcess`.</span></span> <span data-ttu-id="b0bc1-254">Das ist ein Widerspruch zu diesem spezifischen Szenario, auch wenn ich das im nächsten Abschnitt für `ShouldContinue` zeige.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-254">That is an anti-pattern for this specific scenario even though that's what I show you in the next section for `ShouldContinue`.</span></span>

### <a name="shouldcontinue--force"></a><span data-ttu-id="b0bc1-255">ShouldContinue -Force</span><span class="sxs-lookup"><span data-stu-id="b0bc1-255">ShouldContinue -Force</span></span>

<span data-ttu-id="b0bc1-256">Dies ist die richtige Vorgehensweise zum Implementieren von `-Force` mit `ShouldContinue`.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-256">This is the correct way to implement `-Force` with `ShouldContinue`.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="b0bc1-257">Da `$Force` links vom `-or`-Operator platzieren wird, wird der Wert zuerst ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-257">By placing the `$Force` to the left of the `-or` operator, it gets evaluated first.</span></span> <span data-ttu-id="b0bc1-258">Wenn Sie den Code so schreiben, wird die Ausführung der `if`-Anweisung verkürzt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-258">Writing it this way short circuits the execution of the `if` statement.</span></span> <span data-ttu-id="b0bc1-259">Wenn `$force` `$true` ist, wird `ShouldContinue` nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-259">If `$force` is `$true`, then the `ShouldContinue` is not executed.</span></span>

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

<span data-ttu-id="b0bc1-260">Wir müssen uns in diesem Szenario nicht um `-Confirm` oder `-WhatIf` kümmern, da sie nicht von `ShouldContinue` unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-260">We don't have to worry about `-Confirm` or `-WhatIf` in this scenario because they're not supported by `ShouldContinue`.</span></span> <span data-ttu-id="b0bc1-261">Aus diesem Grund muss die Verarbeitung anders erfolgen als mit `ShouldProcess`.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-261">This is why it needs to be handled differently than `ShouldProcess`.</span></span>

## <a name="scope-issues"></a><span data-ttu-id="b0bc1-262">Bereichsprobleme</span><span class="sxs-lookup"><span data-stu-id="b0bc1-262">Scope issues</span></span>

<span data-ttu-id="b0bc1-263">Die Verwendung von `-WhatIf` und `-Confirm` soll für alles innerhalb Ihrer Funktionen und alles, was davon aufgerufen wird, angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-263">Using `-WhatIf` and `-Confirm` are supposed to apply to everything inside your functions and everything they call.</span></span> <span data-ttu-id="b0bc1-264">Dazu legen sie im lokalen Bereich der Funktion `$WhatIfPreference` auf `$true` oder `$ConfirmPreference` auf `Low` fest.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-264">They do this by setting `$WhatIfPreference` to `$true` or setting `$ConfirmPreference` to `Low` in the local scope of the function.</span></span> <span data-ttu-id="b0bc1-265">Wenn Sie eine andere Funktion aufrufen, werden diese Werte von Aufrufen von `ShouldProcess` verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-265">When you call another function, calls to `ShouldProcess` use those values.</span></span>

<span data-ttu-id="b0bc1-266">Dies funktioniert in den meisten Fällen ordnungsgemäß.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-266">This actually works correctly most of the time.</span></span> <span data-ttu-id="b0bc1-267">Es funktioniert jedes Mal, wenn Sie ein integriertes Cmdlet oder eine Funktion im selben Bereich aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-267">Anytime you call built-in cmdlet or a function in your same scope, it works.</span></span> <span data-ttu-id="b0bc1-268">Es funktioniert auch, wenn Sie ein Skript oder eine Funktion in einem Skriptmodul über die Konsole aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-268">It also works when you call a script or a function in a script module from the console.</span></span>

<span data-ttu-id="b0bc1-269">Die einzige Stelle, an der es nicht funktioniert, ist, wenn ein Skript oder ein Skriptmodul eine Funktion in einem anderen Skriptmodul aufruft.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-269">The one specific place where it doesn't work is when a script or a script module calls a function in another script module.</span></span> <span data-ttu-id="b0bc1-270">Das klingt vielleicht nicht besonders problematisch, aber die meisten Module, die Sie erstellen oder aus der PSGallery abrufen, sind Skriptmodule.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-270">This may not sound like a big problem, but most of the modules you create or pull from the PSGallery are script modules.</span></span>

<span data-ttu-id="b0bc1-271">Das Hauptproblem ist, dass Skriptmodule nicht die Werte für `$WhatIfPreference` oder `$ConfirmPreference` (und einige andere) übernehmen, wenn sie von Funktionen in anderen Skriptmodulen aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-271">The core issue is that script modules do not inherit the values for `$WhatIfPreference` or `$ConfirmPreference` (and several others) when called from functions in other script modules.</span></span>

<span data-ttu-id="b0bc1-272">Allgemein lässt sich dies am besten zusammenfassen, dass es für binäre Module korrekt funktioniert und dass man nicht darauf vertrauen kann, dass es für Skriptmodule funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-272">The best way to summarize this as a general rule is that this works correctly for binary modules and never trust it to work for script modules.</span></span> <span data-ttu-id="b0bc1-273">Wenn Sie sich nicht sicher sind, sollten Sie es entweder testen, oder einfach annehmen, dass es nicht richtig funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-273">If you aren't sure, either test it or just assume it doesn't work correctly.</span></span>

<span data-ttu-id="b0bc1-274">Ich persönlich halte das für sehr riskant, weil dadurch Szenarios entstehen, in denen Sie `-WhatIf`-Unterstützung zu mehreren Modulen hinzufügen, die isoliert korrekt funktionieren, aber nicht ordnungsgemäß funktionieren, wenn sie sich gegenseitig aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-274">I personally feel this is very dangerous because it creates scenarios where you add `-WhatIf` support to multiple modules that work correctly in isolation, but fail to work correctly when they call each other.</span></span>

<span data-ttu-id="b0bc1-275">Wir arbeiten an einem GitHub-RFC, um dieses Problem zu beheben.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-275">We do have a GitHub RFC working to get this issue fixed.</span></span> <span data-ttu-id="b0bc1-276">Weitere Informationen finden Sie unter [Propagate execution preferences beyond script module scope][RFC] (Weiterleiten von Ausführungseinstellungen über den Skriptmodulbereich hinaus).</span><span class="sxs-lookup"><span data-stu-id="b0bc1-276">See [Propagate execution preferences beyond script module scope][RFC] for more details.</span></span>

## <a name="in-closing"></a><span data-ttu-id="b0bc1-277">Abschluss</span><span class="sxs-lookup"><span data-stu-id="b0bc1-277">In closing</span></span>

<span data-ttu-id="b0bc1-278">Ich muss jedes Mal nachschlagen, wie ich `ShouldProcess` verwende.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-278">I have to look up how to use `ShouldProcess` every time I need to use it.</span></span> <span data-ttu-id="b0bc1-279">Ich habe lange gebraucht, um `ShouldProcess` von `ShouldContinue` zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-279">It took me a long time to distinguish `ShouldProcess` from `ShouldContinue`.</span></span> <span data-ttu-id="b0bc1-280">Ich muss fast immer nachschlagen, welche Parameter verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-280">I almost always need to look up what parameters to use.</span></span> <span data-ttu-id="b0bc1-281">Machen Sie sich also keine Sorgen, wenn Sie gelegentlich noch etwas verwirrt sind.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-281">So don't worry if you still get confused from time to time.</span></span> <span data-ttu-id="b0bc1-282">Sie können diesen Artikel bei Bedarf jederzeit hier abrufen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-282">This article will be here when you need it.</span></span> <span data-ttu-id="b0bc1-283">Ich bin mir sicher, dass ich ihn selbst häufig zu Rate ziehen werde.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-283">I'm sure I will reference it often myself.</span></span>

<span data-ttu-id="b0bc1-284">Wenn Ihnen dieser Beitrag gefallen hat, können Sie mir Ihre Meinung auf Twitter über den untenstehenden Link mitteilen.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-284">If you liked this post, please share your thoughts with me on Twitter using the link below.</span></span> <span data-ttu-id="b0bc1-285">Ich höre immer gerne von Menschen, für die meine Inhalte hilfreich sind.</span><span class="sxs-lookup"><span data-stu-id="b0bc1-285">I always like hearing from people that get value from my content.</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[original version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Allgemeine Parameter]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[common parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[Alles, was Sie schon immer über Hashtabellen wissen wollten]: everything-about-hashtable.md
[everything you wanted to know about hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
