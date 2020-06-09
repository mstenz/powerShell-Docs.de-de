---
title: Alles, was Sie schon immer über die IF-Anweisung wissen wollten
description: PowerShell verfügt wie viele andere Sprachen auch über Anweisungen zur bedingten Ausführung von Code in Ihren Skripts.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6ffb70af694e80430d31991045b9fadc1a2cc3f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149523"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a><span data-ttu-id="59f9f-103">Alles, was Sie schon immer über die IF-Anweisung wissen wollten</span><span class="sxs-lookup"><span data-stu-id="59f9f-103">Everything you wanted to know about the IF statement</span></span>

<span data-ttu-id="59f9f-104">PowerShell verfügt wie viele andere Sprachen auch über Anweisungen zur bedingten Ausführung von Code in Ihren Skripts.</span><span class="sxs-lookup"><span data-stu-id="59f9f-104">Like many other languages, PowerShell has statements for conditionally executing code in your scripts.</span></span> <span data-ttu-id="59f9f-105">Eine dieser Anweisungen ist die [if][]-Anweisung.</span><span class="sxs-lookup"><span data-stu-id="59f9f-105">One of those statements is the [if][] statement.</span></span> <span data-ttu-id="59f9f-106">In diesem Artikel wird einer der wichtigsten Befehle in PowerShell im Detail erläutert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-106">Today we will take a deep dive into one of the most fundamental commands in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="59f9f-107">Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="59f9f-108">Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="59f9f-109">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="59f9f-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="conditional-execution"></a><span data-ttu-id="59f9f-110">Bedingte Ausführung</span><span class="sxs-lookup"><span data-stu-id="59f9f-110">Conditional execution</span></span>

<span data-ttu-id="59f9f-111">In Ihren Skripts müssen häufig Entscheidungen getroffen werden, welche Logik als Nächstes ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-111">Your scripts often need to make decisions and perform different logic based on those decisions.</span></span>
<span data-ttu-id="59f9f-112">Und genau das ist mit bedingter Ausführung gemeint.</span><span class="sxs-lookup"><span data-stu-id="59f9f-112">This is what I mean by conditional execution.</span></span> <span data-ttu-id="59f9f-113">Sie verfügen über eine Anweisung oder einen Wert, die bzw. der ausgewertet wird, damit basierend auf dieser Auswertung der nächste Codeabschnitt ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="59f9f-113">You have one statement or value to evaluate, then execute a different section of code based on that evaluation.</span></span> <span data-ttu-id="59f9f-114">Dieser Schritt wird mit der `if`-Anweisung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-114">This is exactly what the `if` statement does.</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="59f9f-115">Die IF-Anweisung</span><span class="sxs-lookup"><span data-stu-id="59f9f-115">The if statement</span></span>

<span data-ttu-id="59f9f-116">Nachfolgend ist ein einfaches Beispiel der `if`-Anweisung gezeigt:</span><span class="sxs-lookup"><span data-stu-id="59f9f-116">Here is a basic example of the `if` statement:</span></span>

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

<span data-ttu-id="59f9f-117">Zunächst wertet die `if`-Anweisung den Ausdruck in Klammern aus.</span><span class="sxs-lookup"><span data-stu-id="59f9f-117">The first thing the `if` statement does is evaluate the expression in parentheses.</span></span> <span data-ttu-id="59f9f-118">Wenn das Ergebnis dieser Auswertung `$true` lautet, wird der `scriptblock` in geschweiften Klammern ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-118">If it evaluates to `$true`, then it executes the `scriptblock` in the braces.</span></span> <span data-ttu-id="59f9f-119">Wenn der Wert `$false` lautet, wird der Skriptblock übersprungen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-119">If the value was `$false`, then it would skip over that scriptblock.</span></span>

<span data-ttu-id="59f9f-120">Im vorherigen Beispiel hat die `if`-Anweisung lediglich die Variable `$condition` ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-120">In the previous example, the `if` statement was just evaluating the `$condition` variable.</span></span> <span data-ttu-id="59f9f-121">Das Ergebnis lautete `$true`, sodass der `Write-Output`-Befehl innerhalb des Skriptblocks ausgeführt worden wäre.</span><span class="sxs-lookup"><span data-stu-id="59f9f-121">It was `$true` and would have executed the `Write-Output` command inside the scriptblock.</span></span>

<span data-ttu-id="59f9f-122">In einigen Sprachen können Sie eine einzelne Codezeile nach der `if`-Anweisung einfügen, die dann ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-122">In some languages, you can place a single line of code after the `if` statement and it gets executed.</span></span> <span data-ttu-id="59f9f-123">In PowerShell ist das nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="59f9f-123">That isn't the case in PowerShell.</span></span> <span data-ttu-id="59f9f-124">Für eine ordnungsgemäße Funktionsweise müssen Sie einen vollständigen `scriptblock` mit geschweiften Klammern angeben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-124">You must provide a full `scriptblock` with braces for it to work correctly.</span></span>

## <a name="comparison-operators"></a><span data-ttu-id="59f9f-125">Vergleichsoperatoren</span><span class="sxs-lookup"><span data-stu-id="59f9f-125">Comparison operators</span></span>

<span data-ttu-id="59f9f-126">In den meisten Fällen wird die `if`-Anweisung verwendet, um zwei Elemente zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-126">The most common use of the `if` statement for is comparing two items with each other.</span></span> <span data-ttu-id="59f9f-127">In PowerShell sind für verschiedene Vergleichsszenarien spezielle Operatoren verfügbar.</span><span class="sxs-lookup"><span data-stu-id="59f9f-127">PowerShell has special operators for different comparison scenarios.</span></span> <span data-ttu-id="59f9f-128">Bei Verwendung eines Vergleichsoperators wird der Wert auf der linken Seite mit dem Wert auf der rechten Seite verglichen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-128">When you use a comparison operator, the value on the left-hand side is compared to the value on the right-hand side.</span></span>

### <a name="-eq-for-equality"></a><span data-ttu-id="59f9f-129">Der Operator „-eq“ zum Testen auf Gleichheit</span><span class="sxs-lookup"><span data-stu-id="59f9f-129">-eq for equality</span></span>

<span data-ttu-id="59f9f-130">Mit `-eq` wird überprüft, ob zwei Werte identisch sind.</span><span class="sxs-lookup"><span data-stu-id="59f9f-130">The `-eq` does an equality check between two values to make sure they're equal to each other.</span></span>

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

<span data-ttu-id="59f9f-131">In diesem Beispiel wird verglichen, ob der bekannte Wert `5` mit meinem `$value` übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-131">In this example, I'm taking a known value of `5` and comparing it to my `$value` to see if they match.</span></span>

<span data-ttu-id="59f9f-132">Ein möglicher Anwendungsfall ist die Statusüberprüfung für einen Wert, bevor eine Aktion für diesen Wert durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-132">One possible use case is to check the status of a value before you take an action on it.</span></span> <span data-ttu-id="59f9f-133">Sie können z. B. mit einem Dienst arbeiten und überprüfen, ob er ausgeführt wird, bevor Sie `Restart-Service` für den Dienst aufrufen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-133">You could get a service and check that the status was running before you called `Restart-Service` on it.</span></span>

<span data-ttu-id="59f9f-134">In anderen Sprachen wie C# ist die Verwendung von `==` für Gleichheitsüberprüfungen üblich (z. B.: `5 == $value`). In PowerShell ist dies jedoch nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="59f9f-134">It's common in other languages like C# to use `==` for equality (ex: `5 == $value`) but that doesn't work with PowerShell.</span></span> <span data-ttu-id="59f9f-135">Ein weiterer gängiger Fehler ist, dass das Gleichheitszeichen (z. B.: `5 = $value`) verwendet wird. Dieses Zeichen ist jedoch für das Zuweisen von Werten zu Variablen reserviert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-135">Another common mistake that people make is to use the equals sign (ex: `5 = $value`) that is reserved for assigning values to variables.</span></span> <span data-ttu-id="59f9f-136">Indem Sie Ihren bekannten Wert auf der linken Seite platzieren, ist dieser Fehler weniger wahrscheinlich.</span><span class="sxs-lookup"><span data-stu-id="59f9f-136">By placing your known value on the left, it makes that mistaken more awkward to make.</span></span>

<span data-ttu-id="59f9f-137">Für diesen (und andere) Operatoren gibt es einige Variationen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-137">This operator (and others) has a few variations.</span></span>

- <span data-ttu-id="59f9f-138">`-eq`, Gleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-138">`-eq` case-insensitive equality</span></span>
- <span data-ttu-id="59f9f-139">`-ieq`, Gleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-139">`-ieq` case-insensitive equality</span></span>
- <span data-ttu-id="59f9f-140">`-ceq`, Gleichheitsoperator mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-140">`-ceq` case-sensitive equality</span></span>

### <a name="-ne-not-equal"></a><span data-ttu-id="59f9f-141">Der Operator „-ne“ zum Testen auf Ungleichheit</span><span class="sxs-lookup"><span data-stu-id="59f9f-141">-ne not equal</span></span>

<span data-ttu-id="59f9f-142">Viele Operatoren verfügen über einen verwandten Operator, mit dem eine gegenteilige Überprüfung durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-142">Many operators have a related operator that is checking for the opposite result.</span></span> <span data-ttu-id="59f9f-143">`-ne` überprüft, ob die Werte ungleich sind.</span><span class="sxs-lookup"><span data-stu-id="59f9f-143">`-ne` verifies that the values don't equal each other.</span></span>

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

<span data-ttu-id="59f9f-144">Verwenden Sie diesen Operator, um sicherzustellen, dass die Aktion nur dann ausgeführt wird, wenn der Wert nicht `5` lautet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-144">Use this to make sure that the action only executes if the value isn't `5`.</span></span> <span data-ttu-id="59f9f-145">Ein gutes Beispiel für die Verwendung dieses Operators ist die Überprüfung, ob ein Dienst ausgeführt wird, bevor Sie versuchen, einen Neustart durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-145">A good use-cases where would be to check if a service was in the running state before you try to start it.</span></span>

<span data-ttu-id="59f9f-146">**Variationen:**</span><span class="sxs-lookup"><span data-stu-id="59f9f-146">**Variations:**</span></span>

- <span data-ttu-id="59f9f-147">`-ne` Ungleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-147">`-ne` case-insensitive not equal</span></span>
- <span data-ttu-id="59f9f-148">`-ine` Ungleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-148">`-ine` case-insensitive not equal</span></span>
- <span data-ttu-id="59f9f-149">`-cne` Ungleichheitsoperator mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-149">`-cne` case-sensitive not equal</span></span>

<span data-ttu-id="59f9f-150">Dies sind die umgekehrten Variationen von `-eq`.</span><span class="sxs-lookup"><span data-stu-id="59f9f-150">These are inverse variations of `-eq`.</span></span> <span data-ttu-id="59f9f-151">Diese Typen werden gemeinsam gruppiert, wenn ich Variationen für weitere Operatoren ausführe.</span><span class="sxs-lookup"><span data-stu-id="59f9f-151">I'll group these types together when I list variations for other operators.</span></span>

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a><span data-ttu-id="59f9f-152">Die Operatoren „-gt“, „-ge“, „-lt“ und „-le“ zum Testen, ob ein Wert größer oder kleiner ist</span><span class="sxs-lookup"><span data-stu-id="59f9f-152">-gt -ge -lt -le for greater than or less than</span></span>

<span data-ttu-id="59f9f-153">Mit diesen Operatoren wird überprüft, ob ein Wert im Vergleich zu einem anderen Wert größer oder kleiner ist.</span><span class="sxs-lookup"><span data-stu-id="59f9f-153">These operators are used when checking to see if a value is larger or smaller than another value.</span></span>
<span data-ttu-id="59f9f-154">`-gt -ge -lt -le` stehen für die englischen Bezeichnungen GreaterThan, GreaterThanOrEqual, LessThan und LessThanOrEqual.</span><span class="sxs-lookup"><span data-stu-id="59f9f-154">The `-gt -ge -lt -le` stand for GreaterThan, GreaterThanOrEqual, LessThan, and LessThanOrEqual.</span></span>

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

<span data-ttu-id="59f9f-155">**Variationen:**</span><span class="sxs-lookup"><span data-stu-id="59f9f-155">**Variations:**</span></span>

- <span data-ttu-id="59f9f-156">`-gt`, größer als</span><span class="sxs-lookup"><span data-stu-id="59f9f-156">`-gt` greater than</span></span>
- <span data-ttu-id="59f9f-157">`-igt` größer als, ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-157">`-igt` greater than, case-insensitive</span></span>
- <span data-ttu-id="59f9f-158">`-cgt` größer als, mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-158">`-cgt` greater than, case-sensitive</span></span>
- <span data-ttu-id="59f9f-159">`-ge` größer als oder gleich</span><span class="sxs-lookup"><span data-stu-id="59f9f-159">`-ge` greater than or equal</span></span>
- <span data-ttu-id="59f9f-160">`-ige` größer als oder gleich, ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-160">`-ige` greater than or equal, case-insensitive</span></span>
- <span data-ttu-id="59f9f-161">`-cge` größer als oder gleich, mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-161">`-cge` greater than or equal, case-sensitive</span></span>
- <span data-ttu-id="59f9f-162">`-lt` kleiner als</span><span class="sxs-lookup"><span data-stu-id="59f9f-162">`-lt` less than</span></span>
- <span data-ttu-id="59f9f-163">`-ilt` kleiner als, ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-163">`-ilt` less than, case-insensitive</span></span>
- <span data-ttu-id="59f9f-164">`-clt` kleiner als, mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-164">`-clt` less than, case-sensitive</span></span>
- <span data-ttu-id="59f9f-165">`-le` kleiner als oder gleich</span><span class="sxs-lookup"><span data-stu-id="59f9f-165">`-le` less than or equal</span></span>
- <span data-ttu-id="59f9f-166">`-ile` kleiner als oder gleich, ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-166">`-ile` less than or equal, case-insensitive</span></span>
- <span data-ttu-id="59f9f-167">`-cle` kleiner als oder gleich, mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-167">`-cle` less than or equal, case-sensitive</span></span>

<span data-ttu-id="59f9f-168">Der Zusatz zur Beachtung/Nichtbeachtung der Groß-/Kleinschreibung scheint mir bei diesen Operatoren irrelevant.</span><span class="sxs-lookup"><span data-stu-id="59f9f-168">I don't know why you would use case-sensitive and insensitive options for these operators.</span></span>

### <a name="-like-wildcard-matches"></a><span data-ttu-id="59f9f-169">Der Operator „-like“ für den Abgleich mit Platzhaltern</span><span class="sxs-lookup"><span data-stu-id="59f9f-169">-like wildcard matches</span></span>

<span data-ttu-id="59f9f-170">PowerShell verfügt über eine eigene Syntax für den platzhalterbasierten Musterabgleich, die mit dem Operator `-like` verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="59f9f-170">PowerShell has its own wildcard-based pattern matching syntax and you can use it with the `-like` operator.</span></span> <span data-ttu-id="59f9f-171">Diese Platzhaltermuster sind recht simpel.</span><span class="sxs-lookup"><span data-stu-id="59f9f-171">These wildcard patterns are fairly basic.</span></span>

- <span data-ttu-id="59f9f-172">`?` führt einen Abgleich für ein einzelnes Zeichen durch</span><span class="sxs-lookup"><span data-stu-id="59f9f-172">`?` matches any single character</span></span>
- <span data-ttu-id="59f9f-173">`*` führt einen Abgleich für eine beliebige Anzahl von Zeichen durch</span><span class="sxs-lookup"><span data-stu-id="59f9f-173">`*` matches any number of characters</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

<span data-ttu-id="59f9f-174">Beachten Sie dabei, dass der Musterabgleich immer für die gesamte Zeichenfolge durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-174">It's important to point out that the pattern matches the whole string.</span></span> <span data-ttu-id="59f9f-175">Wenn der Abgleich für Zeichen in der Mitte der Zeichenfolge ausgeführt werden soll, muss `*` sowohl am Anfang als auch am Ende der Zeichenfolge platziert werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-175">If you need to match something in the middle of the string, you need to place the `*` on both ends of the string.</span></span>

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

<span data-ttu-id="59f9f-176">**Variationen:**</span><span class="sxs-lookup"><span data-stu-id="59f9f-176">**Variations:**</span></span>

- <span data-ttu-id="59f9f-177">`-like` Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-177">`-like` case-insensitive wildcard</span></span>
- <span data-ttu-id="59f9f-178">`-ilike` Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-178">`-ilike` case-insensitive wildcard</span></span>
- <span data-ttu-id="59f9f-179">`-clike` Übereinstimmung mit Platzhalter mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-179">`-clike` case-sensitive wildcard</span></span>
- <span data-ttu-id="59f9f-180">`-notlike` Keine Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-180">`-notlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="59f9f-181">`-inotlike` Keine Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-181">`-inotlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="59f9f-182">`-cnotlike` Keine Übereinstimmung mit Platzhalter mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-182">`-cnotlike` case-sensitive wildcard not matched</span></span>

### <a name="-match-regular-expression"></a><span data-ttu-id="59f9f-183">Der Operator „-match“ bei regulären Ausdrücken</span><span class="sxs-lookup"><span data-stu-id="59f9f-183">-match regular expression</span></span>

<span data-ttu-id="59f9f-184">Der Operator `-match` kann verwendet werden, um für eine Zeichenfolge einen Abgleich auszuführen, der auf einem regulären Ausdruck basiert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-184">The `-match` operator allows you to check a string for a regular-expression-based match.</span></span> <span data-ttu-id="59f9f-185">Verwenden Sie diese Option, wenn die Platzhaltermuster für Ihre Anforderungen nicht flexibel genug sind.</span><span class="sxs-lookup"><span data-stu-id="59f9f-185">Use this when the wildcard patterns aren't flexible enough for you.</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

<span data-ttu-id="59f9f-186">Der Abgleich für ein RegEx-Muster wird standardmäßig für eine beliebige Stelle innerhalb der Zeichenfolge durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-186">A regex pattern matches anywhere in the string by default.</span></span> <span data-ttu-id="59f9f-187">Sie können jedoch auch eine Teilzeichenfolge für den Abgleich angeben:</span><span class="sxs-lookup"><span data-stu-id="59f9f-187">So you can specify a substring that you want matched like this:</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

<span data-ttu-id="59f9f-188">RegEx ist eine komplexe und äußerst nützliche Sprache, mit der Sie sich vertraut machen sollten.</span><span class="sxs-lookup"><span data-stu-id="59f9f-188">Regex is a complex language of its own and worth looking into.</span></span> <span data-ttu-id="59f9f-189">In einem anderen Artikel gehe ich näher auf `-match` und [die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken][] ein.</span><span class="sxs-lookup"><span data-stu-id="59f9f-189">I talk more about `-match` and [the many ways to use regex][] in another article.</span></span>

<span data-ttu-id="59f9f-190">**Variationen:**</span><span class="sxs-lookup"><span data-stu-id="59f9f-190">**Variations:**</span></span>

- <span data-ttu-id="59f9f-191">`-match` RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-191">`-match` case-insensitive regex</span></span>
- <span data-ttu-id="59f9f-192">`-imatch` RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-192">`-imatch` case-insensitive regex</span></span>
- <span data-ttu-id="59f9f-193">`-cmatch` RegEx-Übereinstimmung mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-193">`-cmatch` case-sensitive regex</span></span>
- <span data-ttu-id="59f9f-194">`-notmatch` Keine RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-194">`-notmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="59f9f-195">`-inotmatch` Keine RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-195">`-inotmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="59f9f-196">`-cnotmatch` Keine RegEx-Übereinstimmung mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-196">`-cnotmatch` case-sensitive regex not matched</span></span>

### <a name="-is-of-type"></a><span data-ttu-id="59f9f-197">Der Operator „-is“ zum Überprüfen des Typs</span><span class="sxs-lookup"><span data-stu-id="59f9f-197">-is of type</span></span>

<span data-ttu-id="59f9f-198">Sie können den Typ eines Werts mit dem Operator `-is` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-198">You can check a value's type with the `-is` operator.</span></span>

```powershell
if ( $value -is [string] )
{
    # do something
}
```

<span data-ttu-id="59f9f-199">Dies kann nützlich sein, wenn Sie mit Klassen arbeiten oder verschiedene Objekte über die Pipeline akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="59f9f-199">You may use this if you're working with classes or accepting various objects over the pipeline.</span></span> <span data-ttu-id="59f9f-200">Sie könnten z. B. über einen Dienst oder einen Dienstnamen als Eingabe verfügen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-200">You could have either a service or a service name as your input.</span></span> <span data-ttu-id="59f9f-201">Überprüfen Sie dann, ob Sie über einen Dienst verfügen, und rufen Sie den Dienst ab, wenn Sie nur über den Namen verfügen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-201">Then check to see if you have a service and fetch the service if you only have the name.</span></span>

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

<span data-ttu-id="59f9f-202">**Variationen:**</span><span class="sxs-lookup"><span data-stu-id="59f9f-202">**Variations:**</span></span>

- <span data-ttu-id="59f9f-203">`-is` entspricht dem Typ</span><span class="sxs-lookup"><span data-stu-id="59f9f-203">`-is` of type</span></span>
- <span data-ttu-id="59f9f-204">`-isnot` entspricht nicht dem Typ</span><span class="sxs-lookup"><span data-stu-id="59f9f-204">`-isnot` not of type</span></span>

## <a name="collection-operators"></a><span data-ttu-id="59f9f-205">Auflistungsoperatoren</span><span class="sxs-lookup"><span data-stu-id="59f9f-205">Collection operators</span></span>

<span data-ttu-id="59f9f-206">Bei Verwendung der oben stehenden Operatoren mit einem einzelnen Wert lautet das Ergebnis entweder `$true` oder `$false`.</span><span class="sxs-lookup"><span data-stu-id="59f9f-206">When you use the previous operators with a single value, the result is `$true` or `$false`.</span></span> <span data-ttu-id="59f9f-207">Wenn Sie mit Auflistungen arbeiten, funktioniert dies etwas anders.</span><span class="sxs-lookup"><span data-stu-id="59f9f-207">This is handled slightly differently when working with a collection.</span></span> <span data-ttu-id="59f9f-208">Jedes Element innerhalb der Auflistung wird ausgewertet, und der Operator gibt jeden Wert zurück, dessen Ergebnis `$true` lautet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-208">Each item in the collection gets evaluated and the operator returns every value that evaluates to `$true`.</span></span>

```powershell
PS> 1,2,3,4 -eq 3
3
```

<span data-ttu-id="59f9f-209">Bei einer `if`-Anweisung funktioniert dies noch wie gewünscht.</span><span class="sxs-lookup"><span data-stu-id="59f9f-209">This still works correctly in a `if` statement.</span></span> <span data-ttu-id="59f9f-210">Wenn Ihr Operator einen Wert zurückgibt, gilt die gesamte Anweisung als `$true`.</span><span class="sxs-lookup"><span data-stu-id="59f9f-210">So a value is returned by your operator, then the whole statement is `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

<span data-ttu-id="59f9f-211">Allerdings muss in diesem Zusammenhang ein wichtiger Aspekt berücksichtigt werden. Wenn Sie den Operator `-ne` auf diese Weise verwenden, wird die Logik umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-211">There's one small trap hiding in the details here that I need to point out. When using the `-ne` operator this way, it's easy to mistakenly look at the logic backwards.</span></span> <span data-ttu-id="59f9f-212">Denn bei Verwendung von `-ne` mit einer Auflistung wird `$true` zurückgegeben, wenn ein Element innerhalb der Auflistung nicht Ihrem Wert entspricht.</span><span class="sxs-lookup"><span data-stu-id="59f9f-212">Using `-ne` with a collection returns `$true` if any item in the collection doesn't match your value.</span></span>

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

<span data-ttu-id="59f9f-213">In einem solchen Szenario sollten Sie stattdessen mit den Operatoren `-contains` und `-in` arbeiten.</span><span class="sxs-lookup"><span data-stu-id="59f9f-213">This may look like a clever trick, but we have operators `-contains` and `-in` that handle this more efficiently.</span></span> <span data-ttu-id="59f9f-214">Mit dem Operator `-notcontains` wird das erwartete Verhalten erzielt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-214">And `-notcontains` does what you expect.</span></span>

### <a name="-contains"></a><span data-ttu-id="59f9f-215">-contains</span><span class="sxs-lookup"><span data-stu-id="59f9f-215">-contains</span></span>

<span data-ttu-id="59f9f-216">Der Operator `-contains` überprüft, ob Ihr Wert in der Auflistung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="59f9f-216">The `-contains` operator checks the collection for your value.</span></span> <span data-ttu-id="59f9f-217">Sobald eine Übereinstimmung ermittelt wird, gibt der Operator `$true` zurück.</span><span class="sxs-lookup"><span data-stu-id="59f9f-217">As soon as it finds a match, it returns `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

<span data-ttu-id="59f9f-218">Dies ist die bevorzugte Vorgehensweise, um zu überprüfen, ob eine Auflistung Ihren Wert enthält.</span><span class="sxs-lookup"><span data-stu-id="59f9f-218">This is the preferred way to see if a collection contains your value.</span></span> <span data-ttu-id="59f9f-219">Bei Verwendung von `Where-Object` (oder `-eq`) wird bei jedem Durchlauf die gesamte Liste geprüft, sodass der Vorgang deutlich langsamer ist.</span><span class="sxs-lookup"><span data-stu-id="59f9f-219">Using `Where-Object` (or `-eq`) walks the entire list every time and is significantly slower.</span></span>

<span data-ttu-id="59f9f-220">**Variationen:**</span><span class="sxs-lookup"><span data-stu-id="59f9f-220">**Variations:**</span></span>

- <span data-ttu-id="59f9f-221">`-contains` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-221">`-contains` case-insensitive match</span></span>
- <span data-ttu-id="59f9f-222">`-icontains` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-222">`-icontains` case-insensitive match</span></span>
- <span data-ttu-id="59f9f-223">`-ccontains` Übereinstimmung mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-223">`-ccontains` case-sensitive match</span></span>
- <span data-ttu-id="59f9f-224">`-notcontains` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-224">`-notcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="59f9f-225">`-inotcontains` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-225">`-inotcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="59f9f-226">`-cnotcontains` Keine Übereinstimmung mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-226">`-cnotcontains` case-sensitive not matched</span></span>

### <a name="-in"></a><span data-ttu-id="59f9f-227">-in</span><span class="sxs-lookup"><span data-stu-id="59f9f-227">-in</span></span>

<span data-ttu-id="59f9f-228">Der Operator `-in` ist mit dem Operator `-contains` vergleichbar, in diesem Fall steht die Auflistung jedoch rechts.</span><span class="sxs-lookup"><span data-stu-id="59f9f-228">The `-in` operator is just like the `-contains` operator except the collection is on the right-hand side.</span></span>

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

<span data-ttu-id="59f9f-229">**Variationen:**</span><span class="sxs-lookup"><span data-stu-id="59f9f-229">**Variations:**</span></span>

- <span data-ttu-id="59f9f-230">`-in` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-230">`-in` case-insensitive match</span></span>
- <span data-ttu-id="59f9f-231">`-iin` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-231">`-iin` case-insensitive match</span></span>
- <span data-ttu-id="59f9f-232">`-cin` Übereinstimmung mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-232">`-cin` case-sensitive match</span></span>
- <span data-ttu-id="59f9f-233">`-notin` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-233">`-notin` case-insensitive not matched</span></span>
- <span data-ttu-id="59f9f-234">`-inotin` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-234">`-inotin` case-insensitive not matched</span></span>
- <span data-ttu-id="59f9f-235">`-cnotin` Keine Übereinstimmung mit Beachtung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="59f9f-235">`-cnotin` case-sensitive not matched</span></span>

## <a name="logical-operators"></a><span data-ttu-id="59f9f-236">Logische Operatoren</span><span class="sxs-lookup"><span data-stu-id="59f9f-236">Logical operators</span></span>

<span data-ttu-id="59f9f-237">Logische Operatoren werden verwendet, um andere Ausdrücke umzukehren oder zu kombinieren.</span><span class="sxs-lookup"><span data-stu-id="59f9f-237">Logical operators are used to invert or combine other expressions.</span></span>

### <a name="-not"></a><span data-ttu-id="59f9f-238">-not</span><span class="sxs-lookup"><span data-stu-id="59f9f-238">-not</span></span>

<span data-ttu-id="59f9f-239">Mit dem Operator `-not` wird ein Ausdruck von `$false` in `$true` oder von `$true` in `$false` umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-239">The `-not` operator flips an expression from `$false` to `$true` or from `$true` to `$false`.</span></span> <span data-ttu-id="59f9f-240">Im folgenden Beispiel soll eine Aktion ausgeführt werden, wenn für `Test-Path` das Ergebnis `$false` ermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-240">Here is an example where we want to perform an action when `Test-Path` is `$false`.</span></span>

```powershell
if ( -not ( Test-Path -Path $path ) )
```

<span data-ttu-id="59f9f-241">Für die meisten bisher beschriebenen Operatoren gibt es eine Variation, bei der der Operator `-not` nicht verwendet werden muss.</span><span class="sxs-lookup"><span data-stu-id="59f9f-241">Most of the operators we talked about do have a variation where you do not need to use the `-not` operator.</span></span> <span data-ttu-id="59f9f-242">In einigen Situationen ist er jedoch nützlich.</span><span class="sxs-lookup"><span data-stu-id="59f9f-242">But there are still times it is useful.</span></span>

### <a name="-operator"></a><span data-ttu-id="59f9f-243">!</span><span class="sxs-lookup"><span data-stu-id="59f9f-243">!</span></span> <span data-ttu-id="59f9f-244">Operator</span><span class="sxs-lookup"><span data-stu-id="59f9f-244">operator</span></span>

<span data-ttu-id="59f9f-245">Sie können `!` als Alias für `-not` verwenden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-245">You can use `!` as an alias for `-not`.</span></span>

```powershell
if ( -not $value ){}
if ( !$value ){}
```

<span data-ttu-id="59f9f-246">`!` wird häufig von Programmierern verwendet, die üblicherweise mit anderen Sprachen wie C# arbeiten.</span><span class="sxs-lookup"><span data-stu-id="59f9f-246">You may see `!` used more by people that come from another languages like C#.</span></span> <span data-ttu-id="59f9f-247">Ich bevorzuge eine ausgeschriebene Variante, weil ich diesen Operator in meinen Skripts nicht gut erkenne.</span><span class="sxs-lookup"><span data-stu-id="59f9f-247">I prefer to type it out because I find it hard to see when quickly looking at my scripts.</span></span>

### <a name="-and"></a><span data-ttu-id="59f9f-248">-and</span><span class="sxs-lookup"><span data-stu-id="59f9f-248">-and</span></span>

<span data-ttu-id="59f9f-249">Mit dem Operator `-and` lassen sich Ausdrücke kombinieren.</span><span class="sxs-lookup"><span data-stu-id="59f9f-249">You can combine expressions with the `-and` operator.</span></span> <span data-ttu-id="59f9f-250">In diesem Fall muss für beide Ausdrücke `$true` zurückgegeben werden, damit der gesamte Ausdruck als `$true` betrachtet wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-250">When you do that, both sides need to be `$true` for the whole expression to be `$true`.</span></span>

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

<span data-ttu-id="59f9f-251">In diesem Beispiel muss `$age` auf der linken Seite 13 oder größer sein, auf der rechten Seite weniger als 55.</span><span class="sxs-lookup"><span data-stu-id="59f9f-251">In that example, `$age` must be 13 or older for the left side and less than 55 for the right side.</span></span> <span data-ttu-id="59f9f-252">Ich habe zusätzliche Klammern hinzugefügt, um das Beispiel übersichtlicher zu gestalten. Diese Klammern sind bei einfachen Ausdrücken jedoch optional.</span><span class="sxs-lookup"><span data-stu-id="59f9f-252">I added extra parentheses to make it clearer in that example but they're optional as long as the expression is simple.</span></span> <span data-ttu-id="59f9f-253">Nachfolgend sehen Sie ein Beispiel ohne diese Klammern.</span><span class="sxs-lookup"><span data-stu-id="59f9f-253">Here is the same example without them.</span></span>

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

<span data-ttu-id="59f9f-254">Die Auswertung wird von links nach rechts durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-254">Evaluation happens from left to right.</span></span> <span data-ttu-id="59f9f-255">Wenn das Ergebnis für das erste Element `$false` lautet, wird der Vorgang frühzeitig beendet, und der Vergleich auf der rechten Seite wird nicht mehr durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-255">If the first item evaluates to `$false`, it exits early and doesn't perform the right comparison.</span></span> <span data-ttu-id="59f9f-256">Dies ist nützlich, um sicherzustellen, dass ein Wert vorhanden ist, bevor Sie ihn verwenden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-256">This is handy when you need to make sure a value exists before you use it.</span></span> <span data-ttu-id="59f9f-257">Für `Test-Path` wird z. B. ein Fehler zurückgegeben, wenn ein `$null`-Pfad angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-257">For example, `Test-Path` throws an error if you give it a `$null` path.</span></span>

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a><span data-ttu-id="59f9f-258">-or</span><span class="sxs-lookup"><span data-stu-id="59f9f-258">-or</span></span>

<span data-ttu-id="59f9f-259">Mit dem Operator `-or` können Sie zwei Ausdrücke angeben. Wenn das Ergebnis für einen dieser Ausdrücke `$true` lautet, wird `$true` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-259">The `-or` allows for you to specify two expressions and returns `$true` if either one of them is `$true`.</span></span>

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

<span data-ttu-id="59f9f-260">Wie beim `-and`-Operator erfolgt die Auswertung von links nach rechts.</span><span class="sxs-lookup"><span data-stu-id="59f9f-260">Just like with the `-and` operator, the evaluation happens from left to right.</span></span> <span data-ttu-id="59f9f-261">Wenn das Ergebnis des ersten Teils bereits `$true` lautet, wird die gesamte Anweisung als `$true` betrachtet, und der verbleibende Teil der Anweisung wird nicht mehr verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-261">Except that if the first part is `$true`, then the whole statement is `$true` and it doesn't process the rest of the expression.</span></span>

<span data-ttu-id="59f9f-262">Beachten Sie außerdem, wie die Syntax für diese Operatoren funktioniert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-262">Also make note of how the syntax works for these operators.</span></span> <span data-ttu-id="59f9f-263">Sie benötigen zwei separate Ausdrücke.</span><span class="sxs-lookup"><span data-stu-id="59f9f-263">You need two separate expressions.</span></span> <span data-ttu-id="59f9f-264">Mitunter versuchen Benutzer, einen Ausdruck wie `$value -eq 5 -or 6` anzugeben, der nicht korrekt ist.</span><span class="sxs-lookup"><span data-stu-id="59f9f-264">I have seen users try to do something like this `$value -eq 5 -or 6` without realizing their mistake.</span></span>

### <a name="-xor-exclusive-or"></a><span data-ttu-id="59f9f-265">Exklusives OR (-xor)</span><span class="sxs-lookup"><span data-stu-id="59f9f-265">-xor exclusive or</span></span>

<span data-ttu-id="59f9f-266">Dieser Operator ist etwas ungewöhnlich.</span><span class="sxs-lookup"><span data-stu-id="59f9f-266">This one is a little unusual.</span></span> <span data-ttu-id="59f9f-267">Bei `-xor` darf nur für einen Ausdruck das Ergebnis `$true` ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-267">`-xor` allows only one expression to evaluate to `$true`.</span></span> <span data-ttu-id="59f9f-268">Wenn für beide Elemente `$false` oder `$true` zurückgegeben wird, wird der gesamte Ausdruck als `$false` betrachtet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-268">So if both items are `$false` or both items are `$true`, then the whole expression is `$false`.</span></span> <span data-ttu-id="59f9f-269">Der Ausdruck gilt also nur dann als `$true`, wenn unterschiedliche Ergebnisse für die enthaltenen Elemente zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-269">Another way to look at this is the expression is only `$true` when the results of the expression are different.</span></span>

<span data-ttu-id="59f9f-270">Die Anwendungsfälle für diesen logischen Operator sind eher eingeschränkt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-270">It's rare that anyone would ever use this logical operator and I can't think up a good example as to why I would ever use it.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="59f9f-271">Bitweise Operatoren</span><span class="sxs-lookup"><span data-stu-id="59f9f-271">Bitwise operators</span></span>

<span data-ttu-id="59f9f-272">Mit bitweisen Operatoren werden Berechnungen für die Bits innerhalb der Werte durchgeführt, um als Ergebnis einen neuen Wert zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="59f9f-272">Bitwise operators perform calculations on the bits within the values and produce a new value as the result.</span></span> <span data-ttu-id="59f9f-273">Eine detaillierte Beschreibung von [Bitweise Operatoren][] geht über den Umfang dieses Artikels hinaus. Nachfolgend finden Sie jedoch eine Liste dieser Operatoren.</span><span class="sxs-lookup"><span data-stu-id="59f9f-273">Teaching [bitwise operators][] is beyond the scope of this article, but here is the list the them.</span></span>

- <span data-ttu-id="59f9f-274">`-band` binäres AND</span><span class="sxs-lookup"><span data-stu-id="59f9f-274">`-band` binary AND</span></span>
- <span data-ttu-id="59f9f-275">`-bor` binäres OR</span><span class="sxs-lookup"><span data-stu-id="59f9f-275">`-bor` binary OR</span></span>
- <span data-ttu-id="59f9f-276">`-bxor` binäres exklusives OR</span><span class="sxs-lookup"><span data-stu-id="59f9f-276">`-bxor` binary exclusive OR</span></span>
- <span data-ttu-id="59f9f-277">`-bnot` binäres NOT</span><span class="sxs-lookup"><span data-stu-id="59f9f-277">`-bnot` binary NOT</span></span>
- <span data-ttu-id="59f9f-278">`-shl` nach links verschieben</span><span class="sxs-lookup"><span data-stu-id="59f9f-278">`-shl` shift left</span></span>
- <span data-ttu-id="59f9f-279">`-shr` nach rechts verschieben</span><span class="sxs-lookup"><span data-stu-id="59f9f-279">`-shr` shift right</span></span>

## <a name="powershell-expressions"></a><span data-ttu-id="59f9f-280">PowerShell-Ausdrücke</span><span class="sxs-lookup"><span data-stu-id="59f9f-280">PowerShell expressions</span></span>

<span data-ttu-id="59f9f-281">Innerhalb einer Bedingungsanweisung können die normalen PowerShell-Ausdrücke verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-281">We can use normal PowerShell inside the condition statement.</span></span>

```powershell
if ( Test-Path -Path $Path )
```

<span data-ttu-id="59f9f-282">`Test-Path` gibt bei der Ausführung `$true` oder `$false` zurück.</span><span class="sxs-lookup"><span data-stu-id="59f9f-282">`Test-Path` returns `$true` or `$false` when it executes.</span></span> <span data-ttu-id="59f9f-283">Dies gilt ebenso für Befehle, die andere Werte zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-283">This also applies to commands that return other values.</span></span>

```powershell
if ( Get-Process Notepad* )
```

<span data-ttu-id="59f9f-284">Wenn ein Prozess zurückgegeben wird, lautet das Ergebnis `$true`, anderenfalls wird `$false` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-284">It evaluates to `$true` if there's a returned process and `$false` if there'sn'thing.</span></span> <span data-ttu-id="59f9f-285">Auf diese Weise können Pipelineausdrücke oder andere PowerShell-Anweisungen verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="59f9f-285">It's perfectly valid to use pipeline expressions or other PowerShell statements like this:</span></span>

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

<span data-ttu-id="59f9f-286">Diese Ausdrücke lassen sich mit den Operatoren `-and` und `-or` kombinieren. Gegebenenfalls müssen jedoch Klammern verwendet werden, um sie in Teilausdrücke zu untergliedern.</span><span class="sxs-lookup"><span data-stu-id="59f9f-286">These expressions can be combined with each other with the `-and` and `-or` operators, but you may have to use parenthesis to break them into subexpressions.</span></span>

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a><span data-ttu-id="59f9f-287">Überprüfung auf $null</span><span class="sxs-lookup"><span data-stu-id="59f9f-287">Checking for $null</span></span>

<span data-ttu-id="59f9f-288">Wenn kein Ergebnis oder der Wert `$null` zurückgegeben wird, wird dies in der `if`-Anweisung als `$false` betrachtet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-288">Having a no result or a `$null` value evaluates to `$false` in the `if` statement.</span></span> <span data-ttu-id="59f9f-289">Wenn eine dedizierte Überprüfung auf `$null` durchgeführt wird, sollte `$null` auf der linken Seite platziert werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-289">When checking specifically for `$null`, it's a best practice to place the `$null` on the left-hand side.</span></span>

```powershell
if ( $null -eq $value )
```

<span data-ttu-id="59f9f-290">Beim Umgang mit `$null`-Werten in PowerShell müssen einige wichtige Aspekte berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-290">There are quite a few nuances when dealing with `$null` values in PowerShell.</span></span> <span data-ttu-id="59f9f-291">Einzelheiten finden Sie im Artikel [Alles, was Sie schon immer über $null wissen wollten][].</span><span class="sxs-lookup"><span data-stu-id="59f9f-291">If you're interested in diving deeper, I have an article about [everything you wanted to know about $null][].</span></span>

### <a name="variable-assignment"></a><span data-ttu-id="59f9f-292">Variablenzuweisung</span><span class="sxs-lookup"><span data-stu-id="59f9f-292">Variable assignment</span></span>

<span data-ttu-id="59f9f-293">Beinahe hätte ich vergessen, auf diesen Aspekt einzugehen, doch glücklicherweise hat mich [Prasoon Karunan V][] darauf hingewiesen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-293">I almost forgot to add this one until [Prasoon Karunan V][] reminded me of it.</span></span>

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

<span data-ttu-id="59f9f-294">Wenn Sie einer Variablen einen Wert zuweisen, wird der Wert üblicherweise nicht an die Pipeline oder Konsole übergeben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-294">Normally when you assign a value to a variable, the value isn't passed onto the pipeline or console.</span></span> <span data-ttu-id="59f9f-295">Bei der Variablenzuweisung in einem Teilausdruck wird der Wert jedoch an die Pipeline übergeben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-295">When you do a variable assignment in a sub expression, it does get passed on to the pipeline.</span></span>

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

<span data-ttu-id="59f9f-296">Wie Sie sehen, verfügt die `$first`-Zuweisung über keine Ausgabe, die `$second`-Zuweisung jedoch schon.</span><span class="sxs-lookup"><span data-stu-id="59f9f-296">See how the `$first` assignment has no output and the `$second` assignment does?</span></span> <span data-ttu-id="59f9f-297">Bei einer Zuweisung in einer `if`-Anweisung wird diese wie die `$second`-Zuweisung oben ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-297">When an assignment is done in an `if` statement, it executes just like the `$second` assignment above.</span></span> <span data-ttu-id="59f9f-298">Nachfolgend finden Sie ein einfaches Beispiel für die Verwendung:</span><span class="sxs-lookup"><span data-stu-id="59f9f-298">Here is a clean example on how you could use it:</span></span>

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

<span data-ttu-id="59f9f-299">Wenn `$process` ein Wert zugewiesen wird, lautet das Ergebnis `$true`, und `$process` wird beendet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-299">If `$process` gets assigned a value, then the statement is `$true` and `$process` gets stopped.</span></span>

<span data-ttu-id="59f9f-300">Dies ist jedoch keine Gleichheitsüberprüfung und sollte nicht mit `-eq` verwechselt werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-300">Make sure you don't confuse this with `-eq` because this isn't an equality check.</span></span> <span data-ttu-id="59f9f-301">Dieses Feature ist weniger offensichtlich und die meisten Benutzer wissen nicht, dass es auf diese Weise funktioniert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-301">This is a more obscure feature that most people don't realize works this way.</span></span>

## <a name="alternate-execution-path"></a><span data-ttu-id="59f9f-302">Alternativer Ausführungspfad</span><span class="sxs-lookup"><span data-stu-id="59f9f-302">Alternate execution path</span></span>

<span data-ttu-id="59f9f-303">Bei der `if`-Anweisung kann nicht nur eine Aktion für den Fall angegeben werden, dass das Ergebnis `$true` ist, sondern auch für den Fall, dass das Ergebnis `$false` ist.</span><span class="sxs-lookup"><span data-stu-id="59f9f-303">The `if` statement allows you to specify an action for not only when the statement is `$true`, but also for when it's `$false`.</span></span> <span data-ttu-id="59f9f-304">Dazu wird die `else`-Anweisung verwendet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-304">This is where the `else` statement comes into play.</span></span>

### <a name="else"></a><span data-ttu-id="59f9f-305">else</span><span class="sxs-lookup"><span data-stu-id="59f9f-305">else</span></span>

<span data-ttu-id="59f9f-306">Wenn die `else`-Anweisung verwendet wird, ist sie immer der letzte Teil der `if`-Anweisung.</span><span class="sxs-lookup"><span data-stu-id="59f9f-306">The `else` statement is always the last part of the `if` statement when used.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

<span data-ttu-id="59f9f-307">In diesem Beispiel wird `$path` überprüft, um sicherzustellen, dass es sich um eine Datei handelt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-307">In this example, we check the `$path` to make sure it's a file.</span></span> <span data-ttu-id="59f9f-308">Wenn die Datei gefunden wird, wird sie verschoben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-308">If we find the file, we move it.</span></span> <span data-ttu-id="59f9f-309">Anderenfalls wird eine Warnung geschrieben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-309">If not, we write a warning.</span></span> <span data-ttu-id="59f9f-310">Diese Art von Verzweigungslogik wird sehr häufig verwendet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-310">This type of branching logic is very common.</span></span>

### <a name="nested-if"></a><span data-ttu-id="59f9f-311">Geschachtelte IF-Anweisung</span><span class="sxs-lookup"><span data-stu-id="59f9f-311">Nested if</span></span>

<span data-ttu-id="59f9f-312">Da die Anweisungen `if` und `else` in einem Skriptblock verwendet werden, kann ein beliebiger PowerShell-Befehl innerhalb dieser Anweisungen platziert werden (einschließlich einer weiteren `if`-Anweisung).</span><span class="sxs-lookup"><span data-stu-id="59f9f-312">The `if` and `else` statements take a script block, so we can place any PowerShell command inside them, including another `if` statement.</span></span> <span data-ttu-id="59f9f-313">Dadurch können Sie eine deutlich komplexere Logik verwenden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-313">This allows you to make use of much more complicated logic.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

<span data-ttu-id="59f9f-314">In diesem Beispiel testen wir zunächst den Pfad und führen anschließend eine Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="59f9f-314">In this example, we test the happy path first and then take action on it.</span></span> <span data-ttu-id="59f9f-315">Wenn dabei ein Fehler auftritt, wird eine weitere Überprüfung durchgeführt, und der Benutzer erhält nähere Informationen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-315">If that fails, we do another check and to provide more detailed information to the user.</span></span>

### <a name="elseif"></a><span data-ttu-id="59f9f-316">Die elseif-Anweisung</span><span class="sxs-lookup"><span data-stu-id="59f9f-316">elseif</span></span>

<span data-ttu-id="59f9f-317">Wir können nicht nur eine einzelne bedingte Überprüfung durchführen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-317">We aren't limited to just a single conditional check.</span></span> <span data-ttu-id="59f9f-318">Anstatt sie mit der `elseif`-Anweisung zu verschachteln, können wir sie auch mit `if`- und `else`-Anweisungen miteinander verketten.</span><span class="sxs-lookup"><span data-stu-id="59f9f-318">We can chain `if` and `else` statements together instead of nesting them by using the `elseif` statement.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

<span data-ttu-id="59f9f-319">Die Ausführung erfolgt von oben nach unten.</span><span class="sxs-lookup"><span data-stu-id="59f9f-319">The execution happens from the top to the bottom.</span></span> <span data-ttu-id="59f9f-320">Die oberste `if`-Anweisung wird zuerst ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-320">The top `if` statement is evaluated first.</span></span> <span data-ttu-id="59f9f-321">Wenn das Ergebnis `$false` lautet, wird mit der nächsten `elseif`- oder `else`-Anweisung in der Liste fortgefahren.</span><span class="sxs-lookup"><span data-stu-id="59f9f-321">If that is `$false`, then it moves down to the next `elseif` or `else` in the list.</span></span> <span data-ttu-id="59f9f-322">Die letzte `else`-Anweisung ist die Standardaktion, die ausgeführt wird, wenn bei keiner anderen Anweisung `$true` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-322">That last `else` is the default action to take if none of the others return `$true`.</span></span>

### <a name="switch"></a><span data-ttu-id="59f9f-323">switch</span><span class="sxs-lookup"><span data-stu-id="59f9f-323">switch</span></span>

<span data-ttu-id="59f9f-324">An dieser Stelle möchte ich auf die `switch`-Anweisung eingehen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-324">At this point, I need to mention the `switch` statement.</span></span> <span data-ttu-id="59f9f-325">Sie bietet eine alternative Syntax zum Durchführen mehrerer Vergleiche mit einem Wert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-325">It provides an alternate syntax for doing multiple comparisons with a value.</span></span> <span data-ttu-id="59f9f-326">Bei `switch` geben Sie einen Ausdruck an, dessen Ergebnis dann mit einer Reihe unterschiedlicher Werte verglichen wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-326">With the `switch`, you specify an expression and that result gets compared with several different values.</span></span> <span data-ttu-id="59f9f-327">Wenn für einen dieser Werte eine Übereinstimmung ermittelt wird, wird der entsprechende Codeblock ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-327">If one of those values match, the matching code block is executed.</span></span> <span data-ttu-id="59f9f-328">Im Folgenden finden Sie ein Beispiel:</span><span class="sxs-lookup"><span data-stu-id="59f9f-328">Take a look at this example:</span></span>

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

<span data-ttu-id="59f9f-329">Es gibt drei mögliche Werte, die `$itemType` entsprechen können.</span><span class="sxs-lookup"><span data-stu-id="59f9f-329">There three possible values that can match the `$itemType`.</span></span> <span data-ttu-id="59f9f-330">In diesem Fall wird die Übereinstimmung für `Role` erkannt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-330">In this case, it matches with `Role`.</span></span> <span data-ttu-id="59f9f-331">Dieses einfache Beispiel zeigt, wie der `switch`-Operator verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-331">I used a simple example just to give you some exposure to the `switch` operator.</span></span> <span data-ttu-id="59f9f-332">Weitere Informationen zu diesem Operator finden Sie unter [Alles, was Sie schon immer über die Switch-Anweisung wissen wollten][].</span><span class="sxs-lookup"><span data-stu-id="59f9f-332">I talk more about [everything you ever wanted to know about the switch statement][] in another article.</span></span>

## <a name="pipeline"></a><span data-ttu-id="59f9f-333">Pipeline</span><span class="sxs-lookup"><span data-stu-id="59f9f-333">Pipeline</span></span>

<span data-ttu-id="59f9f-334">Die Pipeline ist ein einzigartiges und wichtiges PowerShell-Feature.</span><span class="sxs-lookup"><span data-stu-id="59f9f-334">The pipeline is a unique and important feature of PowerShell.</span></span> <span data-ttu-id="59f9f-335">Alle Werte, die nicht unterdrückt oder einer Variablen zugewiesen werden, werden in der Pipeline platziert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-335">Any value that isn't suppressed or assigned to a variable gets placed in the pipeline.</span></span> <span data-ttu-id="59f9f-336">Mit der `if`-Anweisung lässt sich die Pipeline auf eine Art und Weise nutzen, die nicht unbedingt offensichtlich ist.</span><span class="sxs-lookup"><span data-stu-id="59f9f-336">The `if` provides us a way to take advantage of the pipeline in a way that isn't always obvious.</span></span>

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

<span data-ttu-id="59f9f-337">Jeder Skriptblock platziert die Ergebnisse der Befehle oder den Wert in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="59f9f-337">Each script block is placing the results the commands or the value into the pipeline.</span></span> <span data-ttu-id="59f9f-338">Anschließend wird das Ergebnis der IF-Anweisung der `$discount`-Variablen zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-338">Then we assign the result of the if statement to the `$discount` variable.</span></span> <span data-ttu-id="59f9f-339">In diesem Beispiel hätten diese Werte genauso einfach direkt der `$discount`-Variablen in jedem Skriptblock zugewiesen werden können.</span><span class="sxs-lookup"><span data-stu-id="59f9f-339">That example could have just as easily assigned those values to the `$discount` variable directly in each scriptblock.</span></span> <span data-ttu-id="59f9f-340">Ich verwende in einem solchen Szenario nicht sehr häufig die `if`-Anweisung, in letzter Zeit ist es jedoch zu einem solchen Fall gekommen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-340">I can't say that I use this with the `if` statement often, but I do have an example where I used this recently.</span></span>

### <a name="array-inline"></a><span data-ttu-id="59f9f-341">Inlinearray</span><span class="sxs-lookup"><span data-stu-id="59f9f-341">Array inline</span></span>

<span data-ttu-id="59f9f-342">Ich verfüge über eine Funktion [Invoke-SnowSql][], durch die eine ausführbare Datei mit einer Reihe von Befehlszeilenargumenten gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-342">I have a function called [Invoke-SnowSql][] that launches an executable with several command-line arguments.</span></span> <span data-ttu-id="59f9f-343">Nachfolgend ist ein Ausschnitt dieser Funktion gezeigt, in dem das Array aus Argumenten erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="59f9f-343">Here is a clip from that function where I build the array of arguments.</span></span>

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

<span data-ttu-id="59f9f-344">Die Variablen `$Debug` und `$Path` sind Parameter der Funktion, die vom Endbenutzer angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-344">The `$Debug` and `$Path` variables are parameters on the function that are provided by the end user.</span></span>
<span data-ttu-id="59f9f-345">Sie werden inline innerhalb der Initialisierung meines Arrays ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-345">I evaluate them inline inside the initialization of my array.</span></span> <span data-ttu-id="59f9f-346">Wenn `$Debug` wahr ist, werden diese Werte an der richtigen Stelle in `$snowSqlParam` platziert.</span><span class="sxs-lookup"><span data-stu-id="59f9f-346">If `$Debug` is true, then those values fall into the `$snowSqlParam` in the correct place.</span></span> <span data-ttu-id="59f9f-347">Dasselbe gilt für die Variable `$Path`.</span><span class="sxs-lookup"><span data-stu-id="59f9f-347">Same holds true for the `$Path` variable.</span></span>

## <a name="simplify-complex-operations"></a><span data-ttu-id="59f9f-348">Vereinfachen von komplexen Vorgängen</span><span class="sxs-lookup"><span data-stu-id="59f9f-348">Simplify complex operations</span></span>

<span data-ttu-id="59f9f-349">Situationen mit einer deutlich zu großen Anzahl von Vergleichen, in denen Ihre IF-Anweisung viel zu weit in den rechten Bildschirmbereich hineinreicht, lassen sich nicht vermeiden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-349">It's inevitable that you run into a situation that has way too many comparisons to check and your if statement scrolls way off the right side of the screen.</span></span>

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

<span data-ttu-id="59f9f-350">Ihre Arbeit wird dadurch möglicherweise unübersichtlich, und es kann leicht zu Fehlern kommen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-350">They can be hard to read and that make you more prone to make mistakes.</span></span> <span data-ttu-id="59f9f-351">Doch es gibt einige Tricks, die in diesen Situationen weiterhelfen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-351">There are a few things we can do about that.</span></span>

### <a name="line-continuation"></a><span data-ttu-id="59f9f-352">Zeilenfortsetzung</span><span class="sxs-lookup"><span data-stu-id="59f9f-352">Line continuation</span></span>

<span data-ttu-id="59f9f-353">PowerShell verfügt über einige Operatoren, mit denen Sie Befehlszeilen umbrechen können.</span><span class="sxs-lookup"><span data-stu-id="59f9f-353">There some operators in PowerShell that let you wrap you command to the next line.</span></span> <span data-ttu-id="59f9f-354">Mit den logischen Operatoren `-and` und `-or` können Sie einen Ausdruck umbrechen und in mehreren Zeilen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-354">The logical operators `-and` and `-or` are good operators to use if you want to break your expression into multiple lines.</span></span>

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

<span data-ttu-id="59f9f-355">Der Ausdruck ist immer noch sehr lang, durch den Umbruch wird er jedoch deutlich übersichtlicher.</span><span class="sxs-lookup"><span data-stu-id="59f9f-355">There's still a lot going on there, but placing each piece on its own line makes a big difference.</span></span>
<span data-ttu-id="59f9f-356">Ich greife üblicherweise auf diese Vorgehensweise zurück, wenn ich mehr als zwei Vergleiche durchführe oder zum rechten Bildschirmrand scrollen muss, um meine Logik zu sehen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-356">I generally use this when I get more than two comparisons or if I have to scroll to the right to read any of the logic.</span></span>

### <a name="pre-calculating-results"></a><span data-ttu-id="59f9f-357">Vorabberechnung von Ergebnissen</span><span class="sxs-lookup"><span data-stu-id="59f9f-357">Pre-calculating results</span></span>

<span data-ttu-id="59f9f-358">Diese Anweisung lässt sich außerhalb der IF-Anweisung platzieren, um nur das Ergebnis zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-358">We can take that statement out of the if statement and only check the result.</span></span>

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

<span data-ttu-id="59f9f-359">Dadurch wird die Darstellung wesentlich übersichtlicher als im vorherigen Beispiel.</span><span class="sxs-lookup"><span data-stu-id="59f9f-359">This just feels much cleaner than the previous example.</span></span> <span data-ttu-id="59f9f-360">Darüber hinaus können Sie einen Variablennamen verwenden, der Aufschluss darüber gibt, was Sie überprüfen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-360">You also are given an opportunity to use a variable name that explains what it's that you're really checking.</span></span> <span data-ttu-id="59f9f-361">Dies ist zudem ein Beispiel für selbstdokumentierenden Code, der Kommentare überflüssig machen kann.</span><span class="sxs-lookup"><span data-stu-id="59f9f-361">This is also and example of self-documenting code that saves unnecessary comments.</span></span>

### <a name="multiple-if-statements"></a><span data-ttu-id="59f9f-362">Mehrere IF-Anweisungen</span><span class="sxs-lookup"><span data-stu-id="59f9f-362">Multiple if statements</span></span>

<span data-ttu-id="59f9f-363">Dieser Code lässt sich in mehrere Anweisungen unterteilen, die jeweils einzeln überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-363">We can break this up into multiple statements and check them one at a time.</span></span> <span data-ttu-id="59f9f-364">In diesem Fall werden die Ergebnisse mithilfe eines Flags oder einer Nachverfolgungsvariable zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="59f9f-364">In this case, we use a flag or a tracking variable to combine the results.</span></span>

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

<span data-ttu-id="59f9f-365">Für eine ordnungsgemäße Funktionsweise der Flaglogik musste die Logik in diesem Beispiel umgekehrt werden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-365">I did have to invert the logic to make the flag logic work correctly.</span></span> <span data-ttu-id="59f9f-366">Jede Auswertung wird als einzelne `if`-Anweisung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-366">Each evaluation is an individual `if` statement.</span></span> <span data-ttu-id="59f9f-367">Der Vorteil dieser Vorgehensweise ist, dass Sie beim Debuggen genau erkennen, welche Schritte die Logik ausführt.</span><span class="sxs-lookup"><span data-stu-id="59f9f-367">The advantage of this is that when you're debugging, you can tell exactly what the logic is doing.</span></span> <span data-ttu-id="59f9f-368">Außerdem ist der Code deutlich ausführlicher geworden.</span><span class="sxs-lookup"><span data-stu-id="59f9f-368">I was able to add much better verbosity at the same time.</span></span>

<span data-ttu-id="59f9f-369">Der offensichtliche Nachteil ist, dass viel mehr Code geschrieben werden muss.</span><span class="sxs-lookup"><span data-stu-id="59f9f-369">The obvious downside is that it's so much more code to write.</span></span> <span data-ttu-id="59f9f-370">Außerdem erscheint der Code komplexer, da aus einer einzelnen Logikzeile 25 oder mehr Zeilen entstehen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-370">The code is more complex to look at as it takes a single line of logic and explodes it into 25 or more lines.</span></span>

### <a name="using-functions"></a><span data-ttu-id="59f9f-371">Verwenden von Funktionen</span><span class="sxs-lookup"><span data-stu-id="59f9f-371">Using functions</span></span>

<span data-ttu-id="59f9f-372">Die gesamte Validierungslogik lässt sich auch in eine Funktion verschieben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-372">We can also move all that validation logic into a function.</span></span> <span data-ttu-id="59f9f-373">Wie Sie unten sehen, wird der Code dadurch sehr übersichtlich.</span><span class="sxs-lookup"><span data-stu-id="59f9f-373">Look at how clean this looks at a glance.</span></span>

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

<span data-ttu-id="59f9f-374">Sie müssen zwar die Funktion für die Validierung erstellen, anschließend können Sie jedoch deutlich einfacher mit dem Code arbeiten.</span><span class="sxs-lookup"><span data-stu-id="59f9f-374">You still have to create the function to do the validation, but it makes this code much easier to work with.</span></span> <span data-ttu-id="59f9f-375">Außerdem lässt sich dieser Code leichter testen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-375">It makes this code easier to test.</span></span> <span data-ttu-id="59f9f-376">In Ihren Tests können Sie einen Aufruf von `Test-ADDriveConfiguration` simulieren, und Sie benötigen nur zwei Tests für diese Funktion.</span><span class="sxs-lookup"><span data-stu-id="59f9f-376">In your tests, you can mock the call to `Test-ADDriveConfiguration` and you only need two tests for this function.</span></span> <span data-ttu-id="59f9f-377">In einem Test wird `$true` und im anderen `$false` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="59f9f-377">One where it returns `$true` and one where it returns `$false`.</span></span> <span data-ttu-id="59f9f-378">Aufgrund des geringen Umfangs ist das Testen der anderen Funktion einfacher.</span><span class="sxs-lookup"><span data-stu-id="59f9f-378">Testing the other function is simpler because it's so small.</span></span>

<span data-ttu-id="59f9f-379">Diese Funktion könnte die einzelne Zeile umfassen, mit der wir begonnen haben. Aber auch die umfassende Logik des letzten Abschnitts ist möglich.</span><span class="sxs-lookup"><span data-stu-id="59f9f-379">The body of that function could still be that one-liner we started with or the exploded logic that we used in the last section.</span></span> <span data-ttu-id="59f9f-380">In beiden Fällen funktioniert diese Vorgehensweise gut, und Sie können die Implementierung später problemlos ändern.</span><span class="sxs-lookup"><span data-stu-id="59f9f-380">This works well for both scenarios and allows you to easily change that implementation later.</span></span>

## <a name="error-handling"></a><span data-ttu-id="59f9f-381">Fehlerbehandlung</span><span class="sxs-lookup"><span data-stu-id="59f9f-381">Error handling</span></span>

<span data-ttu-id="59f9f-382">Ein wichtiger Anwendungsfall der `if`-Anweisung ist die Überprüfung auf Fehlerbedingungen, bevor Fehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="59f9f-382">One important use of the `if` statement is to check for error conditions before you run into errors.</span></span> <span data-ttu-id="59f9f-383">Beispielsweise können Sie überprüfen, ob ein Ordner bereits vorhanden ist, bevor Sie ihn erstellen.</span><span class="sxs-lookup"><span data-stu-id="59f9f-383">A good example is to check if a folder already exists before you try to create it.</span></span>

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

<span data-ttu-id="59f9f-384">Wenn Sie davon ausgehen, dass eine Ausnahme auftritt, handelt es sich nicht wirklich um eine Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="59f9f-384">I like to say that if you expect an exception to happen, then it's not really an exception.</span></span> <span data-ttu-id="59f9f-385">Daher sollten Sie so oft wie möglich Ihre Werte überprüfen und Ihre Bedingungen validieren.</span><span class="sxs-lookup"><span data-stu-id="59f9f-385">So check your values and validate your conditions where you can.</span></span>

<span data-ttu-id="59f9f-386">Nähere Informationen zur Ausnahmebehandlung finden Sie im Artikel [Alles, was Sie schon immer über Ausnahmen wissen wollten][].</span><span class="sxs-lookup"><span data-stu-id="59f9f-386">If you want to dive a little more into actual exception handling, I have an article on [everything you ever wanted to know about exceptions][].</span></span>

## <a name="final-words"></a><span data-ttu-id="59f9f-387">Abschließende Worte</span><span class="sxs-lookup"><span data-stu-id="59f9f-387">Final words</span></span>

<span data-ttu-id="59f9f-388">Die `if`-Anweisung ist zwar eine einfache Anweisung, jedoch ein zentrales Element von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="59f9f-388">The `if` statement is such a simple statement but is a fundamental piece of PowerShell.</span></span> <span data-ttu-id="59f9f-389">Üblicherweise wird sie in jedem Skript mehrmals verwendet.</span><span class="sxs-lookup"><span data-stu-id="59f9f-389">You will find yourself using this multiple times in almost every script you write.</span></span> <span data-ttu-id="59f9f-390">Ich hoffe, dass Sie nun besser mit dieser Anweisung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="59f9f-390">I hope you have a better understanding than you had before.</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[original version]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[Bitweise Operatoren]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[bitwise operators]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/ (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken)
[the many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[Alles, was Sie schon immer über Ausnahmen wissen wollten]: everything-about-exceptions.md
[everything you ever wanted to know about exceptions]: everything-about-exceptions.md
[Alles, was Sie schon immer über $null wissen wollten]: everything-about-null.md
[everything you wanted to know about $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Alles, was Sie schon immer über die switch-Anweisung wissen wollten]: everything-about-switch.md
[everything you ever wanted to know about the switch statement]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
