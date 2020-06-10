---
title: Alles, was Sie schon immer über die switch-Anweisung wissen wollten
description: Die switch-Anweisung in PowerShell bietet Features, die es in anderen Sprachen nicht gibt.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ebf6191d56374273465ae6bee49ef82a02cc1580
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149423"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a>Alles, was Sie schon immer über die switch-Anweisung wissen wollten

Wie viele andere Sprachen bietet PowerShell Befehle zur Ablaufsteuerung der Ausführung innerhalb Ihrer Skripts. Eine dieser Anweisungen ist die [switch][]-Anweisung in PowerShell mit Features, die es in anderen Sprachen nicht gibt. Heute beschäftigen wir uns eingehend mit dem Arbeiten mit der PowerShell-Anweisung `switch`.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="if-statement"></a>If-Anweisung

Eine der ersten Anweisungen, die Sie kennenlernen, ist die `if`-Anweisung. Sie können einen Skriptblock ausführen, wenn eine Anweisung `$true` ist.

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

Eine viel kompliziertere Logik ist möglich, wenn Sie die Anweisungen `elseif` und `else` nutzen. Hier ist ein Beispiel, bei dem ich einen numerischen Wert für einen Wochentag habe und ich den Namen als Zeichenfolge abrufen möchte.

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

Es stellt sich heraus, dass dies ein weit verbreitetes Muster ist und dass es viele Möglichkeiten gibt, damit umzugehen. Eine davon ist mit einer `switch`-Anweisung.

## <a name="switch-statement"></a>switch-Anweisung

Mit der `switch`-Anweisung können Sie eine Variable und eine Liste möglicher Werte angeben. Wenn der Wert mit der Variablen übereinstimmt, wird der zugehörige Skriptblock ausgeführt.

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

In diesem Beispiel entspricht der Wert von `$day` einem der numerischen Werte. Dann wird `$result` der richtige Name zugewiesen. Wir weisen in diesem Beispiel nur eine Variable zu, aber jeder beliebige PowerShell-Befehl kann in diesen Skriptblöcken ausgeführt werden.

### <a name="assign-to-a-variable"></a>Zuweisen zu einer Variablen

Dieses letzte Beispiel kann auf andere Weise geschrieben werden.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

Wir legen den Wert in der PowerShell-Pipeline ab und weisen ihn `$result` zu. Dasselbe lässt sich mit den Anweisungen `if` und `foreach` realisieren.

### <a name="default"></a>Standard

Wir können das Schlüsselwort `default` nutzen, um zu bestimmen, was geschehen soll, wenn es keine Übereinstimmung gibt.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

Hier geben wir im Standardfall den Wert `Unknown` zurück.

### <a name="strings"></a>Zeichenfolgen

In den letzten Beispielen habe ich Zahlen auf Übereinstimmung abgeglichen, aber Sie können auch Zeichenfolgen abgleichen.

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

Ich habe beschlossen, die Abgleiche auf `Component`, `Role` und `Location` hier nicht in Anführungszeichen zu setzen, um hervorzuheben, dass sie optional sind. `switch` behandelt diese in den meisten Fällen als Zeichenfolge.

## <a name="arrays"></a>Arrays

Eines der coolen Features der PowerShell-Anweisung `switch` ist die Handhabung von Arrays. Wenn Sie an `switch` ein Array übergeben, wird jedes Element in dieser Sammlung verarbeitet.

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

Wenn Ihr Array sich wiederholende Elemente enthält, werden diese im entsprechenden Abschnitt mehrfach abgeglichen.

### <a name="psitem"></a>PSItem

Sie können `$PSItem` oder `$_` nutzen, um auf das aktuelle Element zu verweisen, das verarbeitet wurde. Wenn wir einen einfachen Abgleich vornehmen, ist `$PSItem` der Wert, den wir auf Übereinstimmung abgleichen. Im nächsten Abschnitt möchte ich einige komplexere Abgleiche durchführen, bei denen diese Variable zum Einsatz kommt.

## <a name="parameters"></a>Parameter

Ein besonderes Merkmal der PowerShell-Anweisung `switch` ist, dass sie über eine Reihe von [switch-Parameter][] verfügt, die ihre Funktionsweise beeinflussen.

### <a name="-casesensitive"></a>-CaseSensitive

Standardmäßig wird beim Abgleich Groß-/Kleinschreibung nicht beachtet. Wenn Sie Groß-/Kleinschreibung beachten müssen, können Sie `-CaseSensitive`verwenden. Dies kann in Kombination mit den anderen Schalterparametern genutzt werden.

### <a name="-wildcard"></a>-Wildcard

Mit dem Schalter `-wildcard` können wir Platzhalterunterstützung aktivieren. Dabei wird für jeden Abgleich auf Übereinstimmung die gleiche Platzhalterlogik wie beim Operator `-like` genutzt.

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

Hier verarbeiten wir eine Nachricht und geben sie dann je nach Inhalt in verschiedenen Datenströmen aus.

### <a name="-regex"></a>-Regex

Die switch-Anweisung unterstützt Übereinstimmungen mit regulären Ausdrücken (RegEx) ebenso wie Platzhalter.

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

Weitere Beispiele für die Nutzung regulärer Ausdrücke finden Sie in einem anderen Artikel von mir: [The many ways to use regex][] (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken)

### <a name="-file"></a>-File

Ein wenig bekanntes Merkmal der switch-Anweisung ist, dass sie eine Datei mit dem Parameter `-File` verarbeiten kann. Sie verwenden `-file` mit einem Pfad zu einer Datei, anstatt dafür einen variablen Ausdruck anzugeben.

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

Dies funktioniert wie die Verarbeitung eines Arrays. In diesem Beispiel kombiniere ich dies mit dem Platzhalterabgleich und nutze `$PSItem`. Damit ließe sich eine Protokolldatei verarbeiten und in Abhängigkeit von Übereinstimmungen mit regulären Ausdrücken in Warn- und Fehlermeldungen umwandeln.

## <a name="advanced-details"></a>Details zur erweiterten Verarbeitung

Jetzt, da Ihnen all diese dokumentierten Merkmale bekannt sind, können wir sie im Rahmen einer komplexeren Verarbeitung nutzen.

### <a name="expressions"></a>Ausdrücke

`switch` kann für einen Ausdruck statt für eine Variable gelten.

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

Das Ergebnis des Ausdrucks ist der für den Abgleich auf Übereinstimmung genutzte Wert.

### <a name="multiple-matches"></a>Mehrere Übereinstimmungen

Möglicherweise haben Sie dies bereits bemerkt, aber eine `switch`-Anweisung kann mit mehreren Bedingungen übereinstimmen. Dies gilt insbesondere, wenn der Abgleich mit `-wildcard` oder `-regex` erfolgt. Sie können dieselbe Bedingung mehrmals hinzufügen, die alle ausgelöst werden.

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

Alle drei dieser Anweisungen werden ausgelöst. Dies zeigt, dass jede Bedingung (der Reihe nach) geprüft wird. Dies gilt für die Verarbeitung von Arrays, bei der jedes Element jede Bedingung prüft.

### <a name="continue"></a>Continue

Normalerweise würde ich an dieser Stelle die Anweisung `break` einführen, aber es ist besser, wenn wir zunächst erfahren, wie `continue` verwendet wird. Ebenso wie bei einer `foreach`-Schleife fährt `continue` mit dem nächsten Element in der Sammlung fort oder verlässt die `switch`-Anweisung, wenn es keine weiteren Elemente mehr gibt. Wir können das letzte Beispiel mit continue-Anweisungen so umschreiben, dass nur eine Anweisung ausgeführt wird.

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

Anstatt alle drei Elemente abzugleichen, wird das erste abgeglichen, und die switch-Anweisung fährt mit dem nächsten Wert fort. Da es keine weiteren Werte zu verarbeiten gibt, endet die switch-Anweisung. Dieses nächste Beispiel zeigt, wie ein Platzhalter mit mehreren Elementen übereinstimmen kann.

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

Da eine Zeile in der Eingabedatei sowohl das Wort `Error` als auch das Wort `Warning` enthalten könnte, möchten wir nur, dass das erste ausgeführt wird, und dann mit der Verarbeitung der Datei fortfahren.

### <a name="break"></a>Break

Eine `break`-Anweisung beendet die switch-Anweisung. Dies ist das gleiche Verhalten wie bei `continue` für einzelne Werte. Der Unterschied zeigt sich bei der Verarbeitung eines Arrays. `break` beendet die gesamte Verarbeitung in der switch-Anweisung, während `continue` zum nächsten Element übergeht.

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

Wenn wir in diesem Fall auf Zeilen stoßen, die mit `Error` beginnen, erhalten wir einen Fehler, woraufhin die switch-Anweisung endet.
Diese Aufgabe erledigt diese `break`-Anweisung für uns. Wenn wir `Error` innerhalb der Zeichenfolge und nicht nur am Anfang finden, schreiben wir dies als Warnung. Das Gleiche machen wir für `Warning`. Es ist möglich, dass eine Zeile die Wörter `Error` und `Warning` enthalten kann, aber wir müssen nur eines davon verarbeiten. Diese Aufgabe erledigt die `continue`-Anweisung für uns.

### <a name="break-labels"></a>break-Bezeichnungen

Die `switch`-Anweisung unterstützt `break/continue`-Bezeichnungen wie `foreach`.

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

Mir persönlich gefallen break-Bezeichnungen nicht, aber ich möchte auf sie hinweisen, weil sie verwirrend sind, wenn Sie sie noch nie zuvor gesehen haben. Wenn Sie mehrere geschachtelte `switch`- oder `foreach`-Anweisungen haben, möchten Sie möglicherweise bei mehr als nur dem innersten Element unterbrechen. Sie können einer `switch`-Anweisung eine Bezeichnung zuweisen, die das Ziel Ihrer `break`-Anweisung sein kann.

### <a name="enum"></a>Enum

Seit PowerShell 5.0 stehen uns Enumerationen zur Verfügung, die wir in einer switch-Anweisung nutzen können.

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

Wenn Sie alles als stark typisierte Enumerationen beibehalten möchten, können Sie sie in Klammern setzen.

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

Die Klammern werden hier benötigt, damit die switch-Anweisung den Wert `[Context]::Location` nicht als Literalzeichenfolge behandelt.

### <a name="scriptblock"></a>ScriptBlock

Bei Bedarf können wir einen Skriptblock verwenden, um die Auswertung für eine Übereinstimmung vorzunehmen.

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

Dies erhöht die Komplexität und kann Ihre `switch`-Anweisung schwer lesbar machen. In den meisten Fällen, in denen Sie so etwas verwenden würden, wäre es besser, mit den Anweisungen `if` und `elseif` zu arbeiten. Ich würde dies erwägen, wenn ich bereits eine große switch-Anweisung hätte und ich zwei Elemente bräuchte, um auf denselben Auswertungsblock zu treffen.

Ein Punkt, der meiner Meinung nach zur Lesbarkeit beiträgt, ist das Setzen des Skriptblocks in Klammern.

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

Er wird weiterhin auf die gleiche Weise ausgeführt und bietet beim schnellen Betrachten eine bessere visuelle Abgrenzung.

### <a name="regex-matches"></a>$matches für reguläre Ausdrücke

Wir müssen reguläre Ausdrücke wieder aufgreifen, um etwas anzusprechen, das nicht sofort offensichtlich ist. Bei Verwendung regulärer Ausdrücke wird die Variable `$matches` aufgefüllt. Ich gehe mehr auf die Verwendung von `$matches` ein, wenn ich auf [The many ways to use regex][] eingehe. Hier ist ein kurzes Beispiel, um das Ganze mit benannten Übereinstimmungen in Aktion zu zeigen.

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a>$null

Sie können einen `$null`-Wert abgleichen, der nicht der Standardwert sein muss.

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

Gleiches gilt für eine leere Zeichenfolge.

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a>Konstanter Ausdruck

Lee Dailey hat darauf hingewiesen, dass wir einen Ausdruck, der konstant `$true` ist, nutzen können, um `[bool]`-Elemente auszuwerten.
Stellen Sie sich vor, wir müssen mehrere Prüfungen boolescher Werte durchführen.

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

Dies ist eine einfache Möglichkeit, den Status mehrerer boolescher Felder auszuwerten und entsprechende Maßnahmen zu ergreifen. Das Besondere daran ist, dass Sie mit einer Übereinstimmung den Status eines noch nicht ausgewerteten Werts umdrehen können.

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

Das Festlegen von `$isEnabled` auf `$true` in diesem Beispiel stellt sicher, dass `$isVisible` auch auf `$true` festgelegt wird. Wenn `$isVisible` dann ausgewertet wird, wird sein Skriptblock aufgerufen. Das ist ein wenig widersinnig, aber eine geschickte Nutzung vorhandener Mechanismen.

### <a name="switch-automatic-variable"></a>$switch (automatische Variable)

Wenn `switch` seine Werte verarbeitet, wird ein Enumerator erstellt, der `$switch` genannt wird. Dies ist eine von PowerShell automatisch erstellte Variable, die Sie direkt verändern können.

Darauf hat mich [/u/frmadsen](https://www.reddit.com/user/frmadsen) aufmerksam gemacht.

<div class="reddit-embed" data-embed-media="www.redditmedia.com" data-embed-parent="false" data-embed-live="false" data-embed-uuid="8f6edbf1-abc6-4513-971e-ccd1d202889d" data-embed-created="2018-12-25T22:05:33.986Z"><a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">Kommentar</a> aus der Diskussion <a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">What should I (IT student) learn to master PowerShell?</a> (Was muss ich [Informatikstudent] lernen, um PowerShell zu beherrschen?).</div><script async src="https://www.redditstatic.com/comment-embed.js"></script>

Dadurch erhalten Sie die folgenden Ergebnisse:

```Output
2
4
```

Indem Sie den Enumerator vorwärts bewegen, wird das nächste Element nicht durch `switch` verarbeitet, aber Sie können direkt auf diesen Wert zugreifen. Das würde ich Aberwitz nennen.

## <a name="other-patterns"></a>Andere Muster

### <a name="hashtables"></a>Hashtabellen

Einer meiner beliebtesten Beiträge ist der zu [Hashtabellen][]. Einer der Anwendungsfälle für eine `hashtable` soll eine Nachschlagetabelle sein. Das ist eine alternative Annäherung an ein gängiges Muster, mit dem sich eine `switch`-Anweisung oft befasst.

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

Wenn ich eine `switch`-Anweisung nur zum Nachschlagen verwende, nutze ich stattdessen oft eine `hashtable`.

### <a name="enum"></a>Enum

Seit PowerShell 5.0 gibt es `Enum`, was in diesem Fall auch eine Option ist.

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

Wir könnten den ganzen Tag damit verbringen, verschiedene Wege zur Lösung dieses Problems zu finden. Ich wollte nur sichergehen, dass Sie wissen, welche Möglichkeiten Sie haben.

## <a name="final-words"></a>Schlusswort

Die switch-Anweisung ist oberflächlich betrachtet einfach, aber sie bietet einige erweiterte Merkmale, von denen die meisten nicht wissen, dass sie zur Verfügung stehen. Durch die Kombination dieser Merkmale steht Ihnen ein leistungsstarkes Instrument zur Verfügung. Ich hoffe, Sie haben etwas gelernt, was Sie vorher noch nicht wussten.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch-Parameter]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression (Die vielfältigen Verwendungsmöglichkeiten von regulären Ausdrücken)
[Hashtabellen]: everything-about-hashtable.md
