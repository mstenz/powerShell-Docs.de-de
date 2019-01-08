---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Verwenden von vertrauten Befehlsnamen
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402082"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="c39db-103">Verwenden vertrauter Befehlsnamen</span><span class="sxs-lookup"><span data-stu-id="c39db-103">Using familiar command names</span></span>

<span data-ttu-id="c39db-104">PowerShell unterstützt Aliase, um mit alternativen Namen auf Befehle zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="c39db-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="c39db-105">Durch Aliase können Benutzer mit Erfahrung in anderen Shell-Umgebungen gängige Befehlsnamen, die sie bereits kennen, für ähnliche Vorgänge in PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="c39db-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="c39db-106">Bei der Aliasverwendung wird einem Befehl ein neuer Name zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="c39db-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="c39db-107">Beispielsweise umfasst PowerShell eine interne Funktion namens `Clear-Host`, mit der das Ausgabefenster gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="c39db-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="c39db-108">Sie können an einer Eingabeaufforderung entweder `cls` oder den Alias `clear` eingeben.</span><span class="sxs-lookup"><span data-stu-id="c39db-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="c39db-109">PowerShell interpretiert diese Aliase und führt die Funktion `Clear-Host` aus.</span><span class="sxs-lookup"><span data-stu-id="c39db-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="c39db-110">Dieses Feature unterstützt Benutzer beim Erlernen von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c39db-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="c39db-111">Zunächst beherrschen die meisten **cmd.exe**- und Unix-Benutzer ein großes Repertoire an Befehlen, deren Namen sie bereits kennen.</span><span class="sxs-lookup"><span data-stu-id="c39db-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="c39db-112">Die PowerShell-Äquivalente führen möglicherweise nicht zu identischen Ergebnissen.</span><span class="sxs-lookup"><span data-stu-id="c39db-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="c39db-113">Dennoch sind die Ergebnisse ähnlich genug, um Benutzern das Arbeiten ohne Kenntnis der PowerShell-Befehlsnamen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="c39db-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="c39db-114">Das „Fingergedächtnis“ ist eine weitere Quelle für Frustrationen beim Erlernen einer neuen Befehlsshell.</span><span class="sxs-lookup"><span data-stu-id="c39db-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="c39db-115">Wenn Sie seit Jahren **cmd.exe** verwenden, geben Sie möglicherweise reflexartig den Befehl `cls` ein, um den Bildschirm zu löschen.</span><span class="sxs-lookup"><span data-stu-id="c39db-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="c39db-116">Ohne den Alias für `Clear-Host` erhalten Sie eine Fehlermeldung und wissen nicht, wie Sie zum Löschen der Ausgabe vorgehen müssen.</span><span class="sxs-lookup"><span data-stu-id="c39db-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="c39db-117">Die folgende Liste zeigt einige wenige der gängigen **cmd.exe**- und Unix-Befehle, die Sie in PowerShell verwenden können:</span><span class="sxs-lookup"><span data-stu-id="c39db-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="c39db-118">cat</span><span class="sxs-lookup"><span data-stu-id="c39db-118">cat</span></span>|<span data-ttu-id="c39db-119">dir</span><span class="sxs-lookup"><span data-stu-id="c39db-119">dir</span></span>|<span data-ttu-id="c39db-120">mount</span><span class="sxs-lookup"><span data-stu-id="c39db-120">mount</span></span>|<span data-ttu-id="c39db-121">rm</span><span class="sxs-lookup"><span data-stu-id="c39db-121">rm</span></span>|
|<span data-ttu-id="c39db-122">cd</span><span class="sxs-lookup"><span data-stu-id="c39db-122">cd</span></span>|<span data-ttu-id="c39db-123">echo</span><span class="sxs-lookup"><span data-stu-id="c39db-123">echo</span></span>|<span data-ttu-id="c39db-124">move</span><span class="sxs-lookup"><span data-stu-id="c39db-124">move</span></span>|<span data-ttu-id="c39db-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="c39db-125">rmdir</span></span>|
|<span data-ttu-id="c39db-126">chdir</span><span class="sxs-lookup"><span data-stu-id="c39db-126">chdir</span></span>|<span data-ttu-id="c39db-127">erase</span><span class="sxs-lookup"><span data-stu-id="c39db-127">erase</span></span>|<span data-ttu-id="c39db-128">popd</span><span class="sxs-lookup"><span data-stu-id="c39db-128">popd</span></span>|<span data-ttu-id="c39db-129">sleep</span><span class="sxs-lookup"><span data-stu-id="c39db-129">sleep</span></span>|
|<span data-ttu-id="c39db-130">clear</span><span class="sxs-lookup"><span data-stu-id="c39db-130">clear</span></span>|<span data-ttu-id="c39db-131">h</span><span class="sxs-lookup"><span data-stu-id="c39db-131">h</span></span>|<span data-ttu-id="c39db-132">ps</span><span class="sxs-lookup"><span data-stu-id="c39db-132">ps</span></span>|<span data-ttu-id="c39db-133">sort</span><span class="sxs-lookup"><span data-stu-id="c39db-133">sort</span></span>|
|<span data-ttu-id="c39db-134">cls</span><span class="sxs-lookup"><span data-stu-id="c39db-134">cls</span></span>|<span data-ttu-id="c39db-135">history</span><span class="sxs-lookup"><span data-stu-id="c39db-135">history</span></span>|<span data-ttu-id="c39db-136">pushd</span><span class="sxs-lookup"><span data-stu-id="c39db-136">pushd</span></span>|<span data-ttu-id="c39db-137">tee</span><span class="sxs-lookup"><span data-stu-id="c39db-137">tee</span></span>|
|<span data-ttu-id="c39db-138">copy</span><span class="sxs-lookup"><span data-stu-id="c39db-138">copy</span></span>|<span data-ttu-id="c39db-139">kill</span><span class="sxs-lookup"><span data-stu-id="c39db-139">kill</span></span>|<span data-ttu-id="c39db-140">pwd</span><span class="sxs-lookup"><span data-stu-id="c39db-140">pwd</span></span>|<span data-ttu-id="c39db-141">type</span><span class="sxs-lookup"><span data-stu-id="c39db-141">type</span></span>|
|<span data-ttu-id="c39db-142">del</span><span class="sxs-lookup"><span data-stu-id="c39db-142">del</span></span>|<span data-ttu-id="c39db-143">lp</span><span class="sxs-lookup"><span data-stu-id="c39db-143">lp</span></span>|<span data-ttu-id="c39db-144">r</span><span class="sxs-lookup"><span data-stu-id="c39db-144">r</span></span>|<span data-ttu-id="c39db-145">write</span><span class="sxs-lookup"><span data-stu-id="c39db-145">write</span></span>|
|<span data-ttu-id="c39db-146">diff</span><span class="sxs-lookup"><span data-stu-id="c39db-146">diff</span></span>|<span data-ttu-id="c39db-147">ls</span><span class="sxs-lookup"><span data-stu-id="c39db-147">ls</span></span>|<span data-ttu-id="c39db-148">ren</span><span class="sxs-lookup"><span data-stu-id="c39db-148">ren</span></span>||

<span data-ttu-id="c39db-149">Das Cmdlet `Get-Alias` zeigt Ihnen den tatsächlichen Namen des nativen PowerShell-Befehls, der einem Alias zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="c39db-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="c39db-150">Interpretieren von Standardaliasen</span><span class="sxs-lookup"><span data-stu-id="c39db-150">Interpreting standard aliases</span></span>

<span data-ttu-id="c39db-151">Die zuvor beschriebenen Aliase wurden für Namenskompatibilität mit anderen Befehlsshells entworfen.</span><span class="sxs-lookup"><span data-stu-id="c39db-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="c39db-152">Die meisten der in PowerShell integrierten Aliase dienen der Verkürzung.</span><span class="sxs-lookup"><span data-stu-id="c39db-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="c39db-153">Kürzere Namen sind einfacher einzugeben, aber schwer zu lesen, wenn Sie deren Bedeutung nicht kennen.</span><span class="sxs-lookup"><span data-stu-id="c39db-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="c39db-154">PowerShell-Aliase versuchen, einen Kompromiss zwischen Aussagekraft und Kürze zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c39db-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="c39db-155">PowerShell verwendet einen Standardsatz an Aliasen für gängige Nomen und Verben.</span><span class="sxs-lookup"><span data-stu-id="c39db-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="c39db-156">Beispielabkürzungen:</span><span class="sxs-lookup"><span data-stu-id="c39db-156">Example abbreviations:</span></span>

| <span data-ttu-id="c39db-157">Nomen oder Verb</span><span class="sxs-lookup"><span data-stu-id="c39db-157">Noun or Verb</span></span> | <span data-ttu-id="c39db-158">Abkürzung</span><span class="sxs-lookup"><span data-stu-id="c39db-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="c39db-159">Abrufen</span><span class="sxs-lookup"><span data-stu-id="c39db-159">Get</span></span>          | <span data-ttu-id="c39db-160">g</span><span class="sxs-lookup"><span data-stu-id="c39db-160">g</span></span>            |
| <span data-ttu-id="c39db-161">Festlegen</span><span class="sxs-lookup"><span data-stu-id="c39db-161">Set</span></span>          | <span data-ttu-id="c39db-162">s</span><span class="sxs-lookup"><span data-stu-id="c39db-162">s</span></span>            |
| <span data-ttu-id="c39db-163">Element</span><span class="sxs-lookup"><span data-stu-id="c39db-163">Item</span></span>         | <span data-ttu-id="c39db-164">i</span><span class="sxs-lookup"><span data-stu-id="c39db-164">i</span></span>            |
| <span data-ttu-id="c39db-165">Speicherort</span><span class="sxs-lookup"><span data-stu-id="c39db-165">Location</span></span>     | <span data-ttu-id="c39db-166">l</span><span class="sxs-lookup"><span data-stu-id="c39db-166">l</span></span>            |
| <span data-ttu-id="c39db-167">Befehl</span><span class="sxs-lookup"><span data-stu-id="c39db-167">Command</span></span>      | <span data-ttu-id="c39db-168">cm</span><span class="sxs-lookup"><span data-stu-id="c39db-168">cm</span></span>           |
| <span data-ttu-id="c39db-169">Alias</span><span class="sxs-lookup"><span data-stu-id="c39db-169">Alias</span></span>        | <span data-ttu-id="c39db-170">al</span><span class="sxs-lookup"><span data-stu-id="c39db-170">al</span></span>           |

<span data-ttu-id="c39db-171">Diese Aliase sind verständlich, wenn Sie die Kurznamen kennen.</span><span class="sxs-lookup"><span data-stu-id="c39db-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="c39db-172">Cmdlet-Name</span><span class="sxs-lookup"><span data-stu-id="c39db-172">Cmdlet name</span></span>    | <span data-ttu-id="c39db-173">Alias</span><span class="sxs-lookup"><span data-stu-id="c39db-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="c39db-174">gi</span><span class="sxs-lookup"><span data-stu-id="c39db-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="c39db-175">si</span><span class="sxs-lookup"><span data-stu-id="c39db-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="c39db-176">gl</span><span class="sxs-lookup"><span data-stu-id="c39db-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="c39db-177">sl</span><span class="sxs-lookup"><span data-stu-id="c39db-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="c39db-178">gcm</span><span class="sxs-lookup"><span data-stu-id="c39db-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="c39db-179">gal</span><span class="sxs-lookup"><span data-stu-id="c39db-179">gal</span></span>   |

<span data-ttu-id="c39db-180">Sobald Sie mit der Aliasverwendung in PowerShell vertraut sind, ist einfach zu erraten, dass **sal** sich auf `Set-Alias` bezieht.</span><span class="sxs-lookup"><span data-stu-id="c39db-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="c39db-181">Erstellen neuer Aliase</span><span class="sxs-lookup"><span data-stu-id="c39db-181">Creating new aliases</span></span>

<span data-ttu-id="c39db-182">Sie können mit dem Cmlet `Set-Alias` eigene Aliase erstellen.</span><span class="sxs-lookup"><span data-stu-id="c39db-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="c39db-183">Mit den folgenden Anweisungen werden beispielsweise die zuvor besprochenen standardmäßigen Cmdlet-Aliase erstellt:</span><span class="sxs-lookup"><span data-stu-id="c39db-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="c39db-184">Intern verwendet PowerShell ähnliche Befehle während des Starts, aber diese Aliase können nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="c39db-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="c39db-185">Wenn Sie versuchen, einen dieser Befehle auszuführen, erhalten Sie einen Fehler mit dem Hinweis, dass Aliase nicht geändert werden können.</span><span class="sxs-lookup"><span data-stu-id="c39db-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="c39db-186">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="c39db-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```