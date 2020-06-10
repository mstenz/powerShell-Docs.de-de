---
title: Alles, was Sie schon immer über Arrays wissen wollten
description: Arrays sind ein grundlegendes Sprachfeature der meisten Programmiersprachen.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 5cab354a99b122401f8f8119de24e075cf9d21f8
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149603"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a><span data-ttu-id="7c40b-103">Alles, was Sie schon immer über Arrays wissen wollten</span><span class="sxs-lookup"><span data-stu-id="7c40b-103">Everything you wanted to know about arrays</span></span>

<span data-ttu-id="7c40b-104">[Arrays][] sind ein grundlegendes Sprachfeature der meisten Programmiersprachen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-104">[Arrays][] are a fundamental language feature of most programming languages.</span></span> <span data-ttu-id="7c40b-105">Es handelt sich um eine Auflistung aus Werten oder Objekten, um die Sie kaum herumkommen werden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-105">They're a collection of values or objects that are difficult to avoid.</span></span> <span data-ttu-id="7c40b-106">Sehen wir uns also Arrays und ihre Möglichkeiten einmal genauer an.</span><span class="sxs-lookup"><span data-stu-id="7c40b-106">Let's take a close look at arrays and everything they have to offer.</span></span>

> [!NOTE]
> <span data-ttu-id="7c40b-107">Die [Originalversion][] dieses Artikels wurde im Blog von [@KevinMarquette][] veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="7c40b-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="7c40b-108">Das PowerShell-Team dankt Kevin, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="7c40b-109">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="7c40b-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="7c40b-110">Was ist ein Array?</span><span class="sxs-lookup"><span data-stu-id="7c40b-110">What is an array?</span></span>

<span data-ttu-id="7c40b-111">Ich beginne mit einer grundlegenden technischen Beschreibung von Arrays und ihrer Verwendung in den meisten Programmiersprachen. Danach werde ich die weiteren Möglichkeiten der Verwendung in PowerShell vorstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-111">I'm going to start with a basic technical description of what arrays are and how they are used by most programming languages before I shift into the other ways PowerShell makes use of them.</span></span>

<span data-ttu-id="7c40b-112">Ein Array ist eine Datenstruktur, die als Auflistung mehrerer Elemente dient.</span><span class="sxs-lookup"><span data-stu-id="7c40b-112">An array is a data structure that serves as a collection of multiple items.</span></span> <span data-ttu-id="7c40b-113">Sie können ein Array durchlaufen oder über einen Index auf einzelne Elemente zugreifen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-113">You can iterate over the array or access individual items using an index.</span></span> <span data-ttu-id="7c40b-114">Ein Array wird als sequenzieller Arbeitsspeicherblock erstellt, in dem die einzelnen Werte direkt nebeneinander gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="7c40b-114">The array is created as a sequential chunk of memory where each value is stored right next to the other.</span></span>

<span data-ttu-id="7c40b-115">Ich werde im Verlauf dieses Artikels auf die Details eingehen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-115">I'll touch on each of those details as we go.</span></span>

## <a name="basic-usage"></a><span data-ttu-id="7c40b-116">Grundlegende Verwendung</span><span class="sxs-lookup"><span data-stu-id="7c40b-116">Basic usage</span></span>

<span data-ttu-id="7c40b-117">Da Arrays ein so grundlegendes Feature von PowerShell sind, gibt es eine einfache Syntax für die Arbeit mit Arrays in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7c40b-117">Because arrays are such a basic feature of PowerShell, there is a simple syntax for working with them in PowerShell.</span></span>

### <a name="create-an-array"></a><span data-ttu-id="7c40b-118">Erstellen eines Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-118">Create an array</span></span>

<span data-ttu-id="7c40b-119">Ein leeres Array lässt sich mit `@()` erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-119">An empty array can be created by using `@()`</span></span>

```powershell
PS> $data = @()
PS> $data.count
0
```

<span data-ttu-id="7c40b-120">Wir können ein Array erstellen und mit Werten füllen, indem wir diese einfach in die runden Klammern `@()` einfügen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-120">We can create an array and seed it with values just by placing them in the `@()` parentheses.</span></span>

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

<span data-ttu-id="7c40b-121">Dieses Array besteht aus vier Elementen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-121">This array has 4 items.</span></span> <span data-ttu-id="7c40b-122">Wenn wir die Variable `$data` aufrufen, wird die Liste der Elemente angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-122">When we call the `$data` variable, we see the list of our items.</span></span> <span data-ttu-id="7c40b-123">Bei einem Zeichenfolgenarray erhalten wir eine Zeile pro Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="7c40b-123">If it's an array of strings, then we get one line per string.</span></span>

<span data-ttu-id="7c40b-124">Wir können ein Array auf mehreren Zeilen deklarieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-124">We can declare an array on multiple lines.</span></span> <span data-ttu-id="7c40b-125">Das Komma ist in diesem Fall optional und wird in der Regel weggelassen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-125">The comma is optional in this case and generally left out.</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

<span data-ttu-id="7c40b-126">Ich deklariere meine Arrays lieber so auf mehreren Zeilen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-126">I prefer to declare my arrays on multiple lines like that.</span></span> <span data-ttu-id="7c40b-127">Das vereinfacht nicht nur bei mehreren Elementen das Lesen des Arrays, Sie können Ihre Arrays auch einfacher mit vorherigen Versionen vergleichen, wenn Sie die Quellcodeverwaltung verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-127">Not only does it get easier to read when you have multiple items, it also makes it easier to compare to previous versions when using source control.</span></span>

#### <a name="other-syntax"></a><span data-ttu-id="7c40b-128">Eine andere Syntax</span><span class="sxs-lookup"><span data-stu-id="7c40b-128">Other syntax</span></span>

<span data-ttu-id="7c40b-129">Im Allgemeinen wird `@()` als Syntax zum Erstellen eines Arrays verwendet, aber durch Trennzeichen getrennte Listen funktionieren meistens auch.</span><span class="sxs-lookup"><span data-stu-id="7c40b-129">It's commonly understood that `@()` is the syntax for creating an array, but comma-separated lists work most of the time.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a><span data-ttu-id="7c40b-130">Write-Output zum Erstellen von Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-130">Write-Output to create arrays</span></span>

<span data-ttu-id="7c40b-131">Ein netter kleiner Trick, den ich nicht unerwähnt lassen möchte: Sie können `Write-Output` verwenden, um schnell Zeichenfolgen an der Konsole zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-131">One cool little trick worth mentioning is that you can use `Write-Output` to quickly create strings at the console.</span></span>

```powershell
$data = Write-Output Zero One Two Three
```

<span data-ttu-id="7c40b-132">Das ist wirklich praktisch, denn Sie müssen keine Anführungszeichen um die Zeichenfolgen setzen, wenn der Parameter Zeichenfolgen akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="7c40b-132">This is handy because you don't have to put quotes around the strings when the parameter accepts strings.</span></span> <span data-ttu-id="7c40b-133">In einem Skript würde ich nie so vorgehen, aber an der Konsole – kein Problem.</span><span class="sxs-lookup"><span data-stu-id="7c40b-133">I would never do this in a script but it's fair game in the console.</span></span>

### <a name="accessing-items"></a><span data-ttu-id="7c40b-134">Zugreifen auf Elemente</span><span class="sxs-lookup"><span data-stu-id="7c40b-134">Accessing items</span></span>

<span data-ttu-id="7c40b-135">Nachdem Sie jetzt über ein Array mit Elementen verfügen, möchten Sie sicher darauf zugreifen und diese Elemente aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-135">Now that you have an array with items in it, you may want to access and update those items.</span></span>

#### <a name="offset"></a><span data-ttu-id="7c40b-136">Offset</span><span class="sxs-lookup"><span data-stu-id="7c40b-136">Offset</span></span>

<span data-ttu-id="7c40b-137">Um auf einzelne Elemente zuzugreifen, verwenden wir die eckigen Klammern `[]` mit einem Offsetwert, der bei 0 beginnt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-137">To access individual items, we use the brackets `[]` with an offset value starting at 0.</span></span> <span data-ttu-id="7c40b-138">So rufen wir das erste Element im Array ab:</span><span class="sxs-lookup"><span data-stu-id="7c40b-138">This is how we get the first item in our array:</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

<span data-ttu-id="7c40b-139">Wir verwenden hier 0, weil das erste Element am Anfang der Liste steht, wir also einen Offset von 0 Elementen benötigen, um zu diesem Element zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-139">The reason why we use zero here is because the first item is at the beginning of the list so we use an offset of 0 items to get to it.</span></span> <span data-ttu-id="7c40b-140">Um zum zweiten Element zu gelangen, müssen wir einen Offset von 1 verwenden, um das erste Element zu überspringen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-140">To get to the second item, we would need to use an offset of 1 to skip the first item.</span></span>

```powershell
PS> $data[1]
One
```

<span data-ttu-id="7c40b-141">Das bedeutet, dass sich das letzte Element am Offsetwert 3 befindet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-141">This would mean that the last item is at offset 3.</span></span>

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a><span data-ttu-id="7c40b-142">Index</span><span class="sxs-lookup"><span data-stu-id="7c40b-142">Index</span></span>

<span data-ttu-id="7c40b-143">Jetzt sehen Sie, warum ich für dieses Beispiel diese Werte ausgewählt habe.</span><span class="sxs-lookup"><span data-stu-id="7c40b-143">Now you can see why I picked the values that I did for this example.</span></span> <span data-ttu-id="7c40b-144">Ich habe das Konzept als „Offset“ vorgestellt, weil es sich tatsächlich um einen solchen handelt. In der Regel wird der Offset aber meist als „Index“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-144">I introduced this as an offset because that is what it really is, but this offset is more commonly referred to as an index.</span></span> <span data-ttu-id="7c40b-145">Ein Index, der bei `0` beginnt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-145">An index that starts at `0`.</span></span> <span data-ttu-id="7c40b-146">Im weiteren Verlauf dieses Artikels werde ich den Offset als Index bezeichnen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-146">For the rest of this article I will call the offset an index.</span></span>

#### <a name="special-index-tricks"></a><span data-ttu-id="7c40b-147">Spezielle Tricks für Indizes</span><span class="sxs-lookup"><span data-stu-id="7c40b-147">Special index tricks</span></span>

<span data-ttu-id="7c40b-148">In den meisten Sprachen können Sie nur eine einzige Zahl als Index angeben und erhalten ein einzelnes Element zurück.</span><span class="sxs-lookup"><span data-stu-id="7c40b-148">In most languages, you can only specify a single number as the index and you get a single item back.</span></span>
<span data-ttu-id="7c40b-149">PowerShell ist da wesentlich flexibler.</span><span class="sxs-lookup"><span data-stu-id="7c40b-149">PowerShell is much more flexible.</span></span> <span data-ttu-id="7c40b-150">Sie können mehrere Indizes gleichzeitig verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-150">You can use multiple indexes at once.</span></span> <span data-ttu-id="7c40b-151">Indem wir eine Liste von Indizes angeben, können wir mehrere Elemente auswählen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-151">By providing a list of indexes, we can select several items.</span></span>

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

<span data-ttu-id="7c40b-152">Die Elemente werden basierend auf der Reihenfolge der angegebenen Indizes zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-152">The items are returned based on the order of the indexes provided.</span></span> <span data-ttu-id="7c40b-153">Wenn Sie einen Index duplizieren, erhalten Sie das entsprechende Element beide Male.</span><span class="sxs-lookup"><span data-stu-id="7c40b-153">If you duplicate an index, you get that item both times.</span></span>

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

<span data-ttu-id="7c40b-154">Mit dem integrierten `..`-Operator können wir eine Sequenz aus Zahlen angeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-154">We can specify a sequence of numbers with the built-in `..` operator.</span></span>

```powershell
PS> $data[1..3]
One
Two
Three
```

<span data-ttu-id="7c40b-155">Das funktioniert auch umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-155">This works in reverse too.</span></span>

```powershell
PS> $data[3..1]
Three
Two
One
```

<span data-ttu-id="7c40b-156">Sie können auch negative Indexwerte angeben, um den Offset vom Ende der Liste anzugeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-156">You can use negative index values to offset from the end.</span></span> <span data-ttu-id="7c40b-157">Wenn Sie also das letzte Element einer Liste abrufen möchten, können Sie `-1` verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-157">So if you need the last item in the list, you can use `-1`.</span></span>

```powershell
PS> $data[-1]
Three
```

<span data-ttu-id="7c40b-158">Beim Operator `..` ist hierbei allerdings Vorsicht geboten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-158">One word of caution here with the `..` operator.</span></span> <span data-ttu-id="7c40b-159">Die Sequenzen `0..-1` und `-1..0` werden zu den Werten `0,-1` und `-1,0` ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-159">The sequence `0..-1` and `-1..0` evaluate to the values `0,-1` and `-1,0`.</span></span> <span data-ttu-id="7c40b-160">Wenn Sie dieses Detail vergessen, könnten Sie fälschlicherweise davon ausgehen, dass `$data[0..-1]` alle Elemente aufzählt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-160">It's easy to see `$data[0..-1]` and think it would enumerate all items if you forget this detail.</span></span> <span data-ttu-id="7c40b-161">Mit `$data[0..-1]` erhalten Sie dieselben Werte wie mit `$data[0,-1]` – das erste und das letzte Element im Array (und keinen der anderen Werte dazwischen).</span><span class="sxs-lookup"><span data-stu-id="7c40b-161">`$data[0..-1]` gives you the same value as `$data[0,-1]` by giving you the first and last item in the array (and none of the other values).</span></span>

#### <a name="out-of-bounds"></a><span data-ttu-id="7c40b-162">Außerhalb des gültigen Bereichs</span><span class="sxs-lookup"><span data-stu-id="7c40b-162">Out of bounds</span></span>

<span data-ttu-id="7c40b-163">In den meisten Sprachen gilt Folgendes: Wenn Sie versuchen, auf den Index eines Elements zuzugreifen, das hinter dem Ende des Arrays liegt, wird ein Fehler oder eine Ausnahme zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-163">In most languages, if you try to access an index of an item that is past the end of the array, you would get some type of error or an exception.</span></span> <span data-ttu-id="7c40b-164">PowerShell gibt einfach nichts zurück.</span><span class="sxs-lookup"><span data-stu-id="7c40b-164">PowerShell silently returns nothing.</span></span>

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a><span data-ttu-id="7c40b-165">In einem NULL-Array kann kein Index erstellt werden</span><span class="sxs-lookup"><span data-stu-id="7c40b-165">Cannot index into a null array</span></span>

<span data-ttu-id="7c40b-166">Wenn Ihre Variable `$null` lautet und Sie versuchen, sie wie ein Array zu indizieren, wird eine `System.Management.Automation.RuntimeException` mit der Meldung `Cannot index into a null array` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-166">If your variable is `$null` and you try to index it like an array, you get a `System.Management.Automation.RuntimeException` exception with the message `Cannot index into a null array`.</span></span>

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

<span data-ttu-id="7c40b-167">Stellen Sie also sicher, dass Ihre Arrays nicht `$null` sind, bevor Sie versuchen, auf Elemente darin zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-167">So make sure your arrays are not `$null` before you try to access elements inside them.</span></span>

#### <a name="count"></a><span data-ttu-id="7c40b-168">Anzahl</span><span class="sxs-lookup"><span data-stu-id="7c40b-168">Count</span></span>

<span data-ttu-id="7c40b-169">Arrays und andere Auflistungen verfügen über eine count-Eigenschaft, die Sie darüber informiert, wie viele Elemente sich im Array befinden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-169">Arrays and other collections have a count property that tells you how many items are in the array.</span></span>

```powershell
PS> $data.count
4
```

<span data-ttu-id="7c40b-170">PowerShell 3.0 hat den meisten Objekten eine count-Eigenschaft hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-170">PowerShell 3.0 added a count property to most objects.</span></span> <span data-ttu-id="7c40b-171">Wenn Sie über ein einzelnes Objekt verfügen, sollte die Anzahl `1` zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-171">you can have a single object and it should give you a count of `1`.</span></span>

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

<span data-ttu-id="7c40b-172">Selbst `$null` besitzt eine count-Eigenschaft, diese gibt allerdings `0` zurück.</span><span class="sxs-lookup"><span data-stu-id="7c40b-172">Even `$null` has a count property except it returns `0`.</span></span>

```powershell
PS> $null.count
0
```

<span data-ttu-id="7c40b-173">Hier gibt es einige potenzielle Fallen, auf die ich weiter unten in diesem Artikel eingehen werde, wenn ich die Überprüfung auf `$null` oder leere Arrays erläutere.</span><span class="sxs-lookup"><span data-stu-id="7c40b-173">There are some traps here that I will revisit when I cover checking for `$null` or empty arrays later on in this article.</span></span>

#### <a name="off-by-one-errors"></a><span data-ttu-id="7c40b-174">Off-by-one-Fehler</span><span class="sxs-lookup"><span data-stu-id="7c40b-174">Off-by-one errors</span></span>

<span data-ttu-id="7c40b-175">Programmierfehler entstehen nicht selten dadurch, dass Arrays am Index 0 beginnen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-175">A common programming error is created because arrays start at index 0.</span></span> <span data-ttu-id="7c40b-176">Off-by-one-Fehler können auf zwei Arten entstehen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-176">Off-by-one errors can be introduced in two ways.</span></span>

<span data-ttu-id="7c40b-177">Im ersten Fall möchten Sie eigentlich das zweite Element über den Index `2` abrufen, erhalten dadurch aber tatsächlich das dritte Element.</span><span class="sxs-lookup"><span data-stu-id="7c40b-177">The first is by mentally thinking you want the second item and using an index of `2` and really getting the third item.</span></span> <span data-ttu-id="7c40b-178">Oder vielleicht verfügen Sie über vier Elemente, von denen Sie das letzte abrufen möchten, und verwenden daher die count-Eigenschaft für den Zugriff auf dieses letzte Element.</span><span class="sxs-lookup"><span data-stu-id="7c40b-178">Or by thinking that you have four items and you want last item, so you use the count to access the last item.</span></span>

```powershell
$data[ $data.count ]
```

<span data-ttu-id="7c40b-179">PowerShell hindert Sie nicht daran, dies zu tun, und gibt Ihnen genau das Element zurück, das sich an Index 4 befindet: `$null`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-179">PowerShell is perfectly happy to let you do that and give you exactly what item exists at index 4: `$null`.</span></span> <span data-ttu-id="7c40b-180">Hierfür sollten Sie also `$data.count - 1` oder `-1` verwenden, wie etwas weiter oben erläutert.</span><span class="sxs-lookup"><span data-stu-id="7c40b-180">You should be using `$data.count - 1` or the `-1` that we learned about above.</span></span>

```powershell
PS> $data[ $data.count - 1 ]
Three
```

<span data-ttu-id="7c40b-181">So können Sie den Index `-1` verwenden, um das letzte Element abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-181">This is where you can use the `-1` index to get the last element.</span></span>

```powershell
PS> $data[ -1 ]
Three
```

<span data-ttu-id="7c40b-182">Lee Dailey hat mich darauf hingewiesen, dass wir auch `$data.GetUpperBound(0)` verwenden können, um die maximale Indexnummer abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-182">Lee Dailey also pointed out to me that we can use `$data.GetUpperBound(0)` to get the max index number.</span></span>

```powershell
PS> $data.GetUpperBound(0)
Three
```

<span data-ttu-id="7c40b-183">Die zweithäufigste Fehlerquelle entsteht dadurch, dass eine Liste durchlaufen und der Durchlauf nicht rechtzeitig angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="7c40b-183">The second most common way is when iterating the list and not stopping at the right time.</span></span> <span data-ttu-id="7c40b-184">Ich werde näher auf dieses Problem eingehen, wenn ich die `for`-Schleife erläutere.</span><span class="sxs-lookup"><span data-stu-id="7c40b-184">I'll revisit this when we talk about using the `for` loop.</span></span>

### <a name="updating-items"></a><span data-ttu-id="7c40b-185">Aktualisieren von Elementen</span><span class="sxs-lookup"><span data-stu-id="7c40b-185">Updating items</span></span>

<span data-ttu-id="7c40b-186">Wir können denselben Index zum Aktualisieren vorhandener Elemente im Array verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-186">We can use the same index to update existing items in the array.</span></span> <span data-ttu-id="7c40b-187">So erhalten wir direkten Zugriff zum Aktualisieren einzelner Elemente.</span><span class="sxs-lookup"><span data-stu-id="7c40b-187">This gives us direct access to update individual items.</span></span>

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

<span data-ttu-id="7c40b-188">Wenn wir versuchen, ein Element zu aktualisieren, das sich hinter dem letzten Element befindet, wird der Fehler `Index was outside the bounds of the array.` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-188">If we try to update an item that is past the last element, then we get an `Index was outside the bounds of the array.` error.</span></span>

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

<span data-ttu-id="7c40b-189">Dieses Problem werde ich später erläutern, wenn ich beschreibe, wie sich ein Array vergrößern lässt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-189">I'll revisit this later when I talk about how to make an array larger.</span></span>

### <a name="iteration"></a><span data-ttu-id="7c40b-190">Iteration</span><span class="sxs-lookup"><span data-stu-id="7c40b-190">Iteration</span></span>

<span data-ttu-id="7c40b-191">An einem bestimmten Punkt werden Sie die gesamte Liste durchlaufen und eine Aktion für jedes Element im Array ausführen müssen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-191">At some point, you might need to walk or iterate the entire list and perform some action for each item in the array.</span></span>

#### <a name="pipeline"></a><span data-ttu-id="7c40b-192">Pipeline</span><span class="sxs-lookup"><span data-stu-id="7c40b-192">Pipeline</span></span>

<span data-ttu-id="7c40b-193">Arrays und die PowerShell-Pipeline sind wie füreinander geschaffen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-193">Arrays and the PowerShell pipeline are meant for each other.</span></span> <span data-ttu-id="7c40b-194">Dies ist eine der einfachsten Möglichkeiten, diese Werte zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-194">This is one of the simplest ways to process over those values.</span></span> <span data-ttu-id="7c40b-195">Wenn Sie ein Array an eine Pipeline übergeben, wird jedes Element im Array individuell verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-195">When you pass an array to a pipeline, each item inside the array is processed individually.</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

<span data-ttu-id="7c40b-196">Wenn Sie `$PSItem` noch nie gesehen haben, müssen Sie zunächst nur wissen, dass es das gleiche ist wie `$_`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-196">If you have not seen `$PSItem` before, just know that it's the same thing as `$_`.</span></span> <span data-ttu-id="7c40b-197">Sie können beide verwenden, weil beide das aktuelle Objekt in der Pipeline repräsentieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-197">You can use either one because they both represent the current object in the pipeline.</span></span>

#### <a name="foreach-loop"></a><span data-ttu-id="7c40b-198">foreach-Schleife</span><span class="sxs-lookup"><span data-stu-id="7c40b-198">ForEach loop</span></span>

<span data-ttu-id="7c40b-199">Die `ForEach`-Schleife funktioniert gut bei Auflistungen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-199">The `ForEach` loop works well with collections.</span></span> <span data-ttu-id="7c40b-200">Die Syntax lautet `foreach ( <variable> in <collection> )`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-200">Using the syntax: `foreach ( <variable> in <collection> )`</span></span>

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a><span data-ttu-id="7c40b-201">foreach-Methode</span><span class="sxs-lookup"><span data-stu-id="7c40b-201">ForEach method</span></span>

<span data-ttu-id="7c40b-202">Ich neige dazu, diese Methode zu vergessen, aber sie funktioniert bei einfachen Vorgängen wirklich gut.</span><span class="sxs-lookup"><span data-stu-id="7c40b-202">I tend to forget about this one but it works well for simple operations.</span></span> <span data-ttu-id="7c40b-203">PowerShell ermöglicht den Aufruf von `.ForEach()` in einer Auflistung.</span><span class="sxs-lookup"><span data-stu-id="7c40b-203">PowerShell allows you to call `.ForEach()` on a collection.</span></span>

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

<span data-ttu-id="7c40b-204">`.foreach()` akzeptiert einen Parameter, bei dem es sich um einen Skriptblock handelt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-204">The `.foreach()` takes a parameter that is a script block.</span></span> <span data-ttu-id="7c40b-205">Sie können die Klammern weglassen und einfach nur den Skriptblock angeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-205">You can drop the parentheses and just provide the script block.</span></span>

```powershell
$data.foreach{"Item [$PSItem]"}
```

<span data-ttu-id="7c40b-206">Diese Syntax ist weniger bekannt, funktioniert aber genauso gut.</span><span class="sxs-lookup"><span data-stu-id="7c40b-206">This is a lesser known syntax but it works just the same.</span></span> <span data-ttu-id="7c40b-207">Diese `foreach`-Methode wurde in PowerShell 4.0 hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-207">This `foreach` method was added in PowerShell 4.0.</span></span>

#### <a name="for-loop"></a><span data-ttu-id="7c40b-208">for-Schleife</span><span class="sxs-lookup"><span data-stu-id="7c40b-208">For loop</span></span>

<span data-ttu-id="7c40b-209">Die `for`-Schleife wird in den meisten anderen Sprachen ausgiebig genutzt, in PowerShell kommt sie nur selten vor.</span><span class="sxs-lookup"><span data-stu-id="7c40b-209">The `for` loop is used heavily in most other languages but you don’t see it much in PowerShell.</span></span> <span data-ttu-id="7c40b-210">Wenn sie vorkommt, dann meist beim Durchlaufen eines Arrays.</span><span class="sxs-lookup"><span data-stu-id="7c40b-210">When you do see it, it's often in the context of walking an array.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="7c40b-211">Als Erstes initialisieren wir einen `$index` mit `0`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-211">The first thing we do is initialize an `$index` to `0`.</span></span> <span data-ttu-id="7c40b-212">Dann fügen wir die Bedingung hinzu, dass `$index` kleiner sein muss als `$data.count`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-212">Then we add the condition that `$index` must be less than `$data.count`.</span></span> <span data-ttu-id="7c40b-213">Schließlich geben wir an, dass bei jedem Durchlaufen der Schleife der Index um `1` erhöht werden muss.</span><span class="sxs-lookup"><span data-stu-id="7c40b-213">Finally, we specify that every time we loop that me must increase the index by `1`.</span></span> <span data-ttu-id="7c40b-214">In diesem Fall ist `$index++` die Kurzform von `$index = $index + 1`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-214">In this case `$index++` is short for `$index = $index + 1`.</span></span>

<span data-ttu-id="7c40b-215">Wann immer Sie eine `for`-Schleife verwenden, achten Sie besonders auf die Bedingung.</span><span class="sxs-lookup"><span data-stu-id="7c40b-215">Whenever you're using a `for` loop, pay special attention to the condition.</span></span> <span data-ttu-id="7c40b-216">Ich habe hier `$index -lt $data.count` verwendet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-216">I used `$index -lt $data.count` here.</span></span> <span data-ttu-id="7c40b-217">Vorsicht: Bei dieser Bedingung können Ihnen leicht kleine Fehler unterlaufen, die dann zu Off-by-one-Fehlern in Ihrer Logik führen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-217">It's easy to get the condition slightly wrong to get an off-by-one error in your logic.</span></span> <span data-ttu-id="7c40b-218">Beispiele für solche kleinen Fehler wären `$index -le $data.count` oder `$index -lt ($data.count - 1)`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-218">Using `$index -le $data.count` or `$index -lt ($data.count - 1)` are ever so slightly wrong.</span></span> <span data-ttu-id="7c40b-219">Das würde dazu führen, dass Ihr Ergebnis zu viele oder zu wenige Elemente verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-219">That would cause your result to process too many or too few items.</span></span> <span data-ttu-id="7c40b-220">Das ist der klassische Off-by-one-Fehler.</span><span class="sxs-lookup"><span data-stu-id="7c40b-220">This is the classic off-by-one error.</span></span>

#### <a name="switch-loop"></a><span data-ttu-id="7c40b-221">switch-Schleife</span><span class="sxs-lookup"><span data-stu-id="7c40b-221">Switch loop</span></span>

<span data-ttu-id="7c40b-222">Diese Schleife wird leicht übersehen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-222">This is one that is easy to overlook.</span></span> <span data-ttu-id="7c40b-223">Wenn Sie in einer [switch-Anweisung][] ein Array angeben, überprüft diese Anweisung jedes Element im Array.</span><span class="sxs-lookup"><span data-stu-id="7c40b-223">If you provide an array to a [switch statement][], it checks each item in the array.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

<span data-ttu-id="7c40b-224">Diese Anweisung bietet einige echt coole Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-224">There are a lot of cool things that we can do with the switch statement.</span></span> <span data-ttu-id="7c40b-225">Ich habe darüber einen ganzen Artikel geschrieben:</span><span class="sxs-lookup"><span data-stu-id="7c40b-225">I have another article dedicated to this.</span></span>

- <span data-ttu-id="7c40b-226">[Alles, was Sie schon immer über die switch-Anweisung wissen wollten][switch-Anweisung]</span><span class="sxs-lookup"><span data-stu-id="7c40b-226">[Everything you ever wanted to know about the switch statement][switch statement]</span></span>

#### <a name="updating-values"></a><span data-ttu-id="7c40b-227">Aktualisieren von Werten</span><span class="sxs-lookup"><span data-stu-id="7c40b-227">Updating values</span></span>

<span data-ttu-id="7c40b-228">Wenn es sich bei Ihrem Array um eine Auflistung von string- oder integer-Typen (Werttypen) handelt, werden Sie die Werte im Array beim Durchlaufen vermutlich aktualisieren wollen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-228">When your array is a collection of string or integers (value types), sometimes you may want to update the values in the array as you loop over them.</span></span> <span data-ttu-id="7c40b-229">Die meisten oben genannten Schleifen verwenden eine Variable in der Schleife, die eine Kopie des Werts enthält.</span><span class="sxs-lookup"><span data-stu-id="7c40b-229">Most of the loops above use a variable in the loop that holds a copy of the value.</span></span> <span data-ttu-id="7c40b-230">Wenn Sie diese Variable aktualisieren, wird der ursprüngliche Wert im Array nicht aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="7c40b-230">If you update that variable, the original value in the array is not updated.</span></span>

<span data-ttu-id="7c40b-231">Die Ausnahme dieser Anweisung ist die `for`-Schleife.</span><span class="sxs-lookup"><span data-stu-id="7c40b-231">The exception to that statement is the `for` loop.</span></span> <span data-ttu-id="7c40b-232">Wenn Sie ein Array durchlaufen und Werte darin aktualisieren möchten, ist die `for`-Schleife genau das, wonach Sie suchen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-232">If you want to walk an array and update values inside it, then the `for` loop is what you're looking for.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="7c40b-233">Dieses Beispiel ruft einen Wert anhand des Indexes ab, nimmt einige Änderungen vor und verwendet denselben Index, um den Wert wieder zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-233">This example takes a value by index, makes a few changes, and then uses that same index to assign it back.</span></span>

## <a name="arrays-of-objects"></a><span data-ttu-id="7c40b-234">Array aus Objekten</span><span class="sxs-lookup"><span data-stu-id="7c40b-234">Arrays of Objects</span></span>

<span data-ttu-id="7c40b-235">Bisher haben wir nur einen Werttyp in einem Array platziert, Arrays können aber auch Objekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-235">So far, the only thing we've placed in an array is a value type, but arrays can also contain objects.</span></span>

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

<span data-ttu-id="7c40b-236">Viele Cmdlets geben Auflistungen von Objekten als Arrays zurück, wenn Sie sie einer Variable zuweisen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-236">Many cmdlets return collections of objects as arrays when you assign them to a variable.</span></span>

```powershell
$processList = Get-Process
```

<span data-ttu-id="7c40b-237">All die grundlegenden Features, die ich Ihnen bereits vorgestellt habe, gelten auch für Arrays aus Objekten. Allerdings gibt es ein paar Details, auf die ich Sie gerne hinweisen möchte.</span><span class="sxs-lookup"><span data-stu-id="7c40b-237">All of the basic features we already talked about still apply to arrays of objects with a few details worth pointing out.</span></span>

### <a name="accessing-properties"></a><span data-ttu-id="7c40b-238">Zugreifen auf Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="7c40b-238">Accessing properties</span></span>

<span data-ttu-id="7c40b-239">Wir können einen Index verwenden, um auf ein einzelnes Element in einer Auflistung zuzugreifen – genau wie bei Werttypen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-239">We can use an index to access an individual item in a collection just like with value types.</span></span>

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="7c40b-240">Wir können auf Eigenschaften zugreifen und diese direkt aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-240">We can access and update properties directly.</span></span>

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a><span data-ttu-id="7c40b-241">Arrayeigenschaften</span><span class="sxs-lookup"><span data-stu-id="7c40b-241">Array properties</span></span>

<span data-ttu-id="7c40b-242">Normalerweise müssten Sie die gesamte Liste wie folgt aufzählen, um auf alle Eigenschaften zuzugreifen:</span><span class="sxs-lookup"><span data-stu-id="7c40b-242">Normally you would have to enumerate the whole list like this to access all the properties:</span></span>

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

<span data-ttu-id="7c40b-243">Sie könnten auch das Cmdlet `Select-Object -ExpandProperty` verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-243">Or by using the `Select-Object -ExpandProperty` cmdlet.</span></span>

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

<span data-ttu-id="7c40b-244">PowerShell bietet aber die Möglichkeit, `LastName` direkt anzufordern.</span><span class="sxs-lookup"><span data-stu-id="7c40b-244">But PowerShell offers us the ability to request `LastName` directly.</span></span> <span data-ttu-id="7c40b-245">PowerShell zählt alle Elemente für uns auf und gibt eine bereinigte Liste zurück.</span><span class="sxs-lookup"><span data-stu-id="7c40b-245">PowerShell enumerates them all for us and returns a clean list.</span></span>

```powershell
PS> $data.LastName

Marquette
Doe
```

<span data-ttu-id="7c40b-246">Die Enumeration erfolgt weiterhin, aber die Komplexität dahinter bleibt verborgen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-246">The enumeration still happens but we don't see the complexity behind it.</span></span>

### <a name="where-object-filtering"></a><span data-ttu-id="7c40b-247">Where-Object-Filterung</span><span class="sxs-lookup"><span data-stu-id="7c40b-247">Where-Object filtering</span></span>

<span data-ttu-id="7c40b-248">Hier kommt `Where-Object` ins Spiel, sodass wir Informationen basierend auf den Eigenschaften des Objekts filtern und auswählen können.</span><span class="sxs-lookup"><span data-stu-id="7c40b-248">This is where `Where-Object` comes in so we can filter and select what we want out of the array based on the properties of the object.</span></span>

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="7c40b-249">Wir können dieselbe Abfrage schreiben, um das gewünschte `FirstName`-Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-249">We can write that same query to get the `FirstName` we are looking for.</span></span>

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a><span data-ttu-id="7c40b-250">Where()</span><span class="sxs-lookup"><span data-stu-id="7c40b-250">Where()</span></span>

<span data-ttu-id="7c40b-251">Arrays enthalten eine `Where()`-Methode, mit der Sie einen `scriptblock` für den Filter angeben können.</span><span class="sxs-lookup"><span data-stu-id="7c40b-251">Arrays have a `Where()` method on them that allows you to specify a `scriptblock` for the filter.</span></span>

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

<span data-ttu-id="7c40b-252">Dieses Feature wurde in PowerShell 4.0 hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-252">This feature was added in PowerShell 4.0.</span></span>

### <a name="updating-objects-in-loops"></a><span data-ttu-id="7c40b-253">Aktualisieren von Objekten in Schleifen</span><span class="sxs-lookup"><span data-stu-id="7c40b-253">Updating objects in loops</span></span>

<span data-ttu-id="7c40b-254">Bei Werttypen besteht die einzige Möglichkeit zum Aktualisieren des Arrays darin, eine for-Schleife zu verwenden, da wir den Index kennen müssen, um den Wert zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-254">With value types, the only way to update the array is to use a for loop because we need to know the index to replace the value.</span></span> <span data-ttu-id="7c40b-255">Bei Objekten haben wir mehr Optionen, weil es sich dabei um Verweistypen handelt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-255">We have more options with objects because they are reference types.</span></span> <span data-ttu-id="7c40b-256">Hier ist ein kurzes Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7c40b-256">Here is a quick example:</span></span>

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

<span data-ttu-id="7c40b-257">Die Schleife durchläuft jedes Objekt im `$data`-Array.</span><span class="sxs-lookup"><span data-stu-id="7c40b-257">This loop is walking every object in the `$data` array.</span></span> <span data-ttu-id="7c40b-258">Da Objekte Verweistypen sind, verweist die Variable `$person` auf exakt dieses Objekt, das sich im Array befindet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-258">Because objects are reference types, the `$person` variable references the exact same object that is in the array.</span></span> <span data-ttu-id="7c40b-259">Updates der Eigenschaften des Objekts aktualisieren also das ursprüngliche Objekt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-259">So updates to its properties do update the original.</span></span>

<span data-ttu-id="7c40b-260">Ersetzen können Sie das gesamte Objekt auf diese Weise immer noch nicht.</span><span class="sxs-lookup"><span data-stu-id="7c40b-260">You still can't replace the whole object this way.</span></span> <span data-ttu-id="7c40b-261">Wenn Sie versuchen, der Variable `$person` ein neues Objekt zuzuweisen, aktualisieren Sie den Variablenverweis auf etwas anderes, das nicht mehr auf das ursprüngliche Objekt im Array verweist.</span><span class="sxs-lookup"><span data-stu-id="7c40b-261">If you try to assign a new object to the `$person` variable, you're updating the variable reference to something else that no longer points to the original object in the array.</span></span> <span data-ttu-id="7c40b-262">Das funktioniert nicht so, wie Sie es erwarten würden:</span><span class="sxs-lookup"><span data-stu-id="7c40b-262">This doesn't work like you would expect:</span></span>

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a><span data-ttu-id="7c40b-263">Operatoren</span><span class="sxs-lookup"><span data-stu-id="7c40b-263">Operators</span></span>

<span data-ttu-id="7c40b-264">Operatoren in PowerShell funktionieren auch in Arrays.</span><span class="sxs-lookup"><span data-stu-id="7c40b-264">The operators in PowerShell also work on arrays.</span></span> <span data-ttu-id="7c40b-265">Bei einigen ist die Funktionsweise allerdings etwas anders.</span><span class="sxs-lookup"><span data-stu-id="7c40b-265">Some of them work slightly differently.</span></span>

### <a name="-join"></a><span data-ttu-id="7c40b-266">-join</span><span class="sxs-lookup"><span data-stu-id="7c40b-266">-join</span></span>

<span data-ttu-id="7c40b-267">Der `-join`-Operator ist der offensichtlichste, also sehen wir uns diesen zuerst an.</span><span class="sxs-lookup"><span data-stu-id="7c40b-267">The `-join` operator is the most obvious one so let's look at it first.</span></span> <span data-ttu-id="7c40b-268">Ich mag den `-join`-Operator und verwende ihn häufig.</span><span class="sxs-lookup"><span data-stu-id="7c40b-268">I like the `-join` operator and use it often.</span></span> <span data-ttu-id="7c40b-269">Er verknüpft alle Elemente im Array mit dem Zeichen oder der Zeichenfolge, das bzw. die Sie angeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-269">It joins all elements in the array with the character or string that you specify.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

<span data-ttu-id="7c40b-270">Eines der Features, das mir am `-join`-Operator gefällt, ist die Verarbeitung einzelner Elemente.</span><span class="sxs-lookup"><span data-stu-id="7c40b-270">One of the features that I like about the `-join` operator is that it handles single items.</span></span>

```powershell
PS> 1 -join '-'
1
```

<span data-ttu-id="7c40b-271">Dieses Feature verwende ich in Protokollierungsmeldungen und ausführlichen Meldungen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-271">I use this inside logging and verbose messages.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a><span data-ttu-id="7c40b-272">-join $array</span><span class="sxs-lookup"><span data-stu-id="7c40b-272">-join $array</span></span>

<span data-ttu-id="7c40b-273">Jetzt zeige ich Ihnen einen cleveren Trick, auf den Lee Dailey mich gebracht hat.</span><span class="sxs-lookup"><span data-stu-id="7c40b-273">Here is a clever trick that Lee Dailey pointed out to me.</span></span> <span data-ttu-id="7c40b-274">Wenn Sie alle Elemente ohne Trennzeichen miteinander verknüpfen möchten, gehen Sie nicht so vor:</span><span class="sxs-lookup"><span data-stu-id="7c40b-274">If you ever want to join everything without a delimiter, instead of doing this:</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

<span data-ttu-id="7c40b-275">Sie können `-join` mit dem Array als Parameter ohne Präfix verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-275">You can use `-join` with the array as the parameter with no prefix.</span></span> <span data-ttu-id="7c40b-276">Sehen Sie sich das folgende Beispiel an, das verdeutlicht, wovon ich spreche.</span><span class="sxs-lookup"><span data-stu-id="7c40b-276">Take a look at this example to see that I'm talking about.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a><span data-ttu-id="7c40b-277">-replace und -split</span><span class="sxs-lookup"><span data-stu-id="7c40b-277">-replace and -split</span></span>

<span data-ttu-id="7c40b-278">Die Operatoren `-replace` und `-split` werden für jedes Element im Array ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-278">The other operators like `-replace` and `-split` execute on each item in the array.</span></span> <span data-ttu-id="7c40b-279">Ich kann nicht behauptet, diese jemals auf diese Weise verwendet zu haben, aber hier finden Sie ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="7c40b-279">I can't say that I have ever used them this way but here is an example.</span></span>

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a><span data-ttu-id="7c40b-280">-contains</span><span class="sxs-lookup"><span data-stu-id="7c40b-280">-contains</span></span>

<span data-ttu-id="7c40b-281">Mit dem `-contains`-Operator können Sie ein Array mit Werten überprüfen, um zu ermitteln, ob es einen bestimmten Wert enthält.</span><span class="sxs-lookup"><span data-stu-id="7c40b-281">The `-contains` operator allows you to check an array of values to see if it contains a specified value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a><span data-ttu-id="7c40b-282">-in</span><span class="sxs-lookup"><span data-stu-id="7c40b-282">-in</span></span>

<span data-ttu-id="7c40b-283">Wenn Sie überprüfen möchten, ob ein einzelner Wert mit einem von mehreren Werten übereinstimmt, können Sie den `-in`-Operator verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-283">When you have a single value that you would like to verify matches one of several values, you can use the `-in` operator.</span></span> <span data-ttu-id="7c40b-284">Der Wert steht dann auf der linken und das Array auf der rechten Seite des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="7c40b-284">The value would be on the left and the array on the right-hand side of the operation.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

<span data-ttu-id="7c40b-285">Das Ganze kann recht umfangreich werden, wenn die Liste lang ist.</span><span class="sxs-lookup"><span data-stu-id="7c40b-285">This can get expensive if the list is large.</span></span> <span data-ttu-id="7c40b-286">Ich verwende häufig ein RegEx-Muster, wenn ich mehr als nur einige wenige Werte überprüfe.</span><span class="sxs-lookup"><span data-stu-id="7c40b-286">I often use a regex pattern if I'm checking more than a few values.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a><span data-ttu-id="7c40b-287">-eq und -ne</span><span class="sxs-lookup"><span data-stu-id="7c40b-287">-eq and -ne</span></span>

<span data-ttu-id="7c40b-288">Die Verwendung des Gleichheitsoperators mit Arrays kann ziemlich kompliziert werden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-288">Equality and arrays can get complicated.</span></span> <span data-ttu-id="7c40b-289">Wenn sich das Array auf der linken Seite befindet, werden alle Elemente verglichen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-289">When the array is on the left side, every item gets compared.</span></span> <span data-ttu-id="7c40b-290">Statt `True` wird das übereinstimmende Objekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-290">Instead of returning `True`, it returns the object that matches.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

<span data-ttu-id="7c40b-291">Wenn Sie den `-ne`-Operator verwenden, erhalten Sie alle Werte, die nicht gleich Ihrem Wert sind.</span><span class="sxs-lookup"><span data-stu-id="7c40b-291">When you use the `-ne` operator, we get all the values that are not equal to our value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

<span data-ttu-id="7c40b-292">Wenn Sie dies in einer `if()`-Anweisung verwenden, ist ein Wert, der zurückgegeben wird, ein `True`-Wert.</span><span class="sxs-lookup"><span data-stu-id="7c40b-292">When you use this in an `if()` statement, a value that is returned is a `True` value.</span></span> <span data-ttu-id="7c40b-293">Wenn kein Wert zurückgegeben wird, handelt es sich um einen `False`-Wert.</span><span class="sxs-lookup"><span data-stu-id="7c40b-293">If no value is returned, then it's a `False` value.</span></span> <span data-ttu-id="7c40b-294">Die beiden nächsten Anweisungen werden zu `True` ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-294">Both of these next statements evaluate to `True`.</span></span>

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

<span data-ttu-id="7c40b-295">Darauf gehe ich gleich näher ein, wenn ich das Überprüfen auf `$null` erläutere.</span><span class="sxs-lookup"><span data-stu-id="7c40b-295">I'll revisit this in a moment when we talk about testing for `$null`.</span></span>

### <a name="-match"></a><span data-ttu-id="7c40b-296">-match</span><span class="sxs-lookup"><span data-stu-id="7c40b-296">-match</span></span>

<span data-ttu-id="7c40b-297">Der Operator `-match` versucht, eine Übereinstimmung für jedes Element in der Auflistung zu finden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-297">The `-match` operator tries to match each item in the collection.</span></span>

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

<span data-ttu-id="7c40b-298">Wenn Sie `-match` mit einem einzelnen Wert verwenden, wird eine spezielle Variable, `$Matches`, mit Übereinstimmungsinformationen aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-298">When you use `-match` with a single value, a special variable `$Matches` gets populated with match info.</span></span> <span data-ttu-id="7c40b-299">Dies ist nicht der Fall, wenn ein Array auf diese Weise verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="7c40b-299">This isn't the case when an array is processed this way.</span></span>

<span data-ttu-id="7c40b-300">Wir können denselben Ansatz mit `Select-String` verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-300">We can take the same approach with `Select-String`.</span></span>

```powershell
$servers | Select-String SQL
```

<span data-ttu-id="7c40b-301">In meinem Blog [The many ways to use regex][] (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken) habe ich `Select-String`, `-match` und die Variable `$matches` genauer erläutert.</span><span class="sxs-lookup"><span data-stu-id="7c40b-301">I take a closer look at `Select-String`,`-match` and the `$matches` variable in another post called [The many ways to use regex][].</span></span>

### <a name="null-or-empty"></a><span data-ttu-id="7c40b-302">$null- oder leere Werte</span><span class="sxs-lookup"><span data-stu-id="7c40b-302">$null or empty</span></span>

<span data-ttu-id="7c40b-303">Die Überprüfung auf `$null` oder leere Arrays kann knifflig sein.</span><span class="sxs-lookup"><span data-stu-id="7c40b-303">Testing for `$null` or empty arrays can be tricky.</span></span> <span data-ttu-id="7c40b-304">Hier zeige ich Ihnen einige häufige Fallen bei Arrays.</span><span class="sxs-lookup"><span data-stu-id="7c40b-304">Here are the common traps with arrays.</span></span>

<span data-ttu-id="7c40b-305">Auf den ersten Blick sieht diese Anweisung aus, als sollte sie funktionieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-305">At a glance, this statement looks like it should work.</span></span>

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

<span data-ttu-id="7c40b-306">Ich habe aber gerade erläutert, wie `-eq` jedes Element im Array überprüft.</span><span class="sxs-lookup"><span data-stu-id="7c40b-306">But I just went over how `-eq` checks each item in the array.</span></span> <span data-ttu-id="7c40b-307">Wenn wir also ein Array aus mehreren Elementen mit einem einzigen $null-Wert haben, würde dieses als `$true` ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-307">So we can have an array of several items with a single $null value and it would evaluate to `$true`</span></span>

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

<span data-ttu-id="7c40b-308">Darum empfiehlt es sich, `$null` auf der linken Seite des Operators zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-308">This is why it's a best practice to place the `$null` on the left side of the operator.</span></span> <span data-ttu-id="7c40b-309">Und schon ist dieses Szenario kein Problem mehr.</span><span class="sxs-lookup"><span data-stu-id="7c40b-309">This makes this scenario a non-issue.</span></span>

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

<span data-ttu-id="7c40b-310">Ein `$null`-Array ist nicht dasselbe wie ein leeres Array.</span><span class="sxs-lookup"><span data-stu-id="7c40b-310">A `$null` array isn't the same thing as an empty array.</span></span> <span data-ttu-id="7c40b-311">Wenn Sie wissen, dass es sich um ein Array handelt, überprüfen Sie die Anzahl von Objekten darin.</span><span class="sxs-lookup"><span data-stu-id="7c40b-311">If you know you have an array, check the count of objects in it.</span></span> <span data-ttu-id="7c40b-312">Wenn das Array `$null` ist, lautet die Anzahl `0`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-312">If the array is `$null`, the count is `0`.</span></span>

```powershell
if ( $array.count -gt 0 )
{
    'Array isn't empty'
}
```

<span data-ttu-id="7c40b-313">Es gibt noch eine weitere Falle, nach der Sie Ausschau halten sollten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-313">There is one more trap to watch out for here.</span></span> <span data-ttu-id="7c40b-314">Sie können `count` verwenden, auch wenn Sie nur über ein einzelnes Objekt verfügen, es sei denn, dieses Objekt ist ein `PSCustomObject`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-314">You can use the `count` even if you have a single object, unless that object is a `PSCustomObject`.</span></span> <span data-ttu-id="7c40b-315">Dies ist ein Fehler, der in PowerShell 6.1 behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="7c40b-315">This is a bug that is fixed in PowerShell 6.1.</span></span>
<span data-ttu-id="7c40b-316">Das sind zwar gute Nachrichten, aber viele Entwickler arbeiten noch mit Version 5.1 und müssen daher an dieser Stelle Vorsicht walten lassen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-316">That's good news, but a lot of people are still on 5.1 and need to watch out for it.</span></span>

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

<span data-ttu-id="7c40b-317">Wenn Sie mit PowerShell 5.1 arbeiten, können Sie das Objekt vor der Überprüfung der Anzahl mit einem Array umschließen, um die exakte Anzahl zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-317">If you're still on PowerShell 5.1, you can wrap the object in an array before checking the count to get an accurate count.</span></span>

```powershell
if ( @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

<span data-ttu-id="7c40b-318">Um ganz sicherzugehen, überprüfen Sie zunächst auf `$null` und überprüfen dann die Anzahl.</span><span class="sxs-lookup"><span data-stu-id="7c40b-318">To fully play it safe, check for `$null`, then check the count.</span></span>

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

### <a name="all--eq"></a><span data-ttu-id="7c40b-319">Alles -eq</span><span class="sxs-lookup"><span data-stu-id="7c40b-319">All -eq</span></span>

<span data-ttu-id="7c40b-320">Jemand frage neulich, [How to verify that every value in an array matches a given value][].</span><span class="sxs-lookup"><span data-stu-id="7c40b-320">I recently saw someone ask [how to verify that every value in an array matches a given value][].</span></span>
<span data-ttu-id="7c40b-321">Der Reddit-Benutzer **/u/bis** hatte diese clevere [Lösung][] parat, die auf falsche Werte überprüft und das Ergebnis dann umdreht.</span><span class="sxs-lookup"><span data-stu-id="7c40b-321">Reddit user **/u/bis** had this clever [solution][] that checks for any incorrect values and then flips the result.</span></span>

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a><span data-ttu-id="7c40b-322">Hinzufügen zu Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-322">Adding to arrays</span></span>

<span data-ttu-id="7c40b-323">Möglicherweise fragen Sie sich an dieser Stelle, wie Sie Elemente zu einem Array hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-323">At this point, you're starting to wonder how to add items to an array.</span></span> <span data-ttu-id="7c40b-324">Die schnelle Antwort lautet: „Gar nicht.“</span><span class="sxs-lookup"><span data-stu-id="7c40b-324">The quick answer is that you can't.</span></span> <span data-ttu-id="7c40b-325">Ein Array weist im Arbeitsspeicher eine unveränderliche Größe auf.</span><span class="sxs-lookup"><span data-stu-id="7c40b-325">An array is a fixed size in memory.</span></span> <span data-ttu-id="7c40b-326">Wenn Sie es erweitern oder ihm ein einzelnes Element hinzufügen müssen, müssen Sie ein neues Array erstellen und die Werte aus dem alten Array hineinkopieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-326">If you need to grow it or add a single item to it, then you need to create a new array and copy all the values over from the old array.</span></span> <span data-ttu-id="7c40b-327">Das klingt nach viel Arbeit und Rechenaufwand, aber in PowerShell ist das Erstellen des neuen Arrays weniger komplex.</span><span class="sxs-lookup"><span data-stu-id="7c40b-327">This sounds expensive and like a lot of work, however, PowerShell hides the complexity of creating the new array.</span></span>

### <a name="array-addition"></a><span data-ttu-id="7c40b-328">Addition eines Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-328">Array addition</span></span>

<span data-ttu-id="7c40b-329">Wir können den Additionsoperator mit Arrays verwenden, um ein neues Array zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-329">We can use the addition operator with arrays to create a new array.</span></span> <span data-ttu-id="7c40b-330">Wir haben diese beiden Arrays:</span><span class="sxs-lookup"><span data-stu-id="7c40b-330">So given these two arrays:</span></span>

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

<span data-ttu-id="7c40b-331">Diese können wir addieren, um ein neues Array zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-331">We can add them together to get a new array.</span></span>

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a><span data-ttu-id="7c40b-332">Plus-gleich (+=)</span><span class="sxs-lookup"><span data-stu-id="7c40b-332">Plus equals +=</span></span>

<span data-ttu-id="7c40b-333">Wir können auf folgende Weise ein neues Array erstellen und diesem ein Element hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="7c40b-333">We can create a new array in place and add an item to it like this:</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

<span data-ttu-id="7c40b-334">Denken Sie daran, dass Sie bei jeder Verwendung von `+=` die Elemente duplizieren und ein neues Array erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-334">Just remember that every time you use `+=` that you're duplicating and creating a new array.</span></span> <span data-ttu-id="7c40b-335">Das ist bei kleinen Datasets kein Problem, lässt sich aber nur schlecht skalieren.</span><span class="sxs-lookup"><span data-stu-id="7c40b-335">This is a not an issue for small datasets but it scales extremely poorly.</span></span>

### <a name="pipeline-assignment"></a><span data-ttu-id="7c40b-336">Pipelinezuweisung</span><span class="sxs-lookup"><span data-stu-id="7c40b-336">Pipeline assignment</span></span>

<span data-ttu-id="7c40b-337">Sie können die Ergebnisse einer Pipeline in einer Variable zuweisen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-337">You can assign the results of any pipeline into a variable.</span></span> <span data-ttu-id="7c40b-338">Wenn mehrere Elemente enthalten sind, handelt es sich um ein Array.</span><span class="sxs-lookup"><span data-stu-id="7c40b-338">It's an array if it contains multiple items.</span></span>

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

<span data-ttu-id="7c40b-339">Wenn wir über die Verwendung der Pipeline nachdenken, denken wir in der Regel an die typischen PowerShell-Einzeiler.</span><span class="sxs-lookup"><span data-stu-id="7c40b-339">Normally when we think of using the pipeline, we think of the typical PowerShell one-liners.</span></span> <span data-ttu-id="7c40b-340">Wir können die Pipeline aber auch mit `foreach()`-Anweisungen und anderen Schleifen nutzen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-340">We can leverage the pipeline with `foreach()` statements and other loops.</span></span> <span data-ttu-id="7c40b-341">Anstatt also Elemente in einer Schleife zu einem Array hinzuzufügen, können wir Elemente in der Pipeline ablegen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-341">So instead of adding items to an array in a loop, we can drop items onto the pipeline.</span></span>

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

<span data-ttu-id="7c40b-342">Indem wir die Ergebnisse von `foreach` einer Variable zuweisen, erfassen wir alle Objekte und erstellen ein einzelnes Array.</span><span class="sxs-lookup"><span data-stu-id="7c40b-342">By assigning the results of the `foreach` to a variable, we capture all the objects and create a single array.</span></span>

## <a name="array-types"></a><span data-ttu-id="7c40b-343">Arraytypen</span><span class="sxs-lookup"><span data-stu-id="7c40b-343">Array Types</span></span>

<span data-ttu-id="7c40b-344">Ein Array wird in PowerShell standardmäßig als `[PSObject[]]`-Typ erstellt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-344">By default, an array in PowerShell is created as a `[PSObject[]]` type.</span></span> <span data-ttu-id="7c40b-345">So kann es jeden Objekt- oder Werttyp enthalten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-345">This allows it to contain any type of object or value.</span></span> <span data-ttu-id="7c40b-346">Das funktioniert, weil alles vom Typ `PSObject` geerbt wird.</span><span class="sxs-lookup"><span data-stu-id="7c40b-346">This works because everything is inherited from the `PSObject` type.</span></span>

### <a name="strongly-typed-arrays"></a><span data-ttu-id="7c40b-347">Stark typisierte Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-347">Strongly typed arrays</span></span>

<span data-ttu-id="7c40b-348">Sie können mit einer ähnlichen Syntax ein Array eines beliebigen Typs erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-348">You can create an array of any type using a similar syntax.</span></span> <span data-ttu-id="7c40b-349">Wenn Sie ein stark typisiertes Array erstellen, kann es nur Werte oder Objekte des angegebenen Typs enthalten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-349">When you create a strongly typed array, it can only contain values or objects the specified type.</span></span>

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a><span data-ttu-id="7c40b-350">ArrayList</span><span class="sxs-lookup"><span data-stu-id="7c40b-350">ArrayList</span></span>

<span data-ttu-id="7c40b-351">Dass sich nicht einfach so Elemente hinzufügen lassen, ist eine der größten Einschränkungen von Arrays, aber es gibt einige andere Auflistungen, mit denen sich dieses Problem lösen lässt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-351">Adding items to an array is one of its biggest limitations, but there are a few other collections that we can turn to that solve this problem.</span></span>

<span data-ttu-id="7c40b-352">Wenn ich ein Array brauche, mit dem ich schneller arbeiten kann, fällt mir in der Regel zuerst eine `ArrayList` ein.</span><span class="sxs-lookup"><span data-stu-id="7c40b-352">The `ArrayList` is commonly one of the first things that we think of when we need an array that is faster to work with.</span></span> <span data-ttu-id="7c40b-353">Eine Arrayliste funktioniert wie ein Objektarray überall dort, wo es notwendig ist, ermöglicht aber das schnelle Hinzufügen von Objekten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-353">It acts like an object array every place that we need it, but it handles adding items quickly.</span></span>

<span data-ttu-id="7c40b-354">So erstellen wir eine `ArrayList` und fügen Elemente hinzu.</span><span class="sxs-lookup"><span data-stu-id="7c40b-354">Here is how we create an `ArrayList` and add items to it.</span></span>

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

<span data-ttu-id="7c40b-355">Wir rufen .NET auf, um diesen Typ zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-355">We are calling into .NET to get this type.</span></span> <span data-ttu-id="7c40b-356">In diesem Fall verwenden wir den Standardkonstruktor zum Erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-356">In this case, we are using the default constructor to create it.</span></span> <span data-ttu-id="7c40b-357">Dann rufen wir die `Add`-Methode auf, um ein Element hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-357">Then we call the `Add` method to add an item to it.</span></span>

<span data-ttu-id="7c40b-358">Ich verwende `[void]` am Anfang der Zeile, weil ich den Rückgabecode unterdrücken möchte.</span><span class="sxs-lookup"><span data-stu-id="7c40b-358">The reason I'm using `[void]` at the beginning of the line is to suppress the return code.</span></span> <span data-ttu-id="7c40b-359">Einige .NET-Aufrufe tun dies, und es kann zu einer unerwarteten Ausgabe führen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-359">Some .NET calls do this and can create unexpected output.</span></span>

<span data-ttu-id="7c40b-360">Wenn die einzigen Daten, die in Ihrem Array enthalten sind, Zeichenfolgen sind, sollten Sie auch die Verwendung von [StringBuilder][] in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-360">If the only data that you have in your array is strings, then also take a look at using [StringBuilder][].</span></span> <span data-ttu-id="7c40b-361">Das ist fast das Gleiche, bietet aber einige Methoden nur für die Verarbeitung von Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-361">It's almost the same thing but has some methods that are just for dealing with strings.</span></span> <span data-ttu-id="7c40b-362">`StringBuilder` wurde speziell im Hinblick auf eine hohe Leistung entwickelt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-362">The `StringBuilder` is specially designed for performance.</span></span>

<span data-ttu-id="7c40b-363">Viele Entwickler steigen von Arrays auf `ArrayList` um.</span><span class="sxs-lookup"><span data-stu-id="7c40b-363">It's common to see people move to `ArrayList` from arrays.</span></span> <span data-ttu-id="7c40b-364">Das stammt aber noch aus Zeiten, in denen C# keine generische Unterstützung bot.</span><span class="sxs-lookup"><span data-stu-id="7c40b-364">But it comes from a time where C# didn't have generic support.</span></span> <span data-ttu-id="7c40b-365">`ArrayList` ist zugunsten des generischen `List[]`-Elements als veraltet gekennzeichnet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-365">The `ArrayList` is depreciated in support for the generic `List[]`</span></span>

### <a name="generic-list"></a><span data-ttu-id="7c40b-366">Generischer List-Typ</span><span class="sxs-lookup"><span data-stu-id="7c40b-366">Generic List</span></span>

<span data-ttu-id="7c40b-367">Ein generischer Typ ist ein spezieller Typ in C#, der eine generalisierte Klasse definiert. Der Benutzer gibt dann bei der Erstellung die verwendeten Datentypen an.</span><span class="sxs-lookup"><span data-stu-id="7c40b-367">A generic type is a special type in C# that defines a generalized class and the user specifies the data types it uses when created.</span></span> <span data-ttu-id="7c40b-368">Wenn Sie also eine Liste mit Zahlen oder Zeichenfolgen haben möchten, definieren Sie, dass Sie eine Liste mit `int`- oder `string`-Typen benötigen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-368">So if you want a list of numbers or strings, you would define that you want list of `int` or `string` types.</span></span>

<span data-ttu-id="7c40b-369">So erstellen Sie eine Liste für Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-369">Here is how you create a List for strings.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

<span data-ttu-id="7c40b-370">Und so erstellen Sie eine Liste für Zahlen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-370">Or a list for numbers.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

<span data-ttu-id="7c40b-371">Wir können ein vorhandenes Array in eine Liste umwandeln, ohne zuerst das Objekt erstellen zu müssen:</span><span class="sxs-lookup"><span data-stu-id="7c40b-371">We can cast an existing array to a list like this without creating the object first:</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

<span data-ttu-id="7c40b-372">Mit der `using namespace`-Anweisung in PowerShell 5 und höher können wir die Syntax kürzen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-372">We can shorten the syntax with the `using namespace` statement in PowerShell 5 and newer.</span></span> <span data-ttu-id="7c40b-373">Die `using`-Anweisung muss die erste Zeile im Skript sein.</span><span class="sxs-lookup"><span data-stu-id="7c40b-373">The `using` statement needs to be the first line of your script.</span></span> <span data-ttu-id="7c40b-374">Durch Deklarieren eines Namespaces können Sie diese Anweisung in PowerShell weglassen, wenn Sie auf Datentypen verweisen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-374">By declaring a namespace, PowerShell lets you leave it off of the data types when you reference them.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

<span data-ttu-id="7c40b-375">Damit wird `List` viel nützlicher.</span><span class="sxs-lookup"><span data-stu-id="7c40b-375">This makes the `List` much more usable.</span></span>

<span data-ttu-id="7c40b-376">Ihnen steht eine weitere ähnliche Methode zur Verfügung: `Add`.</span><span class="sxs-lookup"><span data-stu-id="7c40b-376">You have a similar `Add` method available to you.</span></span> <span data-ttu-id="7c40b-377">Im Gegensatz zu ArrayList gibt es keinen Rückgabewert für die `Add`-Methode, daher müssen wir `void` nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-377">Unlike the ArrayList, there is no return value on the `Add` method so we don't have to `void` it.</span></span>

```powershell
$myList.Add(10)
```

<span data-ttu-id="7c40b-378">Dennoch können wir wie in anderen Arrays auf die Elemente zugreifen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-378">And we can still access the elements like other arrays.</span></span>

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a><span data-ttu-id="7c40b-379">List[PSObject]</span><span class="sxs-lookup"><span data-stu-id="7c40b-379">List[PSObject]</span></span>

<span data-ttu-id="7c40b-380">Sie können mit Listen beliebiger Typen arbeiten. Wenn Sie aber den Objekttyp nicht kennen, können Sie `[List[PSObject]]` als Container für die Objekte verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-380">You can have a list of any type, but when you don’t know the type of objects, you can use `[List[PSObject]]` to contain them.</span></span>

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a><span data-ttu-id="7c40b-381">Remove()</span><span class="sxs-lookup"><span data-stu-id="7c40b-381">Remove()</span></span>

<span data-ttu-id="7c40b-382">Sowohl `ArrayList` als auch das generische `List[]` unterstützen das Entfernen von Elementen aus der Auflistung.</span><span class="sxs-lookup"><span data-stu-id="7c40b-382">The `ArrayList` and the generic `List[]` both support removing items from the collection.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

<span data-ttu-id="7c40b-383">Bei Werttypen wird der erste Wert aus der Liste entfernt.</span><span class="sxs-lookup"><span data-stu-id="7c40b-383">When working with value types, it removes the first one from the list.</span></span> <span data-ttu-id="7c40b-384">Sie können die Funktion immer wieder aufrufen, um den jeweils ersten Wert zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-384">You can call it over and over again to keep removing that value.</span></span> <span data-ttu-id="7c40b-385">Bei Verweistypen müssen Sie das Objekt angeben, das entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="7c40b-385">If you have reference types, you have to provide the object that you want removed.</span></span>

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

<span data-ttu-id="7c40b-386">Die remove-Methode gibt `true` zurück, wenn sie das Element in der Auflistung finden und daraus entfernen konnte.</span><span class="sxs-lookup"><span data-stu-id="7c40b-386">The remove method returns `true` if it was able to find and remove the item from the collection.</span></span>

### <a name="more-collections"></a><span data-ttu-id="7c40b-387">Weitere Auflistungen</span><span class="sxs-lookup"><span data-stu-id="7c40b-387">More collections</span></span>

<span data-ttu-id="7c40b-388">Es gibt noch viel mehr Auflistungen, die verwendet werden können, aber die gerade vorgestellten sind gute generische Ersatzmöglichkeiten für Arrays.</span><span class="sxs-lookup"><span data-stu-id="7c40b-388">There are many other collections that can be used but these are the good generic array replacements.</span></span>
<span data-ttu-id="7c40b-389">Wenn Sie mehr über diese Optionen erfahren möchten, sehen Sie sich dieses [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) an, das [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) zusammengestellt hat.</span><span class="sxs-lookup"><span data-stu-id="7c40b-389">If you're interested in learning about more of these options, take a look at this [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) that [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) put together.</span></span>

## <a name="other-nuances"></a><span data-ttu-id="7c40b-390">Andere Nuancen</span><span class="sxs-lookup"><span data-stu-id="7c40b-390">Other nuances</span></span>

<span data-ttu-id="7c40b-391">Die wichtigen Funktionen habe ich abgedeckt, und jetzt möchte ich Ihnen noch einige weitere Aspekte vorstellen, bevor ich zum Ende komme.</span><span class="sxs-lookup"><span data-stu-id="7c40b-391">Now that I have covered all the major functionality, here are a few more things that I wanted to mention before I wrap this up.</span></span>

### <a name="pre-sized-arrays"></a><span data-ttu-id="7c40b-392">Arrays mit vorab festgelegter Größe</span><span class="sxs-lookup"><span data-stu-id="7c40b-392">Pre-sized arrays</span></span>

<span data-ttu-id="7c40b-393">Ich habe bereits erläutert, dass Sie die Größe eines Arrays nach dem Erstellen nicht mehr ändern können.</span><span class="sxs-lookup"><span data-stu-id="7c40b-393">I mentioned that you can't change the size of an array once it's created.</span></span> <span data-ttu-id="7c40b-394">Wir können ein Array mit einer vorab festgelegten Größe erstellen, indem wir das Array mit dem Konstruktor `new($size)` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-394">We can create an array of a pre-determined size by calling it with the `new($size)` constructor.</span></span>

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a><span data-ttu-id="7c40b-395">Multiplizieren von Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-395">Multiplying arrays</span></span>

<span data-ttu-id="7c40b-396">Ein interessanter kleiner Trick ist, dass Sie ein Array mit einer Ganzzahl multiplizieren können.</span><span class="sxs-lookup"><span data-stu-id="7c40b-396">An interesting little trick is that you can multiply an array by an integer.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a><span data-ttu-id="7c40b-397">Initialisieren mit 0</span><span class="sxs-lookup"><span data-stu-id="7c40b-397">Initialize with 0</span></span>

<span data-ttu-id="7c40b-398">Es kommt häufig vor, dass Sie ein Array erstellen möchten, das nur aus Nullen besteht.</span><span class="sxs-lookup"><span data-stu-id="7c40b-398">A common scenario is that you want to create an array with all zeros.</span></span> <span data-ttu-id="7c40b-399">Wenn Sie nur Ganzzahlen verwenden, enthält ein stark typisiertes Array mit Ganzzahlen standardmäßig nur Nullen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-399">If you're only going to have integers, a strongly typed array of integers defaults to all zeros.</span></span>

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

<span data-ttu-id="7c40b-400">Hier können wir auch den Multiplikationstrick anwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-400">We can use the multiplying trick to do this too.</span></span>

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

<span data-ttu-id="7c40b-401">Das Schöne bei diesem Trick ist, dass Sie jeden Wert verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7c40b-401">The nice thing about the multiplying trick is that you can use any value.</span></span> <span data-ttu-id="7c40b-402">Wenn Sie also lieber `255` als Standardwert haben möchten, ist dies ein guter Ansatz.</span><span class="sxs-lookup"><span data-stu-id="7c40b-402">So if you would rather have `255` as your default value, this would be a good way to do it.</span></span>

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a><span data-ttu-id="7c40b-403">Geschachtelte Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-403">Nested arrays</span></span>

<span data-ttu-id="7c40b-404">Ein Array innerhalb eines Arrays wird als geschachteltes Array bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7c40b-404">An array inside an array is called a nested array.</span></span> <span data-ttu-id="7c40b-405">Ich verwende diese selten in PowerShell, arbeite aber in anderen Sprachen häufig damit.</span><span class="sxs-lookup"><span data-stu-id="7c40b-405">I don't use these much in PowerShell but I have used them more in other languages.</span></span> <span data-ttu-id="7c40b-406">Wenn Ihre Daten in ein rasterförmiges Muster passen, sollten Sie ein Array aus Arrays in Erwägung ziehen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-406">Consider using an array of arrays when your data fits in a grid like pattern.</span></span>

<span data-ttu-id="7c40b-407">Es gibt zwei Möglichkeiten, ein zweidimensionales Array zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-407">Here are two ways we can create a two-dimensional array.</span></span>

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

<span data-ttu-id="7c40b-408">Das Komma ist in diesen Beispielen sehr wichtig.</span><span class="sxs-lookup"><span data-stu-id="7c40b-408">The comma is very important in those examples.</span></span> <span data-ttu-id="7c40b-409">Weiter oben habe ich ein Beispiel eines normalen Arrays auf mehreren Zeilen vorgestellt, bei dem das Komma optional war.</span><span class="sxs-lookup"><span data-stu-id="7c40b-409">I gave an earlier example of a normal array on multiple lines where the comma was optional.</span></span> <span data-ttu-id="7c40b-410">Bei mehrdimensionalen Arrays ist das nicht der Fall.</span><span class="sxs-lookup"><span data-stu-id="7c40b-410">That isn't the case with a multi-dimensional array.</span></span>

<span data-ttu-id="7c40b-411">Bei Verwendung eines geschachtelten Arrays ändert sich die Indexnotation geringfügig.</span><span class="sxs-lookup"><span data-stu-id="7c40b-411">The way we use the index notation changes slightly now that we've a nested array.</span></span> <span data-ttu-id="7c40b-412">Mit `$data` (siehe oben) können wir auf den Wert 3 zugreifen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-412">Using the `$data` above, this is how we would access the value 3.</span></span>

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

<span data-ttu-id="7c40b-413">Umschließen Sie jede Schachtelungsebene des Arrays mit eckigen Klammern.</span><span class="sxs-lookup"><span data-stu-id="7c40b-413">Add a set of bracket for each level of array nesting.</span></span> <span data-ttu-id="7c40b-414">Der erste Satz Klammern umschließt das äußerste Array, danach geht es immer eine Ebene weiter nach innen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-414">The first set of brackets is for the outer most array and then you work your way in from there.</span></span>

### <a name="write-output--noenumerate"></a><span data-ttu-id="7c40b-415">Write-Output -NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="7c40b-415">Write-Output -NoEnumerate</span></span>

<span data-ttu-id="7c40b-416">In PowerShell werden Arrays häufig aufgezählt, oder ihre Umschließung wird aufgehoben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-416">PowerShell likes to unwrap or enumerate arrays.</span></span> <span data-ttu-id="7c40b-417">Dies ist ein wesentlicher Aspekt der Art und Weise, in der PowerShell die Pipeline verwendet, aber manchmal ist diese Vorgehensweise nicht wünschenswert.</span><span class="sxs-lookup"><span data-stu-id="7c40b-417">This is a core aspect of the way PowerShell uses the pipeline but there are times that you don't want that to happen.</span></span>

<span data-ttu-id="7c40b-418">Ich übergebe Objekte meist per Pipe an `Get-Member`, um Informationen zu den Objekten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-418">I commonly pipe objects to `Get-Member` to learn more about them.</span></span> <span data-ttu-id="7c40b-419">Wenn ich auf diese Weise ein Array übergebe, wird dessen Umschließung aufgehoben, und „Get-Member“ zeigt die Member des Arrays an, nicht das tatsächliche Array.</span><span class="sxs-lookup"><span data-stu-id="7c40b-419">When I pipe an array to it, it gets unwrapped and Get-Member sees the members of the array and not the actual array.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

<span data-ttu-id="7c40b-420">Um zu verhindern, dass die Umschließung eines Arrays aufgehoben wird, können Sie `Write-Object -NoEnumerate` verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-420">To prevent that unwrap of the array, you can use `Write-Object -NoEnumerate`.</span></span>

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

<span data-ttu-id="7c40b-421">Ich kenne auch noch eine zwei Möglichkeit, das ist aber eher ein Hack (und in der Regel vermeide ich solche Hacks).</span><span class="sxs-lookup"><span data-stu-id="7c40b-421">I have a second way that's more of a hack (and I try to avoid hacks like this).</span></span> <span data-ttu-id="7c40b-422">Sie können ein Komma vor das Array setzen, bevor Sie es per Pipe übergeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-422">You can place a comma in front of the array before you pipe it.</span></span>

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a><span data-ttu-id="7c40b-423">Zurückgeben eines Arrays</span><span class="sxs-lookup"><span data-stu-id="7c40b-423">Return an array</span></span>

<span data-ttu-id="7c40b-424">Die Umschließung eines Arrays wird auch aufgehoben, wenn Sie Werte aus einer Funktion ausgeben oder zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="7c40b-424">This unwrapping of arrays also happens when you output or return values from a function.</span></span> <span data-ttu-id="7c40b-425">Sie erhalten weiterhin ein Array, wenn Sie die Ausgabe einer Variable zuweisen, daher ist dies in der Regel kein Problem.</span><span class="sxs-lookup"><span data-stu-id="7c40b-425">You can still get an array if you assign the output to a variable so this isn't commonly an issue.</span></span>

<span data-ttu-id="7c40b-426">Der Haken bei der Sache ist, dass Sie dadurch über ein neues Array verfügen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-426">The catch is that you have a new array.</span></span> <span data-ttu-id="7c40b-427">Wenn dies ein Problem darstellt, können Sie `Write-Output -NoEnumerate $array` oder `return ,$array` als Umgehung verwenden.</span><span class="sxs-lookup"><span data-stu-id="7c40b-427">If that is ever a problem, you can use `Write-Output -NoEnumerate $array` or `return ,$array` to work around it.</span></span>

## <a name="anything-else"></a><span data-ttu-id="7c40b-428">Noch etwas?</span><span class="sxs-lookup"><span data-stu-id="7c40b-428">Anything else?</span></span>

<span data-ttu-id="7c40b-429">Ich weiß, das waren eine Menge Informationen.</span><span class="sxs-lookup"><span data-stu-id="7c40b-429">I know this is all a lot to take in.</span></span> <span data-ttu-id="7c40b-430">Ich hoffe, dass Sie jedes Mal, wenn Sie diesen Artikel lesen, etwas Neues lernen und diesen Artikel noch lange als gute Referenz nutzen können.</span><span class="sxs-lookup"><span data-stu-id="7c40b-430">My hope is that you learn something from this article every time you read it and that it turns out to be a good reference for you for a long time to come.</span></span> <span data-ttu-id="7c40b-431">Wenn Sie den Artikel hilfreich finden, teilen Sie ihn gerne mit anderen, die auch davon profitieren könnten.</span><span class="sxs-lookup"><span data-stu-id="7c40b-431">If you found this to be helpful, please share it with others you think may get value out of it.</span></span>

<span data-ttu-id="7c40b-432">Jetzt möchte ich Ihnen noch einen ähnlichen Artikel ans Herz legen, den ich über [Hashtabellen][] geschrieben habe.</span><span class="sxs-lookup"><span data-stu-id="7c40b-432">From here, I would recommend you check out a similar post that I wrote about [hashtables][].</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch-Anweisung]: everything-about-switch.md
[switch statement]: everything-about-switch.md
[Hashtabellen]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/ (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken)
[How to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition (Wie lässt sich überprüfen, ob jeder Wert in einem Array mit einem angegebenen Wert übereinstimmt?)
[how to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[Lösung]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
