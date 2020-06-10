---
title: Alles, was Sie schon immer über Ausnahmen wissen wollten
description: Die Fehlerbehandlung ist nur ein Teil der Aufgaben beim Schreiben von Code.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fd3ddacbf14d1faeee98682697161f86c6ff0c72
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149543"
---
# <a name="everything-you-wanted-to-know-about-exceptions"></a>Alles, was Sie schon immer über Ausnahmen wissen wollten

Die Fehlerbehandlung ist nur ein Teil der Aufgaben beim Schreiben von Code. Wir können häufig die Bedingungen für erwartetes Verhalten überprüfen und validieren. Wenn ein unerwartetes Verhalten auftritt, wird die Ausnahmebehandlung durchgeführt. Sie können die Ausnahmen, die durch den Code anderer Personen generiert wurden, leicht behandeln, oder Sie können Ihre eigenen Ausnahmen generieren, die andere behandeln können.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

## <a name="basic-terminology"></a>Grundlegende Terminologie

Wir müssen einige grundlegende Begriffe klären, bevor wir uns mit diesem Thema befassen.

### <a name="exception"></a>Ausnahme

Eine Ausnahme ist wie ein Ereignis, das ausgelöst wird, wenn die normale Fehlerbehandlung das Problem nicht beheben kann.
Der Versuch, eine Zahl durch 0 zu teilen oder nicht genügend Arbeitsspeicher zu haben, sind Beispiele für Ereignisse, die eine Ausnahme erzeugen. Manchmal erstellt der Autor des Codes, den Sie verwenden, Ausnahmen für bestimmte Probleme, falls diese auftreten.

### <a name="throw-and-catch"></a>Throw und Catch

Wenn eine Ausnahme auftritt, sagen wir, dass eine Ausnahme ausgelöst wird. Um eine ausgelöste Ausnahme zu behandeln, müssen Sie sie abfangen. Wenn eine Ausnahme ausgelöst und nicht abgefangen wird, wird die Ausführung des Skripts beendet.

### <a name="the-call-stack"></a>Die Aufrufliste

Die Aufrufliste ist die Liste der Funktionen, die sich gegenseitig aufgerufen haben. Wenn eine Funktion aufgerufen wird, wird Sie zum Stapel oder dem Anfang der Liste hinzugefügt. Wenn die Funktion beendet oder zurückgegeben wird, wird Sie aus dem Stapel entfernt.

Wenn eine Ausnahme ausgelöst wird, wird diese Aufrufliste eingecheckt, damit sie von einem Ausnahmehandler abgefangen werden kann.

### <a name="terminating-and-non-terminating-errors"></a>Fehler mit und ohne Abbruch

Eine Ausnahme ist im Allgemeinen ein Fehler mit Abbruch. Eine ausgelöste Ausnahme wird entweder abgefangen oder beendet die aktuelle Ausführung. Standardmäßig wird ein Fehler ohne Abbruch durch `Write-Error` generiert, und dem Ausgabestream wird ein Fehler hinzugefügt, ohne dass eine Ausnahme ausgelöst wird.

Ich weise darauf hin, da `Write-Error` und andere Fehler ohne Abbruch `catch` nicht auslösen.

### <a name="swallowing-an-exception"></a>Behalten einer Ausnahme

Dies tritt auf, wenn Sie einen Fehler abfangen, um ihn zu unterdrücken. Gehen Sie dabei vorsichtig vor, da dies das Troubleshooting sehr schwierig machen kann.

## <a name="basic-command-syntax"></a>Grundlegende Befehlssyntax

Hier finden Sie eine kurze Übersicht über die in PowerShell verwendete grundlegende Syntax für die Ausnahmebehandlung.

### <a name="throw"></a>Throw

Zum Erstellen eines eigenen Ausnahmeereignisses, lösen wir eine Ausnahme mit dem Schlüsselwort `throw` aus.

```powershell
function Do-Something
{
    throw "Bad thing happened"
}
```

Dadurch wird eine Laufzeitausnahme erstellt, die ein Fehler mit Abbruch ist. Sie wird von einem `catch` in einer Aufruffunktion behandelt oder beendet das Skript mit einer Meldung wie dieser.

```powershell
PS> Do-Something

Bad thing happened
At line:1 char:1
+ throw "Bad thing happened"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Bad thing happened:String) [], RuntimeException
    + FullyQualifiedErrorId : Bad thing happened
```

#### <a name="write-error--erroraction-stop"></a>Write-Error -ErrorAction Stop

Ich habe bereits erwähnt, dass `Write-Error` nicht standardmäßig einen Fehler mit Abbruch auslöst. Wenn Sie `-ErrorAction Stop` angeben, generiert `Write-Error` einen Fehler mit Abbruch, der mit einem `catch` behandelt werden kann.

```powershell
Write-Error -Message "Houston, we have a problem." -ErrorAction Stop
```

Vielen Dank an Lee Daily, der daran erinnert hat, dass man `-ErrorAction Stop` auch auf diese Weise verwenden kann.

#### <a name="cmdlet--erroraction-stop"></a>Cmdlet -ErrorAction Stop

Wenn Sie `-ErrorAction Stop` in einer beliebigen erweiterten Funktion oder einem Cmdlet angeben, werden alle `Write-Error`-Anweisungen in Fehler mit Abbruch umgewandelt, durch die die Ausführung angehalten wird oder die von einem `catch` behandelt werden können.

```powershell
Do-Something -ErrorAction Stop
```

### <a name="trycatch"></a>Try/Catch

Die Ausnahmebehandlung in PowerShell (und vielen anderen Sprachen) funktioniert so, dass Sie zuerst einen `try`-Vorgang für einen Codeabschnitt ausführen. Wenn dadurch ein Fehler ausgelöst wird, können Sie einen `catch`-Vorgang ausführen. Hier ist ein kurzes Beispiel.

```powershell
try
{
    Do-Something
}
catch
{
    Write-Output "Something threw an exception"
}

try
{
    Do-Something -ErrorAction Stop
}
catch
{
    Write-Output "Something threw an exception or used Write-Error"
}
```

Das `catch`-Skript wird nur ausgeführt, wenn ein Fehler mit Abbruch vorliegt. Wenn `try` ordnungsgemäß ausgeführt wird, wird zu `catch` übergegangen.

### <a name="tryfinally"></a>Try/Finally

Manchmal müssen Sie einen Fehler nicht behandeln, benötigen aber trotzdem Code, der ausgeführt wird, wenn eine Ausnahme auftritt oder nicht. Ein `finally`-Skript macht genau das.

Im Folgenden finden Sie ein Beispiel:

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
$command.Connection.Open()
$command.ExecuteNonQuery()
$command.Connection.Close()
```

Jedes Mal, wenn Sie eine Ressource öffnen oder eine Verbindung mit dieser herstellen, sollten Sie sie auch schließen. Wenn `ExecuteNonQuery()` eine Ausnahme auslöst, wird die Verbindung nicht geschlossen. Hier ist derselbe Code in einem `try/finally`-Block.

```powershell
$command = [System.Data.SqlClient.SqlCommand]::New(queryString, connection)
try
{
    $command.Connection.Open()
    $command.ExecuteNonQuery()
}
finally
{
    $command.Connection.Close()
}
```

In diesem Beispiel wird die Verbindung geschlossen, wenn ein Fehler vorliegt. Sie wird auch geschlossen, wenn kein Fehler vorliegt. Das `finally`-Skript wird jedes Mal ausgeführt.

Da die Ausnahme nicht abgefangen wird, wird Sie weiterhin in der Aufrufliste nach oben weitergegeben.

### <a name="trycatchfinally"></a>Try/Catch/Finally

Es ist durchaus zulässig, `catch` und `finally` in Kombination zu verwenden. In den meisten Fällen verwenden Sie nur eine der Optionen, aber es gibt möglicherweise Szenarios, in denen Sie beide verwenden.

## <a name="psitem"></a>$PSItem

Da wir nun die Grundlagen kennen, können wir uns etwas genauer mit dem Thema beschäftigen.

Innerhalb des `catch`-Blocks gibt es eine automatische Variable (`$PSItem` oder `$_`) vom Typ `ErrorRecord`, die die Details zur Ausnahme enthält. Hie ist eine kurze Übersicht über einige der wichtigsten Eigenschaften.

In diesen Beispielen wurde in `ReadAllText` zum Generieren dieser Ausnahme ein ungültiger Pfad verwendet.

```powershell
[System.IO.File]::ReadAllText( '\\test\no\filefound.log')
```

### <a name="psitemtostring"></a>PSItem.ToString()

Dadurch erhalten Sie die übersichtlichste Meldung, die Sie für die Protokollierung und allgemeine Ausgabe verwenden können. `ToString()` wird automatisch aufgerufen, wenn `$PSItem` in eine Zeichenfolge eingefügt wird.

```powershell
catch
{
    Write-Output "Ran into an issue: $($PSItem.ToString())"
}

catch
{
    Write-Output "Ran into an issue: $PSItem"
}
```

### <a name="psiteminvocationinfo"></a>$PSItem.InvocationInfo

Diese Eigenschaft enthält zusätzliche von PowerShell gesammelte Informationen über die Funktion oder das Skript, in dem die Ausnahme ausgelöst wurde. Hier ist die `InvocationInfo` aus der Beispielausnahme, die ich erstellt habe.

```powershell
PS> $PSItem.InvocationInfo | Format-List *

MyCommand             : Get-Resource
BoundParameters       : {}
UnboundArguments      : {}
ScriptLineNumber      : 5
OffsetInLine          : 5
ScriptName            : C:\blog\throwerror.ps1
Line                  :     Get-Resource
PositionMessage       : At C:\blog\throwerror.ps1:5 char:5
                        +     Get-Resource
                        +     ~~~~~~~~~~~~
PSScriptRoot          : C:\blog
PSCommandPath         : C:\blog\throwerror.ps1
InvocationName        : Get-Resource
```

Die wichtigen Details zeigen hier den `ScriptName`, die `Line` des Codes und die `ScriptLineNumber`, wo der Aufruf begann.

### <a name="psitemscriptstacktrace"></a>$PSItem.ScriptStackTrace

Diese Eigenschaft zeigt die Reihenfolge der Funktionsaufrufe an, mit der Sie den Code erhalten haben, in dem die Ausnahme generiert wurde.

```powershell
PS> $PSItem.ScriptStackTrace
at Get-Resource, C:\blog\throwerror.ps1: line 13
at Do-Something, C:\blog\throwerror.ps1: line 5
at <ScriptBlock>, C:\blog\throwerror.ps1: line 18
```

Ich führe nur Aufrufe von Funktionen im gleichen Skript durch, aber dies würde die Aufrufe nachverfolgen, wenn mehrere Skripts beteiligt wären.

### <a name="psitemexception"></a>$PSItem.Exception

Dies ist die tatsächlich ausgelöste Ausnahme.

#### <a name="psitemexceptionmessage"></a>$PSItem.Exception.Message

Dies ist die allgemeine Meldung, in der die Ausnahme beschrieben wird, und ein guter Startpunkt beim Troubleshooting. Die meisten Ausnahmen verfügen über eine Standardmeldung. Diese können jedoch benutzerdefiniert angepasst werden, wenn die Ausnahme ausgelöst wird.

```powershell
PS> $PSItem.Exception.Message

Exception calling "ReadAllText" with "1" argument(s): "The network path was not found."
```

Dies ist auch die Meldung, die beim Aufrufen von `$PSItem.ToString()` zurückgegeben wird, wenn nichts im `ErrorRecord` festgelegt wurde.

#### <a name="psitemexceptioninnerexception"></a>$PSItem.Exception.InnerException

Ausnahmen können innere Ausnahmen enthalten. Dies ist häufig der Fall, wenn der Code, den Sie aufrufen, eine Ausnahme abfängt und eine andere Ausnahme auslöst. Die ursprüngliche Ausnahme wird in der neuen Ausnahme eingefügt.

```powershell
PS> $PSItem.Exception.InnerExceptionMessage
The network path was not found.
```

Ich werde dies später noch einmal ansprechen, wenn es um das erneute Auslösen von Ausnahmen geht.

#### <a name="psitemexceptionstacktrace"></a>$PSItem.Exception.StackTrace

Das ist die `StackTrace` für die Ausnahme. Ich habe oben eine `ScriptStackTrace` gezeigt, aber diese ist für die Aufrufe von verwaltetem Code vorgesehen.

```Output
at System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean
 useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs,
 String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost)
at System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share, Int32
 bufferSize, FileOptions options, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean
 checkHost)
at System.IO.StreamReader..ctor(String path, Encoding encoding, Boolean detectEncodingFromByteOrderMarks,
 Int32 bufferSize, Boolean checkHost)
at System.IO.File.InternalReadAllText(String path, Encoding encoding, Boolean checkHost)
at CallSite.Target(Closure , CallSite , Type , String )
```

Sie erhalten diese Stapelüberwachung nur, wenn das Ereignis durch verwalteten Code ausgelöst wird. Ich rufe direkt eine .NET Framework-Funktion auf. Das ist also alles, was wir in diesem Beispiel sehen können. Wenn Sie sich eine Stapelüberwachung ansehen, suchen Sie im Allgemeinen nach der Stelle, an der Ihr Code aufhört und die Systemaufrufe beginnen.

## <a name="working-with-exceptions"></a>Arbeiten mit Ausnahmen

Zum Thema Ausnahmen gehört mehr als die grundlegende Syntax und Ausnahmeeigenschaften.

### <a name="catching-typed-exceptions"></a>Abfangen typisierter Ausnahmen

Sie können auswählen, welche Ausnahmen Sie abfangen wollen. Ausnahmen haben einen Typ, und Sie können den Typ der Ausnahme angeben, die Sie abfangen möchten.

```powershell
try
{
    Do-Something -Path $path
}
catch [System.IO.FileNotFoundException]
{
    Write-Output "Could not find $path"
}
catch [System.IO.IOException]
{
        Write-Output "IO error with the file: $path"
}
```

Der Ausnahmetyp wird für jeden `catch`-Block solange geprüft, bis ein solcher Typ gefunden wird, der mit der Ausnahme übereinstimmt.
Es ist wichtig zu wissen, dass Ausnahmen von anderen Ausnahmen Werte übernehmen können. Im Beispiel oben übernimmt `FileNotFoundException` Werte von `IOException`. Wenn also zuerst `IOException` aufgetreten ist, würde das stattdessen aufgerufen werden. Auch bei mehreren Übereinstimmungen wird nur ein Catch-Block aufgerufen.

Wenn wir eine `System.IO.PathTooLongException` hätten, würde die `IOException` übereinstimmen. Hätten wir aber eine `InsufficientMemoryException`, dann würde diese nicht abgefangen und im Stapel nach oben weitergegeben werden.

### <a name="catch-multiple-types-at-once"></a>Gleichzeitiges Abfangen mehrerer Typen

Es können mehrere Ausnahmetypen mit der gleichen `catch`-Anweisung abgefangen werden.

```powershell
try
{
    Do-Something -Path $path -ErrorAction Stop
}
catch [System.IO.DirectoryNotFoundException],[System.IO.FileNotFoundException]
{
    Write-Output "The path or file was not found: [$path]"
}
catch [System.IO.IOException]
{
    Write-Output "IO error with the file: [$path]"
}
```

Vielen Dank an `/u/Sheppard_Ra` für diesen Vorschlag.

### <a name="throwing-typed-exceptions"></a>Auslösen typisierter Ausnahmen

Sie können in PowerShell typisierte Ausnahmen auslösen. Anstatt `throw` mit einer Zeichenfolge aufrufen:

```powershell
throw "Could not find: $path"
```

Verwenden Sie einen Ausnahmebeschleuniger wie den folgenden:

```powershell
throw [System.IO.FileNotFoundException] "Could not find: $path"
```

Wenn Sie diese Möglichkeit verwenden, müssen Sie jedoch eine Meldung angeben.

Sie können auch eine neue Instanz einer Ausnahme erstellen, die ausgelöst werden soll. In diesem Fall ist die Meldung optional, da das System über Standardmeldungen für alle integrierten Ausnahmen verfügt.

```powershell
throw [System.IO.FileNotFoundException]::new()
throw [System.IO.FileNotFoundException]::new("Could not find path: $path")
```

Wenn Sie nicht PowerShell 5.0 oder höher verwenden, müssen Sie den älteren Ansatz `New-Object` verwenden.

```powershell
throw (New-Object -TypeName System.IO.FileNotFoundException )
throw (New-Object -TypeName System.IO.FileNotFoundException -ArgumentList "Could not find path: $path")
```

Wenn Sie eine typisierte Ausnahme verwenden, können Sie (oder andere) die Ausnahme nach Typ abfangen, wie im vorherigen Abschnitt erläutert.

#### <a name="write-error--exception"></a>Write-Error -Exception

Wir können diese typisierten Ausnahmen zu `Write-Error` hinzufügen, und wir können weiterhin einen `catch`-Vorgang für die Fehler nach Ausnahmetyp durchführen. Verwenden Sie `Write-Error` wie in diesen Beispielen:

```powershell
# with normal message
Write-Error -Message "Could not find path: $path" -Exception ([System.IO.FileNotFoundException]::new()) -ErrorAction Stop

# With message inside new exception
Write-Error -Exception ([System.IO.FileNotFoundException]::new("Could not find path: $path")) -ErrorAction Stop

# Pre PS 5.0
Write-Error -Exception ([System.IO.FileNotFoundException]"Could not find path: $path") -ErrorAction Stop

Write-Error -Message "Could not find path: $path" -Exception ( New-Object -TypeName System.IO.FileNotFoundException ) -ErrorAction Stop
```

Dann können wir sie wie folgt abfangen:

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Log $PSItem.ToString()
}
```

#### <a name="the-big-list-of-net-exceptions"></a>Die lange Liste der .NET-Ausnahmen

Ich habe mithilfe der [Reddit/r/PowerShell-Community][] eine Masterliste mit Hunderten .NET-Ausnahmen als Ergänzung für diesen Beitrag zusammengestellt.

- [Die lange Liste der .NET-Ausnahmen][]

Ich durchsuche diese Liste zunächst nach Ausnahme, die meiner Meinung nach gut zu meiner Situation passen. Versuchen Sie, Ausnahmen im Basis-`System`-Namespace zu verwenden.

### <a name="exceptions-are-objects"></a>Ausnahmen sind Objekte

Wenn Sie damit anfangen, viele typisierte Ausnahmen zu verwenden, müssen Sie daran denken, dass es sich um-Objekte handelt. Verschiedene Ausnahmen haben unterschiedliche Konstruktoren und Eigenschaften. Wenn wir in der [FileNotFoundException][]-Dokumentation nach `System.IO.FileNotFoundException`suchen, sehen wir, dass wir eine Meldung und einen Dateipfad übergeben können.

```powershell
[System.IO.FileNotFoundException]::new("Could not find file", $path)
```

Und es gibt eine `FileName`-Eigenschaft, die diesen Dateipfad verfügbar macht.

```powershell
catch [System.IO.FileNotFoundException]
{
    Write-Output $PSItem.Exception.FileName
}
```

Andere Konstruktoren und Objekteigenschaften finden Sie in der [.NET-Dokumentation][].

### <a name="re-throwing-an-exception"></a>Erneutes Auslösen einer Ausnahme

Wenn Sie in Ihrem `catch`-Block lediglich einen `throw`-Vorgang für dieselbe Ausnahme durchführen möchten, dann führen Sie keinen `catch`-Vorgang durch. Sie sollten nur einen `catch`-Vorgang für eine Ausnahme durchführen, die Sie behandeln wollen, oder eine Aktion ausführen, wenn sie auftritt.

Manchmal möchte man eine Aktion für eine Ausnahme ausführen, die Ausnahme aber erneut auslösen, damit ein nachgeschalteter Prozess sie behandeln kann. Wir könnten eine Meldung schreiben oder das Problem in der Nähe der Stelle protokollieren, an der wir es entdeckt haben, das Problem aber weiter oben im Stapel behandeln.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw $PSItem
}
```

Interessanterweise können wir `throw` innerhalb des `catch` aufrufen, und die aktuelle Ausnahme wird erneut ausgelöst.

```powershell
catch
{
    Write-Log $PSItem.ToString()
    throw
}
```

Wir möchten die Ausnahme erneut auslösen, um die ursprünglichen Ausführungsinformationen wie Quellskript und Zeilennummer beizubehalten. Wenn an dieser Stelle eine neue Ausnahme ausgelöst wird, wird ausgeblendet, wo die Ausnahme begonnen hat.

#### <a name="re-throwing-a-new-exception"></a>Erneutes Auslösen einer neuen Ausnahme

Wenn Sie eine Ausnahme abfangen, aber eine andere auslösen möchten, sollten Sie die ursprüngliche Ausnahme in der neuen Ausnahme schachteln. Dadurch kann ein Benutzer weiter unten im Stapel als `$PSItem.Exception.InnerException` darauf zugreifen.

```powershell
catch
{
    throw [System.MissingFieldException]::new('Could not access field',$PSItem.Exception)
}
```

#### <a name="pscmdletthrowterminatingerror"></a>$PSCmdlet.ThrowTerminatingError()

Das Einzige, was mir an der Verwendung von `throw` für unformatierte Ausnahmen nicht gefällt, ist, dass die Fehlermeldung auf die `throw`-Anweisung verweist und angibt, dass sich das Problem in dieser Zeile befindet.

```Output
Unable to find the specified file.
At line:31 char:9
+         throw [System.IO.FileNotFoundException]::new()
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], FileNotFoundException
    + FullyQualifiedErrorId : Unable to find the specified file.
```


Wenn ich die Fehlermeldung bekomme, dass mein Skript fehlerhaft ist, weil ich `throw` in Zeile 31 angerufen habe, ist das für die Benutzer Ihres Skripts eine schlechte Meldung. Sie erhalten dadurch keine hilfreichen Informationen.

Dexter Dhami hat darauf hingewiesen, dass ich `ThrowTerminatingError()` verwenden kann, um dies zu korrigieren.

```powershell
$PSCmdlet.ThrowTerminatingError(
    [System.Management.Automation.ErrorRecord]::new(
        ([System.IO.FileNotFoundException]"Could not find $Path"),
        'My.ID',
        [System.Management.Automation.ErrorCategory]::OpenError,
        $MyObject
    )
)
```

Wenn wir davon ausgehen, dass `ThrowTerminatingError()` innerhalb einer Funktion mit dem Namen `Get-Resource` aufgerufen wurde, sollten wir diesen Fehler sehen.

```Output
Get-Resource : Could not find C:\Program Files (x86)\Reference
Assemblies\Microsoft\Framework\.NETPortable\v4.6\System.IO.xml
At line:6 char:5
+     Get-Resource -Path $Path
+     ~~~~~~~~~~~~
    + CategoryInfo          : OpenError: (:) [Get-Resource], FileNotFoundException
    + FullyQualifiedErrorId : My.ID,Get-Resource
```

Sehen Sie, wie sie auf die `Get-Resource`-Funktion als Quelle des Problems verweist? Das sind hilfreiche Informationen für den Benutzer.

Da `$PSItem` ein `ErrorRecord` ist, können wir `ThrowTerminatingError` auch auf diese Weise zum erneuten Auslösen verwenden.

```powershell
catch
{
    $PSCmdlet.ThrowTerminatingError($PSItem)
}
```

Dadurch wird die Fehlerquelle in das Cmdlet geändert und die Interna Ihrer Funktion vor den Benutzern Ihres Cmdlets ausgeblendet.

## <a name="try-can-create-terminating-errors"></a>Try kann Fehler mit Abbruch erstellen

Kirk Munro zeigt, dass einige Ausnahmen nur bei der Ausführung innerhalb eines `try/catch`-Blocks Fehler mit Abbruch sind. Er hat mir dieses Beispiel gegeben, das eine „Division durch Null“-Laufzeitausnahme generiert.

```powershell
function Do-Something { 1/(1-1) }
```

Führen Sie den Aufruf so aus. Sie sehen dann, dass der Fehler generiert und die Meldung trotzdem ausgegeben wird.

```powershell
&{ Do-Something; Write-Output "We did it. Send Email" }
```

Wenn Sie jedoch denselben Code in einem `try/catch` einfügen, passiert etwas anderes.

```powershell
try
{
    &{ Do-Something; Write-Output "We did it. Send Email" }
}
catch
{
    Write-Output "Notify Admin to fix error and send email"
}
```


Der Fehler wird ein Fehler mit Abbruch, und die erste Meldung wird nicht ausgegeben. Was mir daran nicht gefällt, ist, dass Sie diesen Code in einer Funktion verwenden können, und er verhält sich anders, wenn jemand `try/catch`verwendet.

Ich selbst hatte damit keine Probleme, aber es ist ein Fall, den man kennen muss.

### <a name="pscmdletthrowterminatingerror-inside-trycatch"></a>$PSCmdlet.ThrowTerminatingError() in try/catch

Eine Besonderheit von `$PSCmdlet.ThrowTerminatingError()` besteht darin, dass ein Fehler mit Abbruch innerhalb Ihres Cmdlets erstellt wird, der jedoch nach Verlassen des Cmdlets in einen Fehler ohne Abbruch umgewandelt wird. Dadurch muss der Aufrufer ihrer Funktion entscheiden, wie der Fehler behandelt werden soll. Er kann ihn mit `-ErrorAction Stop` wieder in einen Fehler mit Abbruch umwandeln, oder ihn innerhalb von `try{...}catch{...}` aufrufen.

### <a name="public-function-templates"></a>Öffentliche Funktionsvorlagen

Eine letzte Sache, die ich aus meinem Gespräch mit Kirk Munro mitgenommen habe, war, dass er bei alle seinen erweiterten Funktionen um jeden `begin`-, `process`- und `end`-Block einen `try{...}catch{...}` einfügt. In diesen allgemeinen Catch-Blöcken verwendet er eine einzige Zeile mit `$PSCmdlet.ThrowTerminatingError($PSitem)`, um alle Ausnahmen zu behandeln, die seine Funktionen verlassen.

```powershell
function Do-Something
{
    [cmdletbinding()]
    param()

    process
    {
        try
        {
            ...
        }
        catch
        {
            $PSCmdlet.ThrowTerminatingError($PSitem)
        }
    }
}
```

Da alles in einer `try`-Anweisung innerhalb seiner Funktionen steht, wird alles einheitlich ausgeführt. Dadurch erhält der Endbenutzer auch eindeutige Fehler, die den internen Code vor dem generierten Fehler ausblendet.

## <a name="trap"></a>Trap

Ich haben mich auf den `try/catch`-Aspekt der Ausnahmen konzentriert. Aber es gibt ein altes Feature, das ich erwähnen muss, bevor wir das Thema zusammenfassen.

Ein `trap` wird in einem Skript oder einer Funktion eingefügt, um alle Ausnahmen abzufangen, die in diesem Bereich auftreten. Wenn eine Ausnahme auftritt, wird der Code im `trap` ausgeführt, und anschließend wird der normale Code fortgesetzt. Wenn mehrere Ausnahmen auftreten, wird der Trap immer wieder aufgerufen.

```powershell
trap
{
    Write-Log $PSItem.ToString()
}

throw [System.Exception]::new('first')
throw [System.Exception]::new('second')
throw [System.Exception]::new('third')
```

Ich persönlich habe diesen Ansatz nie verwendet, kann aber den Nutzen in Admin- oder Controllerskripts sehen, die alle Ausnahmen protokollieren und dann trotzdem weiter ausgeführt werden.

## <a name="closing-remarks"></a>Abschließende Hinweise

Durch das Hinzufügen einer richtigen Ausnahmebehandlung zu Ihren Skripts werden diese nicht nur stabiler, sondern es wird Ihnen auch die Fehlerbehebung für diese Ausnahmen erleichtert.

Ich habe lange über `throw` gesprochen, da dies eines der Kernkonzepte der Ausnahmebehandlung ist. PowerShell bietet uns auch `Write-Error`, mit dem alle Situationen behandelt werden können, in denen Sie `throw` verwenden würden. Denken Sie also nicht, dass Sie `throw` verwenden müssen, nachdem Sie das hier gelesen haben.

Nachdem ich mir nun die Zeit genommen habe, die Ausnahmebehandlung ausführlich zu beschreiben, werde ich nun zur Verwendung von `Write-Error -Stop` wechseln, um Fehler in meinem Code zu generieren. Ich werde auch den Rat von Kirk übernehmen und `ThrowTerminatingError` als-Ausnahmehandler für jede Funktion verwenden.

<!-- link references -->
[powershellexplained.com]: https://powershellexplained.com/
[Originalversion]: https://powershellexplained.com/2017-04-10-Powershell-exceptions-everything-you-ever-wanted-to-know/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Reddit/r/PowerShell-Community]: https://www.reddit.com/r/PowerShell/comments/64866o/kevmar_all_net_46_exceptions_list_for_use_with/
[Die lange Liste der .NET-Ausnahmen]: https://powershellexplained.com/2017-04-07-all-dotnet-exception-list
[FileNotFoundException]: https://docs.microsoft.com/dotnet/api/System.IO.FileNotFoundException
[.NET-Dokumentation]: https://docs.microsoft.com/dotnet/api