---
title: Functions
description: Mit PowerShell-Funktionen können Sie Tools erstellen, die in Skripts wiederverwendet werden können.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ca48f3020fa306f8a24328bd18648d5954c48a94
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438201"
---
# <a name="chapter-9---functions"></a>Kapitel 9: Funktionen

Wenn Sie PowerShell-Einzeiler oder -Skripts schreiben und diese häufig für verschiedene Szenarien ändern müssen, besteht die Möglichkeit, dass es sich dabei um einen guten Kandidaten handelt, um in eine Funktion umgewandelt zu werden, die wiederverwendet werden kann.

Wann immer es möglich ist, ziehe ich es vor, Funktionen zu schreiben, da Sie wesentlich toolorientierter sind. Ich kann die Funktionen in einem Skriptmodul ablegen, dieses Modul in `$env:PSModulePath` platzieren und die Funktionen aufrufen, ohne physisch ihren Speicherort auffinden zu müssen. Mithilfe des PowerShellGet-Moduls lassen sich diese Module ganz einfach in einem NuGet-Repository freigeben. „PowerShellGet“ ist im Lieferumfang von PowerShell, Version 5.0 und höher, enthalten. Es steht als getrennter Download für PowerShell, Version 3.0 und höher, zur Verfügung.

Machen Sie Dinge nicht komplizierter, als sie sind. Halten Sie es einfach, und verwenden Sie die direkteste Methode zum Ausführen einer Aufgabe. Vermeiden Sie Aliase und Positionsparameter in Code, den Sie wiederverwenden möchten. Formatieren Sie Ihren Code für bessere Lesbarkeit. Keine Hartcodierung von Parametern, verwenden Sie Parameter und Variablen. Schreiben Sie keinen unnötigen Code, auch nicht, wenn dadurch nichts beeinträchtigt wird. Es erhöht die Komplexität unnötigerweise. Details sind beim Schreiben von PowerShell-Code von großer Bedeutung.

## <a name="naming"></a>Benennung

Wenn Sie Ihre Funktionen in PowerShell benennen, verwenden Sie einen [Pascal-Schreibweise][]-Namen mit einem genehmigten Verb und einem Nomen im Singular. Ich empfehle außerdem, dem Nomen ein Präfix voranzustellen. Beispiel: `<ApprovedVerb>-<Prefix><SingularNoun>`.

In PowerShell gibt es eine spezifische Liste mit genehmigten Verben, die Sie durch Ausführen von `Get-Verb` abrufen können.

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

Im vorherigen Beispiel habe ich die Ergebnisse nach der Spalte **Verb** sortiert. Die Spalte **Gruppe** vermittelt Ihnen eine Idee davon, wie diese Verben verwendet werden. Es ist wichtig, ein genehmigtes Verb in PowerShell auszuwählen, wenn Funktionen zu einem Modul hinzugefügt werden. Das Modul generiert eine Warnmeldung zur Ladezeit, wenn Sie ein nicht genehmigtes Verb auswählen. Eine solche Warnmeldung lässt ihre Funktionen unprofessionell aussehen. Nicht genehmigte Verben schränken außerdem die Auffindbarkeit ihrer Funktionen ein.

## <a name="a-simple-function"></a>Eine einfache Funktion

Eine Funktion in PowerShell wird mit dem Schlüsselwort „function“, gefolgt vom Funktionsnamen und einer geöffneten und einer schließenden geschweiften Klammer, deklariert. Der Code, der von der Funktion ausgeführt wird, steht in diesen geschweiften Klammern.

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

Die gezeigte Funktion ist ein einfaches Beispiel, das die Version von PowerShell zurückgibt.

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Es besteht eine hohe Wahrscheinlichkeit, dass Namenskonflikte mit ähnlich wie `Get-Version` benamten Funktionen, Standardbefehlen in PowerShell und Befehlen, die andere Benutzer möglicherweise schreiben, auftreten können. Aus diesem Grund empfehle ich, dem Nomen-Teil Ihrer Funktionen ein Präfix voranzustellen, um Namenskonflikten vorzubeugen. Im folgenden Beispiel verwende ich das Präfix „PS“.

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

Mit Ausnahme des Namens ist diese Funktion mit der vorherigen identisch.

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Selbst wenn Sie dem Nomen ein Präfix wie „PS“ voranstellen, besteht immer noch eine hohe Wahrscheinlichkeit, dass ein Namenskonflikt auftritt. Ich stelle meinen Funktions-Nomen normalerweise meine Initialen als Präfix voran. Entwickeln Sie einen Standard, und halten Sie ihn ein.

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

Diese Funktion unterscheidet sich von den beiden vorhergehenden nur durch die Verwendung eines sinnvolleren Namens, um Namenskonflikte mit anderen PowerShell-Befehlen zu vermeiden.

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

Nachdem Sie in den Arbeitsspeicher geladen wurde, können Sie Funktionen auf dem PSDrive **Function** sehen.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

Wenn Sie diese Funktionen aus Ihrer aktuellen Sitzung entfernen möchten, müssen Sie sie aus dem PSDrive **Function** entfernen oder PowerShell schließen und neu öffnen.

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

Vergewissern Sie sich, dass die Funktionen tatsächlich entfernt wurden.

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

Wenn die Funktionen als Teil eines Moduls geladen wurden, kann das Modul entladen werden, um sie zu entfernen.

```powershell
Remove-Module -Name <ModuleName>
```

Das Cmdlet `Remove-Module` entfernt Module aus dem Arbeitsspeicher in Ihrer aktuellen PowerShell-Sitzung, entfernt sie aber nicht von Ihrem System oder vom Datenträger.

## <a name="parameters"></a>Parameter

Weisen Sie keine Werte statisch zu! Verwenden Sie Parameter und Variablen. Wenn Sie Ihre Parameter benennen möchten, verwenden Sie dieselben Namen wie die Standard-Cmdlets für Ihre Parameternamen, wann immer dies möglich ist.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Warum habe ich **ComputerName** und nicht **Computer**, **ServerName**oder **Host** als meinen Parameternamen verwendet? Das liegt daran, dass meine Funktion so standardisiert wie die Standard-Cmdlets sein sollte.

Ich erstelle eine Funktion, um alle Befehle in einem System abzufragen und die Anzahl der Befehle zurückzugeben, die über bestimmte Parameternamen verfügen.

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

Wie Sie in den unten gezeigten Ergebnissen sehen können, besitzen 39 Befehle einen Parameter **ComputerName**. Es gibt keine Cmdlets, die Parameter wie **Computer**, **ServerName**, **Host**oder **Machine** haben.

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

Ich empfehle außerdem, dieselbe Groß-/Kleinschreibung für Ihre Parameternamen wie bei den Standard-Cmdlets zu verwenden. Verwenden Sie `ComputerName`, nicht `computername`. Dadurch sehen ihre Funktionen wie die Standard-Cmdlets aus und verhalten sich auch so. Personen, die bereits mit PowerShell vertraut sind, werden sich sofort wohlfühlen.

## <a name="advanced-functions"></a>Erweiterte Funktionen

Eine Funktion in PowerShell in eine erweiterte Funktion umzuwandeln, ist wirklich einfach. Einer der Unterschiede zwischen einer Funktion und einer erweiterten Funktion besteht darin, dass erweiterte Funktionen über eine Reihe allgemeiner Parameter verfügen, die der Funktion automatisch hinzugefügt werden. Zu diesen allgemeinen Parametern zählen Parameter wie **Verbose** und **Debug**.

Ich beginne mit der `Test-MrParameter`-Funktion, die im vorherigen Abschnitt verwendet wurde.

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Beachten Sie hierbei, dass die `Test-MrParameter`-Funktion keine allgemeinen Parameter besitzt. Es gibt eine Reihe unterschiedlicher Möglichkeiten, um die allgemeinen Parameter anzuzeigen. Eine besteht darin, die Syntax mithilfe von `Get-Command` anzuzeigen.

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

Eine andere besteht darin, mit `Get-Command` Detailinformationen zu den Parametern anzuzeigen.

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

Fügen Sie `CmdletBinding` hinzu, um die Funktion in eine erweiterte Funktion umzuwandeln.

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Beim Hinzufügen von `CmdletBinding` werden die allgemeinen Parameter automatisch hinzugefügt. `CmdletBinding` erfordert einen `param`-Block, doch dieser `param`-Block kann leer sein.

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

Beim Anzeigen von Detailinformationen zu den Parametern mithilfe von `Get-Command` werden die tatsächlichen Parameternamen angezeigt, einschließlich der allgemeinen Parameternamen.

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

`SupportsShouldProcess` fügt die Parameter **WhatIf** und **Confirm** hinzu. Diese werden nur für Befehle benötigt, die Änderungen vornehmen.

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

Beachten Sie, dass nun die Parameter **WhatIf** und **Confirm** vorhanden sind.

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

Auch hier können Sie mit `Get-Command` eine Liste der tatsächlichen Parameternamen zurückgeben, einschließlich der allgemeinen Parameternamen zusammen mit „WhatIf“ und „Confirm“.

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a>Parameterüberprüfung

Überprüfen Sie Eingaben frühzeitig. Warum sollten Sie die Fortsetzung Ihres Codes auf einem Pfad zulassen, wenn er nicht ohne gültige Eingaben ausgeführt werden kann?

Geben Sie immer die Variablen ein, die für Ihre Parameter verwendet werden (geben Sie einen Datentyp an).

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

Im vorherigen Beispiel habe ich **String** als Datentyp für den Parameter **ComputerName** angegeben. Dies bewirkt, dass nur ein einzelner Computername angegeben werden kann. Wird mehr als ein Computername über eine durch Trennzeichen getrennte Liste angegeben, wird ein Fehler generiert.

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

Das Problem bei der aktuellen Definition besteht darin, dass es zulässig ist, den Wert des Parameters **ComputerName** auszulassen, wobei aber ein Wert erforderlich ist, damit die Funktion erfolgreich abgeschlossen werden kann. An dieser Stelle ist das Parameterattribut `Mandatory` äußerst praktisch.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

Die im vorherigen Beispiel verwendete Syntax ist kompatibel mit PowerShell, Version 3.0 und höher.
`[Parameter(Mandatory=$true)]` könnte stattdessen angegeben werden, um die Funktion mit PowerShell, Version 2.0 und höher, kompatibel zu machen. Nachdem der **ComputerName** nun erforderlich ist, fordert die Funktion zu seiner Eingabe auf, wenn keiner angegeben ist.

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

Wenn Sie mehr als einen Wert für den Parameter **ComputerName** zulassen möchten, verwenden Sie den Datentyp **String**, aber fügen Sie dem Datentyp öffnende und schließende eckige Klammern hinzu, um ein Array von Zeichenfolgen zu ermöglichen.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

Möglicherweise möchten Sie einen Standardwert für den Parameter **ComputerName** angeben, wenn kein Wert angegeben wird.
Das Problem hierbei ist, dass Standardwerte nicht mit obligatorischen Parametern verwendet werden können. Stattdessen müssen Sie das Parameterüberprüfungsattribut `ValidateNotNullOrEmpty` mit einem Standardwert verwenden.

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

Selbst wenn Sie einen Standardwert festlegen, versuchen Sie, keine statischen Werte zu verwenden. Im vorherigen Beispiel wird `$env:COMPUTERNAME` als Standardwert verwendet, der automatisch in den Namen des lokalen Computers übersetzt wird, wenn kein Wert angegeben ist.

## <a name="verbose-output"></a>Ausführliche Ausgabe (Verbose)

Inlinekommentare sind zwar nützlich, insbesondere, wenn Sie komplexen Code schreiben, doch der Benutzer bekommt sie nur zu Gesicht, wenn er sich den Code ansieht.

Die im folgenden Beispiel gezeigte Funktion hat einen Inlinekommentar in der `foreach`-Schleife. Dieser spezielle Kommentar mag nicht schwer aufzufinden sein, doch stellen Sie sich vor, dass die Funktion Hunderte von Codezeilen enthielte.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

Eine bessere Option ist die Verwendung von `Write-Verbose` anstelle von Inlinekommentaren.

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

Wenn die Funktion ohne den Parameter **Verbose** aufgerufen wird, wird die ausführliche Ausgabe nicht angezeigt.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

Wenn sie mit dem Parameter **Verbose** aufgerufen wird, wird die ausführliche Ausgabe angezeigt.

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a>Pipelineeingabe

Wenn Sie möchten, dass ihre Funktion Pipelineeingaben akzeptiert, ist ein wenig zusätzliche Programmierung erforderlich. Wie bereits in diesem Buch erwähnt, können Befehle Pipelineeingaben **als Wert** (als Typ) oder **als Eigenschaftsname** akzeptieren. Sie können ihre Funktionen genau wie die nativen Befehle schreiben, sodass Sie entweder einen oder beide dieser Eingabetypen akzeptieren.

Um die Pipelineeingabe **als Wert**zu akzeptieren, geben Sie das Parameterattribut `ValueFromPipeline` für diesen bestimmten Parameter an. Denken Sie daran, dass Sie Pipelineeingaben **als Wert** nur von einem des jeweiligen Datentyps akzeptieren können. Wenn Sie beispielsweise über zwei Parameter verfügen, die Zeichenfolgeneingaben (string) akzeptieren, kann nur einer davon Pipelineeingaben **als Wert** akzeptieren, denn wenn Sie dies für beide Zeichenfolgenparameter angeben würden, wüsste die Pipelineeingabe nicht, an welchen sie sich binden sollte. Dies ist ein weiterer Grund, warum ich diese Art von Pipelineeingabe _als Typ_ anstelle von **als Wert** bezeichne.

Pipelineeingaben gelangen gleichzeitig immer nur in ein Element, ähnlich der Art und Weise, wie Elemente in einer `foreach`-Schleife behandelt werden.
Es ist mindestens ein `process`-Block erforderlich, um jedes dieser Elemente zu verarbeiten, wenn Sie ein Array als Eingabe akzeptieren. Wenn Sie nur einen einzelnen Wert als Eingabe akzeptieren, ist ein `process`-Block nicht erforderlich, aber ich empfehle dennoch, ihn aus Gründen der Konsistenz anzugeben.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

Das akzeptieren von Pipelineeingaben **als Eigenschaftsname** ist ähnlich, außer dass es mit dem Parameterattribut `ValueFromPipelineByPropertyName` angegeben wird und für eine beliebige Anzahl von Parametern, unabhängig vom Datentyp, angegeben werden kann. Der Schlüssel besteht darin, dass die Ausgabe des Befehls, der per Pipeline als Eingabe weitergeleitet wird, einen Eigenschaftsnamen besitzen muss, der mit dem Namen des Parameters oder einem Parameteralias Ihrer Funktion übereinstimmt.

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

`BEGIN`- und `END`-Blöcke sind optional. `BEGIN` würde vor dem `PROCESS`-Block angegeben und wird verwendet, um alle anfänglichen Arbeiten durchzuführen, bevor die Elemente von der Pipeline empfangen werden. Es ist wichtig, dies zu verstehen. Auf Werte, die per Pipeline als Eingabe weitergeleitet werden, kann im `BEGIN`-Block nicht zugegriffen werden. Der `END`-Block würde hinter dem `PROCESS`-Block angegeben und für die Bereinigung verwendet, nachdem alle Elemente, die per Pipeline als Eingabe weitergeleitet werden, verarbeitet wurden.

## <a name="error-handling"></a>Fehlerbehandlung

Die im folgenden Beispiel gezeigte Funktion generiert eine nicht behandelte Ausnahme, wenn ein Computer nicht kontaktiert werden kann.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

Es gibt eine Reihe unterschiedlicher Methoden, um Fehler in PowerShell zu behandeln. `Try/Catch` ist die modernere Methode zum Behandeln von Fehlern.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Obwohl die im vorherigen Beispiel gezeigte Funktion Fehlerbehandlung verwendet, generiert sie auch eine nicht behandelte Ausnahme, weil der Befehl keinen Fehler mit Abbruch generiert. Dies zu verstehen, ist ebenfalls wichtig. Nur Fehler mit Abbruch können abgefangen werden. Geben Sie den Parameter **ErrorAction** mit **Stop** als Wert an, um einen Fehler ohne Abbruch in einen mit Abbruch zu verwandeln.

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

Ändern Sie die globale Variable `$ErrorActionPreference` nur, wenn dies unbedingt erforderlich ist. Wenn Sie etwas wie .NET direkt aus ihrer PowerShell-Funktion heraus verwenden, können Sie die **ErrorAction** nicht mit dem Befehl selbst angeben. In diesem Szenario müssen Sie möglicherweise die globale Variable `$ErrorActionPreference` ändern, aber wenn Sie sie ändern, ändern Sie sie sofort nach dem Testen des Befehls wieder zurück.

## <a name="comment-based-help"></a>Kommentarbasierte Hilfe

Es gilt als bewährte Methode, Ihren Funktionen kommentarbasierte Hilfe hinzuzufügen, damit die Personen, mit denen Sie sie teilen, wissen, wie Sie sie verwenden können.

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

Wenn Sie Ihren Funktionen kommentarbasierte Hilfe hinzufügen, lässt sich die Hilfe zu ihnen genau wie für die integrierten Standardbefehle abrufen.

Die Gesamtheit der Syntax zum Schreiben einer Funktion in PowerShell kann überwältigend erscheinen, besonders für jemanden, der gerade erst damit begonnen hat. Wenn ich mich nicht mehr an die Syntax für etwas erinnern kann, öffne ich häufig eine zweite Kopie der ISE auf einem gesonderten Monitor und zeige bei der Eingabe des Codes für meine Funktion den Codeausschnitt „Cmdlet (erweiterte Funktion) – Vollständig“ an. Auf Codeausschnitte können Sie in der PowerShell ISE mithilfe der Tastenkombination <kbd>STRG</kbd>+<kbd>J</kbd> zugreifen.

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie die Grundlagen zum Schreiben von Funktionen in PowerShell kennen gelernt, außerdem, wie Sie eine Funktion in eine erweiterte Funktion umwandeln, sowie einige der wichtigeren Elemente, die Sie beim Schreiben von PowerShell-Funktionen berücksichtigen sollten wie Parameterüberprüfung, ausführliche Ausgabe, Pipelineeingabe, Fehlerbehandlung und kommentarbasierte Hilfe.

## <a name="review"></a>Überprüfung

1. Wie erhalten Sie eine Liste der genehmigten Verben in PowerShell?
1. Wie wandeln Sie eine PowerShell-Funktion in eine erweiterte Funktion um?
1. Wann sollten die Parameter **WhatIf** und **Confirm** Ihren PowerShell-Funktionen hinzugefügt werden?
1. Wie wandeln Sie einen Fehler ohne Abbruch in einen Fehler mit Abbruch um?
1. Warum sollten Sie Ihren Funktionen eine kommentarbasierte Hilfe hinzufügen?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [about_Functions][]
- [about_Functions_Advanced_Parameters][]
- [about_CommonParameters][]
- [about_Functions_CmdletBindingAttribute][]
- [about_Functions_Advanced][]
- [about_Try_Catch_Finally][]
- [about_Comment_Based_Help][]
- [Video: PowerShell-Toolerstellung mit erweiterten Funktionen und Skriptmodulen][]

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Video: PowerShell-Toolerstellung mit erweiterten Funktionen und Skriptmodulen]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [Pascal-Schreibweise]: /dotnet/standard/design-guidelines/capitalization-conventionss
