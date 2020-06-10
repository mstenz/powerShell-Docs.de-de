---
title: Alles, was Sie schon immer über ShouldProcess wissen wollten
description: ShouldProcess ist ein wichtiges Feature, das oft übersehen wird. Mit den WhatIf- und Confirm-Parametern können Sie Ihre Funktionen einfach erweitern.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1d9110302a191b90bd11bdf742f77704a8c9d6f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149483"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a>Alles, was Sie schon immer über ShouldProcess wissen wollten

PowerShell-Funktionen verfügen über mehrere Features, die die Interaktion der Benutzer mit ihnen erheblich verbessern.
Ein wichtiges Feature, das oft übersehen wird, ist die Unterstützung von `-WhatIf` und `-Confirm`. Diese kann ganz einfach zu Ihren Funktionen hinzugefügt werden. In diesem Artikel wird ausführlich erläutert, wie dieses Feature implementiert wird.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

Dies ist ein einfaches Feature, das Sie in Ihren Funktionen aktivieren können, um ein Sicherheitsnetz für die Benutzer bereitzustellen, die es benötigen. Es gibt nichts Schlimmeres, zum ersten Mal einen Befehl auszuführen, von dem man weiß, dass er gefährlich sein kann. Die Option, ihn mit `-WhatIf` auszuführen, kann einen großen Unterschied ausmachen.

## <a name="commonparameters"></a>CommonParameters

Bevor wir uns mit der Implementierung dieser [Allgemeine Parameter][] befassen, möchte ich kurz darauf eingehen, wie sie verwendet werden.

## <a name="using--whatif"></a>Verwenden von -WhatIf

Wenn ein Befehl den `-WhatIf`-Parameter unterstützt, können Sie sehen, was der Befehl getan hätte, anstatt Änderungen vorzunehmen. Das ist eine gute Möglichkeit, die Auswirkungen eines Befehls zu testen, vor allem, bevor Sie etwas machen, was zerstörerische Folgen haben könnte.

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Wenn der Befehl `ShouldProcess` ordnungsgemäß implementiert, sollte er Ihnen alle Änderungen zeigen, die er vorgenommen hätte. Hier ist ein Beispiel für die Verwendung eines Platzhalters zum Löschen mehrerer Dateien.

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>Verwenden von -Confirm

Befehle, die `-WhatIf` unterstützen, unterstützen auch `-Confirm`. Dadurch haben Sie die Möglichkeit, eine Aktion zu bestätigen, bevor Sie sie ausführen.

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

In diesem Fall haben Sie mehrere Optionen, mit denen Sie fortfahren, eine Änderung überspringen oder das Skript anhalten können. In der Hilfeanzeige werden die einzelnen Optionen beschrieben.

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>Lokalisierung

Diese Eingabeaufforderung ist in PowerShell lokalisiert, sodass sich die Sprache basierend auf der Sprache Ihres Betriebssystems ändert. Dies ist ein weiterer Punkt, den PowerShell für Sie übernimmt.

### <a name="switch-parameters"></a>Switch-Parameter

Schauen wir uns kurz an, wie Sie einen Wert an einen Switch-Parameter übergeben. Der Hauptgrund, warum ich dies ausspreche, ist, dass Sie oft Parameterwerte an von Ihnen aufgerufene Funktionen übergeben wollen.

Der erste Ansatz ist eine spezifische Parametersyntax, die zwar für alle Parameter verwendet werden kann, aber meistens für Switch-Parameter eingesetzt wird. Sie geben einen Doppelpunkt an, um einen Wert an den Parameter anzufügen.

```powershell
Remove-Item -Path:* -WhatIf:$true
```

Dasselbe können Sie mit einer Variablen machen.

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

Der zweite Ansatz ist, eine Hashtabelle zum Verteilen des Werts zu verwenden.

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

Wenn Sie noch nicht mit Hashtabellen oder dem Verteilen vertraut sind, lesen Sie den Artikel [Alles, was Sie schon immer über Hashtabellen wissen wollten][].

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

Der erste Schritt zum Aktivieren der `-WhatIf`- und `-Confirm`-Unterstützung besteht darin, `SupportsShouldProcess` in `CmdletBinding` der Funktion anzugeben.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

Wenn Sie `SupportsShouldProcess` so angeben, können wir die Funktion mit `-WhatIf` (oder `-Confirm`) aufrufen.

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Beachten Sie, dass ich keinen Parameter namens `-WhatIf` erstellt habe. Durch das Angeben von `SupportsShouldProcess` wird dieser automatisch für uns erstellt. Wenn wir den `-WhatIf`-Parameter in `Test-ShouldProcess` angeben, führen einige Funktionen, die wir aufrufen, auch eine `-WhatIf`-Verarbeitung aus.

### <a name="trust-but-verify"></a>Vertrauen ist gut – Kontrolle ist besser

Hier besteht eine gewisse Gefahr, wenn man darauf vertraut, dass jeder Befehl, der aufgerufen wird, `-WhatIf`-Werte übernimmt. Bei den weiteren Beispielen gehe ich davon aus, dass es nicht funktioniert, und werde bei Aufrufen anderer Befehle sehr explizit sein. Ich empfehle, dass Sie das auch machen.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

Ich werde auf die Besonderheiten später noch einmal zurückkommen, wenn Sie alle beteiligten Aspekte besser kennen.

## <a name="pscmdletshouldprocess"></a>$PSCmdlet.ShouldProcess

Mit dieser Methode können Sie `SupportsShouldProcess` in `$PSCmdlet.ShouldProcess` implementieren. Sie rufen `$PSCmdlet.ShouldProcess(...)` auf, um festzustellen, ob Sie etwas Logik verarbeiten müssen, und PowerShell kümmert sich um den Rest. Beginnen wir mit einem Beispiel:

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

Durch den Aufruf von `$PSCmdlet.ShouldProcess($file.name)` wir überprüft, ob `-WhatIf` (und der `-Confirm`-Parameter) vorhanden ist, und verarbeitet ihn dann entsprechend. Durch `-WhatIf` gibt `ShouldProcess` eine Beschreibung der Änderung aus und gibt `$false` zurück:

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

Ein Aufruf mit `-Confirm` hält das Skript an und zeigt dem Benutzer die Option zum Fortfahren an. Wenn der Benutzer `Y` ausgewählt hat, wird `$true` zurückgegeben.

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Ein tolles Feature von `$PSCmdlet.ShouldProcess` ist, dass es gleichzeitig eine ausführliche Ausgabe darstellt. Darauf bin ich beim Implementieren von `ShouldProcess` oft angewiesen.

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>Überladungen

Es gibt einige verschiedene Überladungen für `$PSCmdlet.ShouldProcess` mit unterschiedlichen Parametern zum Anpassen des Messaging. Die erste haben wir bereits im obigen Beispiel gesehen. Schauen wir uns das genauer an.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

Dadurch wird sowohl der Funktionsname als auch das Ziel (Wert des Parameters) ausgegeben.

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

Geben Sie einen zweiten Parameter an, da der Vorgang den Vorgangswert anstelle des Funktionsnamens in der Nachricht verwendet.

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

Die nächste Option besteht darin, drei Parameter anzugeben, um die Nachricht vollständig anzupassen. Wenn drei Parameter verwendet werden, ist der erste die gesamte Nachricht. Die nächsten beiden Parameter werden weiterhin in der Meldungsausgabe von `-Confirm` verwendet.

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>Schneller Parameterverweis

Wenn Sie diesen Artikel nur lesen, um herauszufinden, welche Parameter Sie verwenden sollten, finden Sie hier einen kurzen Verweis darauf, wie die Parameter die Nachricht in den verschiedenen `-WhatIf`-Szenarien verändern.

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

Ich verwende in der Regel die Variante mit zwei Parametern.

### <a name="shouldprocessreason"></a>ShouldProcessReason

Wir haben eine vierte Überladung, die ausgereifter ist als die anderen. Diese ermöglicht es Ihnen, den Grund für die Ausführung `ShouldProcess` abzurufen. Ich führe dies hier nur der Vollständigkeit halber an, weil wir einfach prüfen können, ob `$WhatIf` stattdessen `$true` ist.

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

Wir müssen die `$reason`-Variable als Verweisvariable mit `[ref]` an den vierten Parameter übergeben. `ShouldProcess` füllt `$reason` mit dem Wert `None` oder `WhatIf` auf. Ich habe nicht gesagt, dass dies nützlich ist, und es gab für mich bisher auch noch keinen Grund, das so zu verwenden.

### <a name="where-to-place-it"></a>Die richtige Position

Mit `ShouldProcess` können Sie Skripts sicherer gestalten. Sie verwenden es also, wenn Ihre Skripts Änderungen vornehmen. Ich füge den `$PSCmdlet.ShouldProcess`-Aufruf gern so nah wie möglich an der Änderung ein.

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

Wenn ich eine Auflistung von Elementen ausführe, rufe ich es für jedes Element auf. Der Aufruf wird also in der ForEach-Schleife eingefügt.

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

Ich füge `ShouldProcess` eng um die Änderung herum ein, da ich möchte, dass so viel Code wie möglich ausgeführt wird, wenn `-WhatIf` angegeben wird. Ich möchte, dass Setup und Validierung ausgeführt werden, falls möglich, damit der Benutzer diese Fehler sehen kann.

Ich verwende das auch gern in meinen Pester-Tests, mit denen meine Projekte validiert werden. Wenn ich eine Logik verwende, die in Pester schwer zu simulieren ist, kann ich sie häufig in `ShouldProcess` umschließen und mit `-WhatIf` in meinen Tests aufzurufen. Es ist besser, einen Teil Ihres Codes zu testen, als keinen.

### <a name="whatifpreference"></a>$WhatIfPreference

Unsere erste Einstellungsvariable ist `$WhatIfPreference`. Diese ist standardmäßig auf `$false` festgelegt. Wenn Sie sie auf `$true` festlegen, wird die Funktion so ausgeführt, als ob Sie `-WhatIf` angegeben haben. Wenn Sie dies in Ihrer Sitzung festlegen, führen alle Befehle eine `-WhatIf`-Ausführung aus.

Wenn Sie eine Funktion mit `-WhatIf` aufzurufen, wird der Wert von `$WhatIfPreference` innerhalb des Gültigkeitsbereichs der Funktion auf `$true` festgelegt.

## <a name="confirmimpact"></a>ConfirmImpact

Die meisten meiner Beispiele beziehen sich auf `-WhatIf`, sie funktionieren aber auch mit `-Confirm`, um dem Benutzer eine Eingabeaufforderung anzuzeigen. Sie können den `ConfirmImpact`-Parameter der Funktion auf „Hoch“ festlegen, und der Benutzer wird eine Eingabeaufforderung angezeigt, als ob der Aufruf mit `-Confirm` erfolgt ist.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

Da `High` festgelegt wurde, führt der Aufruf von `Test-ShouldProcess` die `-Confirm`-Aktion aus.

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

Das offensichtliche Problem besteht darin, dass es jetzt schwieriger ist, das in anderen Skripten zu verwenden, ohne eine Eingabeaufforderung für den Benutzer anzuzeigen. In diesem Fall können wir ein `$false` an `-Confirm` übergeben, um die Eingabeaufforderung zu unterdrücken.

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

In einem späteren Abschnitt werde ich erläutern, wie die `-Force`-Unterstützung hinzugefügt wird.

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference` ist eine automatische Variable, die steuert, wann `ConfirmImpact` Sie zur Bestätigung der Ausführung auffordert. Hier sind die möglichen Werte für sowohl `$ConfirmPreference` als auch `ConfirmImpact`.

- `High`
- `Medium`
- `Low`
- `None`

Mit diesen Werten können Sie für jede Funktion unterschiedliche Auswirkungsstufen angeben. Wenn Sie `$ConfirmPreference` auf einen höheren Wert als `ConfirmImpact` festgelegt haben, werden Sie nicht aufgefordert, die Ausführung zu bestätigen.

Standardmäßig ist `$ConfirmPreference` auf `High` und `ConfirmImpact` auf `Medium` festgelegt. Wenn Sie möchten, dass die Funktion dem Benutzer automatisch Eingabeaufforderung anzeigt, legen Sie für `ConfirmImpact` `High`fest. Legen Sie andernfalls `Medium` fest, wenn die Funktion destruktiv ist, und verwenden Sie `Low`, wenn der Befehl immer sicher in der Produktion ausgeführt werden kann. Wenn Sie diesen Wert auf `none` festlegen, wird auch dann keine Eingabeaufforderung angezeigt, wenn `-Confirm` angegeben wurde (`-WhatIf` wird jedoch unterstützt).

Wenn Sie eine Funktion mit `-Confirm` aufzurufen, wird der Wert von `$ConfirmPreference` innerhalb des Gültigkeitsbereichs der Funktion auf `Low` festgelegt.

### <a name="suppressing-nested-confirm-prompts"></a>Unterdrücken von geschachtelten Confirm-Eingabeaufforderungen

`$ConfirmPreference` kann von Funktionen übernommen werden, die Sie aufzurufen. Dadurch entstehen Szenarios, in denen Sie eine Confirm-Eingabeaufforderung hinzufügen und die von Ihnen aufgerufene Funktion den Benutzer ebenfalls auffordert.

Ich gebe in der Regel `-Confirm:$false` bei den Befehlen an, die ich aufrufe, wenn ich die Eingabeaufforderung bereits bearbeitet habe.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

Damit kommen wir zurück zu einer früheren Warnung: Es gibt Besonderheiten, wann `-WhatIf` nicht an eine Funktion übergeben wird und wann `-Confirm` an eine Funktion übergeben wird. Ich werde später noch einmal darauf zurückkommen.

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet.ShouldContinue

Wenn Sie mehr Kontrolle benötigen, als `ShouldProcess` Ihnen ermöglicht, können Sie die Eingabeaufforderung direkt mit `ShouldContinue` auslösen. `ShouldContinue` ignoriert `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference` und `-WhatIf`, da bei jeder Ausführung eine Eingabeaufforderung angezeigt wird.

Auf den ersten Blick können `ShouldProcess` und `ShouldContinue` leicht verwechselt werden. Ich erinnere mich daran, eher `ShouldProcess` zu verwenden, da der Parameter in `CmdletBinding` als `SupportsShouldProcess` bezeichnet wird.
Sie sollten in fast jedem Szenario `ShouldProcess` verwenden. Aus diesem Grund habe ich diese Methode zuerst erläutert.

Schauen wir uns `ShouldContinue` in Aktion an.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

Damit wird eine vereinfachte Eingabeaufforderung mit weniger Optionen angezeigt.

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Das größte Problem bei `ShouldContinue` besteht darin, dass es vom Benutzer interaktiv ausgeführt muss, da dem Benutzer immer eine Eingabeaufforderung angezeigt wird. Sie sollten immer Tools zusammenstellen, die von anderen Skripts verwendet werden können. Dafür können Sie `-Force`implementiert. Ich komme auf diesen Punkt später noch einmal zurück.

### <a name="yes-to-all"></a>Ja zu allem

Dies wird automatisch mit `ShouldProcess` bearbeitet, aber für `ShouldContinue` müssen wir etwas mehr Arbeit leisten. Es gibt eine zweite Methodenüberladung, bei der wir ein paar Werte per Verweis übergeben müssen, um die Logik zu steuern.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

Ich habe eine `foreach`-Schleife und eine Auflistung hinzugefügt, um das in Aktion anzuzeigen. Ich habe den `ShouldContinue`-Befehl aus der `if`-Anweisung abgerufen, um die Lesbarkeit zu verbessern. Der Aufruf einer Methode mit vier Parametern wird langsam etwas unschön, aber ich habe versucht, es so übersichtlich wie möglich zu gestalten.

## <a name="implementing--force"></a>Implementieren von -Force

`ShouldProcess` und `ShouldContinue` müssen `-Force` unterschiedlich implementieren. Der Trick bei dieser Implementierungen ist, dass `ShouldProcess` immer ausgeführt werden sollte, aber `ShouldContinue` sollte nicht ausgeführt werden, wenn `-Force` angegeben ist.

### <a name="shouldprocess--force"></a>ShouldProcess -Force

Wenn Sie `ConfirmImpact` auf `high` festlegen, wird der Benutzer zunächst versuchen, das mit `-Force` zu unterdrücken. Das ist sowieso das erste, was ich mache.

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

Wie Sie aus dem Abschnitt `ConfirmImpact` wissen, müssen Sie ihn wie folgt bezeichnen:

```powershell
Test-ShouldProcess -Confirm:$false
```

Nicht allen ist klar, dass das notwendig ist, und `-Confirm:$false` nicht `ShouldContinue` unterdrückt.
Daher sollten wir `-Force` für die Benutzerfreundlichkeit implementieren. Schauen wir uns hier dieses vollständige Beispiel an:

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

Wir fügen unseren eigenen `-Force`-Switch als Parameter hinzu und verwenden den automatischen `$Confirm`-Parameter, der beim Hinzufügen von `SupportsShouldProcess` in `CmdletBinding` verfügbar ist.

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

Hier konzentrieren wir uns auf die `-Force`-Logik:

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

Wenn der Benutzer `-Force` angibt, möchten wir die Confirm-Eingabeaufforderung unterdrücken, es sei denn, es wird auf `-Confirm` angegeben. Dadurch kann ein Benutzer eine Änderung erzwingen, die Änderung aber dennoch bestätigen. Anschließend legen wir `$ConfirmPreference` im lokalen Bereich fest, in dem der Wert durch den Aufruf von `ShouldProcess` ermittelt wird.

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

Wenn sowohl `-Force` als auch `-WhatIf`angegeben werden, muss `-WhatIf` Priorität haben. Dieser Ansatz behält die `-WhatIf`-Verarbeitung bei, da `ShouldProcess` immer ausgeführt wird.

Fügen Sie in der if-Anweisung mit `ShouldProcess` keine Überprüfung auf den `$Force` Wert hinzu. Das ist ein Widerspruch zu diesem spezifischen Szenario, auch wenn ich das im nächsten Abschnitt für `ShouldContinue` zeige.

### <a name="shouldcontinue--force"></a>ShouldContinue -Force

Dies ist die richtige Vorgehensweise zum Implementieren von `-Force` mit `ShouldContinue`.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

Da `$Force` links vom `-or`-Operator platzieren wird, wird der Wert zuerst ausgewertet. Wenn Sie den Code so schreiben, wird die Ausführung der `if`-Anweisung verkürzt. Wenn `$force` `$true` ist, wird `ShouldContinue` nicht ausgeführt.

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

Wir müssen uns in diesem Szenario nicht um `-Confirm` oder `-WhatIf` kümmern, da sie nicht von `ShouldContinue` unterstützt werden. Aus diesem Grund muss die Verarbeitung anders erfolgen als mit `ShouldProcess`.

## <a name="scope-issues"></a>Bereichsprobleme

Die Verwendung von `-WhatIf` und `-Confirm` soll für alles innerhalb Ihrer Funktionen und alles, was davon aufgerufen wird, angewendet werden. Dazu legen sie im lokalen Bereich der Funktion `$WhatIfPreference` auf `$true` oder `$ConfirmPreference` auf `Low` fest. Wenn Sie eine andere Funktion aufrufen, werden diese Werte von Aufrufen von `ShouldProcess` verwenden.

Dies funktioniert in den meisten Fällen ordnungsgemäß. Es funktioniert jedes Mal, wenn Sie ein integriertes Cmdlet oder eine Funktion im selben Bereich aufrufen. Es funktioniert auch, wenn Sie ein Skript oder eine Funktion in einem Skriptmodul über die Konsole aufzurufen.

Die einzige Stelle, an der es nicht funktioniert, ist, wenn ein Skript oder ein Skriptmodul eine Funktion in einem anderen Skriptmodul aufruft. Das klingt vielleicht nicht besonders problematisch, aber die meisten Module, die Sie erstellen oder aus der PSGallery abrufen, sind Skriptmodule.

Das Hauptproblem ist, dass Skriptmodule nicht die Werte für `$WhatIfPreference` oder `$ConfirmPreference` (und einige andere) übernehmen, wenn sie von Funktionen in anderen Skriptmodulen aufgerufen werden.

Allgemein lässt sich dies am besten zusammenfassen, dass es für binäre Module korrekt funktioniert und dass man nicht darauf vertrauen kann, dass es für Skriptmodule funktioniert. Wenn Sie sich nicht sicher sind, sollten Sie es entweder testen, oder einfach annehmen, dass es nicht richtig funktioniert.

Ich persönlich halte das für sehr riskant, weil dadurch Szenarios entstehen, in denen Sie `-WhatIf`-Unterstützung zu mehreren Modulen hinzufügen, die isoliert korrekt funktionieren, aber nicht ordnungsgemäß funktionieren, wenn sie sich gegenseitig aufrufen.

Wir arbeiten an einem GitHub-RFC, um dieses Problem zu beheben. Weitere Informationen finden Sie unter [Propagate execution preferences beyond script module scope][RFC] (Weiterleiten von Ausführungseinstellungen über den Skriptmodulbereich hinaus).

## <a name="in-closing"></a>Abschluss

Ich muss jedes Mal nachschlagen, wie ich `ShouldProcess` verwende. Ich habe lange gebraucht, um `ShouldProcess` von `ShouldContinue` zu unterscheiden. Ich muss fast immer nachschlagen, welche Parameter verwendet werden sollen. Machen Sie sich also keine Sorgen, wenn Sie gelegentlich noch etwas verwirrt sind. Sie können diesen Artikel bei Bedarf jederzeit hier abrufen. Ich bin mir sicher, dass ich ihn selbst häufig zu Rate ziehen werde.

Wenn Ihnen dieser Beitrag gefallen hat, können Sie mir Ihre Meinung auf Twitter über den untenstehenden Link mitteilen. Ich höre immer gerne von Menschen, für die meine Inhalte hilfreich sind.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Allgemeine Parameter]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[Alles, was Sie schon immer über Hashtabellen wissen wollten]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
