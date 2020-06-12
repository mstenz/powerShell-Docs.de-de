---
title: Das Hilfesystem
description: Das Beherrschen des Hilfesystems ist der Schlüssel zum Erfolg mit der PowerShell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 43d2de7e1f59ce5e980c192decb5309d3f6d0ff8
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438111"
---
# <a name="chapter-2---the-help-system"></a><span data-ttu-id="8b973-103">Kapitel 2: Das Hilfesystem</span><span class="sxs-lookup"><span data-stu-id="8b973-103">Chapter 2 - The Help System</span></span>

<span data-ttu-id="8b973-104">Zwei Gruppen von IT-Profis wurden ohne Zugriff auf einen Computer einem schriftlichen Test unterzogen, um Ihre Fähigkeiten hinsichtlich der PowerShell zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8b973-104">Two groups of IT pros were given a written test without access to a computer to determine their skill level with PowerShell.</span></span> <span data-ttu-id="8b973-105">PowerShell-Einsteiger wurden in die eine Gruppe und Experten in die andere Gruppe eingeteilt.</span><span class="sxs-lookup"><span data-stu-id="8b973-105">PowerShell beginners were placed in one group and experts in another.</span></span>
<span data-ttu-id="8b973-106">Basierend auf den Testergebnissen schien kein großer Unterschied bei den Kenntnissen zwischen beiden Gruppen zu bestehen.</span><span class="sxs-lookup"><span data-stu-id="8b973-106">Based on the results of the test, there didn't seem to be much difference in the skill level between the two groups.</span></span> <span data-ttu-id="8b973-107">Beide Gruppen erhielten einen zweiten Test, ähnlich dem ersten.</span><span class="sxs-lookup"><span data-stu-id="8b973-107">Both groups were given a second test similar to the first one.</span></span> <span data-ttu-id="8b973-108">Diesmal erhielten sie allerdings Zugriff auf einen Computer mit PowerShell ohne Internetzugang.</span><span class="sxs-lookup"><span data-stu-id="8b973-108">This time they were given access to a computer with PowerShell that didn't have access to the internet.</span></span> <span data-ttu-id="8b973-109">Das Ergebnis des zweiten Tests zeigte einen großen Unterschied bei den Kenntnissen zwischen beiden Gruppen.</span><span class="sxs-lookup"><span data-stu-id="8b973-109">The results of the second test showed a huge difference in the skill level between the two groups.</span></span> <span data-ttu-id="8b973-110">Experten kennen nicht immer die Antworten, aber sie wissen, wie Sie die an die Antworten kommen können.</span><span class="sxs-lookup"><span data-stu-id="8b973-110">Experts don't always know the answers, but they know how to figure out the answers.</span></span>

<span data-ttu-id="8b973-111">Worin bestand der Unterschied bei den Ergebnissen des ersten und zweiten Tests zwischen diesen beiden Gruppen?</span><span class="sxs-lookup"><span data-stu-id="8b973-111">What was the difference in the results of the first and second test between these two groups?</span></span>

<span data-ttu-id="8b973-112">Die in diesen beiden Tests beobachteten Unterschiede lagen darin, dass Experten sich nicht merken, wie Tausende von Befehlen in PowerShell verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8b973-112">The differences observed in these two tests were because experts don't memorize how to use thousands of commands in PowerShell.</span></span> <span data-ttu-id="8b973-113">Sie lernen, wie Sie das Hilfesystem in PowerShell optimal verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b973-113">They learn how to use the help system within PowerShell extremely well.</span></span>
<span data-ttu-id="8b973-114">Dies ermöglicht es Ihnen, bei Bedarf die erforderlichen Befehle zuerst zu finden und dann, nachdem Sie sie gefunden haben, ihre Verwendung zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8b973-114">This allows them to find the necessary commands when needed and how to use those commands once they've found them.</span></span>

<span data-ttu-id="8b973-115">Ich habe Jeffrey Snover, den Erfinder der PowerShell, mehrmals eine ähnliche Geschichte erzählen gehört.</span><span class="sxs-lookup"><span data-stu-id="8b973-115">I've heard Jeffrey Snover, the inventor of PowerShell, tell a similar story a number of times.</span></span>

<span data-ttu-id="8b973-116">Das Beherrschen des Hilfesystems ist der Schlüssel zum Erfolg mit der PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b973-116">Mastering the help system is the key to being successful with PowerShell.</span></span>

## <a name="discoverability"></a><span data-ttu-id="8b973-117">Erkennbarkeit</span><span class="sxs-lookup"><span data-stu-id="8b973-117">Discoverability</span></span>

<span data-ttu-id="8b973-118">Kompilierte Befehle in PowerShell werden als „Cmdlets“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8b973-118">Compiled commands in PowerShell are called cmdlets.</span></span> <span data-ttu-id="8b973-119">Cmdlet wird wie „Command-let“ (nicht CMD-let) ausgesprochen.</span><span class="sxs-lookup"><span data-stu-id="8b973-119">Cmdlet is pronounced "command-let" (not CMD-let).</span></span> <span data-ttu-id="8b973-120">Namen von Cmdlets weisen die Form von „Verb-Nomen“-Befehlen im Singular auf, damit Sie leicht auffindbar sind.</span><span class="sxs-lookup"><span data-stu-id="8b973-120">Cmdlets names have the form of singular "Verb-Noun" commands to make them easily discoverable.</span></span> <span data-ttu-id="8b973-121">Beispielsweise ist das Cmdlet zur Bestimmung, welche Prozesse ausgeführt werden, `Get-Process`, und das Cmdlet zum Abrufen einer Liste von Diensten und deren Status ist `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="8b973-121">For example, the cmdlet for determining what processes are running is `Get-Process` and the cmdlet for retrieving a list of services and their statuses is `Get-Service`.</span></span> <span data-ttu-id="8b973-122">Es gibt andere Arten von Befehlen in PowerShell, wie z. B. Aliase und Funktionen, die später in diesem Buch behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="8b973-122">There are other types of commands in PowerShell such as aliases and functions that will be covered later in this book.</span></span> <span data-ttu-id="8b973-123">Der Begriff „PowerShell-Befehl“ ist ein allgemeiner Begriff, der häufig verwendet wird, um auf einen beliebigen Befehlstyp in PowerShell zu verweisen, unabhängig davon, ob es sich um ein Cmdlet, eine Funktion oder einen Alias handelt.</span><span class="sxs-lookup"><span data-stu-id="8b973-123">The term PowerShell command is a generic term that's often used to refer to any type of command in PowerShell, regardless of whether or not it's a cmdlet, function, or alias.</span></span>

## <a name="the-three-core-cmdlets-in-powershell"></a><span data-ttu-id="8b973-124">Die drei wesentlichen Cmdlets in PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b973-124">The Three Core Cmdlets in PowerShell</span></span>

- `Get-Command`
- `Get-Help`
- <span data-ttu-id="8b973-125">`Get-Member` (wird in Kapitel 3 behandelt)</span><span class="sxs-lookup"><span data-stu-id="8b973-125">`Get-Member` (covered in chapter 3)</span></span>

<span data-ttu-id="8b973-126">Eine Frage, die mir häufig gestellt wird, ist, wie man herausfindet, was die Befehle in PowerShell sind?</span><span class="sxs-lookup"><span data-stu-id="8b973-126">One question I'm often asked is how do you figure out what the commands are in PowerShell?</span></span> <span data-ttu-id="8b973-127">Sowohl `Get-Command` als auch `Get-Help` kann verwendet werden, um die Befehle zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="8b973-127">Both `Get-Command` and `Get-Help` can be used to determine the commands.</span></span>

## <a name="get-help"></a><span data-ttu-id="8b973-128">Get-Help</span><span class="sxs-lookup"><span data-stu-id="8b973-128">Get-Help</span></span>

<span data-ttu-id="8b973-129">`Get-Help` ist ein multifunktionaler Befehl.</span><span class="sxs-lookup"><span data-stu-id="8b973-129">`Get-Help` is a multipurpose command.</span></span> <span data-ttu-id="8b973-130">`Get-Help` hilft Ihnen, zu erfahren, wie Befehle verwendet werden, nachdem Sie sie gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="8b973-130">`Get-Help` helps you learn how to use commands once you find them.</span></span> <span data-ttu-id="8b973-131">`Get-Help` kann auch verwendet werden, um Befehle zu finden, funktioniert aber auf eine andere und eher indirekte Weise im Vergleich zu `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="8b973-131">`Get-Help` can also be used to help locate commands, but in a different and more indirect way when compared to `Get-Command`.</span></span>

<span data-ttu-id="8b973-132">Wenn `Get-Help` zum Suchen von Befehlen verwendet wird, sucht es zuerst nach Platzhalterübereinstimmungen von Befehlsnamen, basierend auf der bereitgestellten Eingabe.</span><span class="sxs-lookup"><span data-stu-id="8b973-132">When `Get-Help` is used to locate commands, it first searches for wildcard matches of command names based on the provided input.</span></span> <span data-ttu-id="8b973-133">Wenn keine Entsprechung gefunden wird, werden die Hilfethemen selbst durchsucht, und wenn keine Übereinstimmung gefunden wird, wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-133">If it doesn't find a match, it searches through the help topics themselves, and if no match is found an error is returned.</span></span> <span data-ttu-id="8b973-134">Im Gegensatz zur weit verbreiteten Ansicht kann `Get-Help` verwendet werden, um Befehle zu suchen, zu denen es keine Hilfethemen gibt.</span><span class="sxs-lookup"><span data-stu-id="8b973-134">Contrary to popular belief, `Get-Help` can be used to find commands that don't have help topics.</span></span>

<span data-ttu-id="8b973-135">Das Erste, was Sie über das Hilfesystem in PowerShell wissen müssen, ist, wie Sie das Cmdlet `Get-Help` verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b973-135">The first thing you need to know about the help system in PowerShell is how to use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="8b973-136">Der folgende Befehl wird verwendet, um das Hilfethema für `Get-Help` anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8b973-136">The following command is used to display the help topic for `Get-Help`.</span></span>

```powershell
Get-Help -Name Get-Help
```

```Outpout
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="8b973-137">Seit PowerShell, Version 3, wird die PowerShell-Hilfe nicht mehr zusammen mit dem Betriebssystem ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="8b973-137">Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system.</span></span> <span data-ttu-id="8b973-138">Wenn Sie `Get-Help` zum ersten Mal für einen Befehl ausführen, wird die vorherige Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b973-138">The first time `Get-Help` is run for a command, the previous message is displayed.</span></span> <span data-ttu-id="8b973-139">Wenn anstelle des Cmdlets `Get-Help` die Funktion `help` oder der Alias `man` verwendet wird, erhalten Sie diese Eingabeaufforderung nicht.</span><span class="sxs-lookup"><span data-stu-id="8b973-139">If the `help` function or `man` alias is used instead of the `Get-Help` cmdlet, you don't receive this prompt.</span></span>

<span data-ttu-id="8b973-140">Wenn Sie mithilfe von <kbd>Y</kbd> (Yes) mit „Ja“ antworten, wird das Cmdlet `Update-Help` ausgeführt, für das standardmäßig Internetzugriff erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="8b973-140">Answering yes by pressing <kbd>Y</kbd> runs the `Update-Help` cmdlet, which requires internet access by default.</span></span> <span data-ttu-id="8b973-141">`Y` kann als Groß- oder Kleinbuchstabe angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8b973-141">`Y` can be specified in either upper or lower case.</span></span>

<span data-ttu-id="8b973-142">Nachdem die Hilfe heruntergeladen und das Update fertiggestellt wurde, wird das Hilfethema für den angegebenen Befehl zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="8b973-142">Once the help is downloaded and the update is complete, the help topic is returned for the specified command:</span></span>

```powershell
Get-Help -Name Get-Help
```

<span data-ttu-id="8b973-143">Nehmen Sie sich einen Moment Zeit, um dieses Beispiel auf Ihrem Computer auszuführen, sehen Sie sich die Ausgabe an, und beachten Sie, wie die Informationen gruppiert sind:</span><span class="sxs-lookup"><span data-stu-id="8b973-143">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="8b973-144">NAME</span><span class="sxs-lookup"><span data-stu-id="8b973-144">NAME</span></span>
- <span data-ttu-id="8b973-145">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="8b973-145">SYNOPSIS</span></span>
- <span data-ttu-id="8b973-146">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b973-146">SYNTAX</span></span>
- <span data-ttu-id="8b973-147">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8b973-147">DESCRIPTION</span></span>
- <span data-ttu-id="8b973-148">VERWANDTE LINKS</span><span class="sxs-lookup"><span data-stu-id="8b973-148">RELATED LINKS</span></span>
- <span data-ttu-id="8b973-149">ANMERKUNGEN</span><span class="sxs-lookup"><span data-stu-id="8b973-149">REMARKS</span></span>

<span data-ttu-id="8b973-150">Wie Sie sehen können, können Hilfethemen eine große Menge an Informationen enthalten, und das ist noch nicht einmal das gesamte Hilfethema.</span><span class="sxs-lookup"><span data-stu-id="8b973-150">As you can see, help topics can contain an enormous amount of information and this isn't even the entire help topic.</span></span>

<span data-ttu-id="8b973-151">Ein Parameter, wenn auch nicht spezifisch für PowerShell, ist eine Möglichkeit, um Eingaben an einen Befehl zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-151">While not specific to PowerShell, a parameter is a way to provide input to a command.</span></span> <span data-ttu-id="8b973-152">`Get-Help` verfügt über zahlreiche Parameter, die angegeben werden können, um das gesamte Hilfethema oder nur einen Teil davon zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-152">`Get-Help` has many parameters that can be specified in order to return the entire help topic or a subset of it.</span></span>

<span data-ttu-id="8b973-153">Im Abschnitt „Syntax“ des Hilfethemas, das im vorherigen Resultset angezeigt wurde, werden alle Parameter für `Get-Help` aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="8b973-153">The syntax section of the help topic shown in the previous set of results lists all of the parameters for `Get-Help`.</span></span> <span data-ttu-id="8b973-154">Auf den ersten Blick scheinen dieselben Parameter sechs Mal aufgeführt zu sein.</span><span class="sxs-lookup"><span data-stu-id="8b973-154">At first glance, it appears the same parameters are listed six different times.</span></span> <span data-ttu-id="8b973-155">Jeder dieser unterschiedlichen Blöcke im Abschnitt „Syntax“ ist ein Parametersatz.</span><span class="sxs-lookup"><span data-stu-id="8b973-155">Each of those different blocks in the syntax section is a parameter set.</span></span> <span data-ttu-id="8b973-156">Dies bedeutet, dass das Cmdlet `Get-Help` sechs verschiedene Parametersätze aufweist.</span><span class="sxs-lookup"><span data-stu-id="8b973-156">This means the `Get-Help` cmdlet has six different parameter sets.</span></span> <span data-ttu-id="8b973-157">Wenn Sie sich diese näher ansehen, werden Sie feststellen, dass in jedem der Parametersätze mindestens ein Parameter unterschiedlich ist.</span><span class="sxs-lookup"><span data-stu-id="8b973-157">If you take a closer look, you'll notice that at least one parameter is different in each of the parameter sets.</span></span>

<span data-ttu-id="8b973-158">Parametersätze schließen sich gegenseitig aus.</span><span class="sxs-lookup"><span data-stu-id="8b973-158">Parameter sets are mutually exclusive.</span></span> <span data-ttu-id="8b973-159">Sobald ein eindeutiger Parameter verwendet wird, der nur in einem der Parametersätze vorhanden ist, können nur die Parameter verwendet werden, die in diesem Parametersatz enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="8b973-159">Once a unique parameter that only exists in one of the parameter sets is used, only parameters contained within that parameter set can be used.</span></span> <span data-ttu-id="8b973-160">Beispielsweise könnten die Parameter **Full** und **Detailed** nicht gleichzeitig angegeben werden, weil sie sich in verschiedenen Parametersätzen befinden.</span><span class="sxs-lookup"><span data-stu-id="8b973-160">For example, both the **Full** and **Detailed** parameters couldn't be specified at the same time because they are in different parameter sets.</span></span>

<span data-ttu-id="8b973-161">Jeder der folgenden Parameter befindet sich in einem anderen Parametersatz:</span><span class="sxs-lookup"><span data-stu-id="8b973-161">Each of the following parameters are in different parameter sets:</span></span>

- <span data-ttu-id="8b973-162">Vollständig</span><span class="sxs-lookup"><span data-stu-id="8b973-162">Full</span></span>
- <span data-ttu-id="8b973-163">Detailliert</span><span class="sxs-lookup"><span data-stu-id="8b973-163">Detailed</span></span>
- <span data-ttu-id="8b973-164">Beispiele</span><span class="sxs-lookup"><span data-stu-id="8b973-164">Examples</span></span>
- <span data-ttu-id="8b973-165">Online</span><span class="sxs-lookup"><span data-stu-id="8b973-165">Online</span></span>
- <span data-ttu-id="8b973-166">Parameter</span><span class="sxs-lookup"><span data-stu-id="8b973-166">Parameter</span></span>
- <span data-ttu-id="8b973-167">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="8b973-167">ShowWindow</span></span>

<span data-ttu-id="8b973-168">Alle kryptischen Teile der Syntax, z. B. eckige und spitze Klammern, im Abschnitt „Syntax“ haben eine Bedeutung, und werden in Anhang A dieses Buchs behandelt.</span><span class="sxs-lookup"><span data-stu-id="8b973-168">All of the cryptic syntax such as square and angle brackets in the syntax section means something but will be covered in Appendix A of this book.</span></span> <span data-ttu-id="8b973-169">Zwar ist das Erlernen der Bedeutung der kryptischen Syntax wichtig, doch fällt es Einsteigern bei PowerShell, die sie möglicherweise auch nicht täglich verwenden, häufig schwer, sich dies zu merken.</span><span class="sxs-lookup"><span data-stu-id="8b973-169">While important, learning what the cryptic syntax is often difficult to retain for someone who is new to PowerShell and may not use it everyday.</span></span>

<span data-ttu-id="8b973-170">Weitere Informationen zum besseren Verständnis der kryptischen Syntax finden Sie in [Anhang A][].</span><span class="sxs-lookup"><span data-stu-id="8b973-170">For more information to better understand the cryptic syntax, see [Appendix A][].</span></span>

<span data-ttu-id="8b973-171">Für Einsteiger gibt es eine einfachere Möglichkeit, um an dieselben Informationen zu kommen, nur dass sie in normaler Sprache verfasst sind.</span><span class="sxs-lookup"><span data-stu-id="8b973-171">For beginners, there's an easier way to figure out the same information except in plain language.</span></span>

<span data-ttu-id="8b973-172">Wenn der Parameter **Full** für `Get-Help` angegeben wird, wird das gesamte Hilfethema zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-172">When the **Full** parameter of `Get-Help` is specified, the entire help topic is returned.</span></span>

```powershell
Get-Help -Name Get-Help -Full
```

<span data-ttu-id="8b973-173">Nehmen Sie sich einen Moment Zeit, um dieses Beispiel auf Ihrem Computer auszuführen, sehen Sie sich die Ausgabe an, und beachten Sie, wie die Informationen gruppiert sind:</span><span class="sxs-lookup"><span data-stu-id="8b973-173">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="8b973-174">NAME</span><span class="sxs-lookup"><span data-stu-id="8b973-174">NAME</span></span>
- <span data-ttu-id="8b973-175">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="8b973-175">SYNOPSIS</span></span>
- <span data-ttu-id="8b973-176">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b973-176">SYNTAX</span></span>
- <span data-ttu-id="8b973-177">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8b973-177">DESCRIPTION</span></span>
- <span data-ttu-id="8b973-178">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b973-178">PARAMETERS</span></span>
- <span data-ttu-id="8b973-179">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="8b973-179">INPUTS</span></span>
- <span data-ttu-id="8b973-180">AUSGABEN</span><span class="sxs-lookup"><span data-stu-id="8b973-180">OUTPUTS</span></span>
- <span data-ttu-id="8b973-181">HINWEISE</span><span class="sxs-lookup"><span data-stu-id="8b973-181">NOTES</span></span>
- <span data-ttu-id="8b973-182">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="8b973-182">EXAMPLES</span></span>
- <span data-ttu-id="8b973-183">VERWANDTE LINKS</span><span class="sxs-lookup"><span data-stu-id="8b973-183">RELATED LINKS</span></span>

<span data-ttu-id="8b973-184">Beachten Sie, dass durch die Verwendung des Parameters **Full** mehrere zusätzliche Abschnitte zurückgegeben wurden, von denen einer der Abschnitt „PARAMETER“ ist, der mehr Informationen als der kryptisch Abschnitt „SYNTAX“ bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="8b973-184">Notice that using the **Full** parameter returned several additional sections, one of which is the PARAMETERS section that provides more information than the cryptic SYNTAX section.</span></span>

<span data-ttu-id="8b973-185">Der Parameter **Full** ist ein Switch-Parameter (Schalter).</span><span class="sxs-lookup"><span data-stu-id="8b973-185">The **Full** parameter is a switch parameter.</span></span> <span data-ttu-id="8b973-186">Ein Parameter, der keinen Wert erfordert, wird als Switch-Parameter bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8b973-186">A parameter that doesn't require a value is called a switch parameter.</span></span> <span data-ttu-id="8b973-187">Wenn ein Switch-Parameter angegeben wird, ist sein Wert „true“, und er nicht angegeben wird, ist sein Wert „false“.</span><span class="sxs-lookup"><span data-stu-id="8b973-187">When a switch parameter is specified, it's value is true and when it's not, it's value is false.</span></span>

<span data-ttu-id="8b973-188">Wenn Sie dieses Kapitel in der PowerShell-Konsole durchgearbeitet haben, haben Sie bemerkt, dass der vorherige Befehl zum Anzeigen des vollständigen Hilfethemas für `Get-Help` auf dem Bildschirm durchgelaufen ist, ohne dass Sie die Möglichkeit hatten, es zu lesen.</span><span class="sxs-lookup"><span data-stu-id="8b973-188">If you've been working through this chapter in the PowerShell console, you noticed that the previous command to display the full help topic for `Get-Help` flew by on the screen without giving you a chance to read it.</span></span> <span data-ttu-id="8b973-189">Es gibt eine bessere Möglichkeit.</span><span class="sxs-lookup"><span data-stu-id="8b973-189">There's a better way.</span></span>

<span data-ttu-id="8b973-190">`Help` ist eine Funktion, die `Get-Help` per Pipeline an eine Funktion namens `more` weiterleitet, bei der es sich um einen Wrapper für die ausführbare Datei `more.com` in Windows handelt.</span><span class="sxs-lookup"><span data-stu-id="8b973-190">`Help` is a function that pipes `Get-Help` to a function named `more`, which is a wrapper for the `more.com` executable file in Windows.</span></span> <span data-ttu-id="8b973-191">In der PowerShell-Konsole stellt `help` immer eine Seite der Hilfe zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8b973-191">In the PowerShell console, `help` provides one page of help at a time.</span></span> <span data-ttu-id="8b973-192">In der ISE funktioniert der Befehl auf dieselbe Weise wie `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="8b973-192">In the ISE, it works the same way as `Get-Help`.</span></span> <span data-ttu-id="8b973-193">Meine Empfehlung ist es, die `help`-Funktion anstelle des `Get-Help`-Cmdlets zu verwenden, da sie eine bessere Erfahrung bietet, die Eingabe kürzer ist.</span><span class="sxs-lookup"><span data-stu-id="8b973-193">My recommendation is to use the `help` function instead of the `Get-Help` cmdlet since it provides a better experience and it's less to type.</span></span>

<span data-ttu-id="8b973-194">Kürzere Eingaben sind jedoch nicht immer eine gute Sache.</span><span class="sxs-lookup"><span data-stu-id="8b973-194">Less typing isn't always a good thing, however.</span></span> <span data-ttu-id="8b973-195">Wenn Sie Ihre Befehle als Skript speichern oder mit einer anderen Person teilen möchten, achten Sie darauf, dass Sie die vollständigen Cmdlet- und Parameternamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b973-195">If you're going to save your commands as a script or share them with someone else, be sure to use full cmdlet and parameter names.</span></span> <span data-ttu-id="8b973-196">Die vollständigen Namen sind selbstdokumentierend, wodurch sie leichter verständlich werden.</span><span class="sxs-lookup"><span data-stu-id="8b973-196">The full names are self-documenting, which makes them easier to understand.</span></span> <span data-ttu-id="8b973-197">Denken Sie an die nächste Person, die Ihre Befehle lesen und verstehen muss.</span><span class="sxs-lookup"><span data-stu-id="8b973-197">Think about the next person that has to read and understand your commands.</span></span> <span data-ttu-id="8b973-198">Das könnten Sie sein.</span><span class="sxs-lookup"><span data-stu-id="8b973-198">It could be you.</span></span> <span data-ttu-id="8b973-199">Ihre Kollegen und Ihr zukünftiges Ich werden es Ihnen danken.</span><span class="sxs-lookup"><span data-stu-id="8b973-199">Your coworkers and future self will thank you.</span></span>

<span data-ttu-id="8b973-200">Versuchen Sie, die folgenden Befehle in der PowerShell-Konsole auf Ihrem Computer in der Windows 10-Laborumgebung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="8b973-200">Try running the following commands in the PowerShell console on your Windows 10 lab environment computer.</span></span>

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

<span data-ttu-id="8b973-201">Haben Sie Unterschiede in der Ausgabe zu den zuvor aufgeführten Befehle bemerkt, als Sie diese auf Ihrem Computer in der Windows 10-Laborumgebung ausgeführt haben?</span><span class="sxs-lookup"><span data-stu-id="8b973-201">Did you notice any differences in the output from the previously listed commands when you ran them on your Windows 10 lab environment computer?</span></span>

<span data-ttu-id="8b973-202">Es gibt keine Unterschiede, außer dass die letzten beiden Optionen die Ergebnisse seitenweise zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-202">There aren't any differences other than the last two options return the results one page at a time.</span></span>
<span data-ttu-id="8b973-203">Die <kbd>Leertaste</kbd> wird zum Anzeigen der nächsten Inhaltsseite verwendet, wenn die `Help`-Funktion verwendet wird, und mit <kbd>STRG</kbd>+<kbd>C</kbd> werden Befehle abgebrochen, die in der PowerShell-Konsole ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8b973-203">The <kbd>spacebar</kbd> is used to display the next page of content when using the `Help` function and <kbd>Ctrl</kbd>+<kbd>C</kbd> cancels commands that are running in the PowerShell console.</span></span>

<span data-ttu-id="8b973-204">Im ersten Beispiel wird das Cmdlet `Get-Help` verwendet, im zweiten wird die Funktion `Help` verwendet, und im dritten wird der Parameter **Name** bei Verwendung der Funktion `Help` ausgelassen.</span><span class="sxs-lookup"><span data-stu-id="8b973-204">The first example uses the `Get-Help` cmdlet, the second uses the `Help` function, and the third omits the **Name** parameter when using the `Help` function.</span></span> <span data-ttu-id="8b973-205">**Name** ist ein Positionsparameter und wird in diesem Beispiel positionell verwendet.</span><span class="sxs-lookup"><span data-stu-id="8b973-205">**Name** is a positional parameter and it's being used positionally in that example.</span></span> <span data-ttu-id="8b973-206">Dies bedeutet, dass der Wert ohne Angabe des Parameternamens angegeben werden kann, solange der Wert selbst an der korrekten Position angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8b973-206">This means the value can be specified without specifying the parameter name, as long as the value itself is specified in the correct position.</span></span> <span data-ttu-id="8b973-207">Woher weiß ich, an welcher Position der Wert festgelegt werden muss?</span><span class="sxs-lookup"><span data-stu-id="8b973-207">How did I know what position to specify the value in?</span></span> <span data-ttu-id="8b973-208">Indem Sie die Hilfe lesen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b973-208">By reading the help as shown in the following example.</span></span>

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

<span data-ttu-id="8b973-209">Beachten Sie, dass im vorherigen Beispiel der Parameter **Parameter** mit der Help-Funktion verwendet wurde, um nur Informationen aus dem Hilfethema für den Parameter **Name** zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-209">Notice that in the previous example, the **Parameter** parameter was used with the Help function to only return information from the help topic for the **Name** parameter.</span></span> <span data-ttu-id="8b973-210">Dies ist sehr viel bündiger, als manuell durchzusehen, was manchmal wie ein hundertseitiges Hilfethema aussieht.</span><span class="sxs-lookup"><span data-stu-id="8b973-210">This is much more concise than trying to manually sift through what sometimes seems like a hundred page help topic.</span></span>

<span data-ttu-id="8b973-211">Basierend auf diesen Ergebnissen können Sie feststellen, dass der Parameter **Name** positionell ist und an Position Null (der ersten Position) angegeben werden muss, wenn er positionell verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8b973-211">Based on those results, you can see that the **Name** parameter is positional and must be specified in position zero (the first position) when used positionally.</span></span> <span data-ttu-id="8b973-212">Die Reihenfolge, in der Parameter angegeben werden, spielt keine Rolle, wenn der Parametername angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8b973-212">The order that parameters are specified in doesn't matter if the parameter name is specified.</span></span>

<span data-ttu-id="8b973-213">Eine weitere wichtige Information ist, dass der Parameter **Name** erwartet, dass der Datentyp für seinen Wert eine einzelne Zeichenfolge ist, die durch `<String>` gekennzeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="8b973-213">One other important piece of information is that the **Name** parameter expects the datatype for its value to be a single string, which is denoted by `<String>`.</span></span> <span data-ttu-id="8b973-214">Wenn mehrere Zeichenfolgen akzeptiert würden, würde der Datentyp als `<String[]>` aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="8b973-214">If it accepted multiple strings, the datatype would be listed as `<String[]>`.</span></span>

<span data-ttu-id="8b973-215">Manchmal möchten Sie einfach nicht das gesamte Hilfethema für einen Befehl anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8b973-215">Sometimes you simply don't want to display the entire help topic for a command.</span></span> <span data-ttu-id="8b973-216">Neben **Full** gibt es eine Reihe weiterer Parameter, die mit `Get-Help` oder `Help` angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="8b973-216">There are a number of other parameters besides **Full** that can be specified with `Get-Help` or `Help`.</span></span> <span data-ttu-id="8b973-217">Versuchen Sie, die folgenden Befehle auf Ihrem Computer in der Windows 10-Laborumgebung auszuführen:</span><span class="sxs-lookup"><span data-stu-id="8b973-217">Try running the following commands on your Windows 10 lab environment computer:</span></span>

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

<span data-ttu-id="8b973-218">In der Regel verwende ich `help <command name>` mit dem Parameter **Full** oder **Online**.</span><span class="sxs-lookup"><span data-stu-id="8b973-218">I typically use `help <command name>` with the **Full** or **Online** parameter.</span></span> <span data-ttu-id="8b973-219">Wenn ich nur an den Beispielen interessiert bin, verwende ich den Parameter **Examples**, und wenn ich nur an einem bestimmten Parameter interessiert bin, verwende ich den Parameter **Parameter**.</span><span class="sxs-lookup"><span data-stu-id="8b973-219">If I'm only interested in the examples, I'll use the **Examples** parameter and if I'm only interested in a specific parameter, I'll use the **Parameter** parameter.</span></span> <span data-ttu-id="8b973-220">Der Parameter **ShowWindow** öffnet das Hilfethema in einem separaten, durchsuchbaren Fenster, das auf einem anderen Monitor angezeigt werden kann, wenn Sie über mehrere Monitore verfügen.</span><span class="sxs-lookup"><span data-stu-id="8b973-220">The **ShowWindow** parameter opens the help topic in a separate searchable window that can be placed on a different monitor if you have multiple monitors.</span></span> <span data-ttu-id="8b973-221">Ich habe den Parameter **ShowWindow** vermieden, weil es einen bekannten Fehler gibt, durch den nicht das gesamte Hilfethema angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b973-221">I've avoided the **ShowWindow** parameter because there's a known bug where it doesn't display the entire help topic.</span></span>

<span data-ttu-id="8b973-222">Wenn Sie Hilfe in einem separaten Fenster anzeigen möchten, empfehle ich Ihnen, entweder den Parameter **Online** oder den Parameter **Full** zu verwenden und die Ergebnisse per Pipeline an `Out-GridView` weiterzuleiten, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b973-222">If you want help in a separate window, my recommendation is to either use the **Online** parameter or use the **Full** parameter and pipe the results to `Out-GridView`, as shown in the following example.</span></span>

```powershell
help Get-Command -Full | Out-GridView
```

<span data-ttu-id="8b973-223">Sowohl das Cmdlet `Out-GridView` als auch der Parameter **ShowWindow** des Cmdlets `Get-Help` erfordert ein Betriebssystem mit grafischer Benutzeroberfläche (GUI).</span><span class="sxs-lookup"><span data-stu-id="8b973-223">Both the `Out-GridView` cmdlet and the **ShowWindow** parameter of the `Get-Help` cmdlet require an operating system with a GUI (Graphical User Interface).</span></span> <span data-ttu-id="8b973-224">Sie generieren eine Fehlermeldung, wenn Sie versuchen, eins davon unter Windows Server zu verwenden, das mit der Installationsoption „Server Core“ (ohne GUI) installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="8b973-224">They will generate an error message if you attempt to use either of them on Windows Server that's been installed using the server core (no-GUI) installation option.</span></span>

<span data-ttu-id="8b973-225">Wenn Sie `Get-Help` verwenden möchten, um Befehle zu suchen, verwenden Sie das Sternchen-Platzhalterzeichen (`*`) mit dem Parameter **Name**.</span><span class="sxs-lookup"><span data-stu-id="8b973-225">To use `Get-Help` to find commands, use the asterisk (`*`) wildcard character with the **Name** parameter.</span></span> <span data-ttu-id="8b973-226">Geben Sie einen Begriff, mit dem Sie nach Befehlen suchen, als Wert für den Parameter **Name**an, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b973-226">Specify a term that you're searching for commands on as the value for the **Name** parameter as shown in the following example.</span></span>

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

<span data-ttu-id="8b973-227">Im vorherigen Beispiel sind die `*`-Platzhalterzeichen nicht erforderlich, und wenn Sie sie auslassen, erhalten Sie dasselbe Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="8b973-227">In the previous example, the `*` wildcard characters are not required and omitting them produces the same result.</span></span> <span data-ttu-id="8b973-228">`Get-Help` fügt die Platzhalterzeichen automatisch im Hintergrund hinzu.</span><span class="sxs-lookup"><span data-stu-id="8b973-228">`Get-Help` automatically adds the wildcard characters behind the scenes.</span></span>

```powershell
help process
```

<span data-ttu-id="8b973-229">Der vorherige Befehl erzeugt dieselben Ergebnisse wie durch das Angeben des `*`-Platzhalterzeichens an jedem Ende des Prozesses.</span><span class="sxs-lookup"><span data-stu-id="8b973-229">The previous command produces the same results as specifying the `*` wildcard character on each end of process.</span></span>

<span data-ttu-id="8b973-230">Ich ziehe es vor, sie hinzuzufügen, da dies die Option ist, die immer konsistent funktioniert.</span><span class="sxs-lookup"><span data-stu-id="8b973-230">I prefer to add them since that's the option that always works consistently.</span></span> <span data-ttu-id="8b973-231">Andernfalls sind sie in bestimmten Szenarien erforderlich und in anderen nicht.</span><span class="sxs-lookup"><span data-stu-id="8b973-231">Otherwise, they are required in certain scenarios and not others.</span></span> <span data-ttu-id="8b973-232">Sobald Sie ein Platzhalterzeichen in der Mitte des Werts hinzufügen, werden diese nicht mehr automatisch im Hintergrund dem von Ihnen angegebenen Wert hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8b973-232">As soon as you add a wildcard character in the middle of the value, they're no longer automatically added behind the scenes to the value you specified.</span></span>

```powershell
help pr*cess
```

<span data-ttu-id="8b973-233">Von diesem Befehl werden keine Ergebnisse zurückgegeben, es sei denn, das `*`-Platzhalterzeichen wird am Anfang, am Ende oder sowohl am Anfang als auch am Ende von `pr*cess` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8b973-233">No results are returned by that command unless the `*` wildcard character is added to the beginning, end, or both the beginning and end of `pr*cess`.</span></span>

<span data-ttu-id="8b973-234">Wenn der angegebene Wert mit einem Bindestrich beginnt, wird ein Fehler generiert, da er von PowerShell als Parametername interpretiert wird und für das Cmdlet `Get-Help` kein solcher Parametername vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="8b973-234">If the value you specified begins with a dash, then an error is generated because PowerShell interprets it as a parameter name and no such parameter name exists for the `Get-Help` cmdlet.</span></span>

```powershell
help -process
```

<span data-ttu-id="8b973-235">Wenn Sie versuchen, nach Befehlen zu suchen, die auf `-process` enden, müssen Sie das `*`-Platzhalterzeichen nur am Anfang des Werts hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b973-235">If what you're attempting to look for are commands that end with `-process`, you only need to add the `*` wildcard character to the beginning of the value.</span></span>

```powershell
help *-process
```

<span data-ttu-id="8b973-236">Bei der Suche nach PowerShell-Befehlen mit `Get-Help` sollten Sie bei dem Gesuchten stattdessen etwas ungenauer sein, anstatt zu spezifisch.</span><span class="sxs-lookup"><span data-stu-id="8b973-236">When searching for PowerShell commands with `Get-Help`, you want to be a little more vague instead of being too specific with what you're searching for.</span></span>

<span data-ttu-id="8b973-237">Früher wurden bei der Suche nach `process` nur Befehle gefunden, die `process` im Namen des Befehls enthielten, sodass nur diese als Ergebnisse zurückgegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="8b973-237">Searching for `process` earlier found only commands that contained `process` in the name of the command and returned only those results.</span></span> <span data-ttu-id="8b973-238">Wenn `Get-Help` für die Suche nach `processes` verwendet wird, werden keine Übereinstimmungen für Befehlsnamen gefunden. Daher wird eine Suche in allen Hilfethemen in PowerShell auf Ihrem System durchgeführt, und alle gefundenen Übereinstimmungen werden zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-238">When `Get-Help` is used to search for `processes`, it doesn't find any matches for command names, so it performs a search of every help topic in PowerShell on your system and returns any matches it finds.</span></span> <span data-ttu-id="8b973-239">Dadurch wird eine enorme Anzahl von Ergebnissen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-239">This causes it to return an enormous number of results.</span></span>

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

<span data-ttu-id="8b973-240">Die Verwendung von `Help` für die Suche nach `process` hat 10 Ergebnisse zurückgegeben, und die Verwendung zur Suche nach `processes` hat 68 Ergebnisse zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-240">Using `Help` to search for `process` returned 10 results and using it to search for `processes` returned 68 results.</span></span> <span data-ttu-id="8b973-241">Wenn nur ein Ergebnis gefunden wird, wird das Hilfethema selbst anstelle einer Liste von Befehlen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b973-241">If only one result is found, the help topic itself will be displayed instead of a list of commands.</span></span>

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

<span data-ttu-id="8b973-242">Doch entzaubern wir nun den Mythos, dass `Help` in PowerShell nur Befehle finden kann, zu denen es Hilfethemen gibt.</span><span class="sxs-lookup"><span data-stu-id="8b973-242">Now to debunk the myth that `Help` in PowerShell can only find commands that have help topics.</span></span>

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

<span data-ttu-id="8b973-243">Beachten Sie im vorherigen Beispiel, dass `more` kein Hilfethema besitzt, und dass das `Help`-System in PowerShell dennoch in der Lage war, es zu finden.</span><span class="sxs-lookup"><span data-stu-id="8b973-243">Notice in the previous example that `more` doesn't have a help topic, yet the `Help` system in PowerShell was able to find it.</span></span> <span data-ttu-id="8b973-244">Es hat nur eine Übereinstimmung gefunden und die grundlegenden Syntaxinformationen zurückgegeben, die Ihnen angezeigt werden, wenn ein Befehl kein Hilfethema besitzt.</span><span class="sxs-lookup"><span data-stu-id="8b973-244">It only found one match and returned the basic syntax information that you'll see when a command doesn't have a help topic.</span></span>

<span data-ttu-id="8b973-245">PowerShell enthält zahlreiche konzeptionelle („About“) Hilfethemen.</span><span class="sxs-lookup"><span data-stu-id="8b973-245">PowerShell contains numerous conceptual (About) help topics.</span></span> <span data-ttu-id="8b973-246">Der folgende Befehl kann verwendet werden, um eine Liste aller **About**-Hilfethemen in Ihrem System zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-246">The following command can be used to return a list of all **About** help topics on your system.</span></span>

```powershell
help About_*
```

<span data-ttu-id="8b973-247">Wenn Sie die Ergebnisse auf ein einzelnes „About“-Hilfethema beschränken, wird das eigentliche Hilfethema angezeigt, anstatt eine Liste zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-247">Limiting the results to one single About help topic displays the actual help topic instead of returning a list.</span></span>

```powershell
help about_Updatable_Help
```

<span data-ttu-id="8b973-248">Das Hilfesystem in PowerShell muss aktualisiert werden, damit die **About**-Hilfethemen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8b973-248">The help system in PowerShell has to be updated in order for the **About** help topics to be present.</span></span> <span data-ttu-id="8b973-249">Wenn die anfängliche Aktualisierung des Hilfesystems auf dem Computer aus irgendeinem Grund fehlgeschlagen ist, sind die Dateien erst verfügbar, wenn das Cmdlet `Update-Help` erfolgreich ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="8b973-249">If for some reason the initial update of the help system failed on your computer, the files will not be available until the `Update-Help` cmdlet has been run successfully.</span></span>

## <a name="get-command"></a><span data-ttu-id="8b973-250">Get-Command</span><span class="sxs-lookup"><span data-stu-id="8b973-250">Get-Command</span></span>

<span data-ttu-id="8b973-251">`Get-Command` ist darauf ausgelegt, Ihnen beim Auffinden von Befehlen zu helfen.</span><span class="sxs-lookup"><span data-stu-id="8b973-251">`Get-Command` is designed to help you locate commands.</span></span> <span data-ttu-id="8b973-252">Wenn Sie `Get-Command` ohne Parameter ausführen, wird eine Liste aller Befehle auf Ihrem System zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-252">Running `Get-Command` without any parameters returns a list of all the commands on your system.</span></span> <span data-ttu-id="8b973-253">Das folgende Beispiel veranschaulicht die Verwendung des Cmdlets `Get-Command`, um zu bestimmen, welche Befehle für das Arbeiten mit Prozessen vorhanden sind:</span><span class="sxs-lookup"><span data-stu-id="8b973-253">The following example demonstrates using the `Get-Command` cmdlet to determine what commands exist for working with processes:</span></span>

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

<span data-ttu-id="8b973-254">Beachten Sie, dass im vorherigen Beispiel, in dem `Get-Command` ausgeführt wurde, der Parameter **Noun** verwendet und `Process` als Wert für den Parameter **Noun** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8b973-254">Notice in the previous example where `Get-Command` was run, the **Noun** parameter is used and `Process` is specified as the value for the **Noun** parameter.</span></span> <span data-ttu-id="8b973-255">Was ist, wenn Sie nicht wüssten, wie das Cmdlet `Get-Command` verwendet wird?</span><span class="sxs-lookup"><span data-stu-id="8b973-255">What if you didn't know how to use the `Get-Command` cmdlet?</span></span> <span data-ttu-id="8b973-256">Sie könnten `Get-Help` verwenden, um das Hilfethema für `Get-Command` anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8b973-256">You could use `Get-Help` to display the help topic for `Get-Command`.</span></span>

<span data-ttu-id="8b973-257">Die Parameter **Name**, **Noun** und **Verb** akzeptieren Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="8b973-257">The **Name**, **Noun**, and **Verb** parameters accept wildcards.</span></span> <span data-ttu-id="8b973-258">Das folgende Beispiel illustriert die Verwendung von Platzhaltern mit dem Parameter **Name**:</span><span class="sxs-lookup"><span data-stu-id="8b973-258">The following example shows wildcards being used with the **Name** parameter:</span></span>

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

<span data-ttu-id="8b973-259">Ich bin kein großer Freund der Verwendung von Platzhaltern mit dem Parameter **Name** von `Get-Command`, da er auch ausführbare Dateien zurückgibt, die keine nativen PowerShell-Befehle sind.</span><span class="sxs-lookup"><span data-stu-id="8b973-259">I'm not a fan of using wildcards with the **Name** parameter of `Get-Command` since it also returns executable files that are not native PowerShell commands.</span></span>

<span data-ttu-id="8b973-260">Wenn Sie Platzhalterzeichen mit dem Parameter **Name** verwenden möchten, empfehle ich, die Ergebnisse mit dem Parameter **CommandType** einzuschränken.</span><span class="sxs-lookup"><span data-stu-id="8b973-260">If you are going to use wildcard characters with the **Name** parameter, I recommend limiting the results with the **CommandType** parameter.</span></span>

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

<span data-ttu-id="8b973-261">Eine bessere Option ist es, den Parameter **Verb** oder **Noun** oder beide zu verwenden, da nur PowerShell-Befehle sowohl Verben als auch Nomen aufweisen.</span><span class="sxs-lookup"><span data-stu-id="8b973-261">A better option is to use either the **Verb** or **Noun** parameter or both of them since only PowerShell commands have both verbs and nouns.</span></span>

<span data-ttu-id="8b973-262">Haben Sie einen Fehler in einem Hilfethema gefunden?</span><span class="sxs-lookup"><span data-stu-id="8b973-262">Found something wrong with a help topic?</span></span> <span data-ttu-id="8b973-263">Die gute Nachricht ist, dass die Hilfethemen für PowerShell mittlerweile Open Source und somit im Repository [PowerShell-Docs][] auf GitHub verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8b973-263">The good news is the help topics for PowerShell have been open-sourced and available in the [PowerShell-Docs][] repository on GitHub.</span></span> <span data-ttu-id="8b973-264">Denken Sie an die Community, und korrigieren Sie die fehlerhaften Informationen nicht nur für sich, sondern auch für alle anderen.</span><span class="sxs-lookup"><span data-stu-id="8b973-264">Pay it forward by not only fixing the incorrect information for yourself, but everyone else as well.</span></span> <span data-ttu-id="8b973-265">Forken Sie einfach das PowerShell-Dokumentationsrepository auf GitHub, aktualisieren Sie das Hilfethema, und reichen Sie eine Pull Request ein.</span><span class="sxs-lookup"><span data-stu-id="8b973-265">Simply fork the PowerShell documentation repository on GitHub, update the help topic, and submit a pull request.</span></span>
<span data-ttu-id="8b973-266">Nachdem die Pull Request akzeptiert wurde, steht die korrigierte Dokumentation jedem zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8b973-266">Once the pull request is accepted, the corrected documentation is available for everyone.</span></span>

## <a name="updating-help"></a><span data-ttu-id="8b973-267">Aktualisieren der Hilfe</span><span class="sxs-lookup"><span data-stu-id="8b973-267">Updating Help</span></span>

<span data-ttu-id="8b973-268">Die lokale Kopie der PowerShell-Hilfethemen wurde zuvor aktualisiert, als zum ersten Mal Hilfe zu einem Befehl angefordert wurde.</span><span class="sxs-lookup"><span data-stu-id="8b973-268">The local copy of the PowerShell help topics was previously updated the first-time help on a command was requested.</span></span> <span data-ttu-id="8b973-269">Es wird empfohlen, das Hilfesystem regelmäßig zu aktualisieren, da von Zeit zu Zeit Aktualisierungen am Hilfeinhalt vorliegen können.</span><span class="sxs-lookup"><span data-stu-id="8b973-269">It's recommended to periodically update the help system because there can be updates to the help content from time to time.</span></span> <span data-ttu-id="8b973-270">Das Cmdlet `Update-Help` dient der Aktualisierung der Hilfethemen.</span><span class="sxs-lookup"><span data-stu-id="8b973-270">The `Update-Help` cmdlet is used to update the help topics.</span></span>
<span data-ttu-id="8b973-271">Es benötigt standardmäßig Internetzugriff, und Sie müssen PowerShell mit erhöhten Rechten als Administrator ausführen.</span><span class="sxs-lookup"><span data-stu-id="8b973-271">It requires internet access by default and for you to be running PowerShell elevated as an administrator.</span></span>

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : The value of the HelpInfoUri key in the module manifest must resolve to a
container or root URL on a website where the help files are stored. The HelpInfoUri
'https://technet.microsoft.com/en-us/library/dd819413.aspx' does not resolve to a
container.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

<span data-ttu-id="8b973-272">Einige der Module haben Fehler zurückgegeben, was nicht ungewöhnlich ist.</span><span class="sxs-lookup"><span data-stu-id="8b973-272">A couple of the modules returned errors, which is not uncommon.</span></span> <span data-ttu-id="8b973-273">Wenn der Computer über keinen Internetzugang verfügte, könnten Sie das Cmdlet `Save-Help` auf einem anderen Computer mit Internetzugang verwenden, um die aktualisierten Hilfeinformationen zuerst auf einer Dateifreigabe in Ihrem Netzwerk zu speichern, und dann den Parameter **SourcePath** von `Update-Help` verwenden, um diesen Netzwerkspeicherort für die Hilfethemen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="8b973-273">If the machine didn't have internet access, you could use the `Save-Help` cmdlet on another machine that does have internet access to first save the updated help information to a file share on your network and then use the **SourcePath** parameter of `Update-Help` to specify this network location for the help topics.</span></span>

<span data-ttu-id="8b973-274">Erwägen Sie, eine geplante Aufgabe einzurichten oder Ihrem Profilskript in PowerShell eine Logik hinzuzufügen, um den Hilfeinhalt auf Ihrem Computer regelmäßig zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8b973-274">Consider setting up a scheduled task or adding some logic to your profile script in PowerShell to periodically update the help content on your computer.</span></span> <span data-ttu-id="8b973-275">Profilskripts werden in einem der nächsten Kapitel behandelt.</span><span class="sxs-lookup"><span data-stu-id="8b973-275">Profile scripts will be discussed in an upcoming chapter.</span></span>

## <a name="summary"></a><span data-ttu-id="8b973-276">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="8b973-276">Summary</span></span>

<span data-ttu-id="8b973-277">In diesem Kapitel haben Sie erfahren, wie Sie mit `Get-Help` und `Get-Command` Befehle auffinden können.</span><span class="sxs-lookup"><span data-stu-id="8b973-277">In this chapter you've learned how to find commands with both `Get-Help` and `Get-Command`.</span></span> <span data-ttu-id="8b973-278">Sie haben gelernt, wie Sie das Hilfesystem verwenden, um herauszufinden, wie Sie Befehle verwenden können, nachdem Sie diese gefunden haben.</span><span class="sxs-lookup"><span data-stu-id="8b973-278">You've learned how to use the help system to figure out how to use commands once you find them.</span></span> <span data-ttu-id="8b973-279">Sie haben außerdem gelernt, wie Sie den Inhalt der Hilfethemen aktualisieren, wenn Aktualisierungen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8b973-279">You've also learned how to update the content of the help topics when updates are available.</span></span>

<span data-ttu-id="8b973-280">Meine Herausforderung an Sie besteht darin, dass Sie jeden Tag einen PowerShell-Befehl lernen sollten.</span><span class="sxs-lookup"><span data-stu-id="8b973-280">My challenge to you is to learn a PowerShell command a day.</span></span>

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a><span data-ttu-id="8b973-281">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="8b973-281">Review</span></span>

1. <span data-ttu-id="8b973-282">Ist der Parameter **DisplayName** von `Get-Service` positionell?</span><span class="sxs-lookup"><span data-stu-id="8b973-282">Is the **DisplayName** parameter of `Get-Service` positional?</span></span>
1. <span data-ttu-id="8b973-283">Wie viele Parametersätze hat das Cmdlet `Get-Process`?</span><span class="sxs-lookup"><span data-stu-id="8b973-283">How many parameter sets does the `Get-Process` cmdlet have?</span></span>
1. <span data-ttu-id="8b973-284">Welche PowerShell-Befehle gibt es für das Arbeiten mit Ereignisprotokollen?</span><span class="sxs-lookup"><span data-stu-id="8b973-284">What PowerShell commands exist for working with event logs?</span></span>
1. <span data-ttu-id="8b973-285">Wie lautet der PowerShell-Befehl, um eine Liste der PowerShell-Prozesse zurückzugeben, die auf Ihrem Computer ausgeführt werden?</span><span class="sxs-lookup"><span data-stu-id="8b973-285">What is the PowerShell command for returning a list of PowerShell processes running on your computer?</span></span>
1. <span data-ttu-id="8b973-286">Wie aktualisieren Sie den auf Ihrem Computer gespeicherten PowerShell-Hilfeinhalt?</span><span class="sxs-lookup"><span data-stu-id="8b973-286">How do you update the PowerShell help content that's stored on your computer?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="8b973-287">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="8b973-287">Recommended Reading</span></span>

<span data-ttu-id="8b973-288">Wenn Sie weitere Informationen zu den in diesem Kapitel behandelten Themen wünschen, empfehle ich Ihnen, die folgenden PowerShell-Hilfethemen zu lesen.</span><span class="sxs-lookup"><span data-stu-id="8b973-288">If you want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="8b973-289">[Get-Help][]</span><span class="sxs-lookup"><span data-stu-id="8b973-289">[Get-Help][]</span></span>
- <span data-ttu-id="8b973-290">[Get-Command][]</span><span class="sxs-lookup"><span data-stu-id="8b973-290">[Get-Command][]</span></span>
- <span data-ttu-id="8b973-291">[Update-Help][]</span><span class="sxs-lookup"><span data-stu-id="8b973-291">[Update-Help][]</span></span>
- <span data-ttu-id="8b973-292">[Save-Help][]</span><span class="sxs-lookup"><span data-stu-id="8b973-292">[Save-Help][]</span></span>
- <span data-ttu-id="8b973-293">[about_Updatable_Help][]</span><span class="sxs-lookup"><span data-stu-id="8b973-293">[about_Updatable_Help][]</span></span>
- <span data-ttu-id="8b973-294">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="8b973-294">[about_Command_Syntax][]</span></span>

<span data-ttu-id="8b973-295">Im nächsten Kapitel erfahren Sie mehr über das Cmdlet `Get-Member` sowie über Objekte, Eigenschaften und Methoden.</span><span class="sxs-lookup"><span data-stu-id="8b973-295">In the next chapter, you'll learn about the `Get-Member` cmdlet as well as objects, properties, and methods.</span></span>

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[Anhang A]: appendix-a.md
[Appendix A]: appendix-a.md
