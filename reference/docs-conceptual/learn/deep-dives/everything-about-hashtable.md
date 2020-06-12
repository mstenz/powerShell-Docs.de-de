---
title: Alles, was Sie schon immer über Hashtabellen wissen wollten
description: Hashtabellen spielen eine wichtige Rolle in PowerShell, daher sollten Sie mit dem Konzept vertraut sein.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 336c32cca351cc7d87f3300364c075ba7bd8aaeb
ms.sourcegitcommit: 0b9268e7b92fb76b47169b72e28de43e4bfe7fbf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307128"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a><span data-ttu-id="34fa5-103">Alles, was Sie schon immer über Hashtabellen wissen wollten</span><span class="sxs-lookup"><span data-stu-id="34fa5-103">Everything you wanted to know about hashtables</span></span>

<span data-ttu-id="34fa5-104">Heute möchte ich einen Schritt zurückgehen und über [Hashtabellen][] sprechen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-104">I want to take a step back and talk about [hashtables][].</span></span> <span data-ttu-id="34fa5-105">Ich verwende sie die ganze Zeit.</span><span class="sxs-lookup"><span data-stu-id="34fa5-105">I use them all the time now.</span></span> <span data-ttu-id="34fa5-106">Nach dem Treffen unserer Benutzergruppe gestern habe ich sie einem anderen Benutzer erklärt und dabei festgestellt, dass mich dieselben Aspekte verwirren wie ihn.</span><span class="sxs-lookup"><span data-stu-id="34fa5-106">I was teaching someone about them after our user group meeting last night and I realized I had the same confusion about them as he had.</span></span> <span data-ttu-id="34fa5-107">Hashtabellen spielen eine wichtige Rolle in PowerShell, daher sollten Sie mit dem Konzept vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="34fa5-107">Hashtables are really important in PowerShell so it's good to have a solid understanding of them.</span></span>

> [!NOTE]
> <span data-ttu-id="34fa5-108">Die [Originalversion][] dieses Artikels wurde im Blog von [@KevinMarquette][] veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="34fa5-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="34fa5-109">Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="34fa5-110">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="34fa5-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="hashtable-as-a-collection-of-things"></a><span data-ttu-id="34fa5-111">Hashtabellen als Auflistung</span><span class="sxs-lookup"><span data-stu-id="34fa5-111">Hashtable as a collection of things</span></span>

<span data-ttu-id="34fa5-112">Sie sollten sich eine **Hashtabelle** zunächst als Auflistung in der herkömmlichen Definition einer Hashtabelle vorstellen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-112">I want you to first see a **Hashtable** as a collection in the traditional definition of a hashtable.</span></span> <span data-ttu-id="34fa5-113">Diese Definition hilft dabei, die Funktionsweise von Hashtabellen zu verstehen – und dieses Grundverständnis ist erforderlich, wenn es später um fortgeschrittene Prozesse geht.</span><span class="sxs-lookup"><span data-stu-id="34fa5-113">This definition gives you a fundamental understanding of how they work when they get used for more advanced stuff later.</span></span> <span data-ttu-id="34fa5-114">Wenn dieses Grundverständnis fehlt, entsteht oft Verwirrung.</span><span class="sxs-lookup"><span data-stu-id="34fa5-114">Skipping this understanding is often a source of confusion.</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="34fa5-115">Was ist ein Array?</span><span class="sxs-lookup"><span data-stu-id="34fa5-115">What is an array?</span></span>

<span data-ttu-id="34fa5-116">Bevor wir in das Thema **Hashtabelle** eintauchen, muss ich kurz auf [Arrays][] eingehen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-116">Before I jump into what a **Hashtable** is, I need to mention [arrays][] first.</span></span> <span data-ttu-id="34fa5-117">Ein Array ist – zumindest für den Zweck der vorliegenden Diskussion – eine Liste oder Auflistung von Werten oder Objekten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-117">For the purpose of this discussion, an array is a list or collection of values or objects.</span></span>

```powershell
$array = @(1,2,3,5,7,11)
```

<span data-ttu-id="34fa5-118">Sobald Sie Ihre Elemente in ein Array eingefügt haben, können Sie `foreach` zum Durchlaufen der Liste oder einen Index zum Zugreifen auf einzelne Elemente im Array verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-118">Once you have your items into an array, you can either use `foreach` to iterate over the list or use an index to access individual elements in the array.</span></span>

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

<span data-ttu-id="34fa5-119">Sie können auch auf die gleiche Weise Werte mit einem Index aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="34fa5-119">You can also update values using an index in the same way.</span></span>

```powershell
$array[2] = 13
```

<span data-ttu-id="34fa5-120">Damit habe ich praktisch nur an der Oberfläche von Arrays gekratzt, aber ich wollte sie auch nur für das Verständnis von Hashtabellen in den richtigen Kontext setzen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-120">I just scratched the surface on arrays but that should put them into the right context as I move onto hashtables.</span></span>

## <a name="what-is-a-hashtable"></a><span data-ttu-id="34fa5-121">Was ist eine Hashtabelle?</span><span class="sxs-lookup"><span data-stu-id="34fa5-121">What is a hashtable?</span></span>

<span data-ttu-id="34fa5-122">Ich beginne mit einer grundlegenden technischen Beschreibung von Hashtabellen im Allgemeinen, bevor ich mit den weiteren Verwendungsmöglichkeiten in PowerShell fortfahre.</span><span class="sxs-lookup"><span data-stu-id="34fa5-122">I'm going to start with a basic technical description of what hashtables are, in the general sense, before I shift into the other ways PowerShell uses them.</span></span>

<span data-ttu-id="34fa5-123">Eine Hashtabelle ist eine Datenstruktur – ganz ähnlich einem Array, außer dass jeder Wert (bzw. jedes Objekt) mithilfe eines Schlüssels gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="34fa5-123">A hashtable is a data structure, much like an array, except you store each value (object) using a key.</span></span> <span data-ttu-id="34fa5-124">Im Grunde ist es ein Schlüssel-Wert-Speicher.</span><span class="sxs-lookup"><span data-stu-id="34fa5-124">It's a basic key/value store.</span></span> <span data-ttu-id="34fa5-125">Als Erstes erstellen wir eine leere Hashtabelle.</span><span class="sxs-lookup"><span data-stu-id="34fa5-125">First, we create an empty hashtable.</span></span>

```powershell
$ageList = @{}
```

<span data-ttu-id="34fa5-126">Beachten Sie, dass zum Definieren einer Hashtabelle geschweifte statt runde Klammern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-126">Notice that braces, instead of parentheses, are used to define a hashtable.</span></span> <span data-ttu-id="34fa5-127">Dann fügen wir mithilfe eines Schlüssels ein Element hinzu:</span><span class="sxs-lookup"><span data-stu-id="34fa5-127">Then we add an item using a key like this:</span></span>

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

<span data-ttu-id="34fa5-128">Der Name der Person ist der Schlüssel, das Alter ist der Wert, den ich speichern möchte.</span><span class="sxs-lookup"><span data-stu-id="34fa5-128">The person's name is the key and their age is the value that I want to save.</span></span>

## <a name="using-the-brackets-for-access"></a><span data-ttu-id="34fa5-129">Verwenden von eckigen Klammern für den Zugriff</span><span class="sxs-lookup"><span data-stu-id="34fa5-129">Using the brackets for access</span></span>

<span data-ttu-id="34fa5-130">Sobald Sie Werte zur Hashtabelle hinzugefügt haben, können Sie diese mit demselben Schlüssel wieder abrufen (anstatt einen numerischen Index zu verwenden, wie es bei einem Array erforderlich wäre).</span><span class="sxs-lookup"><span data-stu-id="34fa5-130">Once you add your values to the hashtable, you can pull them back out using that same key (instead of using a numeric index like you would have for an array).</span></span>

```powershell
$ageList['Kevin']
$ageList['Alex']
```

<span data-ttu-id="34fa5-131">Wenn ich Kevins Alter abrufen möchte, verwende ich seinen Namen für den Zugriff.</span><span class="sxs-lookup"><span data-stu-id="34fa5-131">When I want Kevin's age, I use his name to access it.</span></span> <span data-ttu-id="34fa5-132">Wir können diesen Ansatz auch verwenden, um Werte zur Hashtabelle hinzuzufügen oder darin zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="34fa5-132">We can use this approach to add or update values into the hashtable too.</span></span> <span data-ttu-id="34fa5-133">Das funktioniert genauso wie die `add()`-Funktion von oben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-133">This is just like using the `add()` function above.</span></span>

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

<span data-ttu-id="34fa5-134">Es gibt eine weitere Syntax, die Sie verwenden können, um auf Werte zuzugreifen und diese zu aktualisieren. Auf diese Syntax werde ich in einem späteren Abschnitt eingehen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-134">There's another syntax you can use for accessing and updating values that I'll cover in a later section.</span></span> <span data-ttu-id="34fa5-135">Wenn Sie vor PowerShell eine andere Sprache verwendet haben, sollten diese Beispiele zu der Art und Weise passen, mit der Sie Hashtabellen bisher verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-135">If you're coming to PowerShell from another language, these examples should fit in with how you may have used hashtables before.</span></span>

### <a name="creating-hashtables-with-values"></a><span data-ttu-id="34fa5-136">Erstellen von Hashtabellen mit Werten</span><span class="sxs-lookup"><span data-stu-id="34fa5-136">Creating hashtables with values</span></span>

<span data-ttu-id="34fa5-137">Bisher habe ich in den Beispielen eine leere Hashtabelle erstellt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-137">So far I've created an empty hashtable for these examples.</span></span> <span data-ttu-id="34fa5-138">Sie können die Schlüssel und Werte beim Erstellen vorab auffüllen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-138">You can pre-populate the keys and values when you create them.</span></span>

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a><span data-ttu-id="34fa5-139">Als Nachschlagetabelle</span><span class="sxs-lookup"><span data-stu-id="34fa5-139">As a lookup table</span></span>

<span data-ttu-id="34fa5-140">Der wahre Wert dieser Art Hashtabelle liegt darin, dass Sie diese als Nachschlagetabelle verwenden können.</span><span class="sxs-lookup"><span data-stu-id="34fa5-140">The real value of this type of a hashtable is that you can use them as a lookup table.</span></span> <span data-ttu-id="34fa5-141">Hier ist ein einfaches Beispiel.</span><span class="sxs-lookup"><span data-stu-id="34fa5-141">Here is a simple example.</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

<span data-ttu-id="34fa5-142">In diesem Beispiel geben Sie eine Umgebung für die Variable `$env` an, und diese wählt den richtigen Server aus.</span><span class="sxs-lookup"><span data-stu-id="34fa5-142">In this example, you specify an environment for the `$env` variable and it will pick the correct server.</span></span> <span data-ttu-id="34fa5-143">Für eine solche Auswahl könnten Sie auch `switch($env){...}` verwenden, aber eine Hashtabelle ist eine gute Option.</span><span class="sxs-lookup"><span data-stu-id="34fa5-143">You could use a `switch($env){...}` for a selection like this but a hashtable is a nice option.</span></span>

<span data-ttu-id="34fa5-144">Diese Option wird sogar noch besser, wenn Sie die Nachschlagetabelle zur späteren Verwendung dynamisch erstellen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-144">This gets even better when you dynamically build the lookup table to use it later.</span></span> <span data-ttu-id="34fa5-145">Behalten Sie diesen Ansatz also im Hinterkopf, wenn Sie Querverweise benötigen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-145">So think about using this approach when you need to cross reference something.</span></span> <span data-ttu-id="34fa5-146">Dieser Ansatz wäre vermutlich noch häufiger zu finden, wenn die Pipefilterung mit `Where-Object` in PowerShell nicht so gut funktionieren würde.</span><span class="sxs-lookup"><span data-stu-id="34fa5-146">I think we would see this even more if PowerShell wasn't so good at filtering on the pipe with `Where-Object`.</span></span> <span data-ttu-id="34fa5-147">Wenn Sie sich jemals in einer Situation befinden, in der die Leistung eine große Rolle spielt, sollten Sie diesen Ansatz in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-147">If you're ever in a situation where performance matters, this approach needs to be considered.</span></span>

<span data-ttu-id="34fa5-148">Ich behaupte nicht, dass dieser Ansatz immer schneller ist, aber er passt in die Regel: [Wenn Leistung wichtig ist, probier es aus][].</span><span class="sxs-lookup"><span data-stu-id="34fa5-148">I won't say that it's faster, but it does fit into the rule of [If performance matters, test it][].</span></span>

#### <a name="multiselection"></a><span data-ttu-id="34fa5-149">Mehrfachauswahl</span><span class="sxs-lookup"><span data-stu-id="34fa5-149">Multiselection</span></span>

<span data-ttu-id="34fa5-150">Im Allgemeinen sollten Sie sich eine Hashtabelle als Schlüssel-Wert-Paar vorstellen, in dem Sie einen Schlüssel bereitstellen und einen Wert erhalten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-150">Generally, you think of a hashtable as a key/value pair, where you provide one key and get one value.</span></span> <span data-ttu-id="34fa5-151">PowerShell ermöglicht die Bereitstellung eines Arrays aus Schlüsseln, um mehrere Werte abzurufen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-151">PowerShell allows you to provide an array of keys to get multiple values.</span></span>

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

<span data-ttu-id="34fa5-152">In diesem Beispiel verwende ich die Nachschlagetabelle von oben und stelle drei verschiedene Arraystile bereit, um die Übereinstimmungen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-152">In this example, I use the same lookup hashtable from above and provide three different array styles to get the matches.</span></span> <span data-ttu-id="34fa5-153">Das ist ein verborgenes Juwel in PowerShell, das den meisten Benutzern nicht bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-153">This is a hidden gem in PowerShell that most people aren't aware of.</span></span>

## <a name="iterating-hashtables"></a><span data-ttu-id="34fa5-154">Durchlaufen von Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-154">Iterating hashtables</span></span>

<span data-ttu-id="34fa5-155">Da eine Hashtabelle eine Auflistung aus Schlüssel-Wert-Paaren ist, durchlaufen Sie diese auf andere Weise als ein Array oder eine „normale“ Elementliste.</span><span class="sxs-lookup"><span data-stu-id="34fa5-155">Because a hashtable is a collection of key/value pairs, you iterate over it differently than you do for an array or a normal list of items.</span></span>

<span data-ttu-id="34fa5-156">Wenn Sie die Hashtabelle weiterreichen, wird sie in der Pipe als ein einzelnes Objekt behandelt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-156">The first thing to notice is that if you pipe your hashtable, the pipe treats it like one object.</span></span>

```powershell
PS> $ageList | Measure-Object
count : 1
```

<span data-ttu-id="34fa5-157">Dies ist der Fall, auch wenn die `.count`-Eigenschaft Sie darüber informiert, wie viele Werte in der Tabelle enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="34fa5-157">Even though the `.count` property tells you how many values it contains.</span></span>

```powershell
PS> $ageList.count
2
```

<span data-ttu-id="34fa5-158">Sie können dieses Problem umgehen, indem Sie die `.values`-Eigenschaft verwenden, wenn Sie nur die Werte benötigen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-158">You get around this issue by using the `.values` property if all you need is just the values.</span></span>

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

<span data-ttu-id="34fa5-159">Häufig ist es sinnvoller, die Schlüssel aufzuzählen und für den Zugriff auf die Werte zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-159">It's often more useful to enumerate the keys and use them to access the values.</span></span>

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

<span data-ttu-id="34fa5-160">Nachfolgend sehen Sie dasselbe Beispiel mit einer `foreach(){...}`-Schleife.</span><span class="sxs-lookup"><span data-stu-id="34fa5-160">Here is the same example with a `foreach(){...}` loop.</span></span>

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

<span data-ttu-id="34fa5-161">Wir durchlaufen jeden Schlüssel in der Hashtabelle und verwenden ihn für den Zugriff auf den entsprechenden Wert.</span><span class="sxs-lookup"><span data-stu-id="34fa5-161">We are walking each key in the hashtable and then using it to access the value.</span></span> <span data-ttu-id="34fa5-162">Dies ist ein gängiges Muster, wenn Hashtabellen als Auflistung eingesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-162">This is a common pattern when working with hashtables as a collection.</span></span>

### <a name="getenumerator"></a><span data-ttu-id="34fa5-163">GetEnumerator()</span><span class="sxs-lookup"><span data-stu-id="34fa5-163">GetEnumerator()</span></span>

<span data-ttu-id="34fa5-164">Damit kommen wir zu `GetEnumerator()` zum Durchlaufen der Hashtabelle.</span><span class="sxs-lookup"><span data-stu-id="34fa5-164">That brings us to `GetEnumerator()` for iterating over our hashtable.</span></span>

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

<span data-ttu-id="34fa5-165">Der Enumerator liefert alle Schlüssel-Wert-Paare nacheinander.</span><span class="sxs-lookup"><span data-stu-id="34fa5-165">The enumerator gives you each key/value pair one after another.</span></span> <span data-ttu-id="34fa5-166">Er wurde speziell für diesen Anwendungsfall entwickelt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-166">It was designed specifically for this use case.</span></span> <span data-ttu-id="34fa5-167">Vielen Dank an [Mark Kraus](https://get-PowerShellblog.blogspot.com), dass er mich daran erinnert hat.</span><span class="sxs-lookup"><span data-stu-id="34fa5-167">Thank you to [Mark Kraus](https://get-PowerShellblog.blogspot.com) for reminding me of this one.</span></span>

### <a name="badenumeration"></a><span data-ttu-id="34fa5-168">BadEnumeration</span><span class="sxs-lookup"><span data-stu-id="34fa5-168">BadEnumeration</span></span>

<span data-ttu-id="34fa5-169">Ein wichtiges Detail: Sie können eine Hashtabelle nicht ändern, während sie aufgezählt wird.</span><span class="sxs-lookup"><span data-stu-id="34fa5-169">One important detail is that you can't modify a hashtable while it's being enumerated.</span></span> <span data-ttu-id="34fa5-170">Wir beginnen mit unserem grundlegenden `$environments`-Beispiel:</span><span class="sxs-lookup"><span data-stu-id="34fa5-170">If we start with our basic `$environments` example:</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

<span data-ttu-id="34fa5-171">Jetzt versuchen wir, jeden Schlüssel auf denselben Serverwert festzulegen. Das geht schief.</span><span class="sxs-lookup"><span data-stu-id="34fa5-171">And trying to set every key to the same server value fails.</span></span>

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

<span data-ttu-id="34fa5-172">Das geht auch dann schief, wenn es so aussieht, als wäre alles in Ordnung:</span><span class="sxs-lookup"><span data-stu-id="34fa5-172">This will also fail even though it looks like it should also be fine:</span></span>

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

<span data-ttu-id="34fa5-173">Der Trick hierbei ist, die Schlüssel zu klonen, bevor die Enumeration erfolgt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-173">The trick to this situation is to clone the keys before doing the enumeration.</span></span>

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a><span data-ttu-id="34fa5-174">Hashtabellen als Auflistung von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="34fa5-174">Hashtable as a collection of properties</span></span>

<span data-ttu-id="34fa5-175">Bisher wiesen alle Objekte, die wir in der Hashtabelle platziert haben, denselben Typ auf.</span><span class="sxs-lookup"><span data-stu-id="34fa5-175">So far the type of objects we placed in our hashtable were all the same type of object.</span></span> <span data-ttu-id="34fa5-176">Ich habe in allen Beispielen das Alter als Wert und den Namen der Personen als Schlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="34fa5-176">I used ages in all those examples and the key was the person's name.</span></span> <span data-ttu-id="34fa5-177">Das ist eine hervorragende Vorgehensweise, wenn alle Objekte in Ihrer Auflistung einen Namen haben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-177">This is a great way to look at it when your collection of objects each have a name.</span></span> <span data-ttu-id="34fa5-178">Eine weiterer gängiger Einsatzzweck von Hashtabellen in PowerShell sind Auflistungen aus Eigenschaften, bei denen der Schlüssel der Name der Eigenschaft ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-178">Another common way to use hashtables in PowerShell is to hold a collection of properties where the key is the name of the property.</span></span> <span data-ttu-id="34fa5-179">Darum geht es im nächsten Beispiel.</span><span class="sxs-lookup"><span data-stu-id="34fa5-179">I'll step into that idea in this next example.</span></span>

### <a name="property-based-access"></a><span data-ttu-id="34fa5-180">Eigenschaftenbasierter Zugriff</span><span class="sxs-lookup"><span data-stu-id="34fa5-180">Property-based access</span></span>

<span data-ttu-id="34fa5-181">Der Einsatz des eigenschaftenbasierten Zugriffs ändert die Dynamik von Hashtabellen und deren Verwendung in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="34fa5-181">The use of property-based access changes the dynamics of hashtables and how you can use them in PowerShell.</span></span> <span data-ttu-id="34fa5-182">Hier sehen Sie das Beispiel von oben, die Schlüssel werden als Eigenschaften behandelt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-182">Here is our usual example from above treating the keys as properties.</span></span>

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

<span data-ttu-id="34fa5-183">Wie in den Beispielen oben fügt dieses Beispiel die Schlüssel hinzu, wenn sie in der Hashtabelle noch nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="34fa5-183">Just like the examples above, this example adds those keys if they don't exist in the hashtable already.</span></span> <span data-ttu-id="34fa5-184">Je nachdem, wie Sie Ihre Schlüssel definiert haben und wie Ihre Werte lauten, ist das entweder ein bisschen merkwürdig oder einfach perfekt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-184">Depending on how you defined your keys and what your values are, this is either a little strange or a perfect fit.</span></span> <span data-ttu-id="34fa5-185">Das Beispiel mit der Altersliste hat bis zu diesem Punkt hervorragend funktioniert.</span><span class="sxs-lookup"><span data-stu-id="34fa5-185">The age list example has worked great up until this point.</span></span> <span data-ttu-id="34fa5-186">Für den weiteren Verlauf benötigen wir aber ein neues Beispiel.</span><span class="sxs-lookup"><span data-stu-id="34fa5-186">We need a new example for this to feel right going forward.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="34fa5-187">Und wir können `$person` wie folgt Attribute hinzufügen und darauf zugreifen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-187">And we can add and access attributes on the `$person` like this.</span></span>

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

<span data-ttu-id="34fa5-188">Siehe da – plötzlich fühlt sich diese Hashtabelle an wie ein Objekt und verhält sich auch so.</span><span class="sxs-lookup"><span data-stu-id="34fa5-188">All of a sudden this hashtable starts to feel and act like an object.</span></span> <span data-ttu-id="34fa5-189">Es handelt sich noch immer um eine Auflistung von Elementen, daher gelten alle obigen Beispiele weiterhin.</span><span class="sxs-lookup"><span data-stu-id="34fa5-189">It's still a collection of things, so all the examples above still apply.</span></span> <span data-ttu-id="34fa5-190">Wir gehen nur aus einem anderen Blickwinkel an das Ganze heran.</span><span class="sxs-lookup"><span data-stu-id="34fa5-190">We just approach it from a different point of view.</span></span>

### <a name="checking-for-keys-and-values"></a><span data-ttu-id="34fa5-191">Überprüfen auf Schlüssel und Werte</span><span class="sxs-lookup"><span data-stu-id="34fa5-191">Checking for keys and values</span></span>

<span data-ttu-id="34fa5-192">In den meisten Fällen können Sie einfach folgendermaßen testen, ob ein Wert vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="34fa5-192">In most cases, you can just test for the value with something like this:</span></span>

```powershell
if( $person.age ){...}
```

<span data-ttu-id="34fa5-193">Das sieht so einfach aus, war aber für mich eine Quelle zahlreicher Fehler, weil ich in meiner Logik ein wichtiges Detail übersehen hatte.</span><span class="sxs-lookup"><span data-stu-id="34fa5-193">It's simple but has been the source of many bugs for me because I was overlooking one important detail in my logic.</span></span> <span data-ttu-id="34fa5-194">Ich habe diese Anweisung verwendet, um zu testen, ob ein Schlüssel vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-194">I started to use it to test if a key was present.</span></span> <span data-ttu-id="34fa5-195">Wenn der Wert `$false` oder Null ist, gibt diese Anweisung unerwartet `$false` zurück.</span><span class="sxs-lookup"><span data-stu-id="34fa5-195">When the value was `$false` or zero, that statement would return `$false` unexpectedly.</span></span>

```powershell
if( $person.age -ne $null ){...}
```

<span data-ttu-id="34fa5-196">Damit lässt sich das Problem der Nullwerte umgehen, aber nicht das Problem von „$null“ im Gegensatz zu nicht vorhandenen Schlüsseln.</span><span class="sxs-lookup"><span data-stu-id="34fa5-196">This works around that issue for zero values but not $null vs non-existent keys.</span></span> <span data-ttu-id="34fa5-197">In den meisten Fällen müssen Sie diesen Unterschied nicht machen, es gibt aber Funktionen, bei denen dies notwendig ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-197">Most of the time you don't need to make that distinction but there are functions for when you do.</span></span>

```powershell
if( $person.ContainsKey('age') ){...}
```

<span data-ttu-id="34fa5-198">Wir haben auch eine `ContainsValue()`-Funktion für Situationen, in denen Sie auf einen Wert prüfen müssen, ohne den Schlüssel zu kennen oder die gesamte Auflistung zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-198">We also have a `ContainsValue()` for the situation where you need to test for a value without knowing the key or iterating the whole collection.</span></span>

### <a name="removing-and-clearing-keys"></a><span data-ttu-id="34fa5-199">Entfernen und Leeren von Schlüsseln</span><span class="sxs-lookup"><span data-stu-id="34fa5-199">Removing and clearing keys</span></span>

<span data-ttu-id="34fa5-200">Sie können Schlüssel mit der Funktion `.Remove()` entfernen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-200">You can remove keys with the `.Remove()` function.</span></span>

```powershell
$person.remove('age')
```

<span data-ttu-id="34fa5-201">Indem Sie einen `$null`-Wert zuweisen, bleibt einfach ein Schlüssel mit einem `$null`-Wert übrig.</span><span class="sxs-lookup"><span data-stu-id="34fa5-201">Assigning them a `$null` value just leaves you with a key that has a `$null` value.</span></span>

<span data-ttu-id="34fa5-202">Eine gängige Vorgehensweise zum Leeren einer Hashtabelle besteht drin, diese in einer leeren Hashtabelle zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="34fa5-202">A common way to clear a hashtable is to just initialize it to an empty hashtable.</span></span>

```powershell
$person = @{}
```

<span data-ttu-id="34fa5-203">Dies funktioniert zwar, aber Sie sollten stattdessen versuchen, die `clear()`-Funktion zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-203">While that does work, try to use the `clear()` function instead.</span></span>

```powershell
$person.clear()
```

<span data-ttu-id="34fa5-204">Dies ist einer der Fälle, in denen durch Verwendung der Funktion ein selbst dokumentierender Code entsteht und die Absichten des Codes sehr klar dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-204">This is one of those instances where using the function creates self-documenting code and it makes the intentions of the code very clean.</span></span>

## <a name="all-the-fun-stuff"></a><span data-ttu-id="34fa5-205">Alles, was Spaß macht</span><span class="sxs-lookup"><span data-stu-id="34fa5-205">All the fun stuff</span></span>

### <a name="ordered-hashtables"></a><span data-ttu-id="34fa5-206">Geordnete Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-206">Ordered hashtables</span></span>

<span data-ttu-id="34fa5-207">Standardmäßig sind Hashtabellen nicht geordnet (sortiert).</span><span class="sxs-lookup"><span data-stu-id="34fa5-207">By default, hashtables aren't ordered (or sorted).</span></span> <span data-ttu-id="34fa5-208">Im herkömmlichen Kontext spielt die Reihenfolge keine Rolle, wenn Sie für den Zugriff auf Werte immer einen Schlüssel verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-208">In the traditional context, the order doesn't matter when you always use a key to access values.</span></span> <span data-ttu-id="34fa5-209">Möglicherweise möchten Sie aber, dass die Eigenschaften in der von Ihnen definierten Reihenfolge bleiben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-209">You may find that you want the properties to stay in the order that you define them.</span></span> <span data-ttu-id="34fa5-210">Glücklicherweise gibt es eine Möglichkeit, dies zu erreichen: mit dem Schlüsselwort `ordered`.</span><span class="sxs-lookup"><span data-stu-id="34fa5-210">Thankfully, there's a way to do that with the `ordered` keyword.</span></span>

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="34fa5-211">Wenn Sie die Schlüssel und Werte jetzt aufzählen, bleiben sie in der gegebenen Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="34fa5-211">Now when you enumerate the keys and values, they stay in that order.</span></span>

### <a name="inline-hashtables"></a><span data-ttu-id="34fa5-212">Inline-Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-212">Inline hashtables</span></span>

<span data-ttu-id="34fa5-213">Wenn Sie eine Hashtabelle auf einer einzigen Zeile definieren, können Sie die Schlüssel-Wert-Paare mit Semikolons trennen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-213">When you're defining a hashtable on one line, you can separate the key/value pairs with a semicolon.</span></span>

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

<span data-ttu-id="34fa5-214">Das ist praktisch, wenn Sie sie in der Pipe erstellen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-214">This will come in handy if you're creating them on the pipe.</span></span>

### <a name="custom-expressions-in-common-pipeline-commands"></a><span data-ttu-id="34fa5-215">Benutzerdefinierte Ausdrücke in gängigen Pipelinebefehlen</span><span class="sxs-lookup"><span data-stu-id="34fa5-215">Custom expressions in common pipeline commands</span></span>

<span data-ttu-id="34fa5-216">Es gibt einige Cmdlets, die die Verwendung von Hashtabellen zum Erstellen benutzerdefinierter oder berechneter Eigenschaften unterstützen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-216">There are a few cmdlets that support the use of hashtables to create custom or calculated properties.</span></span> <span data-ttu-id="34fa5-217">Dies sehen wir meist bei `Select-Object` und `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="34fa5-217">You commonly see this with `Select-Object` and `Format-Table`.</span></span> <span data-ttu-id="34fa5-218">Die Hashtabellen weisen eine spezielle Syntax auf, die bei vollständiger Erweiterung folgendermaßen aussieht.</span><span class="sxs-lookup"><span data-stu-id="34fa5-218">The hashtables have a special syntax that looks like this when fully expanded.</span></span>

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

<span data-ttu-id="34fa5-219">Das Cmdlet bezeichnet die Spalte mit `name`.</span><span class="sxs-lookup"><span data-stu-id="34fa5-219">The `name` is what the cmdlet would label that column.</span></span> <span data-ttu-id="34fa5-220">`expression` ist ein Skriptblock, der ausgeführt wird, wobei `$_` der Wert des Objekts in der Pipe ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-220">The `expression` is a script block that is executed where `$_` is the value of the object on the pipe.</span></span> <span data-ttu-id="34fa5-221">Hier sehen Sie das Skript in Aktion:</span><span class="sxs-lookup"><span data-stu-id="34fa5-221">Here is that script in action:</span></span>

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

<span data-ttu-id="34fa5-222">Ich habe das Ganze in einer Variable platziert, aber Sie könnten es auch inline definieren und bei der Gelegenheit `name` zu `n` sowie `expression` zu `e` verkürzen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-222">I placed that in a variable but it could easily be defined inline and you can shorten `name` to `n` and `expression` to `e` while you're at it.</span></span>

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

<span data-ttu-id="34fa5-223">Mir persönlich gefällt nicht, dass Befehle damit so lang werden, und außerdem werden damit schlechte Angewohnheiten gefördert, in die ich nicht verfallen möchte.</span><span class="sxs-lookup"><span data-stu-id="34fa5-223">I personally don't like how long that makes commands and it often promotes some bad behaviors that I won't get into.</span></span> <span data-ttu-id="34fa5-224">Ich erstelle eher eine neue Hashtabelle oder ein `pscustomobject` mit allen benötigten Feldern und Eigenschaften, als diesen Ansatz in Skripts zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-224">I'm more likely to create a new hashtable or `pscustomobject` with all the fields and properties that I want instead of using this approach in scripts.</span></span> <span data-ttu-id="34fa5-225">Es gibt aber sehr viel Code, in dem das so gehandhabt wird, daher wollte ich Sie darauf aufmerksam machen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-225">But there's a lot of code out there that does this so I wanted you to be aware of it.</span></span> <span data-ttu-id="34fa5-226">Auf das Thema `pscustomobject` komme ich etwas später zurück.</span><span class="sxs-lookup"><span data-stu-id="34fa5-226">I talk about creating a `pscustomobject` later on.</span></span>

### <a name="custom-sort-expression"></a><span data-ttu-id="34fa5-227">Benutzerdefinierter Sortierungsausdruck</span><span class="sxs-lookup"><span data-stu-id="34fa5-227">Custom sort expression</span></span>

<span data-ttu-id="34fa5-228">Es ist einfach, eine Auflistung zu sortieren, wenn die Objekte die Daten enthalten, die Sie sortieren möchten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-228">It's easy to sort a collection if the objects have the data that you want to sort on.</span></span> <span data-ttu-id="34fa5-229">Sie können entweder vor dem Sortieren Daten zum Objekt hinzufügen oder einen benutzerdefinierten Ausdruck für `Sort-Object` erstellen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-229">You can either add the data to the object before you sort it or create a custom expression for `Sort-Object`.</span></span>

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

<span data-ttu-id="34fa5-230">In diesem Beispiel nehme ich eine Liste mit Benutzern und verwende ein benutzerdefiniertes Cmdlet, um zusätzliche Informationen nur zur Sortierung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-230">In this example I'm taking a list of users and using some custom cmdlet to get additional information just for the sort.</span></span>

#### <a name="sort-a-list-of-hashtables"></a><span data-ttu-id="34fa5-231">Sortieren einer Liste von Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-231">Sort a list of Hashtables</span></span>

<span data-ttu-id="34fa5-232">Wenn Sie eine Liste von Hashtabellen sortieren möchten, werden Sie feststellen, dass das `Sort-Object` die Schlüssel nicht als Eigenschaften behandelt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-232">If you have a list of hashtables that you want to sort, you'll find that the `Sort-Object` doesn't treat your keys as properties.</span></span> <span data-ttu-id="34fa5-233">Dieses Problem können wir umgehen, indem wir einen benutzerdefinierten Sortierungsausdruck verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-233">We can get a round that by using a custom sort expression.</span></span>

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a><span data-ttu-id="34fa5-234">Übergabe von Hashtabellen in Cmdlets per Splatting</span><span class="sxs-lookup"><span data-stu-id="34fa5-234">Splatting hashtables at cmdlets</span></span>

<span data-ttu-id="34fa5-235">Das ist eine meiner Lieblingsfunktionen für Hashtabellen, die viele Entwickler kaum kennen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-235">This is one of my favorite things about hashtables that many people don't discover early on.</span></span>
<span data-ttu-id="34fa5-236">Der Gedanke dahinter: Anstatt alle Eigenschaften für ein Cmdlet in einer Zeile anzugeben, können Sie diese zuerst in eine Hashtabelle packen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-236">The idea is that instead of providing all the properties to a cmdlet on one line, you can instead pack them into a hashtable first.</span></span> <span data-ttu-id="34fa5-237">Dann können Sie die Hashtabelle auf spezielle Weise an die Funktion übergeben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-237">Then you can give the hashtable to the function in a special way.</span></span>
<span data-ttu-id="34fa5-238">Hier sehen Sie ein Beispiel für die „normale“ Erstellung eines DHCP-Bereichs.</span><span class="sxs-lookup"><span data-stu-id="34fa5-238">Here is an example of creating a DHCP scope the normal way.</span></span>

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

<span data-ttu-id="34fa5-239">Ohne [Splatting][] müsste all dies auf einer einzigen Zeile definiert werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-239">Without using [splatting][], all those things need to be defined on a single line.</span></span> <span data-ttu-id="34fa5-240">Damit läuft die Zeile aus dem Bild oder wird an beliebigen Stellen umbrochen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-240">It either scrolls off the screen or will wrap where ever it feels like.</span></span> <span data-ttu-id="34fa5-241">Im Vergleich dazu ein Befehl, der Splatting verwendet.</span><span class="sxs-lookup"><span data-stu-id="34fa5-241">Now compare that to a command that uses splatting.</span></span>

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

<span data-ttu-id="34fa5-242">Die Verwendung des `@`-Zeichens anstelle von `$` ruft den Splat-Vorgang auf.</span><span class="sxs-lookup"><span data-stu-id="34fa5-242">The use of the `@` sign instead of the `$` is what invokes the splat operation.</span></span>

<span data-ttu-id="34fa5-243">Nehmen Sie sich einen Moment Zeit, und genießen Sie, wie einfach dieses Beispiel zu lesen ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-243">Just take a moment to appreciate how easy that example is to read.</span></span> <span data-ttu-id="34fa5-244">Es handelt sich um exakt denselben Befehl mit exakt denselben Werten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-244">They are the exact same command with all the same values.</span></span> <span data-ttu-id="34fa5-245">Aber dieses zweite Beispiel lässt sich wesentlich einfacher verstehen und im weiteren Verlauf auch verwalten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-245">The second one is easier to understand and maintain going forward.</span></span>

<span data-ttu-id="34fa5-246">Ich verwende Splatting immer dann, wenn ein Befehl zu lang wird.</span><span class="sxs-lookup"><span data-stu-id="34fa5-246">I use splatting anytime the command gets too long.</span></span> <span data-ttu-id="34fa5-247">Unter „zu lang“ verstehe ich Befehle, die dazu führen, dass mein Fenster nach rechts scrollt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-247">I define too long as causing my window to scroll right.</span></span> <span data-ttu-id="34fa5-248">Wenn ich drei Eigenschaften für eine Funktion benötige, stehen die Chancen gut, dass ich das Ganze zu einer Hashtabelle mit Splatting umschreibe.</span><span class="sxs-lookup"><span data-stu-id="34fa5-248">If I hit three properties for a function, odds are that I'll rewrite it using a splatted hashtable.</span></span>

### <a name="splatting-for-optional-parameters"></a><span data-ttu-id="34fa5-249">Splatting für optionale Parameter</span><span class="sxs-lookup"><span data-stu-id="34fa5-249">Splatting for optional parameters</span></span>

<span data-ttu-id="34fa5-250">Eine der häufigsten Gelegenheiten, bei denen ich Splatting verwende, ist die Verarbeitung von optionalen Parametern, die aus anderen Stellen meines Skripts stammen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-250">One of the most common ways I use splatting is to deal with optional parameters that come from some place else in my script.</span></span> <span data-ttu-id="34fa5-251">Angenommen, ich habe eine Funktion, die einen `Get-CIMInstance`-Aufruf mit einem optionalen `$Credential`-Argument umschließt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-251">Let's say I have a function that wraps a `Get-CIMInstance` call that has an optional `$Credential` argument.</span></span>

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

<span data-ttu-id="34fa5-252">Als Erstes erstelle ich meine Hashtabelle mit allgemeinen Parametern.</span><span class="sxs-lookup"><span data-stu-id="34fa5-252">I start by creating my hashtable with common parameters.</span></span> <span data-ttu-id="34fa5-253">Dann füge ich `$Credential` hinzu, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-253">Then I add the `$Credential` if it exists.</span></span>
<span data-ttu-id="34fa5-254">Da ich hier Splatting verwende, benötige ich den Aufruf von `Get-CIMInstance` nur einmal in meinem Code.</span><span class="sxs-lookup"><span data-stu-id="34fa5-254">Because I'm using splatting here, I only need to have the call to `Get-CIMInstance` in my code once.</span></span> <span data-ttu-id="34fa5-255">Dieses Entwurfsmuster ist sehr übersichtlich und kann problemlos eine Vielzahl optionaler Parameter verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-255">This design pattern is very clean and can handle lots of optional parameters easily.</span></span>

<span data-ttu-id="34fa5-256">Um fair zu sein: Sie können Ihre Befehle so schreiben, dass `$null`-Werte für Parameter zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="34fa5-256">To be fair, you could write your commands to allow `$null` values for parameters.</span></span> <span data-ttu-id="34fa5-257">Sie haben nur nicht immer Kontrolle über die anderen Befehle, die Sie aufrufen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-257">You just don't always have control over the other commands you're calling.</span></span>

### <a name="multiple-splats"></a><span data-ttu-id="34fa5-258">Mehrere Splats</span><span class="sxs-lookup"><span data-stu-id="34fa5-258">Multiple splats</span></span>

<span data-ttu-id="34fa5-259">Sie können per Splatting mehrere Hashtabellen im selben Cmdlet übergeben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-259">You can splat multiple hashtables to the same cmdlet.</span></span> <span data-ttu-id="34fa5-260">Sehen wir uns das ursprüngliche Splatting-Beispiel noch einmal an:</span><span class="sxs-lookup"><span data-stu-id="34fa5-260">If we revisit our original splatting example:</span></span>

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

<span data-ttu-id="34fa5-261">Ich verwende diese Methode, wenn ich einen gemeinsamen Satz Parameter habe, die ich an sehr viele Befehle übergebe.</span><span class="sxs-lookup"><span data-stu-id="34fa5-261">I'll use this method when I have a common set of parameters that I'm passing to lots of commands.</span></span>

### <a name="splatting-for-clean-code"></a><span data-ttu-id="34fa5-262">Splatting für einen sauberen Code</span><span class="sxs-lookup"><span data-stu-id="34fa5-262">Splatting for clean code</span></span>

<span data-ttu-id="34fa5-263">Am Splatting eines einzelnen Parameters ist nichts auszusetzen, wenn Ihr Code dadurch sauberer wird.</span><span class="sxs-lookup"><span data-stu-id="34fa5-263">There's nothing wrong with splatting a single parameter if makes you code cleaner.</span></span>

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a><span data-ttu-id="34fa5-264">Splatting bei ausführbaren Dateien</span><span class="sxs-lookup"><span data-stu-id="34fa5-264">Splatting executables</span></span>

<span data-ttu-id="34fa5-265">Splatting funktioniert auch bei einigen ausführbaren Dateien, die eine `/param:value`-Syntax verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-265">Splatting also works on some executables that use a `/param:value` syntax.</span></span> <span data-ttu-id="34fa5-266">`Robocopy.exe` beispielsweise weist einige Parameter wie die folgenden auf.</span><span class="sxs-lookup"><span data-stu-id="34fa5-266">`Robocopy.exe`, for example, has some parameters like this.</span></span>

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

<span data-ttu-id="34fa5-267">Ich weiß nicht, ob dies sehr nützlich ist, aber ich fand es interessant.</span><span class="sxs-lookup"><span data-stu-id="34fa5-267">I don't know that this is all that useful, but I found it interesting.</span></span>

## <a name="adding-hashtables"></a><span data-ttu-id="34fa5-268">Hinzufügen von Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-268">Adding hashtables</span></span>

<span data-ttu-id="34fa5-269">Hashtabellen unterstützen den Additionsoperator zum Kombinieren zweier Hashtabellen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-269">Hashtables support the addition operator to combine two hashtables.</span></span>

```powershell
$person += @{Zip = '78701'}
```

<span data-ttu-id="34fa5-270">Das funktioniert aber nur, wenn die beiden Hashtabellen keinen gemeinsamen Schlüssel verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-270">This only works if the two hashtables don't share a key.</span></span>

## <a name="nested-hashtables"></a><span data-ttu-id="34fa5-271">Geschachtelte Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-271">Nested hashtables</span></span>

<span data-ttu-id="34fa5-272">Wir können Hashtabellen als Werte innerhalb einer Hashtabelle verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-272">We can use hashtables as values inside a hashtable.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

<span data-ttu-id="34fa5-273">Ich habe mit einer einfachen Hashtabelle mit zwei Schlüsseln angefangen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-273">I started with a basic hashtable containing two keys.</span></span> <span data-ttu-id="34fa5-274">Ich habe einen Schlüssel namens `location` mit einer leeren Hashtabelle hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-274">I added a key called `location` with an empty hashtable.</span></span> <span data-ttu-id="34fa5-275">Dann habe ich die letzten beiden Elemente zu dieser `location`-Hashtabelle hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-275">Then I added the last two items to that `location` hashtable.</span></span> <span data-ttu-id="34fa5-276">Das Ganze geht auch inline.</span><span class="sxs-lookup"><span data-stu-id="34fa5-276">We can do this all inline too.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

<span data-ttu-id="34fa5-277">Damit wird dieselbe Hashtabelle erstellt, die Sie oben bereits gesehen haben, und auf die Eigenschaften wird auf dieselbe Weise zugegriffen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-277">This creates the same hashtable that we saw above and can access the properties the same way.</span></span>

```powershell
$person.location.city
Austin
```

<span data-ttu-id="34fa5-278">Es gibt viele Ansätze für die Struktur Ihrer Objekte.</span><span class="sxs-lookup"><span data-stu-id="34fa5-278">There are many ways to approach the structure of your objects.</span></span> <span data-ttu-id="34fa5-279">Hier ein zweiter Blickwinkel auf eine geschachtelte Hashtabelle.</span><span class="sxs-lookup"><span data-stu-id="34fa5-279">Here is a second way to look at a nested hashtable.</span></span>

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

<span data-ttu-id="34fa5-280">Hier vermischen sich die Konzepte der Verwendung von Hashtabellen als Auflistung von Objekten und als Auflistung von Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="34fa5-280">This mixes the concept of using hashtables as a collection of objects and a collection of properties.</span></span> <span data-ttu-id="34fa5-281">Auf die Werte kann immer noch ganz einfach zugegriffen werden, selbst dann, wenn sie auf eine von Ihnen bevorzugte Weise geschachtelt wurden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-281">The values are still easy to access even when they're nested using whatever approach you prefer.</span></span>

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

<span data-ttu-id="34fa5-282">Ich verwende gerne die dot-Eigenschaft, wenn ich die Hashtabelle als Eigenschaft behandle.</span><span class="sxs-lookup"><span data-stu-id="34fa5-282">I tend to use the dot property when I'm treating it like a property.</span></span> <span data-ttu-id="34fa5-283">Das sind im Allgemeinen Dinge, die ich statisch in meinem Code definiert habe und auswendig weiß.</span><span class="sxs-lookup"><span data-stu-id="34fa5-283">Those are generally things I've defined statically in my code and I know them off the top of my head.</span></span> <span data-ttu-id="34fa5-284">Wenn ich die Liste durchlaufen oder programmgesteuert auf die Schlüssel zugreifen muss, verwende ich eckige Klammern, um den Schlüsselnamen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-284">If I need to walk the list or programmatically access the keys, I use the brackets to provide the key name.</span></span>

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

<span data-ttu-id="34fa5-285">Die Möglichkeit, Hashtabellen zu schachteln, bietet viel Flexibilität und jede Menge Optionen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-285">Having the ability to nest hashtables gives you a lot of flexibility and options.</span></span>

### <a name="looking-at-nested-hashtables"></a><span data-ttu-id="34fa5-286">Betrachten von geschachtelten Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-286">Looking at nested hashtables</span></span>

<span data-ttu-id="34fa5-287">Wenn Sie geschachtelte Hashtabellen verwenden, benötigen Sie eine einfache Möglichkeit, diese an der Konsole zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-287">As soon as you start nesting hashtables, you're going to need an easy way to look at them from the console.</span></span> <span data-ttu-id="34fa5-288">Mit dieser letzten Hashtabelle beispielsweise erhalte ich folgende Ausgabe – und diese ist nicht besonders tief geschachtelt:</span><span class="sxs-lookup"><span data-stu-id="34fa5-288">If I take that last hashtable, I get an output that looks like this and it only goes so deep:</span></span>

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

<span data-ttu-id="34fa5-289">Mein Lieblingsbefehl für die Betrachtung ist `ConvertTo-JSON`, weil dieser Befehl sehr sauber ist und ich JSON häufig auch für andere Dinge verwende.</span><span class="sxs-lookup"><span data-stu-id="34fa5-289">My go to command for looking at these things is `ConvertTo-JSON` because it's very clean and I frequently use JSON on other things.</span></span>

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

<span data-ttu-id="34fa5-290">Auch wenn Sie mit JSON nicht vertraut sind, sollten Sie erkennen können, wonach Sie suchen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-290">Even if you don't know JSON, you should be able to see what you're looking for.</span></span> <span data-ttu-id="34fa5-291">Für solche strukturierten Daten gibt es auch den Befehl `Format-Custom`, aber mir gefällt die JSON-Ansicht besser.</span><span class="sxs-lookup"><span data-stu-id="34fa5-291">There's a `Format-Custom` command for structured data like this but I still like the JSON view better.</span></span>

## <a name="creating-objects"></a><span data-ttu-id="34fa5-292">Erstellen von Objekten</span><span class="sxs-lookup"><span data-stu-id="34fa5-292">Creating objects</span></span>

<span data-ttu-id="34fa5-293">Manchmal benötigen Sie einfach nur ein Objekt, und eine Hashtabelle zum Speichern von Eigenschaften ist dafür nicht besonders gut geeignet.</span><span class="sxs-lookup"><span data-stu-id="34fa5-293">Sometimes you just need to have an object and using a hashtable to hold properties just isn't getting the job done.</span></span> <span data-ttu-id="34fa5-294">Üblicherweise möchten Sie die Schlüssel als Spaltennamen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-294">Most commonly you want to see the keys as column names.</span></span> <span data-ttu-id="34fa5-295">Das lässt sich ganz leicht mit einem `pscustomobject` erreichen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-295">A `pscustomobject` makes that easy.</span></span>

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="34fa5-296">Auch wenn Sie das Objekt anfänglich nicht als `pscustomobject` erstellen, können Sie es bei Bedarf später umwandeln.</span><span class="sxs-lookup"><span data-stu-id="34fa5-296">Even if you don't create it as a `pscustomobject` initially, you can always cast it later when needed.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="34fa5-297">Ich habe bereits eine detaillierte Rezension zu [pscustomobject][] verfasst, die Sie sich im Anschluss ansehen sollten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-297">I already have detailed write-up for [pscustomobject][] that you should go read after this one.</span></span> <span data-ttu-id="34fa5-298">Die Rezension baut auf den Informationen auf, die Sie hier erhalten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-298">It builds on a lot of the things learned here.</span></span>

## <a name="reading-and-writing-hashtables-to-file"></a><span data-ttu-id="34fa5-299">Lesen und Schreiben von Hashtabellen in einer Datei</span><span class="sxs-lookup"><span data-stu-id="34fa5-299">Reading and writing hashtables to file</span></span>

### <a name="saving-to-csv"></a><span data-ttu-id="34fa5-300">Speichern in CSV</span><span class="sxs-lookup"><span data-stu-id="34fa5-300">Saving to CSV</span></span>

<span data-ttu-id="34fa5-301">Die Schwierigkeit, eine Hashtabelle in einer CSV-Datei zu speichern, ist eins der Probleme, die ich weiter oben bereits erwähnte.</span><span class="sxs-lookup"><span data-stu-id="34fa5-301">Struggling with getting a hashtable to save to a CSV is one of the difficulties that I was referring to above.</span></span> <span data-ttu-id="34fa5-302">Konvertieren Sie Ihre Hashtabelle in ein `pscustomobject`, und schon lässt sie sich ordnungsgemäß als CSV speichern.</span><span class="sxs-lookup"><span data-stu-id="34fa5-302">Convert your hashtable to a `pscustomobject` and it will save correctly to CSV.</span></span> <span data-ttu-id="34fa5-303">Es ist hilfreich, wenn Sie mit einem `pscustomobject` beginnen, sodass die Spaltenreihenfolge beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="34fa5-303">It helps if you start with a `pscustomobject` so the column order is preserved.</span></span> <span data-ttu-id="34fa5-304">Sie können aber auch bei Bedarf ein vorhandenes Objekt in ein `pscustomobject` umwandeln.</span><span class="sxs-lookup"><span data-stu-id="34fa5-304">But you can cast it to a `pscustomobject` inline if needed.</span></span>

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

<span data-ttu-id="34fa5-305">Ich kann es nur noch einmal empfehlen: Sehen Sie sich meine Rezension zur Verwendung von [pscustomobject][] an.</span><span class="sxs-lookup"><span data-stu-id="34fa5-305">Again, check out my write-up on using a [pscustomobject][].</span></span>

### <a name="saving-a-nested-hashtable-to-file"></a><span data-ttu-id="34fa5-306">Speichern einer geschachtelten Hashtabelle in einer Datei</span><span class="sxs-lookup"><span data-stu-id="34fa5-306">Saving a nested hashtable to file</span></span>

<span data-ttu-id="34fa5-307">Wenn ich eine geschachtelte Hashtabelle in einer Datei speichern und dann wieder in den Code einlesen muss, verwende ich dafür JSON-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="34fa5-307">If I need to save a nested hashtable to a file and then read it back in again, I use the JSON cmdlets to do it.</span></span>

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

<span data-ttu-id="34fa5-308">Bei dieser Methode sind zwei wichtige Punkte zu beachten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-308">There are two important points about this method.</span></span> <span data-ttu-id="34fa5-309">Erstens: JSON wird auf mehreren Zeilen geschrieben, daher muss ich zum erneuten Einlesen in einer einzigen Zeichenfolge die `-Raw`-Option verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-309">First is that the JSON is written out multiline so I need to use the `-Raw` option to read it back into a single string.</span></span> <span data-ttu-id="34fa5-310">Der zweite Punkt ist, dass das importierte Objekt keine `[hashtable]` mehr ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-310">The Second is that the imported object is no longer a `[hashtable]`.</span></span> <span data-ttu-id="34fa5-311">Es ist jetzt ein `[pscustomobject]`, und das kann zu Problemen führen, wenn Sie nicht damit rechnen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-311">It's now a `[pscustomobject]` and that can cause issues if you don't expect it.</span></span>

<span data-ttu-id="34fa5-312">Achten Sie auf Hashtabellen mit vielen Schachtelungsebenen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-312">Watch for deeply-nested hashtables.</span></span> <span data-ttu-id="34fa5-313">Wenn Sie diese in JSON konvertieren, erhalten Sie möglicherweise nicht die erwarteten Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="34fa5-313">When you convert it to JSON you might not get the results you expect.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

<span data-ttu-id="34fa5-314">Verwenden Sie den **Depth**-Parameter, um sicherzustellen, dass alle geschachtelten Hashtabellen erweitert wurden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-314">Use **Depth** parameter to ensure that you have expanded all the nested hashtables.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

<span data-ttu-id="34fa5-315">Wenn Sie beim Import eine `[hashtable]` benötigen, müssen Sie die Befehle `Export-CliXml` und `Import-CliXml` verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-315">If you need it to be a `[hashtable]` on import, then you need to use the `Export-CliXml` and `Import-CliXml` commands.</span></span>

### <a name="converting-json-to-hashtable"></a><span data-ttu-id="34fa5-316">Konvertieren von JSON in eine Hashtabelle</span><span class="sxs-lookup"><span data-stu-id="34fa5-316">Converting JSON to Hashtable</span></span>

<span data-ttu-id="34fa5-317">Wenn Sie JSON-Code in eine `[hashtable]` konvertieren müssen, kenne ich eine Möglichkeit mit dem [JavaScriptSerializer][] in .NET.</span><span class="sxs-lookup"><span data-stu-id="34fa5-317">If you need to convert JSON to a `[hashtable]`, there's one way that I know of to do it with the [JavaScriptSerializer][] in .NET.</span></span>

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

<span data-ttu-id="34fa5-318">Ab PowerShell v6 verwendet die JSON-Unterstützung JSON.NET von NewtonSoft und die zugehörige Hashtabellenunterstützung.</span><span class="sxs-lookup"><span data-stu-id="34fa5-318">Beginning in PowerShell v6, JSON support uses the NewtonSoft JSON.NET and adds hashtable support.</span></span>

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

<span data-ttu-id="34fa5-319">In PowerShell 6.2 wurde der **Depth**-Parameter zu `ConvertFrom-Json` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-319">PowerShell 6.2 added the **Depth** parameter to `ConvertFrom-Json`.</span></span> <span data-ttu-id="34fa5-320">Der Standardwert für **Depth** ist 1024.</span><span class="sxs-lookup"><span data-stu-id="34fa5-320">The default **Depth** is 1024.</span></span>

### <a name="reading-directly-from-a-file"></a><span data-ttu-id="34fa5-321">Direktes Lesen aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="34fa5-321">Reading directly from a file</span></span>

<span data-ttu-id="34fa5-322">Wenn Sie über eine Datei verfügen, die eine Hashtabelle mit PowerShell-Syntax enthält, gibt es eine Möglichkeit, diese Tabelle direkt zu importieren.</span><span class="sxs-lookup"><span data-stu-id="34fa5-322">If you have a file that contains a hashtable using PowerShell syntax, there's a way to import it directly.</span></span>

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

<span data-ttu-id="34fa5-323">Dieser Code importiert die Dateiinhalte in einen `scriptblock` und führt dann eine Überprüfung durch, um sicherzustellen, dass keine weiteren PowerShell-Befehle vorhanden sind. Erst dann erfolgt die Ausführung.</span><span class="sxs-lookup"><span data-stu-id="34fa5-323">It imports the contents of the file into a `scriptblock`, then checks to make sure it doesn't have any other PowerShell commands in it before it executes it.</span></span>

<span data-ttu-id="34fa5-324">Übrigens: Wussten Sie, dass ein Modulmanifest (die PSD1-Datei) einfach eine Hashtabelle ist?</span><span class="sxs-lookup"><span data-stu-id="34fa5-324">On that note, did you know that a module manifest (the psd1 file) is just a hashtable?</span></span>

## <a name="keys-can-be-any-object"></a><span data-ttu-id="34fa5-325">Bei Schlüsseln kann es sich um jedes Objekt handeln</span><span class="sxs-lookup"><span data-stu-id="34fa5-325">Keys can be any object</span></span>

<span data-ttu-id="34fa5-326">In den meisten Fällen sind Schlüssel einfach nur Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-326">Most of the time, the keys are just strings.</span></span> <span data-ttu-id="34fa5-327">Daher können wir Anführungszeichen um so ziemlich jede Zeichenfolge setzen und diese damit zu einem Schlüssel machen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-327">So we can put quotes around anything and make it a key.</span></span>

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

<span data-ttu-id="34fa5-328">Sie können einige lustige Sachen anstellen, von denen Sie möglicherweise noch nichts wussten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-328">You can do some odd things that you may not have realized you could do.</span></span>

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

<span data-ttu-id="34fa5-329">Aber nur weil Sie etwas machen können, heißt das noch lange nicht, dass es auch ratsam ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-329">Just because you can do something, it doesn't mean that you should.</span></span> <span data-ttu-id="34fa5-330">Dieses letzte Beispiel riecht förmlich danach, dass ein Fehler auftritt, und kann von anderen Personen, die Ihren Code lesen, leicht missverstanden werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-330">That last one just looks like a bug waiting to happen and would be easily misunderstood by anyone reading your code.</span></span>

<span data-ttu-id="34fa5-331">Aus technischer Sicht müssen Schlüssel keine Zeichenfolgen sein, sie sind aber leichter verständlich, wenn Sie nur Zeichenfolgen verwenden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-331">Technically your key doesn't have to be a string but they're easier to think about if you only use strings.</span></span> <span data-ttu-id="34fa5-332">Die Indizierung funktioniert aber nicht so gut mit komplexen Schlüsseln.</span><span class="sxs-lookup"><span data-stu-id="34fa5-332">However, indexing doesn't work well with the complex keys.</span></span>

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

<span data-ttu-id="34fa5-333">Auf einen Wert in der Hashtabelle kann nicht immer anhand des zugehörigen Schlüssels zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-333">Accessing a value in the hashtable by its key doesn't always work.</span></span> <span data-ttu-id="34fa5-334">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="34fa5-334">For example:</span></span>

```powershell
$key = $ht.keys[0]
$ht.$key
$ht[$key]
a
```

<span data-ttu-id="34fa5-335">Die Memberzugriffsnotation (`.`) gibt nichts zurück.</span><span class="sxs-lookup"><span data-stu-id="34fa5-335">Using the member access (`.`) notation returns nothing.</span></span> <span data-ttu-id="34fa5-336">Die Arrayindexnotation (`[]`) dagegen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="34fa5-336">But using the array index (`[]`) notation works.</span></span>

## <a name="use-in-automatic-variables"></a><span data-ttu-id="34fa5-337">Verwenden in automatischen Variablen</span><span class="sxs-lookup"><span data-stu-id="34fa5-337">Use in automatic variables</span></span>

### <a name="psboundparameters"></a><span data-ttu-id="34fa5-338">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="34fa5-338">$PSBoundParameters</span></span>

<span data-ttu-id="34fa5-339">[$PSBoundParameters][] ist eine automatische Variable, die nur im Kontext einer Funktion existiert.</span><span class="sxs-lookup"><span data-stu-id="34fa5-339">[$PSBoundParameters][] is an automatic variable that only exists inside the context of a function.</span></span>
<span data-ttu-id="34fa5-340">Sie enthält alle Parameter, mit denen die Funktion aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="34fa5-340">It contains all the parameters that the function was called with.</span></span> <span data-ttu-id="34fa5-341">Die Variable ist nicht direkt eine Hashtabelle, dieser aber so ähnlich, dass Sie sie als eine solche behandeln können.</span><span class="sxs-lookup"><span data-stu-id="34fa5-341">This isn't exactly a hashtable but close enough that you can treat it like one.</span></span>

<span data-ttu-id="34fa5-342">Das bedeutet, dass Sie auch Schlüssel entfernen und die Variable per Splatting an andere Funktionen übergeben können.</span><span class="sxs-lookup"><span data-stu-id="34fa5-342">That includes removing keys and splatting it to other functions.</span></span> <span data-ttu-id="34fa5-343">Wenn Sie selbst Proxyfunktionen schreiben, sollten Sie sich diese Variable näher ansehen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-343">If you find yourself writing proxy functions, take a closer look at this one.</span></span>

<span data-ttu-id="34fa5-344">Weitere Informationen finden Sie unter [about_Automatic_Variables][].</span><span class="sxs-lookup"><span data-stu-id="34fa5-344">See [about_Automatic_Variables][] for more details.</span></span>

### <a name="psboundparameters-gotcha"></a><span data-ttu-id="34fa5-345">PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="34fa5-345">PSBoundParameters gotcha</span></span>

<span data-ttu-id="34fa5-346">Ein wichtiger Aspekt, den Sie bei dieser Variable immer beachten sollten, ist die Tatsache, dass sie nur die Werte enthält, die als Parameter an sie übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-346">One important thing to remember is that this only includes the values that are passed in as parameters.</span></span> <span data-ttu-id="34fa5-347">Wenn Sie auch über Parameter mit Standardwerten verfügen, diese aber vom Aufrufer nicht übergeben werden, enthält `$PSBoundParameters` diese Werte nicht.</span><span class="sxs-lookup"><span data-stu-id="34fa5-347">If you also have parameters with default values but aren't passed in by the caller, `$PSBoundParameters` doesn't contain those values.</span></span> <span data-ttu-id="34fa5-348">Dieser Aspekt wird häufig übersehen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-348">This is commonly overlooked.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="34fa5-349">$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="34fa5-349">$PSDefaultParameterValues</span></span>

<span data-ttu-id="34fa5-350">Mit dieser automatischen Variable können Sie jedem Cmdlet Standardwerte zuweisen, ohne das Cmdlet zu ändern.</span><span class="sxs-lookup"><span data-stu-id="34fa5-350">This automatic variable lets you assign default values to any cmdlet without changing the cmdlet.</span></span>
<span data-ttu-id="34fa5-351">Sehen Sie sich folgendes Beispiel an.</span><span class="sxs-lookup"><span data-stu-id="34fa5-351">Take a look at this example.</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

<span data-ttu-id="34fa5-352">Dieses Beispiel fügt der Hashtabelle `$PSDefaultParameterValues` einen Eintrag hinzu, der `UTF8` als Standardwert für den Parameter `Out-File -Encoding` festlegt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-352">This adds an entry to the `$PSDefaultParameterValues` hashtable that sets `UTF8` as the default value for the `Out-File -Encoding` parameter.</span></span> <span data-ttu-id="34fa5-353">Die Variable ist sitzungsspezifisch, daher sollten Sie sie in Ihrem `$profile` platzieren.</span><span class="sxs-lookup"><span data-stu-id="34fa5-353">This is session-specific so you should place it in your `$profile`.</span></span>

<span data-ttu-id="34fa5-354">Ich verwende sie sehr häufig, um vorab Werte zuzuweisen, die ich dauernd eingebe.</span><span class="sxs-lookup"><span data-stu-id="34fa5-354">I use this often to pre-assign values that I type quite often.</span></span>

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

<span data-ttu-id="34fa5-355">Die Variable akzeptiert auch Platzhalter, Sie können also Werte per Massenvorgang festlegen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-355">This also accepts wildcards so you can set values in bulk.</span></span> <span data-ttu-id="34fa5-356">Hier einige Anwendungsbeispiele:</span><span class="sxs-lookup"><span data-stu-id="34fa5-356">Here are some ways you can use that:</span></span>

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

<span data-ttu-id="34fa5-357">Eine detailliertere Beschreibung finden Sie in diesem großartigen Artikel zu [Automatische Standardwerte][] von [Michael Sorens][].</span><span class="sxs-lookup"><span data-stu-id="34fa5-357">For a more in-depth breakdown, see this great article on [Automatic Defaults][] by [Michael Sorens][].</span></span>

## <a name="regex-matches"></a><span data-ttu-id="34fa5-358">$Matches für reguläre Ausdrücke</span><span class="sxs-lookup"><span data-stu-id="34fa5-358">Regex $Matches</span></span>

<span data-ttu-id="34fa5-359">Wenn Sie den Operator `-match` verwenden, wird eine automatische Variable namens `$matches` mit den Ergebnissen der Übereinstimmung erstellt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-359">When you use the `-match` operator, an automatic variable called `$matches` is created with the results of the match.</span></span> <span data-ttu-id="34fa5-360">Wenn Ihr regulärer Ausdruck Teilausdrücke enthält, werden diese ebenfalls aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="34fa5-360">If you have any sub expressions in your regex, those sub matches are also listed.</span></span>

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a><span data-ttu-id="34fa5-361">Benannte Übereinstimmungen</span><span class="sxs-lookup"><span data-stu-id="34fa5-361">Named matches</span></span>

<span data-ttu-id="34fa5-362">Das ist eins meiner Lieblingsfeatures, das leider nicht sehr bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-362">This is one of my favorite features that most people don't know about.</span></span> <span data-ttu-id="34fa5-363">Wenn Sie eine benannte Übereinstimmung für einen regulären Ausdruck verwenden, können Sie anhand des Namens auf die Übereinstimmung zugreifen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-363">If you use a named regex match, then you can access that match by name on the matches.</span></span>

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

<span data-ttu-id="34fa5-364">Im Beispiel oben ist `(?<Name>.*)` ein benannter Teilausdruck.</span><span class="sxs-lookup"><span data-stu-id="34fa5-364">In the example above, the `(?<Name>.*)` is a named sub expression.</span></span> <span data-ttu-id="34fa5-365">Dieser Wert wird dann in der Eigenschaft `$Matches.Name` platziert.</span><span class="sxs-lookup"><span data-stu-id="34fa5-365">This value is then placed in the `$Matches.Name` property.</span></span>

## <a name="group-object--ashashtable"></a><span data-ttu-id="34fa5-366">Group-Object -AsHashtable</span><span class="sxs-lookup"><span data-stu-id="34fa5-366">Group-Object -AsHashtable</span></span>

<span data-ttu-id="34fa5-367">Ein wenig bekanntes Feature von `Group-Object` ist die Tatsache, dass damit einige Datasets in eine Hashtabelle umgewandelt werden können.</span><span class="sxs-lookup"><span data-stu-id="34fa5-367">One little known feature of `Group-Object` is that it can turn some datasets into a hashtable for you.</span></span>

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

<span data-ttu-id="34fa5-368">Jede Zeile wird in eine Hashtabelle eingefügt, und für den Zugriff wird die angegebene Eigenschaft als Schlüssel verwendet.</span><span class="sxs-lookup"><span data-stu-id="34fa5-368">This will add each row into a hashtable and use the specified property as the key to access it.</span></span>

## <a name="copying-hashtables"></a><span data-ttu-id="34fa5-369">Kopieren von Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="34fa5-369">Copying Hashtables</span></span>

<span data-ttu-id="34fa5-370">Ein wichtiger Aspekt, der Ihnen bewusst sein muss: Hashtabellen sind Objekte.</span><span class="sxs-lookup"><span data-stu-id="34fa5-370">One important thing to know is that hashtables are objects.</span></span> <span data-ttu-id="34fa5-371">Und jede Variable ist nur ein Verweis auf ein Objekt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-371">And each variable is just a reference to an object.</span></span> <span data-ttu-id="34fa5-372">Das bedeutet, dass es mehr Arbeit ist, eine gültige Kopie einer Hashtabelle zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-372">This means that it takes more work to make a valid copy of a hashtable.</span></span>

### <a name="assigning-reference-types"></a><span data-ttu-id="34fa5-373">Zuweisen von Verweistypen</span><span class="sxs-lookup"><span data-stu-id="34fa5-373">Assigning reference types</span></span>

<span data-ttu-id="34fa5-374">Wenn Sie über eine Hashtabelle verfügen und diese einer zweiten Variable zuweisen, verweisen beide Variablen auf dieselbe Hashtabelle.</span><span class="sxs-lookup"><span data-stu-id="34fa5-374">When you have one hashtable and assign it to a second variable, both variables point to the same hashtable.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="34fa5-375">Dieses Beispiel verdeutlicht, dass es sich um dieselbe Hashtabelle handelt, denn eine Änderung der Werte in der einen Tabelle ändert auch die Werte in der anderen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-375">This highlights that they're the same because altering the values in one will also alter the values in the other.</span></span> <span data-ttu-id="34fa5-376">Dies gilt auch, wenn Sie Hashtabellen an andere Funktionen übergeben.</span><span class="sxs-lookup"><span data-stu-id="34fa5-376">This also applies when passing hashtables into other functions.</span></span> <span data-ttu-id="34fa5-377">Wenn diese Funktionen Änderungen an dieser Hashtabelle vornehmen, wird die ursprüngliche Tabelle ebenfalls geändert.</span><span class="sxs-lookup"><span data-stu-id="34fa5-377">If those functions make changes to that hashtable, your original is also altered.</span></span>

### <a name="shallow-copies-single-level"></a><span data-ttu-id="34fa5-378">Flache Kopien mit einer Ebene</span><span class="sxs-lookup"><span data-stu-id="34fa5-378">Shallow copies, single level</span></span>

<span data-ttu-id="34fa5-379">Bei einer einfachen Hashtabelle wie im obigen Beispiel können wir `.Clone()` verwenden, um eine flache Kopie zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-379">If we have a simple hashtable like our example above, we can use `.Clone()` to make a shallow copy.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

<span data-ttu-id="34fa5-380">So können wir einige grundlegende Änderungen an der einen Tabelle vornehmen, die sich nicht auf die andere auswirken.</span><span class="sxs-lookup"><span data-stu-id="34fa5-380">This will allow us to make some basic changes to one that don't impact the other.</span></span>

### <a name="shallow-copies-nested"></a><span data-ttu-id="34fa5-381">Flache Kopien, geschachtelt</span><span class="sxs-lookup"><span data-stu-id="34fa5-381">Shallow copies, nested</span></span>

<span data-ttu-id="34fa5-382">Diese Kopien werden als „flach“ bezeichnet, weil nur die grundlegenden Eigenschaften kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-382">The reason why it's called a shallow copy is because it only copies the base level properties.</span></span> <span data-ttu-id="34fa5-383">Wenn eine dieser Eigenschaften ein Verweistyp ist (z. B. eine andere Hashtabelle), zeigen diese geschachtelten Objekte weiterhin aufeinander.</span><span class="sxs-lookup"><span data-stu-id="34fa5-383">If one of those properties is a reference type (like another hashtable), then those nested objects will still point to each other.</span></span>

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="34fa5-384">Sie sehen also: Obwohl ich die Hashtabelle geklont habe, wurde der Verweis auf `person` nicht geklont.</span><span class="sxs-lookup"><span data-stu-id="34fa5-384">So you can see that even though I cloned the hashtable, the reference to `person` wasn't cloned.</span></span> <span data-ttu-id="34fa5-385">Wir müssen eine tiefe Kopie erstellen, um tatsächlich eine zweite Hashtabelle zu erhalten, die nicht mit der ersten verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="34fa5-385">We need to make a deep copy to truly have a second hashtable that isn't linked to the first.</span></span>

### <a name="deep-copies"></a><span data-ttu-id="34fa5-386">Tiefe Kopien</span><span class="sxs-lookup"><span data-stu-id="34fa5-386">Deep copies</span></span>

<span data-ttu-id="34fa5-387">Während ich diesen Artikel schreibe, ist mir keine clevere Möglichkeit bekannt, einfach eine tiefe Kopie einer Hashtabelle zu erstellen (und diese als Hashtabelle beizubehalten).</span><span class="sxs-lookup"><span data-stu-id="34fa5-387">At the time of writing this, I'm not aware of any clever ways to just make a deep copy of a hashtable (and keep it as a hashtable).</span></span> <span data-ttu-id="34fa5-388">Wahrscheinlich muss so etwas noch geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="34fa5-388">That's just one of those things that someone needs to write.</span></span>
<span data-ttu-id="34fa5-389">Hier sehen Sie eine schnelle Methode.</span><span class="sxs-lookup"><span data-stu-id="34fa5-389">Here is a quick method to do that.</span></span>

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

<span data-ttu-id="34fa5-390">Dieses Beispiel verarbeitet keine anderen Verweistypen oder Arrays, aber es ist schon mal ein guter Anfang.</span><span class="sxs-lookup"><span data-stu-id="34fa5-390">It doesn't handle any other reference types or arrays, but it's a good starting point.</span></span>

## <a name="anything-else"></a><span data-ttu-id="34fa5-391">Noch etwas?</span><span class="sxs-lookup"><span data-stu-id="34fa5-391">Anything else?</span></span>

<span data-ttu-id="34fa5-392">Ich habe hier in kurzer Zeit sehr viele Aspekte vorgestellt.</span><span class="sxs-lookup"><span data-stu-id="34fa5-392">I covered a lot of ground quickly.</span></span> <span data-ttu-id="34fa5-393">Ich hoffe, dass Sie hier etwas Neues erfahren haben oder einige Aspekte besser verstehen, wenn Sie diesen Artikel erneut lesen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-393">My hope is that you walk away leaning something new or understanding it better every time you read this.</span></span> <span data-ttu-id="34fa5-394">Da ich das komplette Spektrum dieses Features abgedeckt habe, gibt es sicherlich einige Aspekte, die Sie zurzeit noch nicht betreffen.</span><span class="sxs-lookup"><span data-stu-id="34fa5-394">Because I covered the full spectrum of this feature, there are aspects that just may not apply to you right now.</span></span> <span data-ttu-id="34fa5-395">Das ist mir völlig klar, und ich habe damit gerechnet – je nachdem, wie viel und häufig Sie mit PowerShell arbeiten.</span><span class="sxs-lookup"><span data-stu-id="34fa5-395">That is perfectly OK and is kind of expected depending on how much you work with PowerShell.</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[original version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Hashtabellen]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[hashtables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Wenn Leistung wichtig ist, probier es aus]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best%20Practices/Performance.md
[If performance matters, test it]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best%20Practices/Performance.md
[Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Automatische Standardwerte]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Automatic Defaults]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
