---
title: Flusssteuerung
description: PowerShell bietet Methoden zum Erstellen von Schleifen, zum Treffen von Entscheidungen und zur logischen Steuerung des Codeflusses in Skripts.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84437991"
---
# <a name="chapter-6---flow-control"></a><span data-ttu-id="cb5e2-103">Kapitel 6: Flusssteuerung</span><span class="sxs-lookup"><span data-stu-id="cb5e2-103">Chapter 6 - Flow control</span></span>

## <a name="scripting"></a><span data-ttu-id="cb5e2-104">Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="cb5e2-104">Scripting</span></span>

<span data-ttu-id="cb5e2-105">Wenn Sie nicht mehr nur noch PowerShell-Einzeiler, sondern ganze Skripts schreiben sollen, klingt dies erst einmal wesentlich komplizierter, als es tatsächlich ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-105">When you move from writing PowerShell one-liners to writing scripts, it sounds a lot more complicated than it really is.</span></span> <span data-ttu-id="cb5e2-106">Ein Skript besteht aus denselben oder ähnlichen Befehlen, die Sie sonst interaktiv in der PowerShell-Konsole ausführen würden, außer dass diese jetzt als `.PS1`-Datei gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-106">A script is nothing more than the same or similar commands that you would run interactively in the PowerShell console, except they're saved as a `.PS1` file.</span></span> <span data-ttu-id="cb5e2-107">Es gibt einige Skriptkonstrukte, die Sie verwenden können, z. B. eine `foreach`-Schleife anstelle des Cmdlets `ForEach-Object`.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-107">There are some scripting constructs that you may use such as a `foreach` loop instead of the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="cb5e2-108">Für Einsteiger können die Unterschiede verwirrend sein, besonders wenn Sie bedenken, dass `foreach` sowohl ein Skriptkonstrukt als auch ein Alias für das Cmdlet `ForEach-Object` ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-108">To beginners, the differences can be confusing especially when you consider that `foreach` is both a scripting construct and an alias for the `ForEach-Object` cmdlet.</span></span>

## <a name="looping"></a><span data-ttu-id="cb5e2-109">Schleifen</span><span class="sxs-lookup"><span data-stu-id="cb5e2-109">Looping</span></span>

<span data-ttu-id="cb5e2-110">Eine der großartigen Eigenschaften von PowerShell ist, dass es, sobald Sie herausgefunden haben, wie Sie etwas mit einem Element machen, fast genauso einfach ist, dieselbe Aufgabe für Hunderte von Elementen auszuführen.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-110">One of the great things about PowerShell is, once you figure out how to do something for one item, it's almost as easy to do the same task for hundreds of items.</span></span> <span data-ttu-id="cb5e2-111">Durchlaufen Sie die Elemente einfach in einer Schleife, indem Sie eine der zahlreichen verschiedenen Arten von Schleifen in PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-111">Simply loop through the items using one of the many different types of loops in PowerShell.</span></span>

### <a name="foreach-object"></a><span data-ttu-id="cb5e2-112">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="cb5e2-112">ForEach-Object</span></span>

<span data-ttu-id="cb5e2-113">`ForEach-Object` ist ein Cmdlet zum Durchlaufen von Elementen in einer Pipeline, wie mit PowerShell-Einzeilern.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-113">`ForEach-Object` is a cmdlet for iterating through items in a pipeline such as with PowerShell one-liners.</span></span> <span data-ttu-id="cb5e2-114">`ForEach-Object` streamt die Objekte durch die Pipeline.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-114">`ForEach-Object` streams the objects through the pipeline.</span></span>

<span data-ttu-id="cb5e2-115">Obwohl der Parameter **Module** von `Get-Command` mehrere Werte akzeptiert, die Zeichenfolgen sind, akzeptiert er sie nur über die Pipelineeingabe mittels Eigenschaftsname oder über Parametereingaben.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-115">Although the **Module** parameter of `Get-Command` accepts multiple values that are strings, it only accepts them via pipeline input by property name or via parameter input.</span></span> <span data-ttu-id="cb5e2-116">Wenn Sie im folgenden Szenario zwei Zeichenfolgen als Wert an `Get-Command` übergeben möchten, um sie mit dem Parameter **Module** zu verwenden, müssten Sie das Cmdlet `ForEach-Object` verwenden.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-116">In the following scenario, if I want to pipe two strings by value to `Get-Command` for use with the **Module** parameter, I would need to use the `ForEach-Object` cmdlet.</span></span>

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

<span data-ttu-id="cb5e2-117">Im vorherigen Beispiel ist das aktuelle Objekt `$_`.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-117">In the previous example, `$_` is the current object.</span></span> <span data-ttu-id="cb5e2-118">Ab PowerShell-Version 3.0 kann anstelle von `$_` `$PSItem` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-118">Beginning with PowerShell version 3.0, `$PSItem` can be used instead of `$_`.</span></span> <span data-ttu-id="cb5e2-119">Ich bin aber der Meinung, dass die meisten erfahrenen PowerShell-Benutzer immer noch lieber `$_` verwenden, weil es abwärtskompatibel und weniger einzugeben ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-119">But I find that most experienced PowerShell users still prefer using `$_` since it's backward compatible and less to type.</span></span>

<span data-ttu-id="cb5e2-120">Wenn Sie das Schlüsselwort `foreach` verwenden, müssen Sie zuerst alle Elemente im Arbeitsspeicher speichern, bevor Sie diese durchlaufen, was sich schwierig gestalten kann, wenn Sie nicht wissen, mit wie vielen Elementen Sie arbeiten.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-120">When using the `foreach` keyword, you must store all of the items in memory before iterating through them, which could be difficult if you don't know how many items you're working with.</span></span>

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="cb5e2-121">Häufig ist eine Schleife wie `foreach` oder `ForEach-Object` erforderlich.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-121">Many times a loop such as `foreach` or `ForEach-Object` is necessary.</span></span> <span data-ttu-id="cb5e2-122">Andernfalls erhalten Sie eine Fehlermeldung.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-122">Otherwise you'll receive an error message.</span></span>

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

<span data-ttu-id="cb5e2-123">In anderen Fällen können sie dieselben Ergebnisse erzielen und gleichzeitig die Schleife vollständig beseitigen.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-123">Other times, you can get the same results while eliminating the loop altogether.</span></span> <span data-ttu-id="cb5e2-124">Sehen Sie in der Cmdlet-Hilfe nach, um Ihre Optionen herauszufinden.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-124">Consult the cmdlet help to understand your options.</span></span>

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="cb5e2-125">Wie Sie in den vorherigen Beispielen sehen können, akzeptiert der Parameter **Identity** für `Get-ADComputer` nur einen einzelnen Wert, wenn er über die Parametereingabe bereitgestellt wird, lässt aber mehrere Elemente zu, wenn die Eingabe über eine Pipelineeingabe bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-125">As you can see in the previous examples, the **Identity** parameter for `Get-ADComputer` only accepts a single value when provided via parameter input, but it allows for multiple items when the input is provided via pipeline input.</span></span>

### <a name="for"></a><span data-ttu-id="cb5e2-126">Für</span><span class="sxs-lookup"><span data-stu-id="cb5e2-126">For</span></span>

<span data-ttu-id="cb5e2-127">Eine `for`-Schleife wird durchlaufen, während eine bestimmte Bedingung erfüllt (true) ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-127">A `for` loop iterates while a specified condition is true.</span></span> <span data-ttu-id="cb5e2-128">Die `for`-Schleife verwende ich nicht häufig, aber sie hat ihre Berechtigung.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-128">The `for` loop is not something that I use often, but it does have its uses.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

<span data-ttu-id="cb5e2-129">Im vorherigen Beispiel wird die Schleife viermal durchlaufen, beginnend mit der Zahl 1, und wird fortgesetzt, solange die Zählervariable `$i` kleiner als 5 ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-129">In the previous example, the loop will iterate four times by starting off with the number one and continue as long as the counter variable `$i` is less than 5.</span></span> <span data-ttu-id="cb5e2-130">Sie setzt für insgesamt 10 Sekunden aus.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-130">It will sleep for a total of 10 seconds.</span></span>

### <a name="do"></a><span data-ttu-id="cb5e2-131">Sie sollten</span><span class="sxs-lookup"><span data-stu-id="cb5e2-131">Do</span></span>

<span data-ttu-id="cb5e2-132">Es gibt zwei verschiedene `do`-Schleifen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-132">There are two different `do` loops in PowerShell.</span></span> <span data-ttu-id="cb5e2-133">`Do Until` wird ausgeführt, während die angegebene Bedingung nicht erfüllt (false) ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-133">`Do Until` runs while the specified condition is false.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

<span data-ttu-id="cb5e2-134">Das vorherige Beispiel ist ein Zahlenspiel, das solange fortgesetzt wird, bis der von Ihnen geschätzte Wert mit der Zahl übereinstimmt, die das Cmdlet `Get-Random` generiert hat.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-134">The previous example is a numbers game that continues until the value you guess equals the same number that the `Get-Random` cmdlet generated.</span></span>

<span data-ttu-id="cb5e2-135">`Do While` ist genau das Gegenteil.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-135">`Do While` is just the opposite.</span></span> <span data-ttu-id="cb5e2-136">Sie wird ausgeführt, solange die angegebene Bedingung als „true“ ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-136">It runs as long as the specified condition evaluates to true.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

<span data-ttu-id="cb5e2-137">Dieselben Ergebnisse werden mit einer `Do While`-Schleife erzielt, indem die Testbedingung in „ungleich“ umgekehrt wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-137">The same results are achieved with a `Do While` loop by reversing the test condition to not equals.</span></span>

<span data-ttu-id="cb5e2-138">`Do`-Schleifen werden immer mindestens einmal ausgeführt, weil die Bedingung am Ende der Schleife ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-138">`Do` loops always run at least once because the condition is evaluated at the end of the loop.</span></span>

### <a name="while"></a><span data-ttu-id="cb5e2-139">While</span><span class="sxs-lookup"><span data-stu-id="cb5e2-139">While</span></span>

<span data-ttu-id="cb5e2-140">Ähnlich wie bei der `Do While`-Schleife, wird eine `While`-Schleife ausgeführt, solange die angegebene Bedingung erfüllt (true) ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-140">Similar to the `Do While` loop, a `While` loop runs as long as the specified condition is true.</span></span> <span data-ttu-id="cb5e2-141">Der Unterschied besteht jedoch darin, dass eine `While`-Schleife die Bedingung am Anfang der Schleife auswertet, bevor überhaupt Code ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-141">The difference however, is that a `While` loop evaluates the condition at the top of the loop before any code is run.</span></span> <span data-ttu-id="cb5e2-142">Somit wird sie gar nicht ausgeführt, wenn die Bedingung als „false“ ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-142">So it doesn't run if the condition evaluates to false.</span></span>

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

<span data-ttu-id="cb5e2-143">Im vorherigen Beispiel wird berechnet, an welchem Tag in den USA „Thanksgiving“ (Erntedankfest) ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-143">The previous example calculates what day Thanksgiving Day is on in the United States.</span></span> <span data-ttu-id="cb5e2-144">Dies ist immer am vierten Donnerstag im November.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-144">It's always on the fourth Thursday of November.</span></span> <span data-ttu-id="cb5e2-145">Die Schleife beginnt also mit dem 22. Tag im November und fügt einen Tag hinzu, solange der Wochentag nicht gleich Donnerstag ist.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-145">So the loop starts with the 22nd day of November and adds a day while the day of the week isn't equal to Thursday.</span></span> <span data-ttu-id="cb5e2-146">Wenn der 22. ein Donnerstag ist, wird die Schleife überhaupt nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-146">If the 22nd is a Thursday, the loop doesn't run at all.</span></span>

## <a name="break-continue-and-return"></a><span data-ttu-id="cb5e2-147">Break, Continue und Return</span><span class="sxs-lookup"><span data-stu-id="cb5e2-147">Break, Continue, and Return</span></span>

<span data-ttu-id="cb5e2-148">`Break` dient dem Unterbrechen einer Schleife.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-148">`Break` is designed to break out of a loop.</span></span> <span data-ttu-id="cb5e2-149">Es wird auch häufig mit der `switch`-Anweisung verwendet.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-149">It's also commonly used with the `switch` statement.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

<span data-ttu-id="cb5e2-150">Die im vorherigen Beispiel gezeigte `break`-Anweisung bewirkt, dass die Schleife bei der ersten Iterationen beendet wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-150">The `break` statement shown in the previous example causes the loop to exit on the first iteration.</span></span>

<span data-ttu-id="cb5e2-151">„Continue“ ist so konzipiert, dass zur nächsten Iteration einer Schleife gesprungen wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-151">Continue is designed to skip to the next iteration of a loop.</span></span>

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

<span data-ttu-id="cb5e2-152">Das vorherige Beispiel gibt die Zahlen 1, 2, 4 und 5 aus.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-152">The previous example will output the numbers 1, 2, 4, and 5.</span></span> <span data-ttu-id="cb5e2-153">Es überspringt die Zahl 3 und fährt mit der nächsten Iteration der Schleife fort.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-153">It skips number 3 and continues with the next iteration of the loop.</span></span> <span data-ttu-id="cb5e2-154">Ähnlich wie bei `break`, unterbricht `continue` die Schleife, wenn auch nur für die aktuelle Iteration.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-154">Similar to `break`, `continue` breaks out of the loop except only for the current iteration.</span></span> <span data-ttu-id="cb5e2-155">Die Ausführung wird mit der nächsten Iteration fortgesetzt, anstatt die Schleife zu unterbrechen und zu beenden.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-155">Execution continues with the next iteration instead of breaking out of the loop and stopping.</span></span>

<span data-ttu-id="cb5e2-156">„Return“ ist so konzipiert, dass der vorhandene Bereich verlassen wird.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-156">Return is designed to exit out of the existing scope.</span></span>

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

<span data-ttu-id="cb5e2-157">Beachten Sie, dass im vorherigen Beispiel „return“ das erste Ergebnis ausgibt und dann die Schleife beendet.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-157">Notice that in the previous example, return outputs the first result and then exists out of the loop.</span></span> <span data-ttu-id="cb5e2-158">Eine gründlichere Erklärung der result-Anweisung finden Sie in einem meiner Blogartikel: [„Das PowerShell-Schlüsselwort ‚return‘“][].</span><span class="sxs-lookup"><span data-stu-id="cb5e2-158">A more thorough explanation of the result statement can be found in one of my blog articles: ["The PowerShell return keyword"][].</span></span>

## <a name="summary"></a><span data-ttu-id="cb5e2-159">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="cb5e2-159">Summary</span></span>

<span data-ttu-id="cb5e2-160">In diesem Kapitel haben Sie die verschiedenen Arten von Schleifen kennengelernt, die in PowerShell vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="cb5e2-160">In this chapter, you've learned about the different types of loops that exist in PowerShell.</span></span>

## <a name="review"></a><span data-ttu-id="cb5e2-161">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="cb5e2-161">Review</span></span>

1. <span data-ttu-id="cb5e2-162">Worin besteht der Unterschied zwischen dem `ForEach-Object`-Cmdlet und dem foreach-Skriptkonstrukt?</span><span class="sxs-lookup"><span data-stu-id="cb5e2-162">What is the difference in the `ForEach-Object` cmdlet and the foreach scripting construct?</span></span>
1. <span data-ttu-id="cb5e2-163">Worin besteht der primäre Vorteil bei der Verwendung einer While-Schleife anstelle einer „Do While“- oder „Do Until“-Schleife?</span><span class="sxs-lookup"><span data-stu-id="cb5e2-163">What is the primary advantage of using a While loop instead of a Do While or Do Until loop.</span></span>
1. <span data-ttu-id="cb5e2-164">Worin unterscheiden sich break- und continue-Anweisungen?</span><span class="sxs-lookup"><span data-stu-id="cb5e2-164">How do the break and continue statements differ?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="cb5e2-165">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="cb5e2-165">Recommended Reading</span></span>

- <span data-ttu-id="cb5e2-166">[ForEach-Object][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-166">[ForEach-Object][]</span></span>
- <span data-ttu-id="cb5e2-167">[about_ForEach][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-167">[about_ForEach][]</span></span>
- <span data-ttu-id="cb5e2-168">[about_For][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-168">[about_For][]</span></span>
- <span data-ttu-id="cb5e2-169">[about_Do][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-169">[about_Do][]</span></span>
- <span data-ttu-id="cb5e2-170">[about_While][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-170">[about_While][]</span></span>
- <span data-ttu-id="cb5e2-171">[about_Break][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-171">[about_Break][]</span></span>
- <span data-ttu-id="cb5e2-172">[about_Continue][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-172">[about_Continue][]</span></span>
- <span data-ttu-id="cb5e2-173">[about_Return][]</span><span class="sxs-lookup"><span data-stu-id="cb5e2-173">[about_Return][]</span></span>

<!-- link references -->
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
[„Das PowerShell-Schlüsselwort ‚return‘“]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
["The PowerShell return keyword"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
