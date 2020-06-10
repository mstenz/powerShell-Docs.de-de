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
# <a name="everything-you-wanted-to-know-about-null"></a>Alles, was Sie schon immer über $null wissen wollten

Das PowerShell-`$null` scheint oft einfach zu sein, aber es hat viele Nuancen. Sehen wir uns nun `$null` an, damit Sie wissen, was passiert, wenn Sie unerwartet auf einen `$null`-Wert stoßen.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="what-is-null"></a>Was ist NULL?

Sie können sich NULL als unbekannten oder leeren Wert vorstellen. Eine Variable ist NULL, bis Sie ihr einen Wert oder ein Objekt zuweisen. Dies kann wichtig sein, da einige Befehle einen Wert erfordern und Fehler generieren, wenn der Wert NULL ist.

### <a name="powershell-null"></a>PowerShell-$null

`$null` ist eine automatische Variable in PowerShell, die zur Darstellung von NULL verwendet wird. Sie können sie Variablen zuweisen, in Vergleichen verwenden und als Platzhalter für NULL in einer Sammlung verwenden.

PowerShell behandelt `$null` als Objekt mit dem Wert NULL. Dies unterscheidet sich von dem, was Sie möglicherweise erwarten, wenn Sie eine andere Sprache gewohnt sind.

## <a name="examples-of-null"></a>Beispiele für $null

Wenn Sie versuchen, eine Variable zu verwenden, die Sie nicht initialisiert haben, ist der Wert `$null`. Dies ist eine der gängigsten Möglichkeiten, wie sich `$null`-Werte in Ihren Code einschleichen.

```powershell
PS> $null -eq $undefinedVariable
True
```

Wenn Sie einen Variablennamen falsch schreiben, betrachtet PowerShell dies als eine andere Variable, und der Wert ist `$null`.

Eine andere Möglichkeit ist, dass `$null`-Werte von anderen Befehlen stammen, die keine Ergebnisse liefern.

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a>Auswirkungen von $null

Wie sich `$null`-Werte auf Ihren Code auswirken, hängt davon ab, wo sie auftreten.

### <a name="in-strings"></a>In Zeichenfolgen

Wenn Sie `$null` in einer Zeichenfolge verwenden, handelt es sich um einen leeren Wert (oder eine leere Zeichenfolge).

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

Dies ist einer der Gründe, warum ich Variablen in Klammern setze, wenn ich sie in Protokollmeldungen verwende. Es ist noch wichtiger, die Ränder der Variablenwerte zu identifizieren, wenn sich der Wert am Ende der Zeichenfolge befindet.

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

So sind leere Zeichenfolgen und `$null`-Werte leicht zu erkennen.

### <a name="in-numeric-equation"></a>In numerischen Gleichungen

Wenn ein `$null`-Wert in einer numerischen Gleichung verwendet wird, sind die Ergebnisse ungültig, auch wenn sie keinen Fehler verursachen. Manchmal wird `$null` mit `0` ausgewertet, und in anderen Fällen ist das gesamte Ergebnis `$null`.
Im Folgenden finden Sie ein Beispiel für eine Multiplikation, die abhängig von der Reihenfolge der Werte 0 oder `$null` ergibt.

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a>Anstelle einer Sammlung

Mit einer Sammlung können Sie einen Index für den Zugriff auf Werte verwenden. Wenn Sie versuchen, eine Indizierung in einer Sammlung durchzuführen, die tatsächlich `null` ist, erhalten Sie folgende Fehlermeldung: `Cannot index into a null array`.

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

Wenn Sie über eine Sammlung verfügen, aber versuchen, auf ein Element zuzugreifen, das nicht in der Sammlung enthalten ist, erhalten Sie ein `$null`-Ergebnis.

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a>Anstelle eines Objekts

Wenn Sie versuchen, auf eine Eigenschaft oder untergeordnete Eigenschaft eines Objekts zuzugreifen, das nicht über die angegebene Eigenschaft verfügt, erhalten Sie einen `$null`-Wert wie für eine nicht definierte Variable. In diesem Fall spielt es keine Rolle, ob die Variable `$null` oder ein tatsächliches Objekt ist.

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a>Methode für einen Ausdruck mit NULL-Wert

Durch das Aufrufen einer Methode eines `$null`-Objekts wird eine `RuntimeException` ausgelöst.

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

Wenn ich die Meldung `You cannot call a method on a null-valued expression` sehe, suche ich zuerst nach Stellen, an denen ich eine Methode für eine Variable aufrufe, ohne sie zuerst auf `$null` zu überprüfen.

## <a name="checking-for-null"></a>Überprüfung auf $null

Sie haben vielleicht bemerkt, dass ich bei der Überprüfung auf `$null` in meinen Beispielen `$null` immer auf der linken Seite platziere. Dies ist beabsichtigt, denn es handelt sich dabei um eine anerkannte bewährte PowerShell-Methode. Es gibt einige Szenarios, in denen das Platzieren auf der rechten Seite nicht das erwartete Ergebnis liefert.

Sehen Sie sich das nächste Beispiel an, und versuchen Sie, die Ergebnisse vorherzusagen:

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

Wenn ich `$value` nicht definiere, wird der erste Ausdruck als `$true` ausgewertet, und die Meldung lautet `The array is $null`. Die Falle ist, dass ein `$value` erstellt werden kann, bei dem beide Ausdrücke als `$false` ausgewertet werden.

```powershell
$value = @( $null )
```

In diesem Fall ist der `$value` ein Array, das ein `$null` enthält. `-eq` überprüft jeden Wert im Array und gibt das übereinstimmende `$null` zurück. Dies wird als `$false` ausgewertet. `-ne` gibt alle Elemente zurück, die nicht mit `$null` identisch sind, und in diesem Fall gibt es keine Ergebnisse (dies wird auch als `$false` ausgewertet). Keines der beiden ist `$true`, auch wenn es so aussieht, als sollte dies auf eines zutreffen.

Wir können nicht nur einen Wert erstellen, bei dem beide als `$false` ausgewertet werden, es ist auch möglich, einen Wert zu erstellen, bei dem beide als `$true` ausgewertet werden. Ein [guter Beitrag][] von Mathias Jessen (@IISResetMe) behandelt dieses Szenario ausführlich.

### <a name="psscriptanalyzer-and-vscode"></a>PSScriptAnalyzer und VSCode

Das [PSScriptAnalyzer][]-Modul verfügt über eine Regel mit dem Namen `PSPossibleIncorrectComparisonWithNull`, die prüft, ob das Problem vorliegt.

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

Da VS Code die PSScriptAnalyzer-Regeln ebenfalls verwendet, wird dies auch in Ihrem Skript als Problem hervorgehoben oder identifiziert.

### <a name="simple-if-check"></a>Einfache if-Überprüfung

Eine gängige Methode zur Überprüfung auf einen Nicht-$null-Wert ist die Verwendung einer einfachen `if()`-Anweisung ohne Vergleich.

```powershell
if ( $value )
{
    Do-Something
}
```

Wenn der Wert `$null` ist, ergibt dies `$false`. Dies ist leicht lesbar, aber achten Sie darauf, dass genau nach dem gesucht wird, wonach gesucht werden soll. Ich lese diese Codezeile wie folgt:

> Wenn `$value` über einen Wert verfügt.

Aber das ist nicht alles. Diese Zeile sagt tatsächlich aus:

> Wenn `$value` nicht `$null` oder `0` oder `$false` oder ein `empty string` ist

Im Folgenden finden Sie ein ausführlicheres Beispiel für diese Anweisung.

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

Es ist in Ordnung, eine einfache `if`-Prüfung zu verwenden, solange Sie sich merken, dass diese anderen Werte als `$false` zählen und nicht nur, dass eine Variable über einen Wert verfügt.

Beim Umgestalten von Code vor einigen Tagen ist dieses Problem aufgetreten. Er enthielt eine grundlegende Eigenschaftenüberprüfung wie diese.

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

Ich wollte das Vorhandensein einer Objekteigenschaft überprüfen, bevor ich ihr einen Wert zuwies. In den meisten Fällen verfügte das ursprüngliche Objekt über einen Wert, der in der `if`-Anweisung als `$true` ausgewertet wurde. Doch manchmal wurde der Wert nicht festgelegt. Ich habe den Code gedebuggt und festgestellt, dass das Objekt die Eigenschaft enthielt, aber es handelte sich um einen leeren Zeichenfolgenwert. Dadurch wurde die Aktualisierung mit der vorherigen Logik verhindert. Nachdem ich eine ordnungsgemäße `$null`-Überprüfung hinzugefügt hatte, funktionierte alles.

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

Kleine Fehler wie diese sind schwer zu erkennen und lassen mich akribisch Werte auf `$null` überprüfen.

## <a name="nullcount"></a>$null.Count

Wenn Sie versuchen, über einen `$null`-Wert auf eine Eigenschaft zuzugreifen, ist die Eigenschaft auch `$null`. Die `count`-Eigenschaft ist die Ausnahme von dieser Regel.

```powershell
PS> $value = $null
PS> $value.count
0
```

Wenn Sie über einen `$null`-Wert verfügen, ist `count` gleich `0`. Diese spezielle Eigenschaft wird von PowerShell hinzugefügt.

### <a name="pscustomobject-count"></a>[PSCustomObject] Count

Fast alle Objekte in PowerShell haben diese Count-Eigenschaft. Eine wichtige Ausnahme ist `[PSCustomObject]` in Windows PowerShell 5.1 (dies wird in PowerShell 6.0 korrigiert). Es verfügt nicht über eine Count-Eigenschaft, sodass Sie einen `$null`-Wert erhalten, wenn Sie versuchen, sie zu verwenden. Ich betone dies hier, damit Sie nicht versuchen, `.Count` anstelle einer `$null`-Prüfung zu verwenden.

Das Ausführen dieses Beispiels in Windows PowerShell 5.1 und PowerShell 6.0 führt zu unterschiedlichen Ergebnissen.

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a>Leeres NULL

Es gibt eine besondere Art von `$null`, die anders agiert als die anderen. Ich nenne sie das leere `$null`, aber tatsächlich handelt es sich um ein [System.Management.Automation.Internal.AutomationNull][]. Dieses leere `$null` ist das Ergebnis einer Funktion oder eines Skriptblocks, die/der nichts zurückgibt (ein void-Ergebnis).

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

Wenn Sie dies mit `$null` vergleichen, erhalten Sie einen `$null`-Wert. Bei Verwendung in einer Auswertung, wo ein Wert erforderlich ist, ist der Wert immer `$null`. Doch bei Platzierung in einem Array wird es wie ein leeres Array behandelt.

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

Sie können über ein Array verfügen, das einen `$null`-Wert enthält und dessen `count` gleich `1` ist. Wenn Sie jedoch ein leeres Ergebnis in einem Array platzieren, wird es nicht als Element gezählt. Die Anzahl ist `0`.

Wenn Sie das leere `$null` wie eine Sammlung behandeln, ist es leer.

### <a name="pipeline"></a>Pipeline

Dieser Unterschied wird besonders bei Verwendung der Pipeline deutlich. Sie können einer Pipe einen `$null`-Wert übergeben, aber keinen leeren `$null`-Wert.

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

Abhängig von Ihrem Code sollten Sie `$null` in Ihrer Logik berücksichtigen.

Überprüfen Sie in jedem Fall zuerst auf `$null`

- Herausfiltern von NULL in der Pipeline (`... | Where {$null -ne $_} | ...`)
- Verarbeiten von NULL in der Pipelinefunktion

## <a name="foreach"></a>foreach

Eines meiner bevorzugten Features von `foreach` ist, dass es keine Aufzählung für eine `$null`-Sammlung ausführt.

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

Dies erspart mir die Überprüfung der Sammlung auf `$null`, bevor ich eine Aufzählung für sie ausführe. Wenn Sie über eine Sammlung von `$null`-Werten verfügen, kann `$node` weiterhin `$null` sein.

„foreach“ funktioniert so seit PowerShell 3.0. Wenn Sie eine ältere Version haben, ist dies nicht der Fall. Dies ist eine der wichtigen Änderungen, die Sie beachten sollten, wenn Sie Code für die 2.0-Kompatibilität zurückportieren.

## <a name="value-types"></a>Werttypen

Technisch gesehen können nur Verweistypen `$null` werden. PowerShell ist jedoch sehr großzügig und ermöglicht, dass Variablen jeden beliebigen Typ haben können. Wenn Sie jedoch einen Werttyp strikt festlegen, kann er nicht `$null` werden.
PowerShell konvertiert `$null` für viele Typen in einen Standardwert.

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

Für einige Typen gibt es keine gültige Konvertierung aus `$null`. Diese Typen generieren eine `Cannot convert null to type`-Fehlermeldung.

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a>Funktionsparameter

Die Verwendung von Werten mit strikt festgelegtem Typ in Funktionsparametern ist sehr üblich. Im Allgemeinen lernen wir, die Typen unserer Parameter zu definieren, auch wenn wir dazu neigen, die Typen anderer Variablen in unseren Skripts nicht zu definieren. Möglicherweise verfügen Sie in ihren Funktionen bereits über einige Variablen mit strikt festgelegtem Typ und sind sich dessen nicht einmal bewusst.

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

Sobald Sie den Typ des Parameters als `string` festgelegt haben, kann der Wert nie `$null` werden. Es ist üblich, zu überprüfen, ob ein Wert `$null` ist, um festzustellen, ob der Benutzer einen Wert bereitgestellt hat.

```powershell
if ( $null -ne $Value ){...}
```

`$Value` ist eine leere Zeichenfolge `''`, wenn kein Wert angegeben wird. Verwenden Sie stattdessen die automatische Variable `$PSBoundParameters.Value`.

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

`$PSBoundParameters` enthält nur die Parameter, die beim Aufrufen der Funktion angegeben wurden.
Sie können auch die `ContainsKey`-Methode verwenden, um die Eigenschaft zu überprüfen.

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a>IsNotNullOrEmpty

Wenn der Wert eine Zeichenfolge ist, können Sie eine statische Zeichenfolgenfunktion verwenden, um zu überprüfen, ob der Wert gleichzeitig `$null` oder eine leere Zeichenfolge ist.

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

Ich verwende dies häufig, wenn ich weiß, dass der Werttyp eine Zeichenfolge sein sollte.

## <a name="when-i-null-check"></a>Wann ich auf $null überprüfe

Ich bin ein defensiver Skriptschreiber. Jedes Mal, wenn ich eine Funktion aufrufe und einer Variablen zuweise, überprüfe ich sie auf `$null`.

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

Ich ziehe es vor, `if` oder `foreach` statt `try/catch` zu verwenden. Verstehen Sie mich nicht falsch, ich verwende `try/catch` noch oft genug. Wenn ich jedoch auf eine Fehlerbedingung oder einen leeren Ergebnissatz testen kann, kann ich meine Ausnahmebehandlung für echte Ausnahmen reservieren.

Außerdem überprüfe ich gern auf `$null`, bevor ich einen Wert indiziere oder Methoden eines Objekts aufrufe. Diese beiden Aktionen gelingen nicht für ein `$null`-Objekt, darum halte ich es für wichtig, sie zuerst zu überprüfen. Diese Szenarios wurden bereits zuvor in diesem Beitrag behandelt.

### <a name="no-results-scenario"></a>„Keine Ergebnisse“-Szenario

Es ist wichtig zu wissen, dass unterschiedliche Funktionen und Befehle das „Keine Ergebnisse“-Szenario unterschiedlich behandeln. Viele PowerShell-Befehle geben das leere `$null` und eine Fehlermeldung im Fehlerdatenstrom zurück. Aber andere lösen Ausnahmen aus oder geben ein Statusobjekt zurück. Sie müssen immer noch entscheiden, wie die Befehle, die Sie verwenden, mit den „Keine Ergebnisse“- und Fehlerszenarios umgehen.

## <a name="initializing-to-null"></a>Initialisieren mit $null

Eine Gewohnheit, die ich übernommen habe, ist die Initialisierung aller Variablen vor der Verwendung. Sie müssen dies in anderen Sprachen auch tun. Am Anfang meiner Funktion oder während der Eingabe einer foreach-Schleife definiere ich alle Werte, die ich verwende.

Bitte sehen Sie sich das Szenario im Folgenden genau an. Es ist ein Beispiel für einen Fehler, den ich nachverfolgen musste.

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

Hier wird erwartet, dass `Get-Something` entweder ein Ergebnis oder ein leeres `$null` zurückgibt. Wenn ein Fehler auftritt, wird er protokolliert. Dann überprüfen wir das Ergebnis vor der Verarbeitung auf Gültigkeit.

Der in diesem Code versteckte Fehler tritt auf, wenn `Get-Something` eine Ausnahme auslöst und `$result` keinen Wert zuweist. Der Fehler tritt vor der Zuweisung auf, sodass wir nicht einmal `$null` der `$result`-Variablen zuweisen. `$result` enthält weiterhin den vorher gültigen `$result`-Wert aus anderen Iterationen.
`Update-Something` wird in diesem Beispiel mehrfach für das gleiche Objekt ausgeführt.

Ich lege `$result` direkt innerhalb der foreach-Schleife auf `$null` fest, bevor ich es verwende, um dieses Problem zu vermeiden.

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a>Bereichsprobleme

Dies trägt auch dazu bei, Bereichsprobleme zu vermeiden. In diesem Beispiel weisen wir `$result` in einer Schleife immer wieder Werte zu. Da PowerShell jedoch zulässt, dass Variablenwerte von außerhalb der Funktion in den Gültigkeitsbereich der aktuellen Funktion aufgenommen werden, werden durch ihre Initialisierung innerhalb Ihrer Funktion Fehler vermieden, die auf diese Weise eingeführt werden können.

Eine nicht initialisierte Variable in der Funktion ist nicht `$null`, wenn für sie in einem übergeordneten Bereich ein Wert festgelegt wird.
Der übergeordnete Bereich könnte eine andere Funktion sein, die ihre Funktion aufruft und die gleichen Variablennamen verwendet.

Wenn ich in demselben `Do-something` Beispiel die Schleife entferne, würde es folgendem Beispiel ähneln:

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

Wenn der Aufruf von `Get-Something` eine Ausnahme auslöst, findet meine `$null`-Prüfung das `$result` aus `Invoke-Something`. Wenn Sie den Wert in ihrer Funktion initialisieren, wird dieses Problem vermieden.

Die Benennung von Variablen ist schwierig, und es ist üblich, dass ein Autor dieselben Variablennamen in mehreren Funktionen verwendet. Ich weiß, dass ich `$node`, `$result`, `$data` immer wieder verwende. Daher ist das Risiko groß, dass Werte aus unterschiedlichen Bereichen dort auftauchen, wo sie nichts zu suchen haben.

## <a name="redirect-output-to-null"></a>Umleiten der Ausgabe zu $null

Ich habe im gesamten Artikel über `$null`-Werte gesprochen, aber das Thema ist nicht vollständig, wenn ich nicht das Umleiten der Ausgabe zu `$null` erwähne. Manchmal geben Befehle Informationen oder Objekte aus, die Sie unterdrücken möchten. Hierzu können Sie die Ausgabe zu `$null` umleiten.

### <a name="out-null"></a>Out-Null

Der Befehl „Out-Null“ ist die integrierte Möglichkeit zum Umleiten von Pipelinedaten an `$null`.

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a>Zuweisen zu $null

Sie können die Ergebnisse eines Befehls `$null` zuweisen, anstatt `Out-Null` zu verwenden.

```powershell
$null = New-Item -Type Directory -Path $path
```

Da `$null` ein konstanter Wert ist, können Sie ihn nie überschreiben. Es gefällt mir in meinem Code nicht so recht, ist aber häufig schneller als `Out-Null`.

### <a name="redirect-to-null"></a>Umleiten zu $null

Sie können auch den Umleitungsoperator verwenden, um die Ausgabe an `$null` zu senden.

```powershell
New-Item -Type Directory -Path $path > $null
```

Wenn Sie mit in der Befehlszeile ausführbaren Dateien arbeiten, die in unterschiedlichen Datenströmen ausgeben. Sie können alle Ausgabedatenströme wie folgt zu `$null` umleiten:

```powershell
git status *> $null
```

## <a name="summary"></a>Zusammenfassung

Ich habe in diesem Artikel vieles angeschnitten und weiß, dass dieser Artikel fragmentierter ist als die meisten meiner eingehenden Abhandlungen. Der Grund hierfür ist, dass `$null`-Werte an vielen verschiedenen Stellen in PowerShell auftauchen können, und alle Nuancen sind spezifisch für die Positionen, an denen sie auftreten. Ich hoffe, dass Sie Ihre Kenntnisse über `$null` erweitern konnten und sich der obskureren Szenarios bewusst sind, in die Sie hineingeraten könnten.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Guter Beitrag]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
