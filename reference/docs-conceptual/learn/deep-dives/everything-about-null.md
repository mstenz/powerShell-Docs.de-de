---
title: Alles, was Sie schon immer über $null wissen wollten
description: Das PowerShell-$null scheint oft einfach zu sein, aber es hat viele Nuancen. Sehen wir uns nun $null an, damit Sie wissen, was passiert, wenn Sie unerwartet auf einen NULL-Wert stoßen.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149473"
---
# <a name="everything-you-wanted-to-know-about-null"></a><span data-ttu-id="4e0e1-104">Alles, was Sie schon immer über $null wissen wollten</span><span class="sxs-lookup"><span data-stu-id="4e0e1-104">Everything you wanted to know about $null</span></span>

<span data-ttu-id="4e0e1-105">Das PowerShell-`$null` scheint oft einfach zu sein, aber es hat viele Nuancen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-105">The PowerShell `$null` often appears to be simple but it has a lot of nuances.</span></span> <span data-ttu-id="4e0e1-106">Sehen wir uns nun `$null` an, damit Sie wissen, was passiert, wenn Sie unerwartet auf einen `$null`-Wert stoßen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-106">Let's take a close look at `$null` so you know what happens when you unexpectedly run into a `$null` value.</span></span>

> [!NOTE]
> <span data-ttu-id="4e0e1-107">Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="4e0e1-108">Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="4e0e1-109">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="4e0e1-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-null"></a><span data-ttu-id="4e0e1-110">Was ist NULL?</span><span class="sxs-lookup"><span data-stu-id="4e0e1-110">What is NULL?</span></span>

<span data-ttu-id="4e0e1-111">Sie können sich NULL als unbekannten oder leeren Wert vorstellen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-111">You can think of NULL as an unknown or empty value.</span></span> <span data-ttu-id="4e0e1-112">Eine Variable ist NULL, bis Sie ihr einen Wert oder ein Objekt zuweisen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-112">A variable is NULL until you assign a value or an object to it.</span></span> <span data-ttu-id="4e0e1-113">Dies kann wichtig sein, da einige Befehle einen Wert erfordern und Fehler generieren, wenn der Wert NULL ist.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-113">This can be important because there are some commands that require a value and generate errors if the value is NULL.</span></span>

### <a name="powershell-null"></a><span data-ttu-id="4e0e1-114">PowerShell-$null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-114">PowerShell $null</span></span>

<span data-ttu-id="4e0e1-115">`$null` ist eine automatische Variable in PowerShell, die zur Darstellung von NULL verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-115">`$null` is an automatic variable in PowerShell used to represent NULL.</span></span> <span data-ttu-id="4e0e1-116">Sie können sie Variablen zuweisen, in Vergleichen verwenden und als Platzhalter für NULL in einer Sammlung verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-116">You can assign it to variables, use it in comparisons and use it as a place holder for NULL in a collection.</span></span>

<span data-ttu-id="4e0e1-117">PowerShell behandelt `$null` als Objekt mit dem Wert NULL.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-117">PowerShell treats `$null` as an object with a value of NULL.</span></span> <span data-ttu-id="4e0e1-118">Dies unterscheidet sich von dem, was Sie möglicherweise erwarten, wenn Sie eine andere Sprache gewohnt sind.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-118">This is different than what you may expect if you come from another language.</span></span>

## <a name="examples-of-null"></a><span data-ttu-id="4e0e1-119">Beispiele für $null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-119">Examples of $null</span></span>

<span data-ttu-id="4e0e1-120">Wenn Sie versuchen, eine Variable zu verwenden, die Sie nicht initialisiert haben, ist der Wert `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-120">Anytime you try to use a variable that you have not initialized, the value is `$null`.</span></span> <span data-ttu-id="4e0e1-121">Dies ist eine der gängigsten Möglichkeiten, wie sich `$null`-Werte in Ihren Code einschleichen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-121">This is one of the most common ways that `$null` values sneak into your code.</span></span>

```powershell
PS> $null -eq $undefinedVariable
True
```

<span data-ttu-id="4e0e1-122">Wenn Sie einen Variablennamen falsch schreiben, betrachtet PowerShell dies als eine andere Variable, und der Wert ist `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-122">If you happen to mistype a variable name then PowerShell sees it as a different variable and the value is `$null`.</span></span>

<span data-ttu-id="4e0e1-123">Eine andere Möglichkeit ist, dass `$null`-Werte von anderen Befehlen stammen, die keine Ergebnisse liefern.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-123">The other way you find `$null` values is when they come from other commands that don't give you any results.</span></span>

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a><span data-ttu-id="4e0e1-124">Auswirkungen von $null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-124">Impact of $null</span></span>

<span data-ttu-id="4e0e1-125">Wie sich `$null`-Werte auf Ihren Code auswirken, hängt davon ab, wo sie auftreten.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-125">`$null` values impact your code differently depending on where they show up.</span></span>

### <a name="in-strings"></a><span data-ttu-id="4e0e1-126">In Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="4e0e1-126">In strings</span></span>

<span data-ttu-id="4e0e1-127">Wenn Sie `$null` in einer Zeichenfolge verwenden, handelt es sich um einen leeren Wert (oder eine leere Zeichenfolge).</span><span class="sxs-lookup"><span data-stu-id="4e0e1-127">If you use `$null` in a string, then it's a blank value (or empty string).</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

<span data-ttu-id="4e0e1-128">Dies ist einer der Gründe, warum ich Variablen in Klammern setze, wenn ich sie in Protokollmeldungen verwende.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-128">This is one of the reasons that I like to place brackets around variables when using them in log messages.</span></span> <span data-ttu-id="4e0e1-129">Es ist noch wichtiger, die Ränder der Variablenwerte zu identifizieren, wenn sich der Wert am Ende der Zeichenfolge befindet.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-129">It's even more important to identify the edges of your variable values when the value is at the end of the string.</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

<span data-ttu-id="4e0e1-130">So sind leere Zeichenfolgen und `$null`-Werte leicht zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-130">This makes empty strings and `$null` values easy to spot.</span></span>

### <a name="in-numeric-equation"></a><span data-ttu-id="4e0e1-131">In numerischen Gleichungen</span><span class="sxs-lookup"><span data-stu-id="4e0e1-131">In numeric equation</span></span>

<span data-ttu-id="4e0e1-132">Wenn ein `$null`-Wert in einer numerischen Gleichung verwendet wird, sind die Ergebnisse ungültig, auch wenn sie keinen Fehler verursachen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-132">When a `$null` value is used in a numeric equation then your results are invalid if they don't give an error.</span></span> <span data-ttu-id="4e0e1-133">Manchmal wird `$null` mit `0` ausgewertet, und in anderen Fällen ist das gesamte Ergebnis `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-133">Sometimes the `$null` evaluates to `0` and other times it makes the whole result `$null`.</span></span>
<span data-ttu-id="4e0e1-134">Im Folgenden finden Sie ein Beispiel für eine Multiplikation, die abhängig von der Reihenfolge der Werte 0 oder `$null` ergibt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-134">Here is an example with multiplication that gives 0 or `$null` depending on the order of the values.</span></span>

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a><span data-ttu-id="4e0e1-135">Anstelle einer Sammlung</span><span class="sxs-lookup"><span data-stu-id="4e0e1-135">In place of a collection</span></span>

<span data-ttu-id="4e0e1-136">Mit einer Sammlung können Sie einen Index für den Zugriff auf Werte verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-136">A collection allow you use an index to access values.</span></span> <span data-ttu-id="4e0e1-137">Wenn Sie versuchen, eine Indizierung in einer Sammlung durchzuführen, die tatsächlich `null` ist, erhalten Sie folgende Fehlermeldung: `Cannot index into a null array`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-137">If you try to index into a collection that is actually `null`, you get this error: `Cannot index into a null array`.</span></span>

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

<span data-ttu-id="4e0e1-138">Wenn Sie über eine Sammlung verfügen, aber versuchen, auf ein Element zuzugreifen, das nicht in der Sammlung enthalten ist, erhalten Sie ein `$null`-Ergebnis.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-138">If you have a collection but try to access an element that is not in the collection, you get a `$null` result.</span></span>

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a><span data-ttu-id="4e0e1-139">Anstelle eines Objekts</span><span class="sxs-lookup"><span data-stu-id="4e0e1-139">In place of an object</span></span>

<span data-ttu-id="4e0e1-140">Wenn Sie versuchen, auf eine Eigenschaft oder untergeordnete Eigenschaft eines Objekts zuzugreifen, das nicht über die angegebene Eigenschaft verfügt, erhalten Sie einen `$null`-Wert wie für eine nicht definierte Variable.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-140">If you try to access a property or sub property of an object that doesn't have the specified property, you get a `$null` value like you would for an undefined variable.</span></span> <span data-ttu-id="4e0e1-141">In diesem Fall spielt es keine Rolle, ob die Variable `$null` oder ein tatsächliches Objekt ist.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-141">It doesn't matter if the variable is `$null` or an actual object in this case.</span></span>

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a><span data-ttu-id="4e0e1-142">Methode für einen Ausdruck mit NULL-Wert</span><span class="sxs-lookup"><span data-stu-id="4e0e1-142">Method on a null-valued expression</span></span>

<span data-ttu-id="4e0e1-143">Durch das Aufrufen einer Methode eines `$null`-Objekts wird eine `RuntimeException` ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-143">Calling a method on a `$null` object throws a `RuntimeException`.</span></span>

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

<span data-ttu-id="4e0e1-144">Wenn ich die Meldung `You cannot call a method on a null-valued expression` sehe, suche ich zuerst nach Stellen, an denen ich eine Methode für eine Variable aufrufe, ohne sie zuerst auf `$null` zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-144">Whenever I see the phrase `You cannot call a method on a null-valued expression` then the first thing I look for are places where I am calling a method on a variable without first checking it for `$null`.</span></span>

## <a name="checking-for-null"></a><span data-ttu-id="4e0e1-145">Überprüfung auf $null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-145">Checking for $null</span></span>

<span data-ttu-id="4e0e1-146">Sie haben vielleicht bemerkt, dass ich bei der Überprüfung auf `$null` in meinen Beispielen `$null` immer auf der linken Seite platziere.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-146">You may have noticed that I always place the `$null` on the left when checking for `$null` in my examples.</span></span> <span data-ttu-id="4e0e1-147">Dies ist beabsichtigt, denn es handelt sich dabei um eine anerkannte bewährte PowerShell-Methode.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-147">This is intentional and accepted as a PowerShell best practice.</span></span> <span data-ttu-id="4e0e1-148">Es gibt einige Szenarios, in denen das Platzieren auf der rechten Seite nicht das erwartete Ergebnis liefert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-148">There are some scenarios where placing it on the right doesn't give you the expected result.</span></span>

<span data-ttu-id="4e0e1-149">Sehen Sie sich das nächste Beispiel an, und versuchen Sie, die Ergebnisse vorherzusagen:</span><span class="sxs-lookup"><span data-stu-id="4e0e1-149">Look at this next example and try to predict the results:</span></span>

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

<span data-ttu-id="4e0e1-150">Wenn ich `$value` nicht definiere, wird der erste Ausdruck als `$true` ausgewertet, und die Meldung lautet `The array is $null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-150">If I do not define `$value`, the first one evaluates to `$true` and our message is `The array is $null`.</span></span> <span data-ttu-id="4e0e1-151">Die Falle ist, dass ein `$value` erstellt werden kann, bei dem beide Ausdrücke als `$false` ausgewertet werden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-151">The trap here is that it's possible to create a `$value` that allows both of them to be `$false`</span></span>

```powershell
$value = @( $null )
```

<span data-ttu-id="4e0e1-152">In diesem Fall ist der `$value` ein Array, das ein `$null` enthält.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-152">In this case, the `$value` is an array that contains a `$null`.</span></span> <span data-ttu-id="4e0e1-153">`-eq` überprüft jeden Wert im Array und gibt das übereinstimmende `$null` zurück.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-153">The `-eq` checks every value in the array and returns the `$null` that is matched.</span></span> <span data-ttu-id="4e0e1-154">Dies wird als `$false` ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-154">This evaluates to `$false`.</span></span> <span data-ttu-id="4e0e1-155">`-ne` gibt alle Elemente zurück, die nicht mit `$null` identisch sind, und in diesem Fall gibt es keine Ergebnisse (dies wird auch als `$false` ausgewertet).</span><span class="sxs-lookup"><span data-stu-id="4e0e1-155">The `-ne` returns everything that doesn't match `$null` and in this case there are no results (This also evaluates to `$false`).</span></span> <span data-ttu-id="4e0e1-156">Keines der beiden ist `$true`, auch wenn es so aussieht, als sollte dies auf eines zutreffen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-156">Neither one is `$true` even though it looks like one of them should be.</span></span>

<span data-ttu-id="4e0e1-157">Wir können nicht nur einen Wert erstellen, bei dem beide als `$false` ausgewertet werden, es ist auch möglich, einen Wert zu erstellen, bei dem beide als `$true` ausgewertet werden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-157">Not only can we create a value that makes both of them evaluate to `$false`, it's possible to create a value where they both evaluate to `$true`.</span></span> <span data-ttu-id="4e0e1-158">Ein [guter Beitrag][] von Mathias Jessen (@IISResetMe) behandelt dieses Szenario ausführlich.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-158">Mathias Jessen (@IISResetMe) has a [good post][] that dives into that scenario.</span></span>

### <a name="psscriptanalyzer-and-vscode"></a><span data-ttu-id="4e0e1-159">PSScriptAnalyzer und VSCode</span><span class="sxs-lookup"><span data-stu-id="4e0e1-159">PSScriptAnalyzer and VSCode</span></span>

<span data-ttu-id="4e0e1-160">Das [PSScriptAnalyzer][]-Modul verfügt über eine Regel mit dem Namen `PSPossibleIncorrectComparisonWithNull`, die prüft, ob das Problem vorliegt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-160">The [PSScriptAnalyzer][] module has a rule that checks for this issue called `PSPossibleIncorrectComparisonWithNull`.</span></span>

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

<span data-ttu-id="4e0e1-161">Da VS Code die PSScriptAnalyzer-Regeln ebenfalls verwendet, wird dies auch in Ihrem Skript als Problem hervorgehoben oder identifiziert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-161">Because VS Code uses the PSScriptAnalyser rules too, it also highlights or identifies this as a problem in your script.</span></span>

### <a name="simple-if-check"></a><span data-ttu-id="4e0e1-162">Einfache if-Überprüfung</span><span class="sxs-lookup"><span data-stu-id="4e0e1-162">Simple if check</span></span>

<span data-ttu-id="4e0e1-163">Eine gängige Methode zur Überprüfung auf einen Nicht-$null-Wert ist die Verwendung einer einfachen `if()`-Anweisung ohne Vergleich.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-163">A common way that people check for a non-$null value is to use a simple `if()` statement without the comparison.</span></span>

```powershell
if ( $value )
{
    Do-Something
}
```

<span data-ttu-id="4e0e1-164">Wenn der Wert `$null` ist, ergibt dies `$false`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-164">If the value is `$null`, this evaluates to `$false`.</span></span> <span data-ttu-id="4e0e1-165">Dies ist leicht lesbar, aber achten Sie darauf, dass genau nach dem gesucht wird, wonach gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-165">This is easy to read, but be careful that it's looking for exactly what you're expecting it to look for.</span></span> <span data-ttu-id="4e0e1-166">Ich lese diese Codezeile wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4e0e1-166">I read that line of code as:</span></span>

> <span data-ttu-id="4e0e1-167">Wenn `$value` über einen Wert verfügt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-167">If `$value` has a value.</span></span>

<span data-ttu-id="4e0e1-168">Aber das ist nicht alles.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-168">But that's not the whole story.</span></span> <span data-ttu-id="4e0e1-169">Diese Zeile sagt tatsächlich aus:</span><span class="sxs-lookup"><span data-stu-id="4e0e1-169">That line is actually saying:</span></span>

> <span data-ttu-id="4e0e1-170">Wenn `$value` nicht `$null` oder `0` oder `$false` oder ein `empty string` ist</span><span class="sxs-lookup"><span data-stu-id="4e0e1-170">If `$value` is not `$null` or `0` or `$false` or an `empty string`</span></span>

<span data-ttu-id="4e0e1-171">Im Folgenden finden Sie ein ausführlicheres Beispiel für diese Anweisung.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-171">Here is a more complete sample of that statement.</span></span>

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

<span data-ttu-id="4e0e1-172">Es ist in Ordnung, eine einfache `if`-Prüfung zu verwenden, solange Sie sich merken, dass diese anderen Werte als `$false` zählen und nicht nur, dass eine Variable über einen Wert verfügt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-172">It's perfectly OK to use a basic `if` check as long as you remember those other values count as `$false` and not just that a variable has a value.</span></span>

<span data-ttu-id="4e0e1-173">Beim Umgestalten von Code vor einigen Tagen ist dieses Problem aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-173">I ran into this issue when refactoring some code a few days ago.</span></span> <span data-ttu-id="4e0e1-174">Er enthielt eine grundlegende Eigenschaftenüberprüfung wie diese.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-174">It had a basic property check like this.</span></span>

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="4e0e1-175">Ich wollte das Vorhandensein einer Objekteigenschaft überprüfen, bevor ich ihr einen Wert zuwies.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-175">I wanted to assign a value to the object property only if it existed.</span></span> <span data-ttu-id="4e0e1-176">In den meisten Fällen verfügte das ursprüngliche Objekt über einen Wert, der in der `if`-Anweisung als `$true` ausgewertet wurde.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-176">In most cases, the original object had a value that would evaluate to `$true` in the `if` statement.</span></span> <span data-ttu-id="4e0e1-177">Doch manchmal wurde der Wert nicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-177">But I ran into an issue where the value was occasionally not getting set.</span></span> <span data-ttu-id="4e0e1-178">Ich habe den Code gedebuggt und festgestellt, dass das Objekt die Eigenschaft enthielt, aber es handelte sich um einen leeren Zeichenfolgenwert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-178">I debugged the code and found that the object had the property but it was a blank string value.</span></span> <span data-ttu-id="4e0e1-179">Dadurch wurde die Aktualisierung mit der vorherigen Logik verhindert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-179">This prevented it from ever getting updated with the previous logic.</span></span> <span data-ttu-id="4e0e1-180">Nachdem ich eine ordnungsgemäße `$null`-Überprüfung hinzugefügt hatte, funktionierte alles.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-180">So I added a proper `$null` check and everything worked.</span></span>

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="4e0e1-181">Kleine Fehler wie diese sind schwer zu erkennen und lassen mich akribisch Werte auf `$null` überprüfen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-181">It's little bugs like these that are hard to spot and make me aggressively check values for `$null`.</span></span>

## <a name="nullcount"></a><span data-ttu-id="4e0e1-182">$null.Count</span><span class="sxs-lookup"><span data-stu-id="4e0e1-182">$null.Count</span></span>

<span data-ttu-id="4e0e1-183">Wenn Sie versuchen, über einen `$null`-Wert auf eine Eigenschaft zuzugreifen, ist die Eigenschaft auch `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-183">If you try to access a property on a `$null` value, that the property is also `$null`.</span></span> <span data-ttu-id="4e0e1-184">Die `count`-Eigenschaft ist die Ausnahme von dieser Regel.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-184">The `count` property is the exception to this rule.</span></span>

```powershell
PS> $value = $null
PS> $value.count
0
```

<span data-ttu-id="4e0e1-185">Wenn Sie über einen `$null`-Wert verfügen, ist `count` gleich `0`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-185">When you have a `$null` value, then the `count` is `0`.</span></span> <span data-ttu-id="4e0e1-186">Diese spezielle Eigenschaft wird von PowerShell hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-186">This special property is added by PowerShell.</span></span>

### <a name="pscustomobject-count"></a><span data-ttu-id="4e0e1-187">[PSCustomObject] Count</span><span class="sxs-lookup"><span data-stu-id="4e0e1-187">[PSCustomObject] Count</span></span>

<span data-ttu-id="4e0e1-188">Fast alle Objekte in PowerShell haben diese Count-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-188">Almost all objects in PowerShell have that count property.</span></span> <span data-ttu-id="4e0e1-189">Eine wichtige Ausnahme ist `[PSCustomObject]` in Windows PowerShell 5.1 (dies wird in PowerShell 6.0 korrigiert).</span><span class="sxs-lookup"><span data-stu-id="4e0e1-189">One important exception is the `[PSCustomObject]` in Windows PowerShell 5.1 (This is fixed in PowerShell 6.0).</span></span> <span data-ttu-id="4e0e1-190">Es verfügt nicht über eine Count-Eigenschaft, sodass Sie einen `$null`-Wert erhalten, wenn Sie versuchen, sie zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-190">It doesn't have a count property so you get a `$null` value if you try to use it.</span></span> <span data-ttu-id="4e0e1-191">Ich betone dies hier, damit Sie nicht versuchen, `.Count` anstelle einer `$null`-Prüfung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-191">I call this out here so that you don't try to use `.Count` instead of a `$null` check.</span></span>

<span data-ttu-id="4e0e1-192">Das Ausführen dieses Beispiels in Windows PowerShell 5.1 und PowerShell 6.0 führt zu unterschiedlichen Ergebnissen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-192">Running this example on Windows PowerShell 5.1 and PowerShell 6.0 gives you different results.</span></span>

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a><span data-ttu-id="4e0e1-193">Leeres NULL</span><span class="sxs-lookup"><span data-stu-id="4e0e1-193">Empty null</span></span>

<span data-ttu-id="4e0e1-194">Es gibt eine besondere Art von `$null`, die anders agiert als die anderen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-194">There is one special type of `$null` that acts differently than the others.</span></span> <span data-ttu-id="4e0e1-195">Ich nenne sie das leere `$null`, aber tatsächlich handelt es sich um ein [System.Management.Automation.Internal.AutomationNull][].</span><span class="sxs-lookup"><span data-stu-id="4e0e1-195">I am going to call it the empty `$null` but it's really a [System.Management.Automation.Internal.AutomationNull][].</span></span> <span data-ttu-id="4e0e1-196">Dieses leere `$null` ist das Ergebnis einer Funktion oder eines Skriptblocks, die/der nichts zurückgibt (ein void-Ergebnis).</span><span class="sxs-lookup"><span data-stu-id="4e0e1-196">This empty `$null` is the one you get as the result of a function or script block that returns nothing (a void result).</span></span>

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

<span data-ttu-id="4e0e1-197">Wenn Sie dies mit `$null` vergleichen, erhalten Sie einen `$null`-Wert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-197">If you compare it with `$null`, you get a `$null` value.</span></span> <span data-ttu-id="4e0e1-198">Bei Verwendung in einer Auswertung, wo ein Wert erforderlich ist, ist der Wert immer `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-198">When used in an evaluation where a value is required, the value is always `$null`.</span></span> <span data-ttu-id="4e0e1-199">Doch bei Platzierung in einem Array wird es wie ein leeres Array behandelt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-199">But if you place it inside an array, it's treated the same as an empty array.</span></span>

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

<span data-ttu-id="4e0e1-200">Sie können über ein Array verfügen, das einen `$null`-Wert enthält und dessen `count` gleich `1` ist.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-200">You can have an array that contains one `$null` value and its `count` is `1`.</span></span> <span data-ttu-id="4e0e1-201">Wenn Sie jedoch ein leeres Ergebnis in einem Array platzieren, wird es nicht als Element gezählt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-201">But if you place an empty result inside an array then it's not counted as an item.</span></span> <span data-ttu-id="4e0e1-202">Die Anzahl ist `0`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-202">The count is `0`.</span></span>

<span data-ttu-id="4e0e1-203">Wenn Sie das leere `$null` wie eine Sammlung behandeln, ist es leer.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-203">If you treat the empty `$null` like a collection, then it's empty.</span></span>

### <a name="pipeline"></a><span data-ttu-id="4e0e1-204">Pipeline</span><span class="sxs-lookup"><span data-stu-id="4e0e1-204">Pipeline</span></span>

<span data-ttu-id="4e0e1-205">Dieser Unterschied wird besonders bei Verwendung der Pipeline deutlich.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-205">The primary place you see the difference is when using the pipeline.</span></span> <span data-ttu-id="4e0e1-206">Sie können einer Pipe einen `$null`-Wert übergeben, aber keinen leeren `$null`-Wert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-206">You can pipe a `$null` value but not an empty `$null` value.</span></span>

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

<span data-ttu-id="4e0e1-207">Abhängig von Ihrem Code sollten Sie `$null` in Ihrer Logik berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-207">Depending on your code, you should account for the `$null` in your logic.</span></span>

<span data-ttu-id="4e0e1-208">Überprüfen Sie in jedem Fall zuerst auf `$null`</span><span class="sxs-lookup"><span data-stu-id="4e0e1-208">Either check for `$null` first</span></span>

- <span data-ttu-id="4e0e1-209">Herausfiltern von NULL in der Pipeline (`... | Where {$null -ne $_} | ...`)</span><span class="sxs-lookup"><span data-stu-id="4e0e1-209">Filter out null on the pipeline (`... | Where {$null -ne $_} | ...`)</span></span>
- <span data-ttu-id="4e0e1-210">Verarbeiten von NULL in der Pipelinefunktion</span><span class="sxs-lookup"><span data-stu-id="4e0e1-210">Handle it in the pipeline function</span></span>

## <a name="foreach"></a><span data-ttu-id="4e0e1-211">foreach</span><span class="sxs-lookup"><span data-stu-id="4e0e1-211">foreach</span></span>

<span data-ttu-id="4e0e1-212">Eines meiner bevorzugten Features von `foreach` ist, dass es keine Aufzählung für eine `$null`-Sammlung ausführt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-212">One of my favorite features of `foreach` is that it doesn't enumerate over a `$null` collection.</span></span>

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

<span data-ttu-id="4e0e1-213">Dies erspart mir die Überprüfung der Sammlung auf `$null`, bevor ich eine Aufzählung für sie ausführe.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-213">This saves me from having to `$null` check the collection before I enumerate it.</span></span> <span data-ttu-id="4e0e1-214">Wenn Sie über eine Sammlung von `$null`-Werten verfügen, kann `$node` weiterhin `$null` sein.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-214">If you have a collection of `$null` values, the `$node` can still be `$null`.</span></span>

<span data-ttu-id="4e0e1-215">„foreach“ funktioniert so seit PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-215">The foreach started working this way with PowerShell 3.0.</span></span> <span data-ttu-id="4e0e1-216">Wenn Sie eine ältere Version haben, ist dies nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-216">If you happen to be on an older version, then this is not the case.</span></span> <span data-ttu-id="4e0e1-217">Dies ist eine der wichtigen Änderungen, die Sie beachten sollten, wenn Sie Code für die 2.0-Kompatibilität zurückportieren.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-217">This is one of the important changes to be aware of when back-porting code for 2.0 compatibility.</span></span>

## <a name="value-types"></a><span data-ttu-id="4e0e1-218">Werttypen</span><span class="sxs-lookup"><span data-stu-id="4e0e1-218">Value types</span></span>

<span data-ttu-id="4e0e1-219">Technisch gesehen können nur Verweistypen `$null` werden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-219">Technically, only reference types can be `$null`.</span></span> <span data-ttu-id="4e0e1-220">PowerShell ist jedoch sehr großzügig und ermöglicht, dass Variablen jeden beliebigen Typ haben können.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-220">But PowerShell is very generous and allows for variables to be any type.</span></span> <span data-ttu-id="4e0e1-221">Wenn Sie jedoch einen Werttyp strikt festlegen, kann er nicht `$null` werden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-221">If you decide to strongly type a value type, it cannot be `$null`.</span></span>
<span data-ttu-id="4e0e1-222">PowerShell konvertiert `$null` für viele Typen in einen Standardwert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-222">PowerShell converts `$null` to a default value for many types.</span></span>

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

<span data-ttu-id="4e0e1-223">Für einige Typen gibt es keine gültige Konvertierung aus `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-223">There are some types that do not have a valid conversion from `$null`.</span></span> <span data-ttu-id="4e0e1-224">Diese Typen generieren eine `Cannot convert null to type`-Fehlermeldung.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-224">These types generate a `Cannot convert null to type` error.</span></span>

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a><span data-ttu-id="4e0e1-225">Funktionsparameter</span><span class="sxs-lookup"><span data-stu-id="4e0e1-225">Function parameters</span></span>

<span data-ttu-id="4e0e1-226">Die Verwendung von Werten mit strikt festgelegtem Typ in Funktionsparametern ist sehr üblich.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-226">Using a strongly typed values in function parameters is very common.</span></span> <span data-ttu-id="4e0e1-227">Im Allgemeinen lernen wir, die Typen unserer Parameter zu definieren, auch wenn wir dazu neigen, die Typen anderer Variablen in unseren Skripts nicht zu definieren.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-227">We generally learn to define the types of our parameters even if we tend not to define the types of other variables in our scripts.</span></span> <span data-ttu-id="4e0e1-228">Möglicherweise verfügen Sie in ihren Funktionen bereits über einige Variablen mit strikt festgelegtem Typ und sind sich dessen nicht einmal bewusst.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-228">You may already have some strongly typed variables in your functions and not even realize it.</span></span>

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

<span data-ttu-id="4e0e1-229">Sobald Sie den Typ des Parameters als `string` festgelegt haben, kann der Wert nie `$null` werden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-229">As soon as you set the type of the parameter as a `string`, the value can never be `$null`.</span></span> <span data-ttu-id="4e0e1-230">Es ist üblich, zu überprüfen, ob ein Wert `$null` ist, um festzustellen, ob der Benutzer einen Wert bereitgestellt hat.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-230">It's common to check if a value is `$null` to see if the user provided a value or not.</span></span>

```powershell
if ( $null -ne $Value ){...}
```

<span data-ttu-id="4e0e1-231">`$Value` ist eine leere Zeichenfolge `''`, wenn kein Wert angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-231">`$Value` is an empty string `''` when no value is provided.</span></span> <span data-ttu-id="4e0e1-232">Verwenden Sie stattdessen die automatische Variable `$PSBoundParameters.Value`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-232">Use the automatic variable `$PSBoundParameters.Value` instead.</span></span>

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

<span data-ttu-id="4e0e1-233">`$PSBoundParameters` enthält nur die Parameter, die beim Aufrufen der Funktion angegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-233">`$PSBoundParameters` only contains the parameters that were specified when the function was called.</span></span>
<span data-ttu-id="4e0e1-234">Sie können auch die `ContainsKey`-Methode verwenden, um die Eigenschaft zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-234">You can also use the `ContainsKey` method to check for the property.</span></span>

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a><span data-ttu-id="4e0e1-235">IsNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="4e0e1-235">IsNotNullOrEmpty</span></span>

<span data-ttu-id="4e0e1-236">Wenn der Wert eine Zeichenfolge ist, können Sie eine statische Zeichenfolgenfunktion verwenden, um zu überprüfen, ob der Wert gleichzeitig `$null` oder eine leere Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-236">If the value is a string, you can use a static string function to check if the value is `$null` or an empty string at the same time.</span></span>

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

<span data-ttu-id="4e0e1-237">Ich verwende dies häufig, wenn ich weiß, dass der Werttyp eine Zeichenfolge sein sollte.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-237">I find myself using this often when I know the value type should be a string.</span></span>

## <a name="when-i-null-check"></a><span data-ttu-id="4e0e1-238">Wann ich auf $null überprüfe</span><span class="sxs-lookup"><span data-stu-id="4e0e1-238">When I $null check</span></span>

<span data-ttu-id="4e0e1-239">Ich bin ein defensiver Skriptschreiber.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-239">I am a defensive scripter.</span></span> <span data-ttu-id="4e0e1-240">Jedes Mal, wenn ich eine Funktion aufrufe und einer Variablen zuweise, überprüfe ich sie auf `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-240">Anytime I call a function and assign it to a variable, I check it for `$null`.</span></span>

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

<span data-ttu-id="4e0e1-241">Ich ziehe es vor, `if` oder `foreach` statt `try/catch` zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-241">I much prefer using `if` or `foreach` over using `try/catch`.</span></span> <span data-ttu-id="4e0e1-242">Verstehen Sie mich nicht falsch, ich verwende `try/catch` noch oft genug.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-242">Don't get me wrong, I still use `try/catch` a lot.</span></span> <span data-ttu-id="4e0e1-243">Wenn ich jedoch auf eine Fehlerbedingung oder einen leeren Ergebnissatz testen kann, kann ich meine Ausnahmebehandlung für echte Ausnahmen reservieren.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-243">But if I can test for an error condition or an empty set of results, I can allow my exception handling be for true exceptions.</span></span>

<span data-ttu-id="4e0e1-244">Außerdem überprüfe ich gern auf `$null`, bevor ich einen Wert indiziere oder Methoden eines Objekts aufrufe.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-244">I also tend to check for `$null` before I index into a value or call methods on an object.</span></span> <span data-ttu-id="4e0e1-245">Diese beiden Aktionen gelingen nicht für ein `$null`-Objekt, darum halte ich es für wichtig, sie zuerst zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-245">These two actions fail for a `$null` object so I find it important to validate them first.</span></span> <span data-ttu-id="4e0e1-246">Diese Szenarios wurden bereits zuvor in diesem Beitrag behandelt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-246">I already covered those scenarios earlier in this post.</span></span>

### <a name="no-results-scenario"></a><span data-ttu-id="4e0e1-247">„Keine Ergebnisse“-Szenario</span><span class="sxs-lookup"><span data-stu-id="4e0e1-247">No results scenario</span></span>

<span data-ttu-id="4e0e1-248">Es ist wichtig zu wissen, dass unterschiedliche Funktionen und Befehle das „Keine Ergebnisse“-Szenario unterschiedlich behandeln.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-248">It's important to know that different functions and commands handle the no results scenario differently.</span></span> <span data-ttu-id="4e0e1-249">Viele PowerShell-Befehle geben das leere `$null` und eine Fehlermeldung im Fehlerdatenstrom zurück.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-249">Many PowerShell commands return the empty `$null` and an error in the error stream.</span></span> <span data-ttu-id="4e0e1-250">Aber andere lösen Ausnahmen aus oder geben ein Statusobjekt zurück.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-250">But others throw exceptions or give you a status object.</span></span> <span data-ttu-id="4e0e1-251">Sie müssen immer noch entscheiden, wie die Befehle, die Sie verwenden, mit den „Keine Ergebnisse“- und Fehlerszenarios umgehen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-251">It's still up to you to know how the commands you use deal with the no results and error scenarios.</span></span>

## <a name="initializing-to-null"></a><span data-ttu-id="4e0e1-252">Initialisieren mit $null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-252">Initializing to $null</span></span>

<span data-ttu-id="4e0e1-253">Eine Gewohnheit, die ich übernommen habe, ist die Initialisierung aller Variablen vor der Verwendung.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-253">One habit that I have picked up is initializing all my variables before I use them.</span></span> <span data-ttu-id="4e0e1-254">Sie müssen dies in anderen Sprachen auch tun.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-254">You are required to do this in other languages.</span></span> <span data-ttu-id="4e0e1-255">Am Anfang meiner Funktion oder während der Eingabe einer foreach-Schleife definiere ich alle Werte, die ich verwende.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-255">At the top of my function or as I enter a foreach loop, I define all the values that I'm using.</span></span>

<span data-ttu-id="4e0e1-256">Bitte sehen Sie sich das Szenario im Folgenden genau an.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-256">Here is a scenario that I want you to take a close look at.</span></span> <span data-ttu-id="4e0e1-257">Es ist ein Beispiel für einen Fehler, den ich nachverfolgen musste.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-257">It's an example of a bug I had to chase down before.</span></span>

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

<span data-ttu-id="4e0e1-258">Hier wird erwartet, dass `Get-Something` entweder ein Ergebnis oder ein leeres `$null` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-258">The expectation here is that `Get-Something` returns either a result or an empty `$null`.</span></span> <span data-ttu-id="4e0e1-259">Wenn ein Fehler auftritt, wird er protokolliert.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-259">If there is an error, we log it.</span></span> <span data-ttu-id="4e0e1-260">Dann überprüfen wir das Ergebnis vor der Verarbeitung auf Gültigkeit.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-260">Then we check to make sure we got a valid result before processing it.</span></span>

<span data-ttu-id="4e0e1-261">Der in diesem Code versteckte Fehler tritt auf, wenn `Get-Something` eine Ausnahme auslöst und `$result` keinen Wert zuweist.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-261">The bug hiding in this code is when `Get-Something` throws an exception and doesn't assign a value to `$result`.</span></span> <span data-ttu-id="4e0e1-262">Der Fehler tritt vor der Zuweisung auf, sodass wir nicht einmal `$null` der `$result`-Variablen zuweisen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-262">It fails before the assignment so we don't even assign `$null` to the `$result` variable.</span></span> <span data-ttu-id="4e0e1-263">`$result` enthält weiterhin den vorher gültigen `$result`-Wert aus anderen Iterationen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-263">`$result` still contains the previous valid `$result` from other iterations.</span></span>
<span data-ttu-id="4e0e1-264">`Update-Something` wird in diesem Beispiel mehrfach für das gleiche Objekt ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-264">`Update-Something` to execute multiple times on the same object in this example.</span></span>

<span data-ttu-id="4e0e1-265">Ich lege `$result` direkt innerhalb der foreach-Schleife auf `$null` fest, bevor ich es verwende, um dieses Problem zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-265">I set `$result` to `$null` right inside the foreach loop before I use it to mitigate this issue.</span></span>

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a><span data-ttu-id="4e0e1-266">Bereichsprobleme</span><span class="sxs-lookup"><span data-stu-id="4e0e1-266">Scope issues</span></span>

<span data-ttu-id="4e0e1-267">Dies trägt auch dazu bei, Bereichsprobleme zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-267">This also helps mitigate scoping issues.</span></span> <span data-ttu-id="4e0e1-268">In diesem Beispiel weisen wir `$result` in einer Schleife immer wieder Werte zu.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-268">In that example, we assign values to `$result` over and over in a loop.</span></span> <span data-ttu-id="4e0e1-269">Da PowerShell jedoch zulässt, dass Variablenwerte von außerhalb der Funktion in den Gültigkeitsbereich der aktuellen Funktion aufgenommen werden, werden durch ihre Initialisierung innerhalb Ihrer Funktion Fehler vermieden, die auf diese Weise eingeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-269">But because PowerShell allows variable values from outside the function to bleed into the scope of the current function, initializing them inside your function mitigates bugs that can be introduced that way.</span></span>

<span data-ttu-id="4e0e1-270">Eine nicht initialisierte Variable in der Funktion ist nicht `$null`, wenn für sie in einem übergeordneten Bereich ein Wert festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-270">An uninitialized variable in your function is not `$null` if it's set to a value in a parent scope.</span></span>
<span data-ttu-id="4e0e1-271">Der übergeordnete Bereich könnte eine andere Funktion sein, die ihre Funktion aufruft und die gleichen Variablennamen verwendet.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-271">The parent scope could be another function that calls your function and uses the same variable names.</span></span>

<span data-ttu-id="4e0e1-272">Wenn ich in demselben `Do-something` Beispiel die Schleife entferne, würde es folgendem Beispiel ähneln:</span><span class="sxs-lookup"><span data-stu-id="4e0e1-272">If I take that same `Do-something` example and remove the loop, I would end up with something that looks like this example:</span></span>

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

<span data-ttu-id="4e0e1-273">Wenn der Aufruf von `Get-Something` eine Ausnahme auslöst, findet meine `$null`-Prüfung das `$result` aus `Invoke-Something`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-273">If the call to `Get-Something` throws an exception, then my `$null` check finds the `$result` from `Invoke-Something`.</span></span> <span data-ttu-id="4e0e1-274">Wenn Sie den Wert in ihrer Funktion initialisieren, wird dieses Problem vermieden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-274">Initializing the value inside your function mitigates this issue.</span></span>

<span data-ttu-id="4e0e1-275">Die Benennung von Variablen ist schwierig, und es ist üblich, dass ein Autor dieselben Variablennamen in mehreren Funktionen verwendet.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-275">Naming variables is hard and it's common for an author to use the same variable names in multiple functions.</span></span> <span data-ttu-id="4e0e1-276">Ich weiß, dass ich `$node`, `$result`, `$data` immer wieder verwende.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-276">I know I use `$node`,`$result`,`$data` all the time.</span></span> <span data-ttu-id="4e0e1-277">Daher ist das Risiko groß, dass Werte aus unterschiedlichen Bereichen dort auftauchen, wo sie nichts zu suchen haben.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-277">So it would be very easy for values from different scopes to show up in places where they should not be.</span></span>

## <a name="redirect-output-to-null"></a><span data-ttu-id="4e0e1-278">Umleiten der Ausgabe zu $null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-278">Redirect output to $null</span></span>

<span data-ttu-id="4e0e1-279">Ich habe im gesamten Artikel über `$null`-Werte gesprochen, aber das Thema ist nicht vollständig, wenn ich nicht das Umleiten der Ausgabe zu `$null` erwähne.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-279">I have been talking about `$null` values for this entire article but the topic is not complete if I didn't mention redirecting output to `$null`.</span></span> <span data-ttu-id="4e0e1-280">Manchmal geben Befehle Informationen oder Objekte aus, die Sie unterdrücken möchten.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-280">There are times when you have commands that output information or objects that you want to suppress.</span></span> <span data-ttu-id="4e0e1-281">Hierzu können Sie die Ausgabe zu `$null` umleiten.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-281">Redirecting output to `$null` does that.</span></span>

### <a name="out-null"></a><span data-ttu-id="4e0e1-282">Out-Null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-282">Out-Null</span></span>

<span data-ttu-id="4e0e1-283">Der Befehl „Out-Null“ ist die integrierte Möglichkeit zum Umleiten von Pipelinedaten an `$null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-283">The Out-Null command is the built-in way to redirect pipeline data to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a><span data-ttu-id="4e0e1-284">Zuweisen zu $null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-284">Assign to $null</span></span>

<span data-ttu-id="4e0e1-285">Sie können die Ergebnisse eines Befehls `$null` zuweisen, anstatt `Out-Null` zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-285">You can assign the results of a command to `$null` for the same effect as using `Out-Null`.</span></span>

```powershell
$null = New-Item -Type Directory -Path $path
```

<span data-ttu-id="4e0e1-286">Da `$null` ein konstanter Wert ist, können Sie ihn nie überschreiben.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-286">Because `$null` is a constant value, you can never overwrite it.</span></span> <span data-ttu-id="4e0e1-287">Es gefällt mir in meinem Code nicht so recht, ist aber häufig schneller als `Out-Null`.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-287">I don't like the way it looks in my code but it often performs faster than `Out-Null`.</span></span>

### <a name="redirect-to-null"></a><span data-ttu-id="4e0e1-288">Umleiten zu $null</span><span class="sxs-lookup"><span data-stu-id="4e0e1-288">Redirect to $null</span></span>

<span data-ttu-id="4e0e1-289">Sie können auch den Umleitungsoperator verwenden, um die Ausgabe an `$null` zu senden.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-289">You can also use the redirection operator to send output to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path > $null
```

<span data-ttu-id="4e0e1-290">Wenn Sie mit in der Befehlszeile ausführbaren Dateien arbeiten, die in unterschiedlichen Datenströmen ausgeben.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-290">If you're dealing with command-line executables that output on the different streams.</span></span> <span data-ttu-id="4e0e1-291">Sie können alle Ausgabedatenströme wie folgt zu `$null` umleiten:</span><span class="sxs-lookup"><span data-stu-id="4e0e1-291">You can redirect all output streams to `$null` like this:</span></span>

```powershell
git status *> $null
```

## <a name="summary"></a><span data-ttu-id="4e0e1-292">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="4e0e1-292">Summary</span></span>

<span data-ttu-id="4e0e1-293">Ich habe in diesem Artikel vieles angeschnitten und weiß, dass dieser Artikel fragmentierter ist als die meisten meiner eingehenden Abhandlungen.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-293">I covered a lot of ground on this one and I know this article is more fragmented than most of my deep dives.</span></span> <span data-ttu-id="4e0e1-294">Der Grund hierfür ist, dass `$null`-Werte an vielen verschiedenen Stellen in PowerShell auftauchen können, und alle Nuancen sind spezifisch für die Positionen, an denen sie auftreten.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-294">That is because `$null` values can pop up in many different places in PowerShell and all the nuances are specific to where you find it.</span></span> <span data-ttu-id="4e0e1-295">Ich hoffe, dass Sie Ihre Kenntnisse über `$null` erweitern konnten und sich der obskureren Szenarios bewusst sind, in die Sie hineingeraten könnten.</span><span class="sxs-lookup"><span data-stu-id="4e0e1-295">I hope you walk away from this with a better understanding of `$null` and an awareness of the more obscure scenarios you may run into.</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Guter Beitrag]: https://blog.iisreset.me/schrodingers-argumentlist
[good post]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
