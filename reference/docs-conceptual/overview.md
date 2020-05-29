---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: Was ist PowerShell?
ms.openlocfilehash: 267b2938a0892c99c3a961bc7107f573df40a683
ms.sourcegitcommit: 38215ad49e237b219e62bb5a5f0eb3b6b048df1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2020
ms.locfileid: "83868478"
---
# <a name="what-is-powershell"></a><span data-ttu-id="2dba2-103">Was ist PowerShell?</span><span class="sxs-lookup"><span data-stu-id="2dba2-103">What is PowerShell?</span></span>

<span data-ttu-id="2dba2-104">PowerShell ist ein Framework zur plattformübergreifenden Aufgabenautomatisierung und Konfigurationsverwaltung und besteht aus einer Befehlszeilenshell und Skriptsprache.</span><span class="sxs-lookup"><span data-stu-id="2dba2-104">PowerShell is a cross-platform task automation and configuration management framework, consisting of a command-line shell and scripting language.</span></span> <span data-ttu-id="2dba2-105">Im Gegensatz zu den meisten Shells, bei denen Text akzeptiert und zurückgegeben wird, basiert PowerShell auf der .NET Common Language Runtime (CLR) und akzeptiert und gibt .NET-Objekte zurück.</span><span class="sxs-lookup"><span data-stu-id="2dba2-105">Unlike most shells, which accept and return text, PowerShell is built on top of the .NET Common Language Runtime (CLR), and accepts and returns .NET objects.</span></span> <span data-ttu-id="2dba2-106">Diese grundlegende Änderung bringt völlig neue Tools und Methoden für die Automatisierung mit sich.</span><span class="sxs-lookup"><span data-stu-id="2dba2-106">This fundamental change brings entirely new tools and methods for automation.</span></span>

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a><span data-ttu-id="2dba2-107">Die Ausgabe ist objektbasiert</span><span class="sxs-lookup"><span data-stu-id="2dba2-107">Output is object-based</span></span>

<span data-ttu-id="2dba2-108">Im Gegensatz zu herkömmlichen Befehlszeilenschnittstellen sind PowerShell-Cmdlets für den Umgang mit Objekten entworfen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-108">Unlike traditional command-line interfaces, PowerShell cmdlets are designed to deal with objects.</span></span>
<span data-ttu-id="2dba2-109">Ein Objekt setzt sich aus strukturierten Informationen zusammen und ist mehr als nur die Zeichenfolge, die auf dem Bildschirm erscheint.</span><span class="sxs-lookup"><span data-stu-id="2dba2-109">An object is structured information that is more than just the string of characters appearing on the screen.</span></span> <span data-ttu-id="2dba2-110">Die Befehlsausgabe umfasst immer zusätzliche Informationen, die Sie bei Bedarf nutzen können.</span><span class="sxs-lookup"><span data-stu-id="2dba2-110">Command output always carries extra information that you can use if you need it.</span></span>

<span data-ttu-id="2dba2-111">Wenn Sie in schon mal ein Textverarbeitungsprogramm zum Verarbeiten von Daten verwendet haben, werden Sie das abweichende Verhalten der Daten in PowerShell bemerken.</span><span class="sxs-lookup"><span data-stu-id="2dba2-111">If you've used text-processing tools to process data in the past, you'll find that they behave differently when used in PowerShell.</span></span> <span data-ttu-id="2dba2-112">In den meisten Fällen benötigen Sie kein Textverarbeitungsprogramm, um bestimmte Informationen zu extrahieren.</span><span class="sxs-lookup"><span data-stu-id="2dba2-112">In most cases, you don't need text-processing tools to extract specific information.</span></span> <span data-ttu-id="2dba2-113">Sie greifen mit der standardmäßigen PowerShell-Objektsyntax direkt auf Teile der Daten zu.</span><span class="sxs-lookup"><span data-stu-id="2dba2-113">You directly access portions of the data using standard PowerShell object syntax.</span></span>

## <a name="the-command-family-is-extensible"></a><span data-ttu-id="2dba2-114">Die Befehlsfamilie ist erweiterbar</span><span class="sxs-lookup"><span data-stu-id="2dba2-114">The command family is extensible</span></span>

<span data-ttu-id="2dba2-115">Schnittstellen wie `cmd.exe` bieten keine Möglichkeit zur direkten Erweiterung des integrierten Befehlssatzes.</span><span class="sxs-lookup"><span data-stu-id="2dba2-115">Interfaces such as `cmd.exe` don't provide a way for you to directly extend the built-in command set.</span></span> <span data-ttu-id="2dba2-116">Sie können externe Befehlszeilentools erstellen, die in `cmd.exe` ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2dba2-116">You can create external command-line tools that run in `cmd.exe`.</span></span> <span data-ttu-id="2dba2-117">Aber diese externen Tools umfassen keine Dienste wie z.B. eine integrierte Hilfe.</span><span class="sxs-lookup"><span data-stu-id="2dba2-117">But these external tools don't have services, such as Help integration.</span></span> <span data-ttu-id="2dba2-118">`cmd.exe` weiß nicht automatisch, dass es sich bei diesen externen Tools um gültige Befehle handelt.</span><span class="sxs-lookup"><span data-stu-id="2dba2-118">`cmd.exe` doesn't automatically know that these external tools are valid commands.</span></span>

<span data-ttu-id="2dba2-119">Die Befehle in PowerShell werden als _Cmdlets_ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="2dba2-119">The commands in PowerShell are known as _cmdlets_.</span></span> <span data-ttu-id="2dba2-120">Sie können jedes Cmdlet einzeln verwenden, aber deren Leistungsfähigkeit wird freigesetzt, wenn Sie diese kombinieren, um komplexe Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-120">You can use each cmdlet separately, but their power is realized when you combine them to perform complex tasks.</span></span> <span data-ttu-id="2dba2-121">Ähnlich wie viele Shells ermöglicht PowerShell Ihnen Zugriff auf das Dateisystem auf dem Computer.</span><span class="sxs-lookup"><span data-stu-id="2dba2-121">Like many shells, PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="2dba2-122">Mit PowerShell-_Anbietern_ haben Sie die Möglichkeit, auf andere Datenspeicher, etwa die Registrierung und den Zertifikatspeicher, so einfach zuzugreifen wie auf das Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="2dba2-122">PowerShell _providers_ enable you to access other data stores, such as the registry and the certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="2dba2-123">Mithilfe von kompiliertem Code oder Skripts können Sie eigene Cmdlets und Funktionsmodule erstellen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-123">You can create your own cmdlet and function modules using compiled code or scripts.</span></span> <span data-ttu-id="2dba2-124">Mit Modulen können der Shell Cmdlets und Anbieter hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2dba2-124">Modules can add cmdlets and providers to the shell.</span></span> <span data-ttu-id="2dba2-125">PowerShell bietet außerdem Unterstützung für Skripts, analog zu UNIX-Shellskripts und `cmd.exe`-Batchdateien.</span><span class="sxs-lookup"><span data-stu-id="2dba2-125">PowerShell also supports scripts that are analogous to UNIX shell scripts and `cmd.exe` batch files.</span></span>

## <a name="support-for-command-aliases"></a><span data-ttu-id="2dba2-126">Unterstützung für Befehlsaliase</span><span class="sxs-lookup"><span data-stu-id="2dba2-126">Support for command aliases</span></span>

<span data-ttu-id="2dba2-127">PowerShell unterstützt Aliase, um mit alternativen Namen auf Befehle zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-127">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="2dba2-128">Durch Aliase können Benutzer mit Erfahrung in anderen Shell-Umgebungen gängige Befehlsnamen, die sie bereits kennen, für ähnliche Vorgänge in PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dba2-128">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="2dba2-129">Bei der Aliasverwendung wird einem Befehl ein neuer Name zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="2dba2-129">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="2dba2-130">Beispielsweise umfasst PowerShell eine interne Funktion namens `Clear-Host`, mit der das Ausgabefenster gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-130">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="2dba2-131">Sie können an einer Eingabeaufforderung entweder `cls` oder den Alias `clear` eingeben.</span><span class="sxs-lookup"><span data-stu-id="2dba2-131">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="2dba2-132">PowerShell interpretiert diese Aliase und führt die Funktion `Clear-Host` aus.</span><span class="sxs-lookup"><span data-stu-id="2dba2-132">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="2dba2-133">Dieses Feature unterstützt Benutzer beim Erlernen von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2dba2-133">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="2dba2-134">Zunächst beherrschen die meisten `cmd.exe`- und Unix-Benutzer ein großes Repertoire an Befehlen, deren Namen sie bereits kennen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-134">First, most `cmd.exe` and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="2dba2-135">Die PowerShell-Äquivalente führen möglicherweise nicht zu identischen Ergebnissen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-135">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="2dba2-136">Dennoch sind die Ergebnisse ähnlich genug, um Benutzern das Arbeiten ohne Kenntnis der PowerShell-Befehlsnamen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-136">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="2dba2-137">Das „Muskelgedächtnis“ ist eine weitere Quelle für Frustrationen beim Erlernen einer neuen Befehlsshell.</span><span class="sxs-lookup"><span data-stu-id="2dba2-137">"Muscle memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="2dba2-138">Wenn Sie seit Jahren `cmd.exe` verwenden, geben Sie möglicherweise reflexartig den Befehl `cls` ein, um den Bildschirm zu löschen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-138">If you have used `cmd.exe` for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="2dba2-139">Ohne den Alias für `Clear-Host` erhalten Sie eine Fehlermeldung und wissen nicht, wie Sie zum Löschen der Ausgabe vorgehen müssen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-139">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

## <a name="powershell-handles-console-input-and-display"></a><span data-ttu-id="2dba2-140">PowerShell verarbeitet Konsoleneingabe und Anzeige</span><span class="sxs-lookup"><span data-stu-id="2dba2-140">PowerShell handles console input and display</span></span>

<span data-ttu-id="2dba2-141">Wenn Sie einen Befehl eingeben, verarbeitet PowerShell die Befehlszeileneingabe immer sofort.</span><span class="sxs-lookup"><span data-stu-id="2dba2-141">When you type a command, PowerShell always processes the command-line input directly.</span></span> <span data-ttu-id="2dba2-142">PowerShell formatiert darüber hinaus die Ausgabe, die auf dem Bildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-142">PowerShell also formats the output that you see on the screen.</span></span> <span data-ttu-id="2dba2-143">Dieser Unterschied ist wesentlich, weil dadurch die Arbeit für jedes Cmdlet verringert wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-143">This difference is significant because it reduces the work required of each cmdlet.</span></span> <span data-ttu-id="2dba2-144">Es wird sichergestellt, dass Sie Aufgaben mit beliebigen Cmdlets immer gleich ausführen können.</span><span class="sxs-lookup"><span data-stu-id="2dba2-144">It ensures that you can always do things the same way with any cmdlet.</span></span> <span data-ttu-id="2dba2-145">Cmdlet-Entwickler müssen keinen Code schreiben, mit dem die Befehlszeilenargumente analysiert oder die Ausgabe formatiert wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-145">Cmdlet developers don't need to write code to parse the command-line arguments or format the output.</span></span>

<span data-ttu-id="2dba2-146">Herkömmliche Befehlszeilentools haben eigene Schemas zum Anfordern und Anzeigen von Hilfe.</span><span class="sxs-lookup"><span data-stu-id="2dba2-146">Traditional command-line tools have their own schemes for requesting and displaying Help.</span></span> <span data-ttu-id="2dba2-147">Einige Befehlszeilentools verwenden `/?` zum Aufrufen der Hilfe, während andere `-?`, `/H` oder `//` verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dba2-147">Some command-line tools use `/?` to trigger the Help display; others use `-?`, `/H`, or even `//`.</span></span> <span data-ttu-id="2dba2-148">Bei einigen wird Hilfe in einem Fenster auf der grafischen Benutzeroberfläche und nicht in der Konsole angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2dba2-148">Some will display Help in a GUI window, rather than in the console display.</span></span> <span data-ttu-id="2dba2-149">Wenn Sie den falschen Parameter verwenden, ignoriert das Tool möglicherweise Ihre Eingabe und beginnt damit, automatisch einen Task auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-149">If you use the wrong parameter, the tool might ignore what you typed and begin executing a task automatically.</span></span>
<span data-ttu-id="2dba2-150">Da PowerShell die Befehlszeile automatisch analysiert und verarbeitet, bedeutet der Parameter `-?` immer „Hilfe für diesen Befehl anzeigen“.</span><span class="sxs-lookup"><span data-stu-id="2dba2-150">Since PowerShell automatically parses and processes the command line, the `-?` parameter always means "show me Help for this command".</span></span>

> [!NOTE]
> <span data-ttu-id="2dba2-151">Wenn Sie eine grafische Anwendung in PowerShell ausführen, wird das Fenster für die Anwendung geöffnet.</span><span class="sxs-lookup"><span data-stu-id="2dba2-151">If you run a graphic application in PowerShell, the window for the application opens.</span></span>
> <span data-ttu-id="2dba2-152">PowerShell greift nur beim Verarbeiten der angegebenen Befehlszeileneingabe oder zur Ausgabe der Anwendungsergebnisse im Konsolenfenster ein.</span><span class="sxs-lookup"><span data-stu-id="2dba2-152">PowerShell intervenes only when processing the command-line input you supply or the application output returned to the console window.</span></span> <span data-ttu-id="2dba2-153">PowerShell hat keinen Einfluss darauf, wie die Anwendung intern arbeitet.</span><span class="sxs-lookup"><span data-stu-id="2dba2-153">It does not affect how the application works internally.</span></span>

## <a name="powershell-has-a-pipeline"></a><span data-ttu-id="2dba2-154">Die PowerShell-Pipeline</span><span class="sxs-lookup"><span data-stu-id="2dba2-154">PowerShell has a pipeline</span></span>

<span data-ttu-id="2dba2-155">Pipelines sind wohl das wertvollste Konzept, das Befehlszeilenschnittstellen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-155">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="2dba2-156">Bei richtigem Einsatz verringern Pipelines den Aufwand durch die Verwendung von komplexen Befehlen und erleichtern es, den Ablauf zu sehen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-156">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work.</span></span> <span data-ttu-id="2dba2-157">Jeder Befehl in einer Pipeline gibt seine Ausgabe Element für Element an den nächsten Befehl weiter.</span><span class="sxs-lookup"><span data-stu-id="2dba2-157">Each command in a pipeline passes its output, item by item, to the next command.</span></span> <span data-ttu-id="2dba2-158">Befehle müssen jeweils nur ein Element zurzeit verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="2dba2-158">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="2dba2-159">Das Ergebnis ist eine verringerte Ressourcennutzung und die Möglichkeit, die Ausgabe unmittelbar zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2dba2-159">The result is reduced resource consumption and the ability to get output immediately.</span></span>

<span data-ttu-id="2dba2-160">Die Notation für Pipelines ist der Notation in anderen Shells ähnlich.</span><span class="sxs-lookup"><span data-stu-id="2dba2-160">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="2dba2-161">Auf den ersten Blick ist es möglicherweise nicht offensichtlich, wie sich Pipelines in PowerShell unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="2dba2-161">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="2dba2-162">Obwohl Text auf dem Bildschirm angezeigt wird, leitet PowerShell Objekte und keinen Text zwischen Befehlen weiter.</span><span class="sxs-lookup"><span data-stu-id="2dba2-162">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

<span data-ttu-id="2dba2-163">Wenn Sie beispielsweise das Cmdlet `Out-Host` zum Erzwingen einer seitenweisen Anzeige der Ausgabe eines anderen Befehls verwenden, sieht die Ausgabe wie der normale auf dem Bildschirm gezeigte Text aus, der in Seiten unterteilt ist:</span><span class="sxs-lookup"><span data-stu-id="2dba2-163">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="2dba2-164">Durch die Einteilung in Seiten wird auch die CPU-Auslastung reduziert, da die Verarbeitung an das Cmdlet `Out-Host` übertragen wird, wenn eine vollständige Seite für die Anzeige bereit ist.</span><span class="sxs-lookup"><span data-stu-id="2dba2-164">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="2dba2-165">Die Cmdlets, die sich in der Pipeline davor befinden, unterbrechen die Ausführung, bis die nächste Seite der Ausgabe verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2dba2-165">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

### <a name="objects-in-the-pipeline"></a><span data-ttu-id="2dba2-166">Objekte in der Pipeline</span><span class="sxs-lookup"><span data-stu-id="2dba2-166">Objects in the pipeline</span></span>

<span data-ttu-id="2dba2-167">Wenn Sie ein Cmdlet in PowerShell ausführen, sehen Sie eine Textausgabe, da es erforderlich ist, Objekte in einem Konsolenfenster als Text darzustellen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-167">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="2dba2-168">Die Textausgabe enthält möglicherweise nicht alle Eigenschaften des Objekts, das ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-168">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="2dba2-169">Betrachten Sie beispielsweise das Cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="2dba2-169">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="2dba2-170">Die Textausgabe ist eine Zusammenfassung der Informationen, keine vollständige Darstellung des Objekts, das von `Get-Location` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-170">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="2dba2-171">Die Überschrift in der Ausgabe wird durch den Prozess hinzugefügt, der die Daten für die Anzeige auf dem Bildschirm formatiert.</span><span class="sxs-lookup"><span data-stu-id="2dba2-171">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

```powershell
Get-Location
```

```Output
Path
----
C:\
```

<span data-ttu-id="2dba2-172">Wenn Sie die Ausgabe an das Cmdlet `Get-Member` weiterleiten, werden Informationen über das Objekt angezeigt, das von `Get-Location` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="2dba2-172">Piping the output to the `Get-Member` cmdlet displays information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="2dba2-173">`Get-Location` gibt ein **PathInfo**-Objekt zurück, das den aktuellen Pfad und andere Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="2dba2-173">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>

## <a name="built-in-help-system"></a><span data-ttu-id="2dba2-174">Integriertes Hilfesystem</span><span class="sxs-lookup"><span data-stu-id="2dba2-174">Built-in help system</span></span>

<span data-ttu-id="2dba2-175">Ähnlich wie bei `man`-Seiten, umfasst PowerShell ausführliche Hilfeartikel, in denen die Konzepte von PowerShell und die Befehlssyntax erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="2dba2-175">Similar to Unix `man` pages, PowerShell includes detailed help articles that explain PowerShell concepts and command syntax.</span></span> <span data-ttu-id="2dba2-176">Verwenden Sie das Cmdlet [Get-Help][], um diese Artikel über die Eingabeaufforderung anzuzeigen. Sie können aber auch die zuletzt aktualisierten Versionen dieser Artikel in der PowerShell-Dokumentation online anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2dba2-176">Use the [Get-Help][] cmdlet to display these articles at the command prompt or view the most recently updated versions of these articles in the PowerShell documentation online.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2dba2-177">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="2dba2-177">Next steps</span></span>

<span data-ttu-id="2dba2-178">Weitere Informationen zu PowerShell erhalten Sie im Abschnitt **Erlernen von PowerShell** auf dieser Website.</span><span class="sxs-lookup"><span data-stu-id="2dba2-178">To learn more about PowerShell, see the **Learning PowerShell** section of this site.</span></span>

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
