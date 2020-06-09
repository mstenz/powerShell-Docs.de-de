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
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a>Alles, was Sie schon immer über die IF-Anweisung wissen wollten

PowerShell verfügt wie viele andere Sprachen auch über Anweisungen zur bedingten Ausführung von Code in Ihren Skripts. Eine dieser Anweisungen ist die [if][]-Anweisung. In diesem Artikel wird einer der wichtigsten Befehle in PowerShell im Detail erläutert.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="conditional-execution"></a>Bedingte Ausführung

In Ihren Skripts müssen häufig Entscheidungen getroffen werden, welche Logik als Nächstes ausgeführt wird.
Und genau das ist mit bedingter Ausführung gemeint. Sie verfügen über eine Anweisung oder einen Wert, die bzw. der ausgewertet wird, damit basierend auf dieser Auswertung der nächste Codeabschnitt ausgeführt werden kann. Dieser Schritt wird mit der `if`-Anweisung ausgeführt.

## <a name="the-if-statement"></a>Die IF-Anweisung

Nachfolgend ist ein einfaches Beispiel der `if`-Anweisung gezeigt:

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

Zunächst wertet die `if`-Anweisung den Ausdruck in Klammern aus. Wenn das Ergebnis dieser Auswertung `$true` lautet, wird der `scriptblock` in geschweiften Klammern ausgeführt. Wenn der Wert `$false` lautet, wird der Skriptblock übersprungen.

Im vorherigen Beispiel hat die `if`-Anweisung lediglich die Variable `$condition` ausgewertet. Das Ergebnis lautete `$true`, sodass der `Write-Output`-Befehl innerhalb des Skriptblocks ausgeführt worden wäre.

In einigen Sprachen können Sie eine einzelne Codezeile nach der `if`-Anweisung einfügen, die dann ausgeführt wird. In PowerShell ist das nicht möglich. Für eine ordnungsgemäße Funktionsweise müssen Sie einen vollständigen `scriptblock` mit geschweiften Klammern angeben.

## <a name="comparison-operators"></a>Vergleichsoperatoren

In den meisten Fällen wird die `if`-Anweisung verwendet, um zwei Elemente zu vergleichen. In PowerShell sind für verschiedene Vergleichsszenarien spezielle Operatoren verfügbar. Bei Verwendung eines Vergleichsoperators wird der Wert auf der linken Seite mit dem Wert auf der rechten Seite verglichen.

### <a name="-eq-for-equality"></a>Der Operator „-eq“ zum Testen auf Gleichheit

Mit `-eq` wird überprüft, ob zwei Werte identisch sind.

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

In diesem Beispiel wird verglichen, ob der bekannte Wert `5` mit meinem `$value` übereinstimmt.

Ein möglicher Anwendungsfall ist die Statusüberprüfung für einen Wert, bevor eine Aktion für diesen Wert durchgeführt wird. Sie können z. B. mit einem Dienst arbeiten und überprüfen, ob er ausgeführt wird, bevor Sie `Restart-Service` für den Dienst aufrufen.

In anderen Sprachen wie C# ist die Verwendung von `==` für Gleichheitsüberprüfungen üblich (z. B.: `5 == $value`). In PowerShell ist dies jedoch nicht möglich. Ein weiterer gängiger Fehler ist, dass das Gleichheitszeichen (z. B.: `5 = $value`) verwendet wird. Dieses Zeichen ist jedoch für das Zuweisen von Werten zu Variablen reserviert. Indem Sie Ihren bekannten Wert auf der linken Seite platzieren, ist dieser Fehler weniger wahrscheinlich.

Für diesen (und andere) Operatoren gibt es einige Variationen.

- `-eq`, Gleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung
- `-ieq`, Gleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung
- `-ceq`, Gleichheitsoperator mit Beachtung der Groß-/Kleinschreibung

### <a name="-ne-not-equal"></a>Der Operator „-ne“ zum Testen auf Ungleichheit

Viele Operatoren verfügen über einen verwandten Operator, mit dem eine gegenteilige Überprüfung durchgeführt wird. `-ne` überprüft, ob die Werte ungleich sind.

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

Verwenden Sie diesen Operator, um sicherzustellen, dass die Aktion nur dann ausgeführt wird, wenn der Wert nicht `5` lautet. Ein gutes Beispiel für die Verwendung dieses Operators ist die Überprüfung, ob ein Dienst ausgeführt wird, bevor Sie versuchen, einen Neustart durchzuführen.

**Variationen:**

- `-ne` Ungleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung
- `-ine` Ungleichheitsoperator ohne Beachtung der Groß-/Kleinschreibung
- `-cne` Ungleichheitsoperator mit Beachtung der Groß-/Kleinschreibung

Dies sind die umgekehrten Variationen von `-eq`. Diese Typen werden gemeinsam gruppiert, wenn ich Variationen für weitere Operatoren ausführe.

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a>Die Operatoren „-gt“, „-ge“, „-lt“ und „-le“ zum Testen, ob ein Wert größer oder kleiner ist

Mit diesen Operatoren wird überprüft, ob ein Wert im Vergleich zu einem anderen Wert größer oder kleiner ist.
`-gt -ge -lt -le` stehen für die englischen Bezeichnungen GreaterThan, GreaterThanOrEqual, LessThan und LessThanOrEqual.

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

**Variationen:**

- `-gt`, größer als
- `-igt` größer als, ohne Beachtung der Groß-/Kleinschreibung
- `-cgt` größer als, mit Beachtung der Groß-/Kleinschreibung
- `-ge` größer als oder gleich
- `-ige` größer als oder gleich, ohne Beachtung der Groß-/Kleinschreibung
- `-cge` größer als oder gleich, mit Beachtung der Groß-/Kleinschreibung
- `-lt` kleiner als
- `-ilt` kleiner als, ohne Beachtung der Groß-/Kleinschreibung
- `-clt` kleiner als, mit Beachtung der Groß-/Kleinschreibung
- `-le` kleiner als oder gleich
- `-ile` kleiner als oder gleich, ohne Beachtung der Groß-/Kleinschreibung
- `-cle` kleiner als oder gleich, mit Beachtung der Groß-/Kleinschreibung

Der Zusatz zur Beachtung/Nichtbeachtung der Groß-/Kleinschreibung scheint mir bei diesen Operatoren irrelevant.

### <a name="-like-wildcard-matches"></a>Der Operator „-like“ für den Abgleich mit Platzhaltern

PowerShell verfügt über eine eigene Syntax für den platzhalterbasierten Musterabgleich, die mit dem Operator `-like` verwendet werden kann. Diese Platzhaltermuster sind recht simpel.

- `?` führt einen Abgleich für ein einzelnes Zeichen durch
- `*` führt einen Abgleich für eine beliebige Anzahl von Zeichen durch

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

Beachten Sie dabei, dass der Musterabgleich immer für die gesamte Zeichenfolge durchgeführt wird. Wenn der Abgleich für Zeichen in der Mitte der Zeichenfolge ausgeführt werden soll, muss `*` sowohl am Anfang als auch am Ende der Zeichenfolge platziert werden.

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

**Variationen:**

- `-like` Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung
- `-ilike` Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung
- `-clike` Übereinstimmung mit Platzhalter mit Beachtung der Groß-/Kleinschreibung
- `-notlike` Keine Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung
- `-inotlike` Keine Übereinstimmung mit Platzhalter ohne Beachtung der Groß-/Kleinschreibung
- `-cnotlike` Keine Übereinstimmung mit Platzhalter mit Beachtung der Groß-/Kleinschreibung

### <a name="-match-regular-expression"></a>Der Operator „-match“ bei regulären Ausdrücken

Der Operator `-match` kann verwendet werden, um für eine Zeichenfolge einen Abgleich auszuführen, der auf einem regulären Ausdruck basiert. Verwenden Sie diese Option, wenn die Platzhaltermuster für Ihre Anforderungen nicht flexibel genug sind.

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

Der Abgleich für ein RegEx-Muster wird standardmäßig für eine beliebige Stelle innerhalb der Zeichenfolge durchgeführt. Sie können jedoch auch eine Teilzeichenfolge für den Abgleich angeben:

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

RegEx ist eine komplexe und äußerst nützliche Sprache, mit der Sie sich vertraut machen sollten. In einem anderen Artikel gehe ich näher auf `-match` und [die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken][] ein.

**Variationen:**

- `-match` RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-imatch` RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-cmatch` RegEx-Übereinstimmung mit Beachtung der Groß-/Kleinschreibung
- `-notmatch` Keine RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-inotmatch` Keine RegEx-Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-cnotmatch` Keine RegEx-Übereinstimmung mit Beachtung der Groß-/Kleinschreibung

### <a name="-is-of-type"></a>Der Operator „-is“ zum Überprüfen des Typs

Sie können den Typ eines Werts mit dem Operator `-is` überprüfen.

```powershell
if ( $value -is [string] )
{
    # do something
}
```

Dies kann nützlich sein, wenn Sie mit Klassen arbeiten oder verschiedene Objekte über die Pipeline akzeptieren. Sie könnten z. B. über einen Dienst oder einen Dienstnamen als Eingabe verfügen. Überprüfen Sie dann, ob Sie über einen Dienst verfügen, und rufen Sie den Dienst ab, wenn Sie nur über den Namen verfügen.

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

**Variationen:**

- `-is` entspricht dem Typ
- `-isnot` entspricht nicht dem Typ

## <a name="collection-operators"></a>Auflistungsoperatoren

Bei Verwendung der oben stehenden Operatoren mit einem einzelnen Wert lautet das Ergebnis entweder `$true` oder `$false`. Wenn Sie mit Auflistungen arbeiten, funktioniert dies etwas anders. Jedes Element innerhalb der Auflistung wird ausgewertet, und der Operator gibt jeden Wert zurück, dessen Ergebnis `$true` lautet.

```powershell
PS> 1,2,3,4 -eq 3
3
```

Bei einer `if`-Anweisung funktioniert dies noch wie gewünscht. Wenn Ihr Operator einen Wert zurückgibt, gilt die gesamte Anweisung als `$true`.

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

Allerdings muss in diesem Zusammenhang ein wichtiger Aspekt berücksichtigt werden. Wenn Sie den Operator `-ne` auf diese Weise verwenden, wird die Logik umgekehrt. Denn bei Verwendung von `-ne` mit einer Auflistung wird `$true` zurückgegeben, wenn ein Element innerhalb der Auflistung nicht Ihrem Wert entspricht.

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

In einem solchen Szenario sollten Sie stattdessen mit den Operatoren `-contains` und `-in` arbeiten. Mit dem Operator `-notcontains` wird das erwartete Verhalten erzielt.

### <a name="-contains"></a>-contains

Der Operator `-contains` überprüft, ob Ihr Wert in der Auflistung vorhanden ist. Sobald eine Übereinstimmung ermittelt wird, gibt der Operator `$true` zurück.

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

Dies ist die bevorzugte Vorgehensweise, um zu überprüfen, ob eine Auflistung Ihren Wert enthält. Bei Verwendung von `Where-Object` (oder `-eq`) wird bei jedem Durchlauf die gesamte Liste geprüft, sodass der Vorgang deutlich langsamer ist.

**Variationen:**

- `-contains` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-icontains` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-ccontains` Übereinstimmung mit Beachtung der Groß-/Kleinschreibung
- `-notcontains` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-inotcontains` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-cnotcontains` Keine Übereinstimmung mit Beachtung der Groß-/Kleinschreibung

### <a name="-in"></a>-in

Der Operator `-in` ist mit dem Operator `-contains` vergleichbar, in diesem Fall steht die Auflistung jedoch rechts.

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

**Variationen:**

- `-in` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-iin` Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-cin` Übereinstimmung mit Beachtung der Groß-/Kleinschreibung
- `-notin` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-inotin` Keine Übereinstimmung ohne Beachtung der Groß-/Kleinschreibung
- `-cnotin` Keine Übereinstimmung mit Beachtung der Groß-/Kleinschreibung

## <a name="logical-operators"></a>Logische Operatoren

Logische Operatoren werden verwendet, um andere Ausdrücke umzukehren oder zu kombinieren.

### <a name="-not"></a>-not

Mit dem Operator `-not` wird ein Ausdruck von `$false` in `$true` oder von `$true` in `$false` umgekehrt. Im folgenden Beispiel soll eine Aktion ausgeführt werden, wenn für `Test-Path` das Ergebnis `$false` ermittelt wird.

```powershell
if ( -not ( Test-Path -Path $path ) )
```

Für die meisten bisher beschriebenen Operatoren gibt es eine Variation, bei der der Operator `-not` nicht verwendet werden muss. In einigen Situationen ist er jedoch nützlich.

### <a name="-operator"></a>! Operator

Sie können `!` als Alias für `-not` verwenden.

```powershell
if ( -not $value ){}
if ( !$value ){}
```

`!` wird häufig von Programmierern verwendet, die üblicherweise mit anderen Sprachen wie C# arbeiten. Ich bevorzuge eine ausgeschriebene Variante, weil ich diesen Operator in meinen Skripts nicht gut erkenne.

### <a name="-and"></a>-and

Mit dem Operator `-and` lassen sich Ausdrücke kombinieren. In diesem Fall muss für beide Ausdrücke `$true` zurückgegeben werden, damit der gesamte Ausdruck als `$true` betrachtet wird.

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

In diesem Beispiel muss `$age` auf der linken Seite 13 oder größer sein, auf der rechten Seite weniger als 55. Ich habe zusätzliche Klammern hinzugefügt, um das Beispiel übersichtlicher zu gestalten. Diese Klammern sind bei einfachen Ausdrücken jedoch optional. Nachfolgend sehen Sie ein Beispiel ohne diese Klammern.

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

Die Auswertung wird von links nach rechts durchgeführt. Wenn das Ergebnis für das erste Element `$false` lautet, wird der Vorgang frühzeitig beendet, und der Vergleich auf der rechten Seite wird nicht mehr durchgeführt. Dies ist nützlich, um sicherzustellen, dass ein Wert vorhanden ist, bevor Sie ihn verwenden. Für `Test-Path` wird z. B. ein Fehler zurückgegeben, wenn ein `$null`-Pfad angegeben wird.

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a>-or

Mit dem Operator `-or` können Sie zwei Ausdrücke angeben. Wenn das Ergebnis für einen dieser Ausdrücke `$true` lautet, wird `$true` zurückgegeben.

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

Wie beim `-and`-Operator erfolgt die Auswertung von links nach rechts. Wenn das Ergebnis des ersten Teils bereits `$true` lautet, wird die gesamte Anweisung als `$true` betrachtet, und der verbleibende Teil der Anweisung wird nicht mehr verarbeitet.

Beachten Sie außerdem, wie die Syntax für diese Operatoren funktioniert. Sie benötigen zwei separate Ausdrücke. Mitunter versuchen Benutzer, einen Ausdruck wie `$value -eq 5 -or 6` anzugeben, der nicht korrekt ist.

### <a name="-xor-exclusive-or"></a>Exklusives OR (-xor)

Dieser Operator ist etwas ungewöhnlich. Bei `-xor` darf nur für einen Ausdruck das Ergebnis `$true` ermittelt werden. Wenn für beide Elemente `$false` oder `$true` zurückgegeben wird, wird der gesamte Ausdruck als `$false` betrachtet. Der Ausdruck gilt also nur dann als `$true`, wenn unterschiedliche Ergebnisse für die enthaltenen Elemente zurückgegeben werden.

Die Anwendungsfälle für diesen logischen Operator sind eher eingeschränkt.

## <a name="bitwise-operators"></a>Bitweise Operatoren

Mit bitweisen Operatoren werden Berechnungen für die Bits innerhalb der Werte durchgeführt, um als Ergebnis einen neuen Wert zu ermitteln. Eine detaillierte Beschreibung von [Bitweise Operatoren][] geht über den Umfang dieses Artikels hinaus. Nachfolgend finden Sie jedoch eine Liste dieser Operatoren.

- `-band` binäres AND
- `-bor` binäres OR
- `-bxor` binäres exklusives OR
- `-bnot` binäres NOT
- `-shl` nach links verschieben
- `-shr` nach rechts verschieben

## <a name="powershell-expressions"></a>PowerShell-Ausdrücke

Innerhalb einer Bedingungsanweisung können die normalen PowerShell-Ausdrücke verwendet werden.

```powershell
if ( Test-Path -Path $Path )
```

`Test-Path` gibt bei der Ausführung `$true` oder `$false` zurück. Dies gilt ebenso für Befehle, die andere Werte zurückgeben.

```powershell
if ( Get-Process Notepad* )
```

Wenn ein Prozess zurückgegeben wird, lautet das Ergebnis `$true`, anderenfalls wird `$false` zurückgegeben. Auf diese Weise können Pipelineausdrücke oder andere PowerShell-Anweisungen verwendet werden:

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

Diese Ausdrücke lassen sich mit den Operatoren `-and` und `-or` kombinieren. Gegebenenfalls müssen jedoch Klammern verwendet werden, um sie in Teilausdrücke zu untergliedern.

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a>Überprüfung auf $null

Wenn kein Ergebnis oder der Wert `$null` zurückgegeben wird, wird dies in der `if`-Anweisung als `$false` betrachtet. Wenn eine dedizierte Überprüfung auf `$null` durchgeführt wird, sollte `$null` auf der linken Seite platziert werden.

```powershell
if ( $null -eq $value )
```

Beim Umgang mit `$null`-Werten in PowerShell müssen einige wichtige Aspekte berücksichtigt werden. Einzelheiten finden Sie im Artikel [Alles, was Sie schon immer über $null wissen wollten][].

### <a name="variable-assignment"></a>Variablenzuweisung

Beinahe hätte ich vergessen, auf diesen Aspekt einzugehen, doch glücklicherweise hat mich [Prasoon Karunan V][] darauf hingewiesen.

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

Wenn Sie einer Variablen einen Wert zuweisen, wird der Wert üblicherweise nicht an die Pipeline oder Konsole übergeben. Bei der Variablenzuweisung in einem Teilausdruck wird der Wert jedoch an die Pipeline übergeben.

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

Wie Sie sehen, verfügt die `$first`-Zuweisung über keine Ausgabe, die `$second`-Zuweisung jedoch schon. Bei einer Zuweisung in einer `if`-Anweisung wird diese wie die `$second`-Zuweisung oben ausgeführt. Nachfolgend finden Sie ein einfaches Beispiel für die Verwendung:

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

Wenn `$process` ein Wert zugewiesen wird, lautet das Ergebnis `$true`, und `$process` wird beendet.

Dies ist jedoch keine Gleichheitsüberprüfung und sollte nicht mit `-eq` verwechselt werden. Dieses Feature ist weniger offensichtlich und die meisten Benutzer wissen nicht, dass es auf diese Weise funktioniert.

## <a name="alternate-execution-path"></a>Alternativer Ausführungspfad

Bei der `if`-Anweisung kann nicht nur eine Aktion für den Fall angegeben werden, dass das Ergebnis `$true` ist, sondern auch für den Fall, dass das Ergebnis `$false` ist. Dazu wird die `else`-Anweisung verwendet.

### <a name="else"></a>else

Wenn die `else`-Anweisung verwendet wird, ist sie immer der letzte Teil der `if`-Anweisung.

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

In diesem Beispiel wird `$path` überprüft, um sicherzustellen, dass es sich um eine Datei handelt. Wenn die Datei gefunden wird, wird sie verschoben. Anderenfalls wird eine Warnung geschrieben. Diese Art von Verzweigungslogik wird sehr häufig verwendet.

### <a name="nested-if"></a>Geschachtelte IF-Anweisung

Da die Anweisungen `if` und `else` in einem Skriptblock verwendet werden, kann ein beliebiger PowerShell-Befehl innerhalb dieser Anweisungen platziert werden (einschließlich einer weiteren `if`-Anweisung). Dadurch können Sie eine deutlich komplexere Logik verwenden.

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

In diesem Beispiel testen wir zunächst den Pfad und führen anschließend eine Aktion aus. Wenn dabei ein Fehler auftritt, wird eine weitere Überprüfung durchgeführt, und der Benutzer erhält nähere Informationen.

### <a name="elseif"></a>Die elseif-Anweisung

Wir können nicht nur eine einzelne bedingte Überprüfung durchführen. Anstatt sie mit der `elseif`-Anweisung zu verschachteln, können wir sie auch mit `if`- und `else`-Anweisungen miteinander verketten.

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

Die Ausführung erfolgt von oben nach unten. Die oberste `if`-Anweisung wird zuerst ausgewertet. Wenn das Ergebnis `$false` lautet, wird mit der nächsten `elseif`- oder `else`-Anweisung in der Liste fortgefahren. Die letzte `else`-Anweisung ist die Standardaktion, die ausgeführt wird, wenn bei keiner anderen Anweisung `$true` zurückgegeben wird.

### <a name="switch"></a>switch

An dieser Stelle möchte ich auf die `switch`-Anweisung eingehen. Sie bietet eine alternative Syntax zum Durchführen mehrerer Vergleiche mit einem Wert. Bei `switch` geben Sie einen Ausdruck an, dessen Ergebnis dann mit einer Reihe unterschiedlicher Werte verglichen wird. Wenn für einen dieser Werte eine Übereinstimmung ermittelt wird, wird der entsprechende Codeblock ausgeführt. Im Folgenden finden Sie ein Beispiel:

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

Es gibt drei mögliche Werte, die `$itemType` entsprechen können. In diesem Fall wird die Übereinstimmung für `Role` erkannt. Dieses einfache Beispiel zeigt, wie der `switch`-Operator verwendet wird. Weitere Informationen zu diesem Operator finden Sie unter [Alles, was Sie schon immer über die Switch-Anweisung wissen wollten][].

## <a name="pipeline"></a>Pipeline

Die Pipeline ist ein einzigartiges und wichtiges PowerShell-Feature. Alle Werte, die nicht unterdrückt oder einer Variablen zugewiesen werden, werden in der Pipeline platziert. Mit der `if`-Anweisung lässt sich die Pipeline auf eine Art und Weise nutzen, die nicht unbedingt offensichtlich ist.

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

Jeder Skriptblock platziert die Ergebnisse der Befehle oder den Wert in der Pipeline. Anschließend wird das Ergebnis der IF-Anweisung der `$discount`-Variablen zugewiesen. In diesem Beispiel hätten diese Werte genauso einfach direkt der `$discount`-Variablen in jedem Skriptblock zugewiesen werden können. Ich verwende in einem solchen Szenario nicht sehr häufig die `if`-Anweisung, in letzter Zeit ist es jedoch zu einem solchen Fall gekommen.

### <a name="array-inline"></a>Inlinearray

Ich verfüge über eine Funktion [Invoke-SnowSql][], durch die eine ausführbare Datei mit einer Reihe von Befehlszeilenargumenten gestartet wird. Nachfolgend ist ein Ausschnitt dieser Funktion gezeigt, in dem das Array aus Argumenten erstellt wird.

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

Die Variablen `$Debug` und `$Path` sind Parameter der Funktion, die vom Endbenutzer angegeben werden.
Sie werden inline innerhalb der Initialisierung meines Arrays ausgewertet. Wenn `$Debug` wahr ist, werden diese Werte an der richtigen Stelle in `$snowSqlParam` platziert. Dasselbe gilt für die Variable `$Path`.

## <a name="simplify-complex-operations"></a>Vereinfachen von komplexen Vorgängen

Situationen mit einer deutlich zu großen Anzahl von Vergleichen, in denen Ihre IF-Anweisung viel zu weit in den rechten Bildschirmbereich hineinreicht, lassen sich nicht vermeiden.

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

Ihre Arbeit wird dadurch möglicherweise unübersichtlich, und es kann leicht zu Fehlern kommen. Doch es gibt einige Tricks, die in diesen Situationen weiterhelfen.

### <a name="line-continuation"></a>Zeilenfortsetzung

PowerShell verfügt über einige Operatoren, mit denen Sie Befehlszeilen umbrechen können. Mit den logischen Operatoren `-and` und `-or` können Sie einen Ausdruck umbrechen und in mehreren Zeilen anzeigen.

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

Der Ausdruck ist immer noch sehr lang, durch den Umbruch wird er jedoch deutlich übersichtlicher.
Ich greife üblicherweise auf diese Vorgehensweise zurück, wenn ich mehr als zwei Vergleiche durchführe oder zum rechten Bildschirmrand scrollen muss, um meine Logik zu sehen.

### <a name="pre-calculating-results"></a>Vorabberechnung von Ergebnissen

Diese Anweisung lässt sich außerhalb der IF-Anweisung platzieren, um nur das Ergebnis zu überprüfen.

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

Dadurch wird die Darstellung wesentlich übersichtlicher als im vorherigen Beispiel. Darüber hinaus können Sie einen Variablennamen verwenden, der Aufschluss darüber gibt, was Sie überprüfen. Dies ist zudem ein Beispiel für selbstdokumentierenden Code, der Kommentare überflüssig machen kann.

### <a name="multiple-if-statements"></a>Mehrere IF-Anweisungen

Dieser Code lässt sich in mehrere Anweisungen unterteilen, die jeweils einzeln überprüft werden. In diesem Fall werden die Ergebnisse mithilfe eines Flags oder einer Nachverfolgungsvariable zusammengefasst.

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

Für eine ordnungsgemäße Funktionsweise der Flaglogik musste die Logik in diesem Beispiel umgekehrt werden. Jede Auswertung wird als einzelne `if`-Anweisung ausgeführt. Der Vorteil dieser Vorgehensweise ist, dass Sie beim Debuggen genau erkennen, welche Schritte die Logik ausführt. Außerdem ist der Code deutlich ausführlicher geworden.

Der offensichtliche Nachteil ist, dass viel mehr Code geschrieben werden muss. Außerdem erscheint der Code komplexer, da aus einer einzelnen Logikzeile 25 oder mehr Zeilen entstehen.

### <a name="using-functions"></a>Verwenden von Funktionen

Die gesamte Validierungslogik lässt sich auch in eine Funktion verschieben. Wie Sie unten sehen, wird der Code dadurch sehr übersichtlich.

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

Sie müssen zwar die Funktion für die Validierung erstellen, anschließend können Sie jedoch deutlich einfacher mit dem Code arbeiten. Außerdem lässt sich dieser Code leichter testen. In Ihren Tests können Sie einen Aufruf von `Test-ADDriveConfiguration` simulieren, und Sie benötigen nur zwei Tests für diese Funktion. In einem Test wird `$true` und im anderen `$false` zurückgegeben. Aufgrund des geringen Umfangs ist das Testen der anderen Funktion einfacher.

Diese Funktion könnte die einzelne Zeile umfassen, mit der wir begonnen haben. Aber auch die umfassende Logik des letzten Abschnitts ist möglich. In beiden Fällen funktioniert diese Vorgehensweise gut, und Sie können die Implementierung später problemlos ändern.

## <a name="error-handling"></a>Fehlerbehandlung

Ein wichtiger Anwendungsfall der `if`-Anweisung ist die Überprüfung auf Fehlerbedingungen, bevor Fehler auftreten. Beispielsweise können Sie überprüfen, ob ein Ordner bereits vorhanden ist, bevor Sie ihn erstellen.

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

Wenn Sie davon ausgehen, dass eine Ausnahme auftritt, handelt es sich nicht wirklich um eine Ausnahme. Daher sollten Sie so oft wie möglich Ihre Werte überprüfen und Ihre Bedingungen validieren.

Nähere Informationen zur Ausnahmebehandlung finden Sie im Artikel [Alles, was Sie schon immer über Ausnahmen wissen wollten][].

## <a name="final-words"></a>Abschließende Worte

Die `if`-Anweisung ist zwar eine einfache Anweisung, jedoch ein zentrales Element von PowerShell. Üblicherweise wird sie in jedem Skript mehrmals verwendet. Ich hoffe, dass Sie nun besser mit dieser Anweisung vertraut sind.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[Bitweise Operatoren]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/ (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken)
[Alles, was Sie schon immer über Ausnahmen wissen wollten]: everything-about-exceptions.md
[Alles, was Sie schon immer über $null wissen wollten]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[Alles, was Sie schon immer über die switch-Anweisung wissen wollten]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
