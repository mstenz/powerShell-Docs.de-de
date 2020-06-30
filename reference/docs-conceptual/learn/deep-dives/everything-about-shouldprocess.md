---
title: Alles, was Sie schon immer über ShouldProcess wissen wollten
description: ShouldProcess ist ein wichtiges Feature, das oft übersehen wird. Mit den WhatIf- und Confirm-Parametern können Sie Ihre Funktionen ganz einfach erweitern.
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
Ein wichtiges Feature, das oft übersehen wird, ist die Unterstützung von `-WhatIf` und `-Confirm` – diese lässt sich ganz einfach zu Ihren Funktionen hingefügen. In diesem Artikel möchte ich Ihnen ausführlich erläutern, wie Sie dieses Feature implementieren.

> [!NOTE]
> Die [Originalversion][] dieses Artikels ist im Blog von [@KevinMarquette][] erschienen. Das PowerShell-Team dankt Kevin Marquette dafür, dass er diesen Inhalt mit uns teilt. Weitere Informationen finden Sie in seinem Blog auf [PowerShellExplained.com][].

Dies ist ein einfaches Feature, das Sie in Ihren Funktionen aktivieren können, um ein Sicherheitsnetz für die Benutzer bereitzustellen, die es benötigen. Es kann schon sehr beängstigend sein, zum ersten Mal einen Befehl auszuführen, von dem Sie wissen, dass er gefährlich sein kann. Die Option, ihn mit `-WhatIf` auszuführen, kann da einen großen Unterschied ausmachen.

## <a name="commonparameters"></a>CommonParameters

Bevor wir uns mit der Implementierung dieser [Allgemeine Parameter][] befassen, möchte ich kurz darauf eingehen, wie diese verwendet werden.

## <a name="using--whatif"></a>Verwenden: -WhatIf

Wenn ein Befehl den `-WhatIf`-Parameter unterstützt, können Sie sehen, was der Befehl getan hätte, anstatt die Änderungen direkt vorzunehmen. Das ist eine gute Möglichkeit, die Auswirkungen eines Befehls zu testen, vor allem, bevor Sie etwas tun, das zerstörerische Folgen haben könnte.

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Wenn der Befehl `ShouldProcess` ordnungsgemäß implementiert, sollte er Ihnen alle Änderungen zeigen, die er vorgenommen hätte. Im Folgenden sehen Sie ein Beispiel für die Verwendung eines Platzhalters zum Löschen mehrerer Dateien.

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a>Verwenden: -Confirm

Befehle, die `-WhatIf` unterstützen, unterstützen auch `-Confirm`. Dadurch haben Sie die Möglichkeit, eine Aktion zu bestätigen, bevor Sie sie ausführen.

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

In diesem Fall haben Sie mehrere Optionen, mit denen Sie das Skript fortsetzen, eine Änderung überspringen oder das Skript anhalten können. In der Hilfeanzeige werden die einzelnen Optionen beschrieben.

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a>Lokalisierung

Diese Eingabeaufforderung ist in PowerShell lokalisiert, sodass sich die Sprache basierend auf der Sprache Ihres Betriebssystems ändert. Dies ist ein weiterer Aspekt, den PowerShell für Sie übernimmt.

### <a name="switch-parameters"></a>Switch-Parameter

Schauen wir uns kurz an, wie Sie einen Wert an einen Switch-Parameter übergeben. Ich spreche diesen Aspekt hauptsächlich deswegen an, weil es häufig vorkommen wird, dass Sie Parameterwerte an die Funktionen übergeben möchten, die Sie aufrufen.

Der erste Ansatz ist eine spezifische Parametersyntax, die sich zwar für alle Parameter eignet, aber meistens für Switch-Parameter eingesetzt wird. Um einen Wert an den Parameter anzufügen, geben Sie einen Doppelpunkt an.

```powershell
Remove-Item -Path:* -WhatIf:$true
```

Dasselbe können Sie mit einer Variablen machen.

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

Der zweite Ansatz besteht darin, eine Hashtabelle zum Splatten des Werts zu verwenden.

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

Wenn Sie noch nicht mit Hashtabellen oder dem Splatting vertraut sind, lesen Sie den Artikel [Alles, was Sie schon immer über Hashtabellen wissen wollten][].

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

Der erste Schritt beim Aktivieren der Unterstützung für `-WhatIf` und `-Confirm` besteht darin, `SupportsShouldProcess` in der `CmdletBinding` der Funktion anzugeben.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

Wenn wir `SupportsShouldProcess` auf diese Weise angeben, können wir die Funktion mit `-WhatIf` (oder `-Confirm`) aufrufen.

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

Beachten Sie, dass ich keinen Parameter namens `-WhatIf` erstellt habe. Durch die Angabe von `SupportsShouldProcess` wird dieser automatisch für uns erstellt. Wenn wir den `-WhatIf`-Parameter in `Test-ShouldProcess` angeben, führen einige Funktionen, die wir aufrufen, auch eine `-WhatIf`-Verarbeitung aus.

### <a name="trust-but-verify"></a>Vertrauen ist gut – Kontrolle ist besser

Hier lauert eine gewisse Gefahr, wenn Sie blind darauf vertrauen, dass jeder Befehl, der aufgerufen wird, `-WhatIf`-Werte erbt. Bei den weiteren Beispielen gehe ich davon aus, dass dies nicht funktioniert, und werde bei Aufrufen anderer Befehle sehr explizit sein. Ich empfehle Ihnen, genauso vorzugehen.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

Ich werde auf die Besonderheiten später noch einmal zurückkommen, wenn Sie alle Puzzleteile kennen.

## <a name="pscmdletshouldprocess"></a>$PSCmdlet.ShouldProcess

Zum Implementieren von `SupportsShouldProcess` benötigen Sie die Methode `$PSCmdlet.ShouldProcess`. Sie rufen `$PSCmdlet.ShouldProcess(...)` auf, um festzustellen, ob Logik verarbeitet werden muss – um den Rest kümmert sich PowerShell. Beginnen wir mit einem Beispiel:

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

Der Aufruf von `$PSCmdlet.ShouldProcess($file.name)` überprüft, ob der Parameter `-WhatIf` (und der Parameter `-Confirm`) vorhanden ist, und verarbeitet ihn dann entsprechend. Durch `-WhatIf` gibt `ShouldProcess` eine Beschreibung der Änderung aus und gibt `$false` zurück:

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

Ein Aufruf mit `-Confirm` hält das Skript an und fordert den Benutzer zum Fortfahren auf. Wenn der Benutzer `Y` ausgewählt hat, wird `$true` zurückgegeben.

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Ein tolles Feature von `$PSCmdlet.ShouldProcess` ist, dass es auch eine ausführliche Ausgabe bietet. Das benötige ich beim Implementieren von `ShouldProcess` häufig.

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a>Überladungen

Es gibt verschiedene Überladungen für `$PSCmdlet.ShouldProcess` mit unterschiedlichen Parametern zum Anpassen des Messaging. Die erste findet sich bereits im Beispiel oben. Sehen wir uns das einmal genauer an.

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

Die Ausgabe dieses Beispiels enthält sowohl den Funktionsnamen als auch das Ziel (den Wert des Parameters).

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

Jetzt geben wir einen zweiten Parameter an, da der Vorgang den Vorgangswert statt des Funktionsnamens in der Meldung verwendet.

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

Die nächste Option besteht darin, drei Parameter anzugeben, um die Meldung vollständig anzupassen. Wenn drei Parameter verwendet werden, ist der erste die gesamte Meldung. Die nächsten beiden Parameter werden weiterhin in der Meldungsausgabe von `-Confirm` verwendet.

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a>Kurze Parameterreferenz

Wenn Sie diesen Artikel nur lesen, um herauszufinden, welche Parameter Sie verwenden sollten, finden Sie hier eine kurze Referenz, die zeigt, wie die Parameter die Meldung in den verschiedenen `-WhatIf`-Szenarien verändern.

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

Es gibt noch eine vierte Überladung, die ausgereifter ist als die anderen. Mit dieser können Sie den Grund für die Ausführung von `ShouldProcess` abrufen. Ich führe dies hier nur der Vollständigkeit halber an, weil wir einfach prüfen können, ob `$WhatIf` stattdessen `$true` ist.

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

Wir müssen die `$reason`-Variable als Verweisvariable mit `[ref]` an den vierten Parameter übergeben. `ShouldProcess` füllt `$reason` mit dem Wert `None` oder `WhatIf` auf. Ich behaupte nicht, dass dies nützlich ist, und es gab für mich bisher auch noch keinen Grund, das so zu verwenden.

### <a name="where-to-place-it"></a>Die richtige Position

Mit `ShouldProcess` können Sie Ihre Skripts sicherer machen. Verwenden Sie das Feature also dann, wenn Ihre Skripts Änderungen vornehmen. Ich füge den `$PSCmdlet.ShouldProcess`-Aufruf gern so nah wie möglich an der Änderung ein.

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

Wenn ich eine Auflistung von Elementen verarbeite, rufe ich das Feature für jedes Element auf. Der Aufruf wird also in der ForEach-Schleife eingefügt.

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

Ich platziere `ShouldProcess` um die Änderung, weil ich möchte, dass so viel Code wie möglich ausgeführt wird, wenn `-WhatIf` angegeben wird. Die Setup- und Validierungsprozesse sollen nach Möglichkeit ausgeführt werden, damit der Benutzer diese Fehler sehen kann.

Ich verwende das auch gern in meinen Pester-Tests, mit denen meine Projekte validiert werden. Wenn ich mit Logik arbeite, die in Pester schwer zu simulieren ist, kann ich sie häufig in `ShouldProcess` umschließen und mit `-WhatIf` in meinen Tests aufzurufen. Es ist immer noch besser, einen Teil Ihres Codes zu testen als gar keinen.

### <a name="whatifpreference"></a>$WhatIfPreference

Unsere erste Einstellungsvariable ist `$WhatIfPreference`. Diese ist standardmäßig auf `$false` festgelegt. Wenn Sie sie auf `$true` festlegen, wird die Funktion so ausgeführt, als ob Sie `-WhatIf` angegeben haben. Wenn Sie dies in Ihrer Sitzung festlegen, werden alle Befehle mit `-WhatIf` ausgeführt.

Wenn Sie eine Funktion mit `-WhatIf` aufrufen, wird der Wert von `$WhatIfPreference` innerhalb des Gültigkeitsbereichs der Funktion auf `$true` festgelegt.

## <a name="confirmimpact"></a>ConfirmImpact

Die meisten meiner Beispiele beziehen sich auf `-WhatIf`, sie funktionieren aber auch mit `-Confirm`, um dem Benutzer eine Eingabeaufforderung anzuzeigen. Sie können den `ConfirmImpact`-Parameter der Funktion auf „High“ festlegen, und der Benutzer wird zu einer Eingabe aufgefordert, so als ob der Aufruf mit `-Confirm` erfolgt wäre.

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

Da `High` festgelegt wurde, führt dieser Aufruf von `Test-ShouldProcess` die `-Confirm`-Aktion aus.

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

Das offensichtliche Problem besteht darin, dass es jetzt schwieriger ist, das Ganze in anderen Skripten zu verwenden, ohne eine Eingabeaufforderung für den Benutzer anzuzeigen. In diesem Fall können wir `$false` an `-Confirm` übergeben, um die Eingabeaufforderung zu unterdrücken.

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

In einem späteren Abschnitt werde ich erläutern, wie die `-Force`-Unterstützung hinzugefügt wird.

### <a name="confirmpreference"></a>$ConfirmPreference

`$ConfirmPreference` ist eine automatische Variable, die steuert, wann `ConfirmImpact` Sie zur Bestätigung der Ausführung auffordert. Hier sind die möglichen Werte sowohl für `$ConfirmPreference` als auch für `ConfirmImpact`.

- `High`
- `Medium`
- `Low`
- `None`

Mit diesen Werten können Sie für jede Funktion unterschiedliche Auswirkungsstufen angeben. Wenn Sie `$ConfirmPreference` auf einen höheren Wert als `ConfirmImpact` festgelegt haben, werden Sie nicht aufgefordert, die Ausführung zu bestätigen.

Standardmäßig ist `$ConfirmPreference` auf `High` und `ConfirmImpact` auf `Medium` festgelegt. Wenn Sie möchten, dass die Funktion dem Benutzer automatisch eine Eingabeaufforderung anzeigt, legen Sie `ConfirmImpact` auf `High` fest. Legen Sie andernfalls den Wert `Medium` fest, wenn die Funktion destruktiv ist, und verwenden Sie `Low`, wenn der Befehl in der Produktion immer sicher ausgeführt werden kann. Wenn Sie diesen Wert auf `none` festlegen, wird auch dann keine Eingabeaufforderung angezeigt, wenn `-Confirm` angegeben wurde (`-WhatIf` wird jedoch weiter unterstützt).

Wenn Sie eine Funktion mit `-Confirm` aufzurufen, wird der Wert von `$ConfirmPreference` innerhalb des Gültigkeitsbereichs der Funktion auf `Low` festgelegt.

### <a name="suppressing-nested-confirm-prompts"></a>Unterdrücken von geschachtelten Bestätigungsaufforderungen

`$ConfirmPreference` kann von Funktionen übernommen werden, die Sie aufzurufen. Dadurch können Szenarien entstehen, in denen Sie eine Bestätigungsaufforderung hinzufügen und die von Ihnen aufgerufene Funktion den Benutzer ebenfalls auffordert.

Ich gebe in der Regel `-Confirm:$false` bei den Befehlen an, die ich aufrufe, wenn ich die Eingabeaufforderung bereits verarbeitet habe.

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

Damit kommen wir zurück zu einer früheren Warnung: Es gibt einige feine Unterschiede, wann `-WhatIf` nicht an eine Funktion übergeben wird und wann `-Confirm` an eine Funktion übergeben wird. Ich werde später noch einmal darauf zurückkommen, versprochen.

## <a name="pscmdletshouldcontinue"></a>$PSCmdlet.ShouldContinue

Wenn Sie mehr Kontrolle benötigen, als `ShouldProcess` Ihnen ermöglicht, können Sie die Eingabeaufforderung direkt mit `ShouldContinue` auslösen. `ShouldContinue` ignoriert `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference` und `-WhatIf`, da bei jeder Ausführung eine Eingabeaufforderung angezeigt wird.

Auf den ersten Blick können `ShouldProcess` und `ShouldContinue` leicht verwechselt werden. Ich erinnere mich meist deswegen an die Verwendung von `ShouldProcess`, weil der Parameter in `CmdletBinding` als `SupportsShouldProcess` bezeichnet wird.
Sie sollten `ShouldProcess` in so ziemlich jedem Szenario verwenden. Aus diesem Grund habe ich diese Methode zuerst erläutert.

Sehen wir uns `ShouldContinue` in Aktion an.

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

So erhalten wir eine vereinfachte Eingabeaufforderung mit weniger Optionen.

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Das größte Problem bei `ShouldContinue` besteht darin, dass die Ausführung durch den Benutzer interaktiv erfolgen muss, weil der Benutzer immer eine Eingabeaufforderung erhält. Sie sollten immer Tools erstellen, die von anderen Skripts verwendet werden können. Zu diesem Zweck implementieren Sie `-Force`. Ich komme auf diesen Punkt später noch einmal zurück.

### <a name="yes-to-all"></a>Ja zu allem

Dies wird mit `ShouldProcess` automatisch verarbeitet, aber für `ShouldContinue` müssen wir etwas mehr Arbeit investieren. Es gibt eine zweite Methodenüberladung, bei der wir per Verweis einige Werte übergeben müssen, um die Logik zu steuern.

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

Ich habe eine `foreach`-Schleife und eine Auflistung hinzugefügt, um das Ganze in Aktion anzuzeigen. Ich habe den `ShouldContinue`-Befehl aus der `if`-Anweisung herausgezogen, um die Lesbarkeit zu verbessern. Der Aufruf einer Methode mit vier Parametern wird langsam etwas unschön, aber ich habe versucht, es so übersichtlich wie möglich zu gestalten.

## <a name="implementing--force"></a>Implementieren: -Force

`ShouldProcess` und `ShouldContinue` müssen `-Force` unterschiedlich implementieren. Der Trick bei diesen Implementierungen ist, dass `ShouldProcess` immer ausgeführt werden sollte, `ShouldContinue` aber nicht ausgeführt werden sollte, wenn `-Force` angegeben ist.

### <a name="shouldprocess--force"></a>ShouldProcess: -Force

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

Wenn der Benutzer `-Force` angibt, möchten wir die Bestätigungsaufforderung unterdrücken, es sei denn, es wird auch `-Confirm` angegeben. Dadurch kann ein Benutzer eine Änderung erzwingen, diese aber dennoch bestätigen. Anschließend legen wir `$ConfirmPreference` im lokalen Gültigkeitsbereich fest, in dem der Wert durch den Aufruf von `ShouldProcess` ermittelt wird.

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

Wenn sowohl `-Force` als auch `-WhatIf` angegeben werden, muss `-WhatIf` Priorität haben. Dieser Ansatz behält die `-WhatIf`-Verarbeitung bei, weil `ShouldProcess` immer ausgeführt wird.

Fügen Sie in der if-Anweisung mit `ShouldProcess` keine Überprüfung auf den `$Force`-Wert hinzu. Es ist ein Antimuster für dieses spezifische Szenario, auch wenn ich Ihnen genau das im nächsten Abschnitt für `ShouldContinue` zeige.

### <a name="shouldcontinue--force"></a>ShouldContinue: -Force

Im Folgenden sehen Sie die richtige Vorgehensweise zum Implementieren von `-Force` mit `ShouldContinue`.

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

Durch Platzierung links vom `-or`-Operator wird `$Force` zuerst ausgewertet. Auf diese Weise wird die Ausführung der `if`-Anweisung umgangen. Wenn `$force` den Wert `$true` aufweist, wird `ShouldContinue` nicht ausgeführt.

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

Wir müssen uns in diesem Szenario nicht um `-Confirm` oder `-WhatIf` kümmern, da sie von `ShouldContinue` nicht unterstützt werden. Aus diesem Grund muss die Verarbeitung anders erfolgen als bei `ShouldProcess`.

## <a name="scope-issues"></a>Probleme mit dem Gültigkeitsbereich

Die Verwendung `-WhatIf` und `-Confirm` sollte für alle Aspekte in Ihren Funktionen sowie für alle Elemente gelten, die von Ihren Funktionen aufgerufen werden. Dazu legen sie im lokalen Gültigkeitsbereich der Funktion `$WhatIfPreference` auf `$true` oder `$ConfirmPreference` auf `Low` fest. Wenn Sie eine andere Funktion aufrufen, werden diese Werte in Aufrufen von `ShouldProcess` verwendet.

Dies funktioniert in den meisten Fällen ordnungsgemäß. Es funktioniert jedes Mal, wenn Sie ein integriertes Cmdlet oder eine Funktion im selben Gültigkeitsbereich aufrufen. Es funktioniert auch, wenn Sie ein Skript oder eine Funktion in einem Skriptmodul über die Konsole aufzurufen.

Es gibt nur eine Situation, in der das Ganze nicht funktioniert: Wenn ein Skript oder ein Skriptmodul eine Funktion in einem anderen Skriptmodul aufruft. Das klingt vielleicht nicht besonders problematisch, aber die meisten Module, die Sie erstellen oder aus der PSGallery abrufen, sind Skriptmodule.

Das Hauptproblem ist, dass Skriptmodule die Werte für `$WhatIfPreference` oder `$ConfirmPreference` (und einige andere) nicht erben, wenn sie von Funktionen in anderen Skriptmodulen aufgerufen werden.

Eine allgemeine Regel lässt sich vielleicht so formulieren: Das Ganze funktioniert ordnungsgemäß für binäre Module, aber vertrauen Sie nie darauf, dass es auch für Skriptmodule funktioniert. Wenn Sie sich nicht sicher sind, sollten Sie es entweder testen, oder einfach annehmen, dass es nicht richtig funktioniert.

Ich persönlich sehe ein großes Risiko, weil dadurch Szenarien entstehen, in denen Sie `-WhatIf`-Unterstützung zu mehreren Modulen hinzufügen, die isoliert korrekt funktionieren, dies aber nicht mehr tun, wenn sie sich gegenseitig aufrufen.

Wir arbeiten an einem GitHub-RFC, um dieses Problem zu beheben. Weitere Informationen finden Sie unter [Propagate execution preferences beyond script module scope][RFC] (Weitergeben von Ausführungseinstellungen über den Gültigkeitsbereich des Skriptmoduls hinaus).

## <a name="in-closing"></a>Abschluss

Ich muss jedes Mal nachschlagen, wie ich `ShouldProcess` verwende. Ich habe lange gebraucht, um `ShouldProcess` von `ShouldContinue` zu unterscheiden. Ich muss fast immer nachschlagen, welche Parameter ich verwenden darf. Machen Sie sich also keine Sorgen, wenn Sie gelegentlich noch etwas verwirrt sind. Sie können diesen Artikel bei Bedarf jederzeit hier lesen. Ich bin mir sicher, dass ich ihn selbst häufig zu Rate ziehen werde.

Wenn Ihnen dieser Beitrag gefallen hat, können Sie mir Ihre Meinung auf Twitter über den untenstehenden Link mitteilen. Ich höre immer gerne von Menschen, für die meine Inhalte hilfreich sind.

<!-- link references -->
[Originalversion]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Allgemeine Parameter]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[Alles, was Sie schon immer über Hashtabellen wissen wollten]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
