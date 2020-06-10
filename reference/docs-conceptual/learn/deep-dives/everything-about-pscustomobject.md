---
title: Was Sie schon immer über PSCustomObject wissen wollten
description: PSCustomObject ist eine einfache Möglichkeit zum Erstellen strukturierter Daten.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fbc8b5b6d2cfafaa75fa820f420762a1804074ac
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149493"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a><span data-ttu-id="82a8d-103">Was Sie schon immer über PSCustomObject wissen wollten</span><span class="sxs-lookup"><span data-stu-id="82a8d-103">Everything you wanted to know about PSCustomObject</span></span>

<span data-ttu-id="82a8d-104">`PSCustomObject` ist ein großartiges Tool, das Sie Ihrer PowerShell-Toolsammlung hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="82a8d-104">`PSCustomObject`s are a great tool to add into your PowerShell tool belt.</span></span> <span data-ttu-id="82a8d-105">Lassen Sie uns mit den Grundlagen beginnen und dann zu den komplexeren Features vorarbeiten.</span><span class="sxs-lookup"><span data-stu-id="82a8d-105">Let's start with the basics and work our way into the more advanced features.</span></span> <span data-ttu-id="82a8d-106">Zweck von `PSCustomObject` ist das Bieten einer einfachen Möglichkeit zum Erstellen strukturierter Daten.</span><span class="sxs-lookup"><span data-stu-id="82a8d-106">The idea behind using a `PSCustomObject` is to have a simple way to create structured data.</span></span> <span data-ttu-id="82a8d-107">Werfen Sie einen Blick auf das erste Beispiel, um eine bessere Vorstellung davon zu bekommen, was das bedeutet.</span><span class="sxs-lookup"><span data-stu-id="82a8d-107">Take a look at the first example and you'll have a better idea of what that means.</span></span>

> [!NOTE]
> <span data-ttu-id="82a8d-108">Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="82a8d-109">Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="82a8d-110">Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="82a8d-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="creating-a-pscustomobject"></a><span data-ttu-id="82a8d-111">Erstellen eines PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="82a8d-111">Creating a PSCustomObject</span></span>

<span data-ttu-id="82a8d-112">Ich verwende `[PSCustomObject]` sehr gern in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82a8d-112">I love using `[PSCustomObject]` in PowerShell.</span></span> <span data-ttu-id="82a8d-113">Das Erstellen eines nützlichen Objekts war noch nie so einfach.</span><span class="sxs-lookup"><span data-stu-id="82a8d-113">Creating a usable object has never been easier.</span></span>
<span data-ttu-id="82a8d-114">Aus diesem Grund überspringe ich alle anderen Möglichkeiten zum Erstellen eines Objekts, aber ich muss erwähnen, dass die meisten dieser Beispiele sich auf PowerShell 3.0 und neuer beziehen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-114">Because of that, I'm going to skip over all the other ways you can create an object but I need to mention that most of these examples are PowerShell v3.0 and newer.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

<span data-ttu-id="82a8d-115">Diese Methode funktioniert bei mir gut, weil ich für so gut wie alles Hashtabellen nutze.</span><span class="sxs-lookup"><span data-stu-id="82a8d-115">This method works well for me because I use hashtables for just about everything.</span></span> <span data-ttu-id="82a8d-116">Aber es gibt Situationen, in denen ich möchte, dass PowerShell Hashtabellen eher wie ein Objekt behandelt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-116">But there are times when I would like PowerShell to treat hashtables more like an object.</span></span> <span data-ttu-id="82a8d-117">Den Unterschied merken Sie erst, wenn Sie `Format-Table` oder `Export-CSV` einsetzen möchten und Ihnen klar wird, dass eine Hashtabelle nur eine Sammlung von Schlüssel-Wert-Paaren ist.</span><span class="sxs-lookup"><span data-stu-id="82a8d-117">The first place you notice the difference is when you want to use `Format-Table` or `Export-CSV` and you realize that a hashtable is just a collection of key/value pairs.</span></span>

<span data-ttu-id="82a8d-118">Sie können dann wie bei einem normalen Objekt auf die Werte zugreifen und sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="82a8d-118">You can then access and use the values like you would a normal object.</span></span>

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a><span data-ttu-id="82a8d-119">Konvertieren einer Hashtabelle</span><span class="sxs-lookup"><span data-stu-id="82a8d-119">Converting a hashtable</span></span>

<span data-ttu-id="82a8d-120">Wo ich gerade beim Thema bin, wussten Sie, dass Sie dies tun können:</span><span class="sxs-lookup"><span data-stu-id="82a8d-120">While I am on the topic, did you know you could do this:</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

<span data-ttu-id="82a8d-121">Ich erstelle das Objekt am liebsten von Grund auf, aber es gibt Fälle, in denen Sie zunächst mit einer Hashtabelle arbeiten müssen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-121">I do prefer to create the object from the start but there are times you have to work with a hashtable first.</span></span> <span data-ttu-id="82a8d-122">Dieses Beispiel funktioniert, weil der Konstruktor eine Hashtabelle für die Objekteigenschaften verwendet.</span><span class="sxs-lookup"><span data-stu-id="82a8d-122">This example works because the constructor takes a hashtable for the object properties.</span></span> <span data-ttu-id="82a8d-123">Ein wichtiger Hinweis ist, dass diese Methode zwar funktioniert, aber kein exaktes Pendant darstellt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-123">One important note is that while this method works, it isn't an exact equivalent.</span></span> <span data-ttu-id="82a8d-124">Der größte Unterschied besteht darin, dass die Reihenfolge der Eigenschaften nicht beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="82a8d-124">The biggest difference is that the order of the properties isn't preserved.</span></span>

### <a name="legacy-approach"></a><span data-ttu-id="82a8d-125">Methode für ältere PowerShell-Versionen</span><span class="sxs-lookup"><span data-stu-id="82a8d-125">Legacy approach</span></span>

<span data-ttu-id="82a8d-126">Sie haben vielleicht gesehen, dass `New-Object` zum Erstellen benutzerdefinierter Objekte genutzt wird.</span><span class="sxs-lookup"><span data-stu-id="82a8d-126">You may have seen people use `New-Object` to create custom objects.</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

<span data-ttu-id="82a8d-127">Diese Methode ist zwar etwas langsamer, könnte aber bei älteren Versionen von PowerShell die beste Wahl sein.</span><span class="sxs-lookup"><span data-stu-id="82a8d-127">This way is quite a bit slower but it may be your best option on early versions of PowerShell.</span></span>

### <a name="saving-to-a-file"></a><span data-ttu-id="82a8d-128">Speichern in einer Datei</span><span class="sxs-lookup"><span data-stu-id="82a8d-128">Saving to a file</span></span>

<span data-ttu-id="82a8d-129">Ich finde, die beste Möglichkeit, eine Hashtabelle in einer Datei zu speichern, ist die Speicherung als JSON.</span><span class="sxs-lookup"><span data-stu-id="82a8d-129">I find the best way to save a hashtable to a file is to save it as JSON.</span></span> <span data-ttu-id="82a8d-130">Sie können sie zurück in ein `[PSCusomObject]` importieren.</span><span class="sxs-lookup"><span data-stu-id="82a8d-130">You can import it back into a `[PSCusomObject]`</span></span>

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

<span data-ttu-id="82a8d-131">Weitere Möglichkeiten, Objekte in einer Datei zu speichern, beschreibe ich in meinem Artikel über [die vielen Möglichkeiten, Daten in Dateien zu lesen und zu schreiben][].</span><span class="sxs-lookup"><span data-stu-id="82a8d-131">I cover more ways to save objects to a file in my article on [The many ways to read and write to files][].</span></span>

## <a name="working-with-properties"></a><span data-ttu-id="82a8d-132">Arbeiten mit Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="82a8d-132">Working with properties</span></span>

### <a name="adding-properties"></a><span data-ttu-id="82a8d-133">Hinzufügen von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="82a8d-133">Adding properties</span></span>

<span data-ttu-id="82a8d-134">Sie können Ihrem `PSCustomObject` weiterhin mit `Add-Member` neue Eigenschaften hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-134">You can still add new properties to your `PSCustomObject` with `Add-Member`.</span></span>

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a><span data-ttu-id="82a8d-135">Entfernen von Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="82a8d-135">Remove properties</span></span>

<span data-ttu-id="82a8d-136">Sie können Eigenschaften auch aus einem Objekt entfernen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-136">You can also remove properties off of an object.</span></span>

```powershell
$myObject.psobject.properties.remove('ID')
```

<span data-ttu-id="82a8d-137">`psobject` ist eine verborgene Eigenschaft, die Ihnen Zugriff auf grundlegende Objektmetadaten bietet.</span><span class="sxs-lookup"><span data-stu-id="82a8d-137">The `psobject` is a hidden property that gives you access to base object metadata.</span></span>

### <a name="enumerating-property-names"></a><span data-ttu-id="82a8d-138">Aufzählen von Eigenschaftsnamen</span><span class="sxs-lookup"><span data-stu-id="82a8d-138">Enumerating property names</span></span>

<span data-ttu-id="82a8d-139">Gelegentlich benötigen Sie eine Liste mit den Namen aller Eigenschaften eines Objekts.</span><span class="sxs-lookup"><span data-stu-id="82a8d-139">Sometimes you need a list of all the property names on an object.</span></span>

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

<span data-ttu-id="82a8d-140">Wir können diese Liste auch aus der `psobject`-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-140">We can get this same list off of the `psobject` property too.</span></span>

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a><span data-ttu-id="82a8d-141">Dynamisches Zugreifen auf Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="82a8d-141">Dynamically accessing properties</span></span>

<span data-ttu-id="82a8d-142">Ich habe bereits erwähnt, dass Sie auf Eigenschaftswerte direkt zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="82a8d-142">I already mentioned that you can access property values directly.</span></span>

```powershell
$myObject.Name
```

<span data-ttu-id="82a8d-143">Sie können eine Zeichenfolge für den Eigenschaftsnamen nutzen und sie funktioniert trotzdem.</span><span class="sxs-lookup"><span data-stu-id="82a8d-143">You can use a string for the property name and it will still work.</span></span>

```powershell
$myObject.'Name'
```

<span data-ttu-id="82a8d-144">Wir können noch einen Schritt weitergehen und eine Variable für den Eigenschaftsnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="82a8d-144">We can take this one more step and use a variable for the property name.</span></span>

```powershell
$property = 'Name'
$myObject.$property
```

<span data-ttu-id="82a8d-145">Ich weiß, das sieht seltsam aus, aber es funktioniert.</span><span class="sxs-lookup"><span data-stu-id="82a8d-145">I know that looks strange, but it works.</span></span>

### <a name="convert-pscustomboject-into-a-hashtable"></a><span data-ttu-id="82a8d-146">Konvertieren von PSCustomObject in eine Hashtabelle</span><span class="sxs-lookup"><span data-stu-id="82a8d-146">Convert pscustomboject into a hashtable</span></span>

<span data-ttu-id="82a8d-147">Zur Fortsetzung des letzten Abschnitts können Sie die Eigenschaften dynamisch durchlaufen und daraus eine Hashtabelle erstellen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-147">To continue on from the last section, you can dynamically walk the properties and create a hashtable from them.</span></span>

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a><span data-ttu-id="82a8d-148">Testen auf Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="82a8d-148">Testing for properties</span></span>

<span data-ttu-id="82a8d-149">Wenn Sie wissen müssen, ob eine Eigenschaft vorhanden ist, können Sie einfach prüfen, ob diese Eigenschaft einen Wert hat.</span><span class="sxs-lookup"><span data-stu-id="82a8d-149">If you need to know if a property exists, you could just check for that property to have a value.</span></span>

```powershell
if( $null -ne $myObject.ID )
```

<span data-ttu-id="82a8d-150">Aber wenn der Wert `$null` sein könnte und Sie trotzdem auf diesen prüfen müssen, können Sie `psobject.properties` darauf untersuchen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-150">But if the value could be `$null` and you still need to check for it, you can check the `psobject.properties` for it.</span></span>

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a><span data-ttu-id="82a8d-151">Hinzufügen von Objektmethoden</span><span class="sxs-lookup"><span data-stu-id="82a8d-151">Adding object methods</span></span>

<span data-ttu-id="82a8d-152">Wenn Sie einem Objekt eine Skriptmethode hinzufügen müssen, können Sie dies mit `Add-Member` und einem `ScriptBlock` tun.</span><span class="sxs-lookup"><span data-stu-id="82a8d-152">If you need to add a script method to an object, you can do it with `Add-Member` and a `ScriptBlock`.</span></span> <span data-ttu-id="82a8d-153">Sie müssen die automatische Variable `this` verwenden, um auf das aktuelle Objekt zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-153">You have to use the `this` automatic variable reference the current object.</span></span> <span data-ttu-id="82a8d-154">Hier ist ein `scriptblock` zum Umwandeln eines Objekts in eine Hashtabelle.</span><span class="sxs-lookup"><span data-stu-id="82a8d-154">Here is a `scriptblock` to turn an object into a hashtable.</span></span> <span data-ttu-id="82a8d-155">(gleicher Code aus dem letzten Beispiel)</span><span class="sxs-lookup"><span data-stu-id="82a8d-155">(same code form the last example)</span></span>

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

<span data-ttu-id="82a8d-156">Dann fügen wir ihn unserem Objekt als Skripteigenschaft hinzu.</span><span class="sxs-lookup"><span data-stu-id="82a8d-156">Then we add it to our object as a script property.</span></span>

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

<span data-ttu-id="82a8d-157">Anschließend können wir unsere Funktion wie folgt aufrufen:</span><span class="sxs-lookup"><span data-stu-id="82a8d-157">Then we can call our function like this:</span></span>

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a><span data-ttu-id="82a8d-158">Objekte im Vergleich zu Werttypen</span><span class="sxs-lookup"><span data-stu-id="82a8d-158">Objects vs Value types</span></span>

<span data-ttu-id="82a8d-159">Objekte und Werttypen behandeln Variablenzuweisungen nicht auf gleiche Weise.</span><span class="sxs-lookup"><span data-stu-id="82a8d-159">Objects and value types don't handle variable assignments the same way.</span></span> <span data-ttu-id="82a8d-160">Wenn Sie Werttypen einander zuweisen, wird nur der Wert in die neue Variable kopiert.</span><span class="sxs-lookup"><span data-stu-id="82a8d-160">If you assign value types to each other, only the value get copied to the new variable.</span></span>

```powershell
$first = 1
$second = $first
$second = 2
```

<span data-ttu-id="82a8d-161">In diesem Fall ist `$first` gleich 1 und `$second` gleich 2.</span><span class="sxs-lookup"><span data-stu-id="82a8d-161">In this case, `$first` is 1 and `$second` is 2.</span></span>

<span data-ttu-id="82a8d-162">Objektvariablen enthalten einen Verweis auf das tatsächliche Objekt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-162">Object variables hold a reference to the actual object.</span></span> <span data-ttu-id="82a8d-163">Wenn Sie ein Objekt einer neuen Variablen zuweisen, verweist es immer noch auf dasselbe Objekt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-163">When you assign one object to a new variable, they still reference the same object.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

<span data-ttu-id="82a8d-164">Da `$third` und `$fourth` auf dieselbe Instanz eines Objekts verweisen, sind sowohl `$third.key` als auch `$fourth.Key` gleich 4.</span><span class="sxs-lookup"><span data-stu-id="82a8d-164">Because `$third` and `$fourth` reference the same instance of an object, both `$third.key` and `$fourth.Key` are 4.</span></span>

### <a name="psobjectcopy"></a><span data-ttu-id="82a8d-165">psobject.copy()</span><span class="sxs-lookup"><span data-stu-id="82a8d-165">psobject.copy()</span></span>

<span data-ttu-id="82a8d-166">Wenn Sie eine originalgetreue Kopie eines Objekts benötigen, können Sie es klonen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-166">If you need a true copy of an object, you can clone it.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

<span data-ttu-id="82a8d-167">Beim Klonen wird eine flache Kopie des Objekts erstellt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-167">Clone creates a shallow copy of the object.</span></span> <span data-ttu-id="82a8d-168">Es gibt jetzt verschiedene Instanzen, wobei in diesem Beispiel `$third.key` gleich 3 und `$fourth.Key` gleich 4 ist.</span><span class="sxs-lookup"><span data-stu-id="82a8d-168">They have different instances now and `$third.key` is 3 and `$fourth.Key` is 4 in this example.</span></span>

<span data-ttu-id="82a8d-169">Ich nenne dies eine flache Kopie, weil es geschachtelte Objekte gibt</span><span class="sxs-lookup"><span data-stu-id="82a8d-169">I call this a shallow copy because if you have nested objects.</span></span> <span data-ttu-id="82a8d-170">(bei denen die Eigenschaften andere Objekte enthalten).</span><span class="sxs-lookup"><span data-stu-id="82a8d-170">(where the properties contain other objects).</span></span> <span data-ttu-id="82a8d-171">Nur die Werte auf oberster Ebene werden kopiert.</span><span class="sxs-lookup"><span data-stu-id="82a8d-171">Only the top-level values are copied.</span></span> <span data-ttu-id="82a8d-172">Die untergeordneten Objekte verweisen aufeinander.</span><span class="sxs-lookup"><span data-stu-id="82a8d-172">The child objects will reference each other.</span></span>

### <a name="pstypename-for-custom-object-types"></a><span data-ttu-id="82a8d-173">PSTypeName für benutzerdefinierte Objekttypen</span><span class="sxs-lookup"><span data-stu-id="82a8d-173">PSTypeName for custom object types</span></span>

<span data-ttu-id="82a8d-174">Jetzt, da wir ein Objekt haben, können wir noch ein paar Dinge damit anstellen, die möglicherweise nicht ganz so offensichtlich sind.</span><span class="sxs-lookup"><span data-stu-id="82a8d-174">Now that we have an object, there are a few more things we can do with it that may not be nearly as obvious.</span></span> <span data-ttu-id="82a8d-175">Als Erstes müssen wir ihm einen `PSTypeName` zuweisen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-175">First thing we need to do is give it a `PSTypeName`.</span></span> <span data-ttu-id="82a8d-176">Dies erfolgt meist so:</span><span class="sxs-lookup"><span data-stu-id="82a8d-176">This is the most common way I see people do it:</span></span>

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

<span data-ttu-id="82a8d-177">In diesem [Beitrag von /u/markekraus][] habe ich vor Kurzem eine weitere Möglichkeit entdeckt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-177">I recently discovered another way to do this from this [post by /u/markekraus][].</span></span> <span data-ttu-id="82a8d-178">Ich habe ein wenig recherchiert und weitere Beiträge zu der Idee von [Adam Bertram][] und [Mike Shepard][] gefunden, in denen sie über diesen Ansatz sprechen, der es Ihnen erlaubt, ihn inline zu definieren.</span><span class="sxs-lookup"><span data-stu-id="82a8d-178">I did a little digging and more posts about the idea from [Adam Bertram][] and [Mike Shepard][] where they talk about this approach that allows you to define it inline.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

<span data-ttu-id="82a8d-179">Es gefällt mir, wie gut das einfach zur Sprache passt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-179">I love how nicely this just fits into the language.</span></span> <span data-ttu-id="82a8d-180">Nachdem wir nun über ein Objekt mit einem ordnungsgemäßen Typnamen verfügen, können wir weitere Aktionen ausführen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-180">Now that we have an object with a proper type name, we can do some more things.</span></span>

## <a name="using-defaultpropertyset-the-long-way"></a><span data-ttu-id="82a8d-181">Verwenden von DefaultPropertySet (Langfassung)</span><span class="sxs-lookup"><span data-stu-id="82a8d-181">Using DefaultPropertySet (the long way)</span></span>

<span data-ttu-id="82a8d-182">PowerShell entscheidet für uns, welche Eigenschaften standardmäßig angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="82a8d-182">PowerShell decides for us what properties to display by default.</span></span> <span data-ttu-id="82a8d-183">Bei vielen der nativen Befehle gibt es die [Formatierungsdatei][] `.ps1xml`, die alle anfallenden Aufgaben übernimmt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-183">A lot of the native commands have a `.ps1xml` [formatting file][] that does all the heavy lifting.</span></span> <span data-ttu-id="82a8d-184">In diesem [Beitrag von Boe Prox][] gibt es eine weitere Möglichkeit, wie wir dies nur mithilfe von PowerShell auf unser benutzerdefiniertes Objekt anwenden können.</span><span class="sxs-lookup"><span data-stu-id="82a8d-184">From this [post by Boe Prox][], there's another way for us to do this on our custom object using just PowerShell.</span></span> <span data-ttu-id="82a8d-185">Wir können ihm ein `MemberSet` zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-185">We can give it a `MemberSet` for it to use.</span></span>

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

<span data-ttu-id="82a8d-186">Wenn mein Objekt nun einfach in der Shell verwendet wird, zeigt es standardmäßig nur diese Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="82a8d-186">Now when my object just falls to the shell, it will only show those properties by default.</span></span>

### <a name="update-typedata-with-defaultpropertyset"></a><span data-ttu-id="82a8d-187">Update-TypeData mit DefaultPropertySet</span><span class="sxs-lookup"><span data-stu-id="82a8d-187">Update-TypeData with DefaultPropertySet</span></span>

<span data-ttu-id="82a8d-188">Das ist zwar ganz nett, aber ich habe kürzlich in [PowerShell unplugged 2016 mit Jeffrey Snover und Don Jones][psunplugged] eine bessere Möglichkeit gesehen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-188">This is nice but I recently saw a better way when watching [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span></span> <span data-ttu-id="82a8d-189">Jeffrey nutzte [Update-TypeData][], um die Standardeigenschaften anzugeben.</span><span class="sxs-lookup"><span data-stu-id="82a8d-189">Jeffrey was using [Update-TypeData][] to specify the default properties.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

<span data-ttu-id="82a8d-190">Das ist so einfach, dass ich mich fast daran erinnern könnte, wenn ich diesen Beitrag nicht als Schnellreferenz hätte.</span><span class="sxs-lookup"><span data-stu-id="82a8d-190">That is simple enough that I could almost remember it if I didn't have this post as a quick reference.</span></span> <span data-ttu-id="82a8d-191">Jetzt kann ich ganz einfach Objekte mit vielen Eigenschaften erstellen und trotzdem eine ansprechende, übersichtliche Ansicht bieten, wenn ich sie in der Shell betrachte.</span><span class="sxs-lookup"><span data-stu-id="82a8d-191">Now I can easily create objects with lots of properties and still give it a nice clean view when looking at it from the shell.</span></span> <span data-ttu-id="82a8d-192">Wenn ich auf diese anderen Eigenschaften zugreifen oder sie einsehen muss, sind sie immer noch da.</span><span class="sxs-lookup"><span data-stu-id="82a8d-192">If I need to access or see those other properties, they're still there.</span></span>

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a><span data-ttu-id="82a8d-193">Update-TypeData mit ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="82a8d-193">Update-TypeData with ScriptProperty</span></span>

<span data-ttu-id="82a8d-194">Etwas anderes, was ich in diesem Video erfahren habe, war das Erstellen von Skripteigenschaften für Ihre Objekte.</span><span class="sxs-lookup"><span data-stu-id="82a8d-194">Something else I got out of that video was creating script properties for your objects.</span></span> <span data-ttu-id="82a8d-195">Dies wäre ein guter Zeitpunkt, darauf hinzuweisen, dass dies auch für bestehende Objekte gilt.</span><span class="sxs-lookup"><span data-stu-id="82a8d-195">This would be a good time to point out that this works for existing objects too.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

<span data-ttu-id="82a8d-196">Sie können dies vor oder nach der Erstellung Ihres Objekts tun, wobei es weiterhin funktionieren wird.</span><span class="sxs-lookup"><span data-stu-id="82a8d-196">You can do this before your object is created or after and it will still work.</span></span> <span data-ttu-id="82a8d-197">Das ist der Unterschied zur Nutzung von `Add-Member` mit einer Skripteigenschaft.</span><span class="sxs-lookup"><span data-stu-id="82a8d-197">This is what makes this different then using `Add-Member` with a script property.</span></span> <span data-ttu-id="82a8d-198">Wenn Sie `Add-Member` wie zuvor beschrieben nutzen, ist es nur in dieser speziellen Instanz des Objekts vorhanden.</span><span class="sxs-lookup"><span data-stu-id="82a8d-198">When you use `Add-Member` the way I referenced earlier, it only exists on that specific instance of the object.</span></span> <span data-ttu-id="82a8d-199">Dieser gilt für alle Objekte mit diesem `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="82a8d-199">This one applies to all objects with this `TypeName`.</span></span>

## <a name="function-parameters"></a><span data-ttu-id="82a8d-200">Funktionsparameter</span><span class="sxs-lookup"><span data-stu-id="82a8d-200">Function parameters</span></span>

<span data-ttu-id="82a8d-201">Sie können diese benutzerdefinierten Typen jetzt für Parameter in Ihren Funktionen und Skripts nutzen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-201">You can now use these custom types for parameters in your functions and scripts.</span></span> <span data-ttu-id="82a8d-202">Sie können diese benutzerdefinierten Objekte von einer Funktion erstellen lassen und sie dann an andere Funktionen übergeben.</span><span class="sxs-lookup"><span data-stu-id="82a8d-202">You can have one function create these custom objects and then pass them into other functions.</span></span>

```powershell
param( [PSTypeName('My.Object')]$Data )
```

<span data-ttu-id="82a8d-203">PowerShell setzt voraus, dass das Objekt dem von Ihnen angegebenen Typ entspricht.</span><span class="sxs-lookup"><span data-stu-id="82a8d-203">PowerShell requires that the object is the type you specified.</span></span> <span data-ttu-id="82a8d-204">Ein Validierungsfehler wird automatisch ausgelöst, wenn der Typ nicht übereinstimmt, um Ihnen in Ihrem Code den Testschritt dafür zu ersparen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-204">It throws a validation error if the type doesn't match automatically to save you the step of testing for it in your code.</span></span> <span data-ttu-id="82a8d-205">Ein großartiges Beispiel dafür, PowerShell das tun zu lassen, was es am besten kann.</span><span class="sxs-lookup"><span data-stu-id="82a8d-205">A great example of letting PowerShell do what it does best.</span></span>

### <a name="function-outputtype"></a><span data-ttu-id="82a8d-206">OutputType von Funktion</span><span class="sxs-lookup"><span data-stu-id="82a8d-206">Function OutputType</span></span>

<span data-ttu-id="82a8d-207">Sie können für Ihre erweiterten Funktionen auch einen `OutputType` definieren.</span><span class="sxs-lookup"><span data-stu-id="82a8d-207">You can also define an `OutputType` for your advanced functions.</span></span>

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

<span data-ttu-id="82a8d-208">Der Wert des Attributs **OutputType** ist nur ein Dokumentationshinweis.</span><span class="sxs-lookup"><span data-stu-id="82a8d-208">The **OutputType** attribute value is only a documentation note.</span></span> <span data-ttu-id="82a8d-209">Er ist nicht vom Funktionscode abgeleitet bzw. wird nicht mit der tatsächlichen Funktionsausgabe verglichen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-209">It isn't derived from the function code or compared to the actual function output.</span></span>

<span data-ttu-id="82a8d-210">Der Hauptgrund für die Nutzung eines Ausgabetyps besteht darin, dass Metainformationen zu Ihrer Funktion Ihre Absichten widerspiegeln sollen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-210">The main reason you would use an output type is so that meta information about your function reflects your intentions.</span></span> <span data-ttu-id="82a8d-211">Dinge wie `Get-Command` und `Get-Help`, die sich Ihre Entwicklungsumgebung zunutze machen kann.</span><span class="sxs-lookup"><span data-stu-id="82a8d-211">Things like `Get-Command` and `Get-Help` that your development environment can take advantage of.</span></span> <span data-ttu-id="82a8d-212">Wenn Sie weitere Informationen wünschen, werfen Sie einen Blick in die Hilfe dazu: [about_Functions_OutputTypeAttribute][].</span><span class="sxs-lookup"><span data-stu-id="82a8d-212">If you want more information, then take a look at the help for it: [about_Functions_OutputTypeAttribute][].</span></span>

<span data-ttu-id="82a8d-213">Wenn Sie mit Pester Komponententests Ihrer Funktionen durchführen, wäre es eine gute Idee, die Ausgabeobjekte zu überprüfen, die Ihrem **OutputType** entsprechen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-213">With that said, if you're using Pester to unit test your functions then it would be a good idea to validate the output objects match your **OutputType**.</span></span> <span data-ttu-id="82a8d-214">Dadurch könnten Variablen abgefangen werden, die sonst durchfallen würden, obwohl sie das nicht sollten.</span><span class="sxs-lookup"><span data-stu-id="82a8d-214">This could catch variables that just fall to the pipe when they shouldn't.</span></span>

## <a name="closing-thoughts"></a><span data-ttu-id="82a8d-215">Schlussbemerkung</span><span class="sxs-lookup"><span data-stu-id="82a8d-215">Closing thoughts</span></span>

<span data-ttu-id="82a8d-216">In diesem Artikel ging es um `[PSCustomObject]`, aber viele dieser Informationen gelten für Objekte im Allgemeinen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-216">The context of this was all about `[PSCustomObject]`, but a lot of this information applies to objects in general.</span></span>

<span data-ttu-id="82a8d-217">Ich habe die meisten dieser Features schon einmal im Vorübergehen gesehen, aber bislang nicht als eine Sammlung von Informationen zu `PSCustomObject` präsentiert bekommen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-217">I have seen most of these features in passing before but never saw them presented as a collection of information on `PSCustomObject`.</span></span> <span data-ttu-id="82a8d-218">Erst letzte Woche bin ich über ein weiteres gestolpert und war überrascht, dass ich es vorher noch nicht gesehen hatte.</span><span class="sxs-lookup"><span data-stu-id="82a8d-218">Just this last week I stumbled upon another one and was surprised that I had not seen it before.</span></span> <span data-ttu-id="82a8d-219">Ich wollte all diese Ideen zusammenbringen, damit Sie hoffentlich das große Ganze sehen und sich im Bedarfsfall Ihrer Möglichkeiten bewusst sind.</span><span class="sxs-lookup"><span data-stu-id="82a8d-219">I wanted to pull all these ideas together so you can hopefully see the bigger picture and be aware of them when you have an opportunity to use them.</span></span> <span data-ttu-id="82a8d-220">Ich hoffe, Sie haben etwas gelernt und können eine Möglichkeit finden, dies in Ihre Skripts einzubauen.</span><span class="sxs-lookup"><span data-stu-id="82a8d-220">I hope you learned something and can find a way to work this into your scripts.</span></span>

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[original version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Beitrag von Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[post by Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[Formatierungsdatei]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[formatting file]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[Die vielen Möglichkeiten, Daten in Dateien zu lesen und zu schreiben]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[The many ways to read and write to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[Beitrag von /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
