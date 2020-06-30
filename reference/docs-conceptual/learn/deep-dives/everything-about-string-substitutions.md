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
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a>Alles, was Sie schon immer über die Variablenersetzung in Zeichenfolgen wissen wollten

Es gibt viele Möglichkeiten, Variablen in Zeichenfolgen zu verwenden. Ich nenne das Variablenersetzung, aber gemeint ist eigentlich jeder Fall, in dem eine Zeichenfolge so formatiert werden soll, dass sie Werte aus Variablen enthält. Das erläutere ich oft für neue Skriptentwickler.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette dafür, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="concatenation"></a>Verkettung

Die erste Klasse der Methoden kann als Verkettung bezeichnet werden. Dabei geht es im Grunde darum, mehrere Zeichenfolgen miteinander zu verknüpfen. Verkettungen werden schon lange zum Erstellen formatierter Zeichenfolgen verwendet.

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

Die Verkettung funktioniert gut, wenn nur wenige Werte hinzugefügt werden müssen. Allerdings kann die Angelegenheit schnell komplizierter werden.

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

Das folgende Beispiel ist zwar einfach, aber dennoch schwierig zu lesen.

## <a name="variable-substitution"></a>Variablenersetzung

PowerShell bietet eine andere Option, die einfacher ist. Sie können die Variablen direkt in den Zeichenfolgen angeben.

```powershell
$message = "Hello, $first $last."
```

Der Unterschied besteht im Typ der Anführungszeichen, in die Sie die Zeichenfolge setzen. Bei einer Zeichenfolge mit doppelten Anführungszeichen ist eine Ersetzung möglich, bei einer Zeichenfolge mit einfachen Anführungszeichen nicht. Sie können die eine oder die andere Variante verwenden, haben aber stets die freie Wahl.

## <a name="command-substitution"></a>Befehlsersetzung

Es wird ein wenig komplizierter, wenn Sie versuchen, die Werte von Eigenschaften in eine Zeichenfolge zu übernehmen. Hier kommen viele Neulinge ins Straucheln. Ich möchte Ihnen zunächst zeigen, was ihrer Meinung nach funktionieren sollte (und auf den ersten Blick sieht es fast so aus, als würde es das auch).

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

Sie würden erwarten, dass Sie den Wert `CreationTime` aus `$directory` abrufen, stattdessen erhalten Sie jedoch `Time: c:\windows.CreationTime` als Wert. Der Grund dafür ist, dass bei dieser Art der Ersetzung nur die Basisvariable betrachtet wird. Der Punkt wird als Teil der Zeichenfolge angesehen, sodass der Wert nicht weiter aufgelöst wird.

Zufällig gibt dieses Objekt eine Zeichenfolge als Standardwert an, wenn es in eine Zeichenfolge eingefügt wird.
Bei einigen Objekte erhalten Sie stattdessen den Typnamen, wie z. B. `System.Collections.Hashtable`. Darauf sollten Sie achten.

PowerShell ermöglicht mit einer speziellen Syntax die Befehlsausführung innerhalb der Zeichenfolge. Dadurch können wir die Eigenschaften dieser Objekte abrufen und jeden anderen Befehl ausführen, um einen Wert zu erhalten.

```powershell
$message = "Time: $($directory.CreationTime)"
```

Das funktioniert in manchen Situationen sehr gut, kann aber genauso kompliziert wie eine Verkettung werden, wenn Sie nur ein paar Variablen haben.

### <a name="command-execution"></a>Befehlsausführung

Sie können in einer Zeichenfolge Befehle ausführen. Diese Möglichkeit besteht zwar, aber ich rate von ihrer Verwendung ab. Es wird schnell unübersichtlich und schwer zu debuggen. Ich führe entweder den Befehl aus und speichere ihn in einer Variablen oder verwende eine Formatzeichenfolge.

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a>Formatzeichenfolge

.NET bietet eine Möglichkeit zum Formatieren von Zeichenfolgen, die meiner Meinung nach recht einfach zu verwenden ist. Zunächst möchte ich Ihnen die statische Methode dafür vorstellen, bevor ich Ihnen die PowerShell-Verknüpfung zeige, mit der Sie dasselbe tun können.

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

In diesem Fall wird die Zeichenfolge für die Token `{0}` und `{1}` analysiert. Anschließend wird diese Zahl verwendet, um aus den angegebenen Werten auszuwählen. Wenn Sie einen Wert an einer Stelle in der Zeichenfolge wiederholen möchten, können Sie die Nummer dieses Werts wieder verwenden.

Je komplexer die Zeichenfolge wird, desto größer ist der Nutzen, den dieser Ansatz bietet.

### <a name="format-values-as-arrays"></a>Formatieren von Werten als Arrays

Wenn die Formatzeile zu lang wird, können Sie Ihre Werte zuerst in ein Array einfügen.

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

Hierbei handelt es sich nicht um ein Splatting, da ich das gesamte Array einfüge, aber die Idee ist ähnlich.

## <a name="advanced-formatting"></a>Erweiterte Formatierung

Ich habe ganz bewusst gesagt, dass diese Option aus .NET stammt, weil es dort bereits viele gut [dokumentierte][] Formatierungsoptionen gibt. Es gibt integrierte Möglichkeiten, verschiedene Datentypen zu formatieren.

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

Ich werde an dieser Stelle nicht näher darauf eingehen, sondern wollte lediglich darauf hinweisen, dass dies eine sehr leistungsfähige Formatierungs-Engine ist, falls Sie eine solche benötigen.

## <a name="joining-strings"></a>Verknüpfen von Zeichenfolgen

Es gibt allerdings auch Fälle, in denen Sie tatsächlich eine Liste mit Werten miteinander verketten möchten. Dafür gibt es einen `-join`-Operator. Damit können Sie sogar ein Zeichen angeben, das zwischen den Zeichenfolgen verknüpft werden soll.

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

Wenn Sie Zeichenfolgen mit `-join` ohne ein solches Trennzeichen verknüpfen möchten, geben Sie einfach eine leere Zeichenfolge `''` an.
Wenn das aber alles ist, was Sie machen möchten, gibt es eine schnellere Option.

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

Sie sollten ferner wissen, dass Sie Zeichenfolgen auch mit `-split` teilen können.

## <a name="join-path"></a>Join-Path

Dies wird oft übersehen, ist aber ein gutes Cmdlet zum Erstellen eines Dateipfads.

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

Das Tolle daran ist, dass es die umgekehrten Schrägstriche richtig verarbeitet, wenn die Werte zusammengesetzt werden. Dies ist besonders wichtig, wenn Sie Werte von Benutzern oder aus Konfigurationsdateien verwenden.

Das funktioniert auch gut mit `Split-Path` und `Test-Path`. Darüber spreche ich auch in meinem Beitrag zum [Lesen und Speichern in Dateien][].

## <a name="strings-are-arrays"></a>Zeichenfolgen sind Arrays

Bevor ich fortfahre, muss ich an dieser Stelle noch ein Wort über die Zeichenfolgenaddition verlieren. Denken Sie daran, dass eine Zeichenfolge nur ein Array aus Zeichen ist. Wenn Sie mehrere Zeichenfolgen addieren, entsteht jedes Mal ein neues Array.

Sehen Sie sich folgendes Beispiel an:

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

Sieht einfach aus, oder? Was Sie jedoch nicht sehen: Jedes Mal, wenn eine Zeichenfolge zu `$message` addiert wird, wird eine ganz neue Zeichenfolge erstellt. Arbeitsspeicher wird zugeordnet, Daten werden kopiert, und veraltete Daten werden verworfen.
Das ist keine große Sache, wenn es nur ein paar Mal gemacht wird, aber eine Schleife wie diese würde wirklich zu Problemen führen.

### <a name="stringbuilder"></a>StringBuilder

Auch StringBuilder wird gerne zur Erstellung langer Zeichenfolgen aus mehreren kürzeren Zeichenfolgen verwendet. Der Grund dafür ist, dass er einfach alle Zeichenfolgen sammelt, die Sie addieren, und sie erst am Ende verkettet, wenn Sie den Wert abrufen.

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

Auch das ist etwas, wofür ich .NET verwende. Ich nutze es zwar nicht mehr häufig, aber es ist einfach gut zu wissen, dass es bei Bedarf verfügbar ist.

## <a name="delineation-with-braces"></a>Abgrenzung mit geschweiften Klammern

Dies wird für die Suffixverkettung innerhalb der Zeichenfolge verwendet. Manchmal verfügt Ihre Variable nicht über eine eindeutige Wortgrenze.

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

Vielen Dank dafür an [/u/real_parbold][].

Hier ist eine Alternative zu diesem Ansatz:

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

Hierfür verwende ich persönlich eine Formatzeichenfolge, aber es ist gut zu wissen, dass es das gibt, falls es Ihnen in der Praxis einmal begegnet.

## <a name="find-and-replace-tokens"></a>Suchen und Ersetzen von Token

Bei den meisten dieser Features müssen Sie zwar nicht unbedingt eine eigene Lösung entwickeln, aber es kann vorkommen, dass Sie mit großen Vorlagendateien arbeiten, in denen Sie Zeichenfolgen ersetzen möchten.

Nehmen wir an, Sie haben eine Vorlage mit sehr viel Text aus einer Datei abgerufen.

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

Es müssen möglicherweise viele Token ersetzt werden. Der Trick besteht darin, ein sehr eindeutiges Token zu verwenden, das leicht zu finden und zu ersetzen ist. In der Regel verwende ich ein Sonderzeichen an beiden Enden, um es klar abgrenzen zu können.

Ich habe vor Kurzem einen neuen Ansatz dafür gefunden. Ich habe mich entschieden, diesen Abschnitt stehen zu lassen, weil dieses Muster häufig verwendet wird.

### <a name="replace-multiple-tokens"></a>Ersetzen mehrerer Token

Wenn ich eine ganze Liste von Token ersetzen muss, verfolge ich einen allgemeineren Ansatz. Ich füge sie in einer Hashtabelle ein und durchlaufe sie, um die Ersetzung durchzuführen.

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

Diese Token können bei Bedarf aus einer JSON- oder CSV-Datei geladen werden.

### <a name="executioncontext-expandstring"></a>ExecutionContext ExpandString

Es gibt einen wirklich cleveren Weg, eine Ersetzungszeichenfolge mit einfachen Anführungszeichen zu definieren und die Variablen später zu erweitern. Sehen Sie sich folgendes Beispiel an:

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

Der Aufruf von `.InvokeCommand.ExpandString` im aktuellen Ausführungskontext verwendet die Variablen im aktuellen Gültigkeitsbereich für die Ersetzung. Der wichtigste Punkt hierbei ist, dass `$message` sehr früh definiert werden kann, noch bevor die Variablen überhaupt vorhanden sind.

Wenn wir das nur ein wenig erweitern, können wir diese Ersetzung immer wieder mit unterschiedlichen Werten durchführen.

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

Um diese Idee weiter zu verfolgen, könnten Sie beispielsweise eine umfangreiche E-Mail-Vorlage aus einer Textdatei importieren. Ich danke [Mark Kraus][] für diesen [Vorschlag][].

## <a name="whatever-works-the-best-for-you"></a>Was immer für Sie am besten geeignet ist

Ich arbeite sehr gern mit Formatzeichenfolgen. Ich verwende sie auf jeden Fall bei komplizierteren Zeichenfolgen oder wenn es mehrere Variablen gibt. Bei sehr kurzen Zeichenfolgen kann ich jeden dieser Ansätze verwenden.

## <a name="anything-else"></a>Noch etwas?

Ich habe hier sehr viele Aspekte vorgestellt. Ich hoffe, dass Sie etwas Neues lernen konnten.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[Vorschlag]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[Lesen und Speichern in Dateien]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[dokumentierte]: /dotnet/api/system.string.format#overloads
