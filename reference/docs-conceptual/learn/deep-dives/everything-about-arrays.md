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
# <a name="everything-you-wanted-to-know-about-arrays"></a>Alles, was Sie schon immer über Arrays wissen wollten

[Arrays][] sind ein grundlegendes Sprachfeature der meisten Programmiersprachen. Es handelt sich um eine Auflistung aus Werten oder Objekten, um die Sie kaum herumkommen werden. Sehen wir uns also Arrays und ihre Möglichkeiten einmal genauer an.

> [!NOTE]
> Die [Originalversion][] dieses Artikels wurde im Blog von [@KevinMarquette][] veröffentlicht. Das PowerShell-Team dankt Kevin, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="what-is-an-array"></a>Was ist ein Array?

Ich beginne mit einer grundlegenden technischen Beschreibung von Arrays und ihrer Verwendung in den meisten Programmiersprachen. Danach werde ich die weiteren Möglichkeiten der Verwendung in PowerShell vorstellen.

Ein Array ist eine Datenstruktur, die als Auflistung mehrerer Elemente dient. Sie können ein Array durchlaufen oder über einen Index auf einzelne Elemente zugreifen. Ein Array wird als sequenzieller Arbeitsspeicherblock erstellt, in dem die einzelnen Werte direkt nebeneinander gespeichert sind.

Ich werde im Verlauf dieses Artikels auf die Details eingehen.

## <a name="basic-usage"></a>Grundlegende Verwendung

Da Arrays ein so grundlegendes Feature von PowerShell sind, gibt es eine einfache Syntax für die Arbeit mit Arrays in PowerShell.

### <a name="create-an-array"></a>Erstellen eines Arrays

Ein leeres Array lässt sich mit `@()` erstellen.

```powershell
PS> $data = @()
PS> $data.count
0
```

Wir können ein Array erstellen und mit Werten füllen, indem wir diese einfach in die runden Klammern `@()` einfügen.

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

Dieses Array besteht aus vier Elementen. Wenn wir die Variable `$data` aufrufen, wird die Liste der Elemente angezeigt. Bei einem Zeichenfolgenarray erhalten wir eine Zeile pro Zeichenfolge.

Wir können ein Array auf mehreren Zeilen deklarieren. Das Komma ist in diesem Fall optional und wird in der Regel weggelassen.

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

Ich deklariere meine Arrays lieber so auf mehreren Zeilen. Das vereinfacht nicht nur bei mehreren Elementen das Lesen des Arrays, Sie können Ihre Arrays auch einfacher mit vorherigen Versionen vergleichen, wenn Sie die Quellcodeverwaltung verwenden.

#### <a name="other-syntax"></a>Eine andere Syntax

Im Allgemeinen wird `@()` als Syntax zum Erstellen eines Arrays verwendet, aber durch Trennzeichen getrennte Listen funktionieren meistens auch.

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a>Write-Output zum Erstellen von Arrays

Ein netter kleiner Trick, den ich nicht unerwähnt lassen möchte: Sie können `Write-Output` verwenden, um schnell Zeichenfolgen an der Konsole zu erstellen.

```powershell
$data = Write-Output Zero One Two Three
```

Das ist wirklich praktisch, denn Sie müssen keine Anführungszeichen um die Zeichenfolgen setzen, wenn der Parameter Zeichenfolgen akzeptiert. In einem Skript würde ich nie so vorgehen, aber an der Konsole – kein Problem.

### <a name="accessing-items"></a>Zugreifen auf Elemente

Nachdem Sie jetzt über ein Array mit Elementen verfügen, möchten Sie sicher darauf zugreifen und diese Elemente aktualisieren.

#### <a name="offset"></a>Offset

Um auf einzelne Elemente zuzugreifen, verwenden wir die eckigen Klammern `[]` mit einem Offsetwert, der bei 0 beginnt. So rufen wir das erste Element im Array ab:

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

Wir verwenden hier 0, weil das erste Element am Anfang der Liste steht, wir also einen Offset von 0 Elementen benötigen, um zu diesem Element zu gelangen. Um zum zweiten Element zu gelangen, müssen wir einen Offset von 1 verwenden, um das erste Element zu überspringen.

```powershell
PS> $data[1]
One
```

Das bedeutet, dass sich das letzte Element am Offsetwert 3 befindet.

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a>Index

Jetzt sehen Sie, warum ich für dieses Beispiel diese Werte ausgewählt habe. Ich habe das Konzept als „Offset“ vorgestellt, weil es sich tatsächlich um einen solchen handelt. In der Regel wird der Offset aber meist als „Index“ bezeichnet. Ein Index, der bei `0` beginnt. Im weiteren Verlauf dieses Artikels werde ich den Offset als Index bezeichnen.

#### <a name="special-index-tricks"></a>Spezielle Tricks für Indizes

In den meisten Sprachen können Sie nur eine einzige Zahl als Index angeben und erhalten ein einzelnes Element zurück.
PowerShell ist da wesentlich flexibler. Sie können mehrere Indizes gleichzeitig verwenden. Indem wir eine Liste von Indizes angeben, können wir mehrere Elemente auswählen.

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

Die Elemente werden basierend auf der Reihenfolge der angegebenen Indizes zurückgegeben. Wenn Sie einen Index duplizieren, erhalten Sie das entsprechende Element beide Male.

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

Mit dem integrierten `..`-Operator können wir eine Sequenz aus Zahlen angeben.

```powershell
PS> $data[1..3]
One
Two
Three
```

Das funktioniert auch umgekehrt.

```powershell
PS> $data[3..1]
Three
Two
One
```

Sie können auch negative Indexwerte angeben, um den Offset vom Ende der Liste anzugeben. Wenn Sie also das letzte Element einer Liste abrufen möchten, können Sie `-1` verwenden.

```powershell
PS> $data[-1]
Three
```

Beim Operator `..` ist hierbei allerdings Vorsicht geboten. Die Sequenzen `0..-1` und `-1..0` werden zu den Werten `0,-1` und `-1,0` ausgewertet. Wenn Sie dieses Detail vergessen, könnten Sie fälschlicherweise davon ausgehen, dass `$data[0..-1]` alle Elemente aufzählt. Mit `$data[0..-1]` erhalten Sie dieselben Werte wie mit `$data[0,-1]` – das erste und das letzte Element im Array (und keinen der anderen Werte dazwischen).

#### <a name="out-of-bounds"></a>Außerhalb des gültigen Bereichs

In den meisten Sprachen gilt Folgendes: Wenn Sie versuchen, auf den Index eines Elements zuzugreifen, das hinter dem Ende des Arrays liegt, wird ein Fehler oder eine Ausnahme zurückgegeben. PowerShell gibt einfach nichts zurück.

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a>In einem NULL-Array kann kein Index erstellt werden

Wenn Ihre Variable `$null` lautet und Sie versuchen, sie wie ein Array zu indizieren, wird eine `System.Management.Automation.RuntimeException` mit der Meldung `Cannot index into a null array` zurückgegeben.

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

Stellen Sie also sicher, dass Ihre Arrays nicht `$null` sind, bevor Sie versuchen, auf Elemente darin zuzugreifen.

#### <a name="count"></a>Anzahl

Arrays und andere Auflistungen verfügen über eine count-Eigenschaft, die Sie darüber informiert, wie viele Elemente sich im Array befinden.

```powershell
PS> $data.count
4
```

PowerShell 3.0 hat den meisten Objekten eine count-Eigenschaft hinzugefügt. Wenn Sie über ein einzelnes Objekt verfügen, sollte die Anzahl `1` zurückgegeben werden.

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

Selbst `$null` besitzt eine count-Eigenschaft, diese gibt allerdings `0` zurück.

```powershell
PS> $null.count
0
```

Hier gibt es einige potenzielle Fallen, auf die ich weiter unten in diesem Artikel eingehen werde, wenn ich die Überprüfung auf `$null` oder leere Arrays erläutere.

#### <a name="off-by-one-errors"></a>Off-by-one-Fehler

Programmierfehler entstehen nicht selten dadurch, dass Arrays am Index 0 beginnen. Off-by-one-Fehler können auf zwei Arten entstehen.

Im ersten Fall möchten Sie eigentlich das zweite Element über den Index `2` abrufen, erhalten dadurch aber tatsächlich das dritte Element. Oder vielleicht verfügen Sie über vier Elemente, von denen Sie das letzte abrufen möchten, und verwenden daher die count-Eigenschaft für den Zugriff auf dieses letzte Element.

```powershell
$data[ $data.count ]
```

PowerShell hindert Sie nicht daran, dies zu tun, und gibt Ihnen genau das Element zurück, das sich an Index 4 befindet: `$null`. Hierfür sollten Sie also `$data.count - 1` oder `-1` verwenden, wie etwas weiter oben erläutert.

```powershell
PS> $data[ $data.count - 1 ]
Three
```

So können Sie den Index `-1` verwenden, um das letzte Element abzurufen.

```powershell
PS> $data[ -1 ]
Three
```

Lee Dailey hat mich darauf hingewiesen, dass wir auch `$data.GetUpperBound(0)` verwenden können, um die maximale Indexnummer abzurufen.

```powershell
PS> $data.GetUpperBound(0)
Three
```

Die zweithäufigste Fehlerquelle entsteht dadurch, dass eine Liste durchlaufen und der Durchlauf nicht rechtzeitig angehalten wird. Ich werde näher auf dieses Problem eingehen, wenn ich die `for`-Schleife erläutere.

### <a name="updating-items"></a>Aktualisieren von Elementen

Wir können denselben Index zum Aktualisieren vorhandener Elemente im Array verwenden. So erhalten wir direkten Zugriff zum Aktualisieren einzelner Elemente.

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

Wenn wir versuchen, ein Element zu aktualisieren, das sich hinter dem letzten Element befindet, wird der Fehler `Index was outside the bounds of the array.` zurückgegeben.

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

Dieses Problem werde ich später erläutern, wenn ich beschreibe, wie sich ein Array vergrößern lässt.

### <a name="iteration"></a>Iteration

An einem bestimmten Punkt werden Sie die gesamte Liste durchlaufen und eine Aktion für jedes Element im Array ausführen müssen.

#### <a name="pipeline"></a>Pipeline

Arrays und die PowerShell-Pipeline sind wie füreinander geschaffen. Dies ist eine der einfachsten Möglichkeiten, diese Werte zu verarbeiten. Wenn Sie ein Array an eine Pipeline übergeben, wird jedes Element im Array individuell verarbeitet.

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

Wenn Sie `$PSItem` noch nie gesehen haben, müssen Sie zunächst nur wissen, dass es das gleiche ist wie `$_`. Sie können beide verwenden, weil beide das aktuelle Objekt in der Pipeline repräsentieren.

#### <a name="foreach-loop"></a>foreach-Schleife

Die `ForEach`-Schleife funktioniert gut bei Auflistungen. Die Syntax lautet `foreach ( <variable> in <collection> )`.

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a>foreach-Methode

Ich neige dazu, diese Methode zu vergessen, aber sie funktioniert bei einfachen Vorgängen wirklich gut. PowerShell ermöglicht den Aufruf von `.ForEach()` in einer Auflistung.

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

`.foreach()` akzeptiert einen Parameter, bei dem es sich um einen Skriptblock handelt. Sie können die Klammern weglassen und einfach nur den Skriptblock angeben.

```powershell
$data.foreach{"Item [$PSItem]"}
```

Diese Syntax ist weniger bekannt, funktioniert aber genauso gut. Diese `foreach`-Methode wurde in PowerShell 4.0 hinzugefügt.

#### <a name="for-loop"></a>for-Schleife

Die `for`-Schleife wird in den meisten anderen Sprachen ausgiebig genutzt, in PowerShell kommt sie nur selten vor. Wenn sie vorkommt, dann meist beim Durchlaufen eines Arrays.

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

Als Erstes initialisieren wir einen `$index` mit `0`. Dann fügen wir die Bedingung hinzu, dass `$index` kleiner sein muss als `$data.count`. Schließlich geben wir an, dass bei jedem Durchlaufen der Schleife der Index um `1` erhöht werden muss. In diesem Fall ist `$index++` die Kurzform von `$index = $index + 1`.

Wann immer Sie eine `for`-Schleife verwenden, achten Sie besonders auf die Bedingung. Ich habe hier `$index -lt $data.count` verwendet. Vorsicht: Bei dieser Bedingung können Ihnen leicht kleine Fehler unterlaufen, die dann zu Off-by-one-Fehlern in Ihrer Logik führen. Beispiele für solche kleinen Fehler wären `$index -le $data.count` oder `$index -lt ($data.count - 1)`. Das würde dazu führen, dass Ihr Ergebnis zu viele oder zu wenige Elemente verarbeitet. Das ist der klassische Off-by-one-Fehler.

#### <a name="switch-loop"></a>switch-Schleife

Diese Schleife wird leicht übersehen. Wenn Sie in einer [switch-Anweisung][] ein Array angeben, überprüft diese Anweisung jedes Element im Array.

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

Diese Anweisung bietet einige echt coole Möglichkeiten. Ich habe darüber einen ganzen Artikel geschrieben:

- [Alles, was Sie schon immer über die switch-Anweisung wissen wollten][switch-Anweisung]

#### <a name="updating-values"></a>Aktualisieren von Werten

Wenn es sich bei Ihrem Array um eine Auflistung von string- oder integer-Typen (Werttypen) handelt, werden Sie die Werte im Array beim Durchlaufen vermutlich aktualisieren wollen. Die meisten oben genannten Schleifen verwenden eine Variable in der Schleife, die eine Kopie des Werts enthält. Wenn Sie diese Variable aktualisieren, wird der ursprüngliche Wert im Array nicht aktualisiert.

Die Ausnahme dieser Anweisung ist die `for`-Schleife. Wenn Sie ein Array durchlaufen und Werte darin aktualisieren möchten, ist die `for`-Schleife genau das, wonach Sie suchen.

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

Dieses Beispiel ruft einen Wert anhand des Indexes ab, nimmt einige Änderungen vor und verwendet denselben Index, um den Wert wieder zuzuweisen.

## <a name="arrays-of-objects"></a>Array aus Objekten

Bisher haben wir nur einen Werttyp in einem Array platziert, Arrays können aber auch Objekte enthalten.

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

Viele Cmdlets geben Auflistungen von Objekten als Arrays zurück, wenn Sie sie einer Variable zuweisen.

```powershell
$processList = Get-Process
```

All die grundlegenden Features, die ich Ihnen bereits vorgestellt habe, gelten auch für Arrays aus Objekten. Allerdings gibt es ein paar Details, auf die ich Sie gerne hinweisen möchte.

### <a name="accessing-properties"></a>Zugreifen auf Eigenschaften

Wir können einen Index verwenden, um auf ein einzelnes Element in einer Auflistung zuzugreifen – genau wie bei Werttypen.

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

Wir können auf Eigenschaften zugreifen und diese direkt aktualisieren.

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a>Arrayeigenschaften

Normalerweise müssten Sie die gesamte Liste wie folgt aufzählen, um auf alle Eigenschaften zuzugreifen:

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

Sie könnten auch das Cmdlet `Select-Object -ExpandProperty` verwenden.

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

PowerShell bietet aber die Möglichkeit, `LastName` direkt anzufordern. PowerShell zählt alle Elemente für uns auf und gibt eine bereinigte Liste zurück.

```powershell
PS> $data.LastName

Marquette
Doe
```

Die Enumeration erfolgt weiterhin, aber die Komplexität dahinter bleibt verborgen.

### <a name="where-object-filtering"></a>Where-Object-Filterung

Hier kommt `Where-Object` ins Spiel, sodass wir Informationen basierend auf den Eigenschaften des Objekts filtern und auswählen können.

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

Wir können dieselbe Abfrage schreiben, um das gewünschte `FirstName`-Objekt abzurufen.

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a>Where()

Arrays enthalten eine `Where()`-Methode, mit der Sie einen `scriptblock` für den Filter angeben können.

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

Dieses Feature wurde in PowerShell 4.0 hinzugefügt.

### <a name="updating-objects-in-loops"></a>Aktualisieren von Objekten in Schleifen

Bei Werttypen besteht die einzige Möglichkeit zum Aktualisieren des Arrays darin, eine for-Schleife zu verwenden, da wir den Index kennen müssen, um den Wert zu ersetzen. Bei Objekten haben wir mehr Optionen, weil es sich dabei um Verweistypen handelt. Hier ist ein kurzes Beispiel:

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

Die Schleife durchläuft jedes Objekt im `$data`-Array. Da Objekte Verweistypen sind, verweist die Variable `$person` auf exakt dieses Objekt, das sich im Array befindet. Updates der Eigenschaften des Objekts aktualisieren also das ursprüngliche Objekt.

Ersetzen können Sie das gesamte Objekt auf diese Weise immer noch nicht. Wenn Sie versuchen, der Variable `$person` ein neues Objekt zuzuweisen, aktualisieren Sie den Variablenverweis auf etwas anderes, das nicht mehr auf das ursprüngliche Objekt im Array verweist. Das funktioniert nicht so, wie Sie es erwarten würden:

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a>Operatoren

Operatoren in PowerShell funktionieren auch in Arrays. Bei einigen ist die Funktionsweise allerdings etwas anders.

### <a name="-join"></a>-join

Der `-join`-Operator ist der offensichtlichste, also sehen wir uns diesen zuerst an. Ich mag den `-join`-Operator und verwende ihn häufig. Er verknüpft alle Elemente im Array mit dem Zeichen oder der Zeichenfolge, das bzw. die Sie angeben.

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

Eines der Features, das mir am `-join`-Operator gefällt, ist die Verarbeitung einzelner Elemente.

```powershell
PS> 1 -join '-'
1
```

Dieses Feature verwende ich in Protokollierungsmeldungen und ausführlichen Meldungen.

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a>-join $array

Jetzt zeige ich Ihnen einen cleveren Trick, auf den Lee Dailey mich gebracht hat. Wenn Sie alle Elemente ohne Trennzeichen miteinander verknüpfen möchten, gehen Sie nicht so vor:

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

Sie können `-join` mit dem Array als Parameter ohne Präfix verwenden. Sehen Sie sich das folgende Beispiel an, das verdeutlicht, wovon ich spreche.

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a>-replace und -split

Die Operatoren `-replace` und `-split` werden für jedes Element im Array ausgeführt. Ich kann nicht behauptet, diese jemals auf diese Weise verwendet zu haben, aber hier finden Sie ein Beispiel.

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a>-contains

Mit dem `-contains`-Operator können Sie ein Array mit Werten überprüfen, um zu ermitteln, ob es einen bestimmten Wert enthält.

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a>-in

Wenn Sie überprüfen möchten, ob ein einzelner Wert mit einem von mehreren Werten übereinstimmt, können Sie den `-in`-Operator verwenden. Der Wert steht dann auf der linken und das Array auf der rechten Seite des Vorgangs.

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

Das Ganze kann recht umfangreich werden, wenn die Liste lang ist. Ich verwende häufig ein RegEx-Muster, wenn ich mehr als nur einige wenige Werte überprüfe.

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a>-eq und -ne

Die Verwendung des Gleichheitsoperators mit Arrays kann ziemlich kompliziert werden. Wenn sich das Array auf der linken Seite befindet, werden alle Elemente verglichen. Statt `True` wird das übereinstimmende Objekt zurückgegeben.

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

Wenn Sie den `-ne`-Operator verwenden, erhalten Sie alle Werte, die nicht gleich Ihrem Wert sind.

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

Wenn Sie dies in einer `if()`-Anweisung verwenden, ist ein Wert, der zurückgegeben wird, ein `True`-Wert. Wenn kein Wert zurückgegeben wird, handelt es sich um einen `False`-Wert. Die beiden nächsten Anweisungen werden zu `True` ausgewertet.

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

Darauf gehe ich gleich näher ein, wenn ich das Überprüfen auf `$null` erläutere.

### <a name="-match"></a>-match

Der Operator `-match` versucht, eine Übereinstimmung für jedes Element in der Auflistung zu finden.

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

Wenn Sie `-match` mit einem einzelnen Wert verwenden, wird eine spezielle Variable, `$Matches`, mit Übereinstimmungsinformationen aufgefüllt. Dies ist nicht der Fall, wenn ein Array auf diese Weise verarbeitet wird.

Wir können denselben Ansatz mit `Select-String` verwenden.

```powershell
$servers | Select-String SQL
```

In meinem Blog [The many ways to use regex][] (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken) habe ich `Select-String`, `-match` und die Variable `$matches` genauer erläutert.

### <a name="null-or-empty"></a>$null- oder leere Werte

Die Überprüfung auf `$null` oder leere Arrays kann knifflig sein. Hier zeige ich Ihnen einige häufige Fallen bei Arrays.

Auf den ersten Blick sieht diese Anweisung aus, als sollte sie funktionieren.

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

Ich habe aber gerade erläutert, wie `-eq` jedes Element im Array überprüft. Wenn wir also ein Array aus mehreren Elementen mit einem einzigen $null-Wert haben, würde dieses als `$true` ausgewertet.

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

Darum empfiehlt es sich, `$null` auf der linken Seite des Operators zu platzieren. Und schon ist dieses Szenario kein Problem mehr.

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

Ein `$null`-Array ist nicht dasselbe wie ein leeres Array. Wenn Sie wissen, dass es sich um ein Array handelt, überprüfen Sie die Anzahl von Objekten darin. Wenn das Array `$null` ist, lautet die Anzahl `0`.

```powershell
if ( $array.count -gt 0 )
{
    'Array isn't empty'
}
```

Es gibt noch eine weitere Falle, nach der Sie Ausschau halten sollten. Sie können `count` verwenden, auch wenn Sie nur über ein einzelnes Objekt verfügen, es sei denn, dieses Objekt ist ein `PSCustomObject`. Dies ist ein Fehler, der in PowerShell 6.1 behoben wurde.
Das sind zwar gute Nachrichten, aber viele Entwickler arbeiten noch mit Version 5.1 und müssen daher an dieser Stelle Vorsicht walten lassen.

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

Wenn Sie mit PowerShell 5.1 arbeiten, können Sie das Objekt vor der Überprüfung der Anzahl mit einem Array umschließen, um die exakte Anzahl zu erhalten.

```powershell
if ( @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

Um ganz sicherzugehen, überprüfen Sie zunächst auf `$null` und überprüfen dann die Anzahl.

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

### <a name="all--eq"></a>Alles -eq

Jemand frage neulich, [How to verify that every value in an array matches a given value][].
Der Reddit-Benutzer **/u/bis** hatte diese clevere [Lösung][] parat, die auf falsche Werte überprüft und das Ergebnis dann umdreht.

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a>Hinzufügen zu Arrays

Möglicherweise fragen Sie sich an dieser Stelle, wie Sie Elemente zu einem Array hinzufügen. Die schnelle Antwort lautet: „Gar nicht.“ Ein Array weist im Arbeitsspeicher eine unveränderliche Größe auf. Wenn Sie es erweitern oder ihm ein einzelnes Element hinzufügen müssen, müssen Sie ein neues Array erstellen und die Werte aus dem alten Array hineinkopieren. Das klingt nach viel Arbeit und Rechenaufwand, aber in PowerShell ist das Erstellen des neuen Arrays weniger komplex.

### <a name="array-addition"></a>Addition eines Arrays

Wir können den Additionsoperator mit Arrays verwenden, um ein neues Array zu erstellen. Wir haben diese beiden Arrays:

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

Diese können wir addieren, um ein neues Array zu erhalten.

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a>Plus-gleich (+=)

Wir können auf folgende Weise ein neues Array erstellen und diesem ein Element hinzufügen:

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

Denken Sie daran, dass Sie bei jeder Verwendung von `+=` die Elemente duplizieren und ein neues Array erstellen. Das ist bei kleinen Datasets kein Problem, lässt sich aber nur schlecht skalieren.

### <a name="pipeline-assignment"></a>Pipelinezuweisung

Sie können die Ergebnisse einer Pipeline in einer Variable zuweisen. Wenn mehrere Elemente enthalten sind, handelt es sich um ein Array.

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

Wenn wir über die Verwendung der Pipeline nachdenken, denken wir in der Regel an die typischen PowerShell-Einzeiler. Wir können die Pipeline aber auch mit `foreach()`-Anweisungen und anderen Schleifen nutzen. Anstatt also Elemente in einer Schleife zu einem Array hinzuzufügen, können wir Elemente in der Pipeline ablegen.

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

Indem wir die Ergebnisse von `foreach` einer Variable zuweisen, erfassen wir alle Objekte und erstellen ein einzelnes Array.

## <a name="array-types"></a>Arraytypen

Ein Array wird in PowerShell standardmäßig als `[PSObject[]]`-Typ erstellt. So kann es jeden Objekt- oder Werttyp enthalten. Das funktioniert, weil alles vom Typ `PSObject` geerbt wird.

### <a name="strongly-typed-arrays"></a>Stark typisierte Arrays

Sie können mit einer ähnlichen Syntax ein Array eines beliebigen Typs erstellen. Wenn Sie ein stark typisiertes Array erstellen, kann es nur Werte oder Objekte des angegebenen Typs enthalten.

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a>ArrayList

Dass sich nicht einfach so Elemente hinzufügen lassen, ist eine der größten Einschränkungen von Arrays, aber es gibt einige andere Auflistungen, mit denen sich dieses Problem lösen lässt.

Wenn ich ein Array brauche, mit dem ich schneller arbeiten kann, fällt mir in der Regel zuerst eine `ArrayList` ein. Eine Arrayliste funktioniert wie ein Objektarray überall dort, wo es notwendig ist, ermöglicht aber das schnelle Hinzufügen von Objekten.

So erstellen wir eine `ArrayList` und fügen Elemente hinzu.

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

Wir rufen .NET auf, um diesen Typ zu erhalten. In diesem Fall verwenden wir den Standardkonstruktor zum Erstellen. Dann rufen wir die `Add`-Methode auf, um ein Element hinzuzufügen.

Ich verwende `[void]` am Anfang der Zeile, weil ich den Rückgabecode unterdrücken möchte. Einige .NET-Aufrufe tun dies, und es kann zu einer unerwarteten Ausgabe führen.

Wenn die einzigen Daten, die in Ihrem Array enthalten sind, Zeichenfolgen sind, sollten Sie auch die Verwendung von [StringBuilder][] in Betracht ziehen. Das ist fast das Gleiche, bietet aber einige Methoden nur für die Verarbeitung von Zeichenfolgen. `StringBuilder` wurde speziell im Hinblick auf eine hohe Leistung entwickelt.

Viele Entwickler steigen von Arrays auf `ArrayList` um. Das stammt aber noch aus Zeiten, in denen C# keine generische Unterstützung bot. `ArrayList` ist zugunsten des generischen `List[]`-Elements als veraltet gekennzeichnet.

### <a name="generic-list"></a>Generischer List-Typ

Ein generischer Typ ist ein spezieller Typ in C#, der eine generalisierte Klasse definiert. Der Benutzer gibt dann bei der Erstellung die verwendeten Datentypen an. Wenn Sie also eine Liste mit Zahlen oder Zeichenfolgen haben möchten, definieren Sie, dass Sie eine Liste mit `int`- oder `string`-Typen benötigen.

So erstellen Sie eine Liste für Zeichenfolgen.

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

Und so erstellen Sie eine Liste für Zahlen.

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

Wir können ein vorhandenes Array in eine Liste umwandeln, ohne zuerst das Objekt erstellen zu müssen:

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

Mit der `using namespace`-Anweisung in PowerShell 5 und höher können wir die Syntax kürzen. Die `using`-Anweisung muss die erste Zeile im Skript sein. Durch Deklarieren eines Namespaces können Sie diese Anweisung in PowerShell weglassen, wenn Sie auf Datentypen verweisen.

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

Damit wird `List` viel nützlicher.

Ihnen steht eine weitere ähnliche Methode zur Verfügung: `Add`. Im Gegensatz zu ArrayList gibt es keinen Rückgabewert für die `Add`-Methode, daher müssen wir `void` nicht verwenden.

```powershell
$myList.Add(10)
```

Dennoch können wir wie in anderen Arrays auf die Elemente zugreifen.

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a>List[PSObject]

Sie können mit Listen beliebiger Typen arbeiten. Wenn Sie aber den Objekttyp nicht kennen, können Sie `[List[PSObject]]` als Container für die Objekte verwenden.

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a>Remove()

Sowohl `ArrayList` als auch das generische `List[]` unterstützen das Entfernen von Elementen aus der Auflistung.

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

Bei Werttypen wird der erste Wert aus der Liste entfernt. Sie können die Funktion immer wieder aufrufen, um den jeweils ersten Wert zu entfernen. Bei Verweistypen müssen Sie das Objekt angeben, das entfernt werden soll.

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

Die remove-Methode gibt `true` zurück, wenn sie das Element in der Auflistung finden und daraus entfernen konnte.

### <a name="more-collections"></a>Weitere Auflistungen

Es gibt noch viel mehr Auflistungen, die verwendet werden können, aber die gerade vorgestellten sind gute generische Ersatzmöglichkeiten für Arrays.
Wenn Sie mehr über diese Optionen erfahren möchten, sehen Sie sich dieses [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) an, das [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) zusammengestellt hat.

## <a name="other-nuances"></a>Andere Nuancen

Die wichtigen Funktionen habe ich abgedeckt, und jetzt möchte ich Ihnen noch einige weitere Aspekte vorstellen, bevor ich zum Ende komme.

### <a name="pre-sized-arrays"></a>Arrays mit vorab festgelegter Größe

Ich habe bereits erläutert, dass Sie die Größe eines Arrays nach dem Erstellen nicht mehr ändern können. Wir können ein Array mit einer vorab festgelegten Größe erstellen, indem wir das Array mit dem Konstruktor `new($size)` aufrufen.

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a>Multiplizieren von Arrays

Ein interessanter kleiner Trick ist, dass Sie ein Array mit einer Ganzzahl multiplizieren können.

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

### <a name="initialize-with-0"></a>Initialisieren mit 0

Es kommt häufig vor, dass Sie ein Array erstellen möchten, das nur aus Nullen besteht. Wenn Sie nur Ganzzahlen verwenden, enthält ein stark typisiertes Array mit Ganzzahlen standardmäßig nur Nullen.

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

Hier können wir auch den Multiplikationstrick anwenden.

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

Das Schöne bei diesem Trick ist, dass Sie jeden Wert verwenden können. Wenn Sie also lieber `255` als Standardwert haben möchten, ist dies ein guter Ansatz.

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a>Geschachtelte Arrays

Ein Array innerhalb eines Arrays wird als geschachteltes Array bezeichnet. Ich verwende diese selten in PowerShell, arbeite aber in anderen Sprachen häufig damit. Wenn Ihre Daten in ein rasterförmiges Muster passen, sollten Sie ein Array aus Arrays in Erwägung ziehen.

Es gibt zwei Möglichkeiten, ein zweidimensionales Array zu erstellen.

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

Das Komma ist in diesen Beispielen sehr wichtig. Weiter oben habe ich ein Beispiel eines normalen Arrays auf mehreren Zeilen vorgestellt, bei dem das Komma optional war. Bei mehrdimensionalen Arrays ist das nicht der Fall.

Bei Verwendung eines geschachtelten Arrays ändert sich die Indexnotation geringfügig. Mit `$data` (siehe oben) können wir auf den Wert 3 zugreifen.

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

Umschließen Sie jede Schachtelungsebene des Arrays mit eckigen Klammern. Der erste Satz Klammern umschließt das äußerste Array, danach geht es immer eine Ebene weiter nach innen.

### <a name="write-output--noenumerate"></a>Write-Output -NoEnumerate

In PowerShell werden Arrays häufig aufgezählt, oder ihre Umschließung wird aufgehoben. Dies ist ein wesentlicher Aspekt der Art und Weise, in der PowerShell die Pipeline verwendet, aber manchmal ist diese Vorgehensweise nicht wünschenswert.

Ich übergebe Objekte meist per Pipe an `Get-Member`, um Informationen zu den Objekten zu erhalten. Wenn ich auf diese Weise ein Array übergebe, wird dessen Umschließung aufgehoben, und „Get-Member“ zeigt die Member des Arrays an, nicht das tatsächliche Array.

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

Um zu verhindern, dass die Umschließung eines Arrays aufgehoben wird, können Sie `Write-Object -NoEnumerate` verwenden.

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

Ich kenne auch noch eine zwei Möglichkeit, das ist aber eher ein Hack (und in der Regel vermeide ich solche Hacks). Sie können ein Komma vor das Array setzen, bevor Sie es per Pipe übergeben.

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a>Zurückgeben eines Arrays

Die Umschließung eines Arrays wird auch aufgehoben, wenn Sie Werte aus einer Funktion ausgeben oder zurückgeben. Sie erhalten weiterhin ein Array, wenn Sie die Ausgabe einer Variable zuweisen, daher ist dies in der Regel kein Problem.

Der Haken bei der Sache ist, dass Sie dadurch über ein neues Array verfügen. Wenn dies ein Problem darstellt, können Sie `Write-Output -NoEnumerate $array` oder `return ,$array` als Umgehung verwenden.

## <a name="anything-else"></a>Noch etwas?

Ich weiß, das waren eine Menge Informationen. Ich hoffe, dass Sie jedes Mal, wenn Sie diesen Artikel lesen, etwas Neues lernen und diesen Artikel noch lange als gute Referenz nutzen können. Wenn Sie den Artikel hilfreich finden, teilen Sie ihn gerne mit anderen, die auch davon profitieren könnten.

Jetzt möchte ich Ihnen noch einen ähnlichen Artikel ans Herz legen, den ich über [Hashtabellen][] geschrieben habe.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[switch-Anweisung]: everything-about-switch.md
[Hashtabellen]: everything-about-hashtable.md
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/ (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken)
[How to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition (Wie lässt sich überprüfen, ob jeder Wert in einem Array mit einem angegebenen Wert übereinstimmt?)
[Lösung]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
