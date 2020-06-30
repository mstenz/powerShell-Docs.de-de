---
title: Alles, was Sie schon immer über die Variablenersetzung in Zeichenfolgen wissen wollten
description: Es gibt viele Möglichkeiten, Variablen in Zeichenfolgen zu verwenden, um formatierten Text zu erstellen.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1e65e90ffa09b34f62bc49ad64b062d429483c33
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149463"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a><span data-ttu-id="9c50a-103">Alles, was Sie schon immer über die Variablenersetzung in Zeichenfolgen wissen wollten</span><span class="sxs-lookup"><span data-stu-id="9c50a-103">Everything you wanted to know about variable substitution in strings</span></span>

<span data-ttu-id="9c50a-104">Es gibt viele Möglichkeiten, Variablen in Zeichenfolgen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-104">There are many ways to use variables in strings.</span></span> <span data-ttu-id="9c50a-105">Ich nenne das Variablenersetzung, aber gemeint ist eigentlich jeder Fall, in dem eine Zeichenfolge so formatiert werden soll, dass sie Werte aus Variablen enthält.</span><span class="sxs-lookup"><span data-stu-id="9c50a-105">I'm calling this variable substitution but I'm referring to any time you want to format a string to include values from variables.</span></span> <span data-ttu-id="9c50a-106">Das erläutere ich oft für neue Skriptentwickler.</span><span class="sxs-lookup"><span data-stu-id="9c50a-106">This is something that I often find myself explaining to new scripters.</span></span>

> [!NOTE]
> <span data-ttu-id="9c50a-107">Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="9c50a-108">Das PowerShell-Team dankt Kevin Marquette dafür, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="9c50a-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="9c50a-109">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="9c50a-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="concatenation"></a><span data-ttu-id="9c50a-110">Verkettung</span><span class="sxs-lookup"><span data-stu-id="9c50a-110">Concatenation</span></span>

<span data-ttu-id="9c50a-111">Die erste Klasse der Methoden kann als Verkettung bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-111">The the first class of methods can be referred to as concatenation.</span></span> <span data-ttu-id="9c50a-112">Dabei geht es im Grunde darum, mehrere Zeichenfolgen miteinander zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-112">It's basically taking several strings and joining them together.</span></span> <span data-ttu-id="9c50a-113">Verkettungen werden schon lange zum Erstellen formatierter Zeichenfolgen verwendet.</span><span class="sxs-lookup"><span data-stu-id="9c50a-113">There's a long history of using concatenation to build formatted strings.</span></span>

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

<span data-ttu-id="9c50a-114">Die Verkettung funktioniert gut, wenn nur wenige Werte hinzugefügt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-114">Concatenation works out OK when there are only a few values to add.</span></span> <span data-ttu-id="9c50a-115">Allerdings kann die Angelegenheit schnell komplizierter werden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-115">But this can get complicated quickly.</span></span>

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

<span data-ttu-id="9c50a-116">Das folgende Beispiel ist zwar einfach, aber dennoch schwierig zu lesen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-116">This simple example is already getting harder to read.</span></span>

## <a name="variable-substitution"></a><span data-ttu-id="9c50a-117">Variablenersetzung</span><span class="sxs-lookup"><span data-stu-id="9c50a-117">Variable substitution</span></span>

<span data-ttu-id="9c50a-118">PowerShell bietet eine andere Option, die einfacher ist.</span><span class="sxs-lookup"><span data-stu-id="9c50a-118">PowerShell has another option that is easier.</span></span> <span data-ttu-id="9c50a-119">Sie können die Variablen direkt in den Zeichenfolgen angeben.</span><span class="sxs-lookup"><span data-stu-id="9c50a-119">You can specify your variables directly in the strings.</span></span>

```powershell
$message = "Hello, $first $last."
```

<span data-ttu-id="9c50a-120">Der Unterschied besteht im Typ der Anführungszeichen, in die Sie die Zeichenfolge setzen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-120">The type of quotes you use around the string makes a difference.</span></span> <span data-ttu-id="9c50a-121">Bei einer Zeichenfolge mit doppelten Anführungszeichen ist eine Ersetzung möglich, bei einer Zeichenfolge mit einfachen Anführungszeichen nicht.</span><span class="sxs-lookup"><span data-stu-id="9c50a-121">A double quoted string allows the substitution but a single quoted string doesn't.</span></span> <span data-ttu-id="9c50a-122">Sie können die eine oder die andere Variante verwenden, haben aber stets die freie Wahl.</span><span class="sxs-lookup"><span data-stu-id="9c50a-122">There are times you want one or the other so you have an option.</span></span>

## <a name="command-substitution"></a><span data-ttu-id="9c50a-123">Befehlsersetzung</span><span class="sxs-lookup"><span data-stu-id="9c50a-123">Command substitution</span></span>

<span data-ttu-id="9c50a-124">Es wird ein wenig komplizierter, wenn Sie versuchen, die Werte von Eigenschaften in eine Zeichenfolge zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-124">Things get a little tricky when you start trying to get the values of properties into a string.</span></span> <span data-ttu-id="9c50a-125">Hier kommen viele Neulinge ins Straucheln.</span><span class="sxs-lookup"><span data-stu-id="9c50a-125">This is where many new people get tripped up.</span></span> <span data-ttu-id="9c50a-126">Ich möchte Ihnen zunächst zeigen, was ihrer Meinung nach funktionieren sollte (und auf den ersten Blick sieht es fast so aus, als würde es das auch).</span><span class="sxs-lookup"><span data-stu-id="9c50a-126">First let me show you what they think should work (and at face value almost looks like it should).</span></span>

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

<span data-ttu-id="9c50a-127">Sie würden erwarten, dass Sie den Wert `CreationTime` aus `$directory` abrufen, stattdessen erhalten Sie jedoch `Time: c:\windows.CreationTime` als Wert.</span><span class="sxs-lookup"><span data-stu-id="9c50a-127">You would be expecting to get the `CreationTime` off of the `$directory`, but instead you get this `Time: c:\windows.CreationTime` as your value.</span></span> <span data-ttu-id="9c50a-128">Der Grund dafür ist, dass bei dieser Art der Ersetzung nur die Basisvariable betrachtet wird.</span><span class="sxs-lookup"><span data-stu-id="9c50a-128">The reason is that this type of substitution only sees the base variable.</span></span> <span data-ttu-id="9c50a-129">Der Punkt wird als Teil der Zeichenfolge angesehen, sodass der Wert nicht weiter aufgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="9c50a-129">It considers the period as part of the string so it stops resolving the value any deeper.</span></span>

<span data-ttu-id="9c50a-130">Zufällig gibt dieses Objekt eine Zeichenfolge als Standardwert an, wenn es in eine Zeichenfolge eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="9c50a-130">It just so happens that this object gives a string as a default value when placed into a string.</span></span>
<span data-ttu-id="9c50a-131">Bei einigen Objekte erhalten Sie stattdessen den Typnamen, wie z. B. `System.Collections.Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="9c50a-131">Some objects give you the type name instead like `System.Collections.Hashtable`.</span></span> <span data-ttu-id="9c50a-132">Darauf sollten Sie achten.</span><span class="sxs-lookup"><span data-stu-id="9c50a-132">Just something to watch for.</span></span>

<span data-ttu-id="9c50a-133">PowerShell ermöglicht mit einer speziellen Syntax die Befehlsausführung innerhalb der Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="9c50a-133">PowerShell allows you to do command execution inside the string with a special syntax.</span></span> <span data-ttu-id="9c50a-134">Dadurch können wir die Eigenschaften dieser Objekte abrufen und jeden anderen Befehl ausführen, um einen Wert zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9c50a-134">This allows us to get the properties of these objects and run any other command to get a value.</span></span>

```powershell
$message = "Time: $($directory.CreationTime)"
```

<span data-ttu-id="9c50a-135">Das funktioniert in manchen Situationen sehr gut, kann aber genauso kompliziert wie eine Verkettung werden, wenn Sie nur ein paar Variablen haben.</span><span class="sxs-lookup"><span data-stu-id="9c50a-135">This works great for some situations but it can get just as crazy as concatenation if you have just a few variables.</span></span>

### <a name="command-execution"></a><span data-ttu-id="9c50a-136">Befehlsausführung</span><span class="sxs-lookup"><span data-stu-id="9c50a-136">Command execution</span></span>

<span data-ttu-id="9c50a-137">Sie können in einer Zeichenfolge Befehle ausführen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-137">You can run commands inside a string.</span></span> <span data-ttu-id="9c50a-138">Diese Möglichkeit besteht zwar, aber ich rate von ihrer Verwendung ab.</span><span class="sxs-lookup"><span data-stu-id="9c50a-138">Even though I have this option, I don't like it.</span></span> <span data-ttu-id="9c50a-139">Es wird schnell unübersichtlich und schwer zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-139">It gets cluttered quickly and hard to debug.</span></span> <span data-ttu-id="9c50a-140">Ich führe entweder den Befehl aus und speichere ihn in einer Variablen oder verwende eine Formatzeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="9c50a-140">I either run the command and save to a variable or use a format string.</span></span>

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a><span data-ttu-id="9c50a-141">Formatzeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9c50a-141">Format string</span></span>

<span data-ttu-id="9c50a-142">.NET bietet eine Möglichkeit zum Formatieren von Zeichenfolgen, die meiner Meinung nach recht einfach zu verwenden ist.</span><span class="sxs-lookup"><span data-stu-id="9c50a-142">.NET has a way to format strings that I find fairly easy to work with.</span></span> <span data-ttu-id="9c50a-143">Zunächst möchte ich Ihnen die statische Methode dafür vorstellen, bevor ich Ihnen die PowerShell-Verknüpfung zeige, mit der Sie dasselbe tun können.</span><span class="sxs-lookup"><span data-stu-id="9c50a-143">First let me show you the static method for it before I show you the PowerShell shortcut to do the same thing.</span></span>

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

<span data-ttu-id="9c50a-144">In diesem Fall wird die Zeichenfolge für die Token `{0}` und `{1}` analysiert. Anschließend wird diese Zahl verwendet, um aus den angegebenen Werten auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-144">What is happening here is that the string is parsed for the tokens `{0}` and `{1}`, then it uses that number to pick from the values provided.</span></span> <span data-ttu-id="9c50a-145">Wenn Sie einen Wert an einer Stelle in der Zeichenfolge wiederholen möchten, können Sie die Nummer dieses Werts wieder verwenden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-145">If you want to repeat one value some place in the string, you can reuse that values number.</span></span>

<span data-ttu-id="9c50a-146">Je komplexer die Zeichenfolge wird, desto größer ist der Nutzen, den dieser Ansatz bietet.</span><span class="sxs-lookup"><span data-stu-id="9c50a-146">The more complicated the string gets, the more value you get out of this approach.</span></span>

### <a name="format-values-as-arrays"></a><span data-ttu-id="9c50a-147">Formatieren von Werten als Arrays</span><span class="sxs-lookup"><span data-stu-id="9c50a-147">Format values as arrays</span></span>

<span data-ttu-id="9c50a-148">Wenn die Formatzeile zu lang wird, können Sie Ihre Werte zuerst in ein Array einfügen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-148">If your format line gets too long, you can place your values into an array first.</span></span>

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

<span data-ttu-id="9c50a-149">Hierbei handelt es sich nicht um ein Splatting, da ich das gesamte Array einfüge, aber die Idee ist ähnlich.</span><span class="sxs-lookup"><span data-stu-id="9c50a-149">This is not splatting because I'm passing the whole array in, but the idea is similar.</span></span>

## <a name="advanced-formatting"></a><span data-ttu-id="9c50a-150">Erweiterte Formatierung</span><span class="sxs-lookup"><span data-stu-id="9c50a-150">Advanced formatting</span></span>

<span data-ttu-id="9c50a-151">Ich habe ganz bewusst gesagt, dass diese Option aus .NET stammt, weil es dort bereits viele gut [dokumentierte][] Formatierungsoptionen gibt.</span><span class="sxs-lookup"><span data-stu-id="9c50a-151">I intentionally called these out as coming from .NET because there are lots of formatting options already well [documented][] on it.</span></span> <span data-ttu-id="9c50a-152">Es gibt integrierte Möglichkeiten, verschiedene Datentypen zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="9c50a-152">There are built in ways to format various data types.</span></span>

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

<span data-ttu-id="9c50a-153">Ich werde an dieser Stelle nicht näher darauf eingehen, sondern wollte lediglich darauf hinweisen, dass dies eine sehr leistungsfähige Formatierungs-Engine ist, falls Sie eine solche benötigen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-153">I'm not going to go into them but I just wanted to let you know that this is a very powerful formatting engine if you need it.</span></span>

## <a name="joining-strings"></a><span data-ttu-id="9c50a-154">Verknüpfen von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="9c50a-154">Joining strings</span></span>

<span data-ttu-id="9c50a-155">Es gibt allerdings auch Fälle, in denen Sie tatsächlich eine Liste mit Werten miteinander verketten möchten.</span><span class="sxs-lookup"><span data-stu-id="9c50a-155">Sometimes you actually do want to concatenate a list of values together.</span></span> <span data-ttu-id="9c50a-156">Dafür gibt es einen `-join`-Operator.</span><span class="sxs-lookup"><span data-stu-id="9c50a-156">There's a `-join` operator that can do that for you.</span></span> <span data-ttu-id="9c50a-157">Damit können Sie sogar ein Zeichen angeben, das zwischen den Zeichenfolgen verknüpft werden soll.</span><span class="sxs-lookup"><span data-stu-id="9c50a-157">It even lets you specify a character to join between the strings.</span></span>

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

<span data-ttu-id="9c50a-158">Wenn Sie Zeichenfolgen mit `-join` ohne ein solches Trennzeichen verknüpfen möchten, geben Sie einfach eine leere Zeichenfolge `''` an.</span><span class="sxs-lookup"><span data-stu-id="9c50a-158">If you want to `-join` some strings without a separator, you need to specify an empty string `''`.</span></span>
<span data-ttu-id="9c50a-159">Wenn das aber alles ist, was Sie machen möchten, gibt es eine schnellere Option.</span><span class="sxs-lookup"><span data-stu-id="9c50a-159">But if that is all you need, there's a faster option.</span></span>

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

<span data-ttu-id="9c50a-160">Sie sollten ferner wissen, dass Sie Zeichenfolgen auch mit `-split` teilen können.</span><span class="sxs-lookup"><span data-stu-id="9c50a-160">It's also worth pointing out that you can also `-split` strings too.</span></span>

## <a name="join-path"></a><span data-ttu-id="9c50a-161">Join-Path</span><span class="sxs-lookup"><span data-stu-id="9c50a-161">Join-Path</span></span>

<span data-ttu-id="9c50a-162">Dies wird oft übersehen, ist aber ein gutes Cmdlet zum Erstellen eines Dateipfads.</span><span class="sxs-lookup"><span data-stu-id="9c50a-162">This is often overlooked but a great cmdlet for building a file path.</span></span>

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

<span data-ttu-id="9c50a-163">Das Tolle daran ist, dass es die umgekehrten Schrägstriche richtig verarbeitet, wenn die Werte zusammengesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-163">The great thing about this is it works out the backslashes correctly when it puts the values together.</span></span> <span data-ttu-id="9c50a-164">Dies ist besonders wichtig, wenn Sie Werte von Benutzern oder aus Konfigurationsdateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-164">This is especially important if you are taking values from users or config files.</span></span>

<span data-ttu-id="9c50a-165">Das funktioniert auch gut mit `Split-Path` und `Test-Path`.</span><span class="sxs-lookup"><span data-stu-id="9c50a-165">This also goes well with `Split-Path` and `Test-Path`.</span></span> <span data-ttu-id="9c50a-166">Darüber spreche ich auch in meinem Beitrag zum [Lesen und Speichern in Dateien][].</span><span class="sxs-lookup"><span data-stu-id="9c50a-166">I also cover these in my post about [reading and saving to files][].</span></span>

## <a name="strings-are-arrays"></a><span data-ttu-id="9c50a-167">Zeichenfolgen sind Arrays</span><span class="sxs-lookup"><span data-stu-id="9c50a-167">Strings are arrays</span></span>

<span data-ttu-id="9c50a-168">Bevor ich fortfahre, muss ich an dieser Stelle noch ein Wort über die Zeichenfolgenaddition verlieren.</span><span class="sxs-lookup"><span data-stu-id="9c50a-168">I do need to mention adding strings here before I go on.</span></span> <span data-ttu-id="9c50a-169">Denken Sie daran, dass eine Zeichenfolge nur ein Array aus Zeichen ist.</span><span class="sxs-lookup"><span data-stu-id="9c50a-169">Remember that a string is just an array of characters.</span></span> <span data-ttu-id="9c50a-170">Wenn Sie mehrere Zeichenfolgen addieren, entsteht jedes Mal ein neues Array.</span><span class="sxs-lookup"><span data-stu-id="9c50a-170">When you add multiple strings together, a new array is created each time.</span></span>

<span data-ttu-id="9c50a-171">Sehen Sie sich folgendes Beispiel an:</span><span class="sxs-lookup"><span data-stu-id="9c50a-171">Look at this example:</span></span>

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

<span data-ttu-id="9c50a-172">Sieht einfach aus, oder? Was Sie jedoch nicht sehen: Jedes Mal, wenn eine Zeichenfolge zu `$message` addiert wird, wird eine ganz neue Zeichenfolge erstellt.</span><span class="sxs-lookup"><span data-stu-id="9c50a-172">It looks very basic but what you don't see is that each time a string is added to `$message` that a whole new string is created.</span></span> <span data-ttu-id="9c50a-173">Arbeitsspeicher wird zugeordnet, Daten werden kopiert, und veraltete Daten werden verworfen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-173">Memory gets allocated, data gets copied and the old one is discarded.</span></span>
<span data-ttu-id="9c50a-174">Das ist keine große Sache, wenn es nur ein paar Mal gemacht wird, aber eine Schleife wie diese würde wirklich zu Problemen führen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-174">Not a big deal when it's only done a few times, but a loop like this would really expose the issue.</span></span>

### <a name="stringbuilder"></a><span data-ttu-id="9c50a-175">StringBuilder</span><span class="sxs-lookup"><span data-stu-id="9c50a-175">StringBuilder</span></span>

<span data-ttu-id="9c50a-176">Auch StringBuilder wird gerne zur Erstellung langer Zeichenfolgen aus mehreren kürzeren Zeichenfolgen verwendet.</span><span class="sxs-lookup"><span data-stu-id="9c50a-176">StringBuilder is also very popular for building large strings from lots of smaller strings.</span></span> <span data-ttu-id="9c50a-177">Der Grund dafür ist, dass er einfach alle Zeichenfolgen sammelt, die Sie addieren, und sie erst am Ende verkettet, wenn Sie den Wert abrufen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-177">The reason why is because it just collects all the strings you add to it and only concatenates all of them at the end when you retrieve the value.</span></span>

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

<span data-ttu-id="9c50a-178">Auch das ist etwas, wofür ich .NET verwende.</span><span class="sxs-lookup"><span data-stu-id="9c50a-178">Again, this is something that I'm reaching out to .NET for.</span></span> <span data-ttu-id="9c50a-179">Ich nutze es zwar nicht mehr häufig, aber es ist einfach gut zu wissen, dass es bei Bedarf verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="9c50a-179">I don't use it often anymore but it's good to know it's there.</span></span>

## <a name="delineation-with-braces"></a><span data-ttu-id="9c50a-180">Abgrenzung mit geschweiften Klammern</span><span class="sxs-lookup"><span data-stu-id="9c50a-180">Delineation with braces</span></span>

<span data-ttu-id="9c50a-181">Dies wird für die Suffixverkettung innerhalb der Zeichenfolge verwendet.</span><span class="sxs-lookup"><span data-stu-id="9c50a-181">This is used for suffix concatenation within the string.</span></span> <span data-ttu-id="9c50a-182">Manchmal verfügt Ihre Variable nicht über eine eindeutige Wortgrenze.</span><span class="sxs-lookup"><span data-stu-id="9c50a-182">Sometimes your variable doesn't have a clean word boundary.</span></span>

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

<span data-ttu-id="9c50a-183">Vielen Dank dafür an [/u/real_parbold][].</span><span class="sxs-lookup"><span data-stu-id="9c50a-183">Thank you [/u/real_parbold][] for that one.</span></span>

<span data-ttu-id="9c50a-184">Hier ist eine Alternative zu diesem Ansatz:</span><span class="sxs-lookup"><span data-stu-id="9c50a-184">Here is an alternate to this approach:</span></span>

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

<span data-ttu-id="9c50a-185">Hierfür verwende ich persönlich eine Formatzeichenfolge, aber es ist gut zu wissen, dass es das gibt, falls es Ihnen in der Praxis einmal begegnet.</span><span class="sxs-lookup"><span data-stu-id="9c50a-185">I personally use format string for this, but this is good to know incase you see it in the wild.</span></span>

## <a name="find-and-replace-tokens"></a><span data-ttu-id="9c50a-186">Suchen und Ersetzen von Token</span><span class="sxs-lookup"><span data-stu-id="9c50a-186">Find and replace tokens</span></span>

<span data-ttu-id="9c50a-187">Bei den meisten dieser Features müssen Sie zwar nicht unbedingt eine eigene Lösung entwickeln, aber es kann vorkommen, dass Sie mit großen Vorlagendateien arbeiten, in denen Sie Zeichenfolgen ersetzen möchten.</span><span class="sxs-lookup"><span data-stu-id="9c50a-187">While most of these features limit your need to roll your own solution, there are times where you may have large template files where you want to replace strings inside.</span></span>

<span data-ttu-id="9c50a-188">Nehmen wir an, Sie haben eine Vorlage mit sehr viel Text aus einer Datei abgerufen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-188">Let us assume you pulled in a template from a file that has a lot of text.</span></span>

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

<span data-ttu-id="9c50a-189">Es müssen möglicherweise viele Token ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-189">You may have lots of tokens to replace.</span></span> <span data-ttu-id="9c50a-190">Der Trick besteht darin, ein sehr eindeutiges Token zu verwenden, das leicht zu finden und zu ersetzen ist.</span><span class="sxs-lookup"><span data-stu-id="9c50a-190">The trick is to use a very distinct token that is easy to find and replace.</span></span> <span data-ttu-id="9c50a-191">In der Regel verwende ich ein Sonderzeichen an beiden Enden, um es klar abgrenzen zu können.</span><span class="sxs-lookup"><span data-stu-id="9c50a-191">I tend to use a special character at both ends to help distinguish it.</span></span>

<span data-ttu-id="9c50a-192">Ich habe vor Kurzem einen neuen Ansatz dafür gefunden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-192">I recently found a new way to approach this.</span></span> <span data-ttu-id="9c50a-193">Ich habe mich entschieden, diesen Abschnitt stehen zu lassen, weil dieses Muster häufig verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9c50a-193">I decided to leave this section in here because this is a pattern that is commonly used.</span></span>

### <a name="replace-multiple-tokens"></a><span data-ttu-id="9c50a-194">Ersetzen mehrerer Token</span><span class="sxs-lookup"><span data-stu-id="9c50a-194">Replace multiple tokens</span></span>

<span data-ttu-id="9c50a-195">Wenn ich eine ganze Liste von Token ersetzen muss, verfolge ich einen allgemeineren Ansatz.</span><span class="sxs-lookup"><span data-stu-id="9c50a-195">When I have a list of tokens that I need to replace, I take a more generic approach.</span></span> <span data-ttu-id="9c50a-196">Ich füge sie in einer Hashtabelle ein und durchlaufe sie, um die Ersetzung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-196">I would place them in a hashtable and iterate over them to do the replace.</span></span>

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

<span data-ttu-id="9c50a-197">Diese Token können bei Bedarf aus einer JSON- oder CSV-Datei geladen werden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-197">Those tokens could be loaded from JSON or CSV if needed.</span></span>

### <a name="executioncontext-expandstring"></a><span data-ttu-id="9c50a-198">ExecutionContext ExpandString</span><span class="sxs-lookup"><span data-stu-id="9c50a-198">ExecutionContext ExpandString</span></span>

<span data-ttu-id="9c50a-199">Es gibt einen wirklich cleveren Weg, eine Ersetzungszeichenfolge mit einfachen Anführungszeichen zu definieren und die Variablen später zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="9c50a-199">There's a clever way to define a substitution string with single quotes and expand the variables later.</span></span> <span data-ttu-id="9c50a-200">Sehen Sie sich folgendes Beispiel an:</span><span class="sxs-lookup"><span data-stu-id="9c50a-200">Look at this example:</span></span>

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

<span data-ttu-id="9c50a-201">Der Aufruf von `.InvokeCommand.ExpandString` im aktuellen Ausführungskontext verwendet die Variablen im aktuellen Gültigkeitsbereich für die Ersetzung.</span><span class="sxs-lookup"><span data-stu-id="9c50a-201">The call to `.InvokeCommand.ExpandString` on the current execution context uses the variables in the current scope for substitution.</span></span> <span data-ttu-id="9c50a-202">Der wichtigste Punkt hierbei ist, dass `$message` sehr früh definiert werden kann, noch bevor die Variablen überhaupt vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="9c50a-202">The key thing here is that the `$message` can be defined very early before the variables even exist.</span></span>

<span data-ttu-id="9c50a-203">Wenn wir das nur ein wenig erweitern, können wir diese Ersetzung immer wieder mit unterschiedlichen Werten durchführen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-203">If we expand on that just a little bit, we can perform this substitution over and over wih different values.</span></span>

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

<span data-ttu-id="9c50a-204">Um diese Idee weiter zu verfolgen, könnten Sie beispielsweise eine umfangreiche E-Mail-Vorlage aus einer Textdatei importieren.</span><span class="sxs-lookup"><span data-stu-id="9c50a-204">To keep going on this idea; you could be importing a large email template from a text file to do this.</span></span> <span data-ttu-id="9c50a-205">Ich danke [Mark Kraus][] für diesen [Vorschlag][].</span><span class="sxs-lookup"><span data-stu-id="9c50a-205">I have to thank [Mark Kraus][] for this [suggestion][].</span></span>

## <a name="whatever-works-the-best-for-you"></a><span data-ttu-id="9c50a-206">Was immer für Sie am besten geeignet ist</span><span class="sxs-lookup"><span data-stu-id="9c50a-206">Whatever works the best for you</span></span>

<span data-ttu-id="9c50a-207">Ich arbeite sehr gern mit Formatzeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="9c50a-207">I'm a fan of the format string approach.</span></span> <span data-ttu-id="9c50a-208">Ich verwende sie auf jeden Fall bei komplizierteren Zeichenfolgen oder wenn es mehrere Variablen gibt.</span><span class="sxs-lookup"><span data-stu-id="9c50a-208">I definitely do this with the more complicated strings or if there are multiple variables.</span></span> <span data-ttu-id="9c50a-209">Bei sehr kurzen Zeichenfolgen kann ich jeden dieser Ansätze verwenden.</span><span class="sxs-lookup"><span data-stu-id="9c50a-209">On anything that is very short, I may use any one of these.</span></span>

## <a name="anything-else"></a><span data-ttu-id="9c50a-210">Noch etwas?</span><span class="sxs-lookup"><span data-stu-id="9c50a-210">Anything else?</span></span>

<span data-ttu-id="9c50a-211">Ich habe hier sehr viele Aspekte vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="9c50a-211">I covered a lot of ground on this one.</span></span> <span data-ttu-id="9c50a-212">Ich hoffe, dass Sie etwas Neues lernen konnten.</span><span class="sxs-lookup"><span data-stu-id="9c50a-212">My hope is that you walk away learning something new.</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[original version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[Vorschlag]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[suggestion]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[Lesen und Speichern in Dateien]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[reading and saving to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[dokumentierte]: /dotnet/api/system.string.format#overloads
[documented]: /dotnet/api/system.string.format#overloads
