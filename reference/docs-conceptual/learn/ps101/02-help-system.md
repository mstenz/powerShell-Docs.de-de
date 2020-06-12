---
title: Das Hilfesystem
description: Das Beherrschen des Hilfesystems ist der Schlüssel zum Erfolg mit der PowerShell.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 43d2de7e1f59ce5e980c192decb5309d3f6d0ff8
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438111"
---
# <a name="chapter-2---the-help-system"></a>Kapitel 2: Das Hilfesystem

Zwei Gruppen von IT-Profis wurden ohne Zugriff auf einen Computer einem schriftlichen Test unterzogen, um Ihre Fähigkeiten hinsichtlich der PowerShell zu ermitteln. PowerShell-Einsteiger wurden in die eine Gruppe und Experten in die andere Gruppe eingeteilt.
Basierend auf den Testergebnissen schien kein großer Unterschied bei den Kenntnissen zwischen beiden Gruppen zu bestehen. Beide Gruppen erhielten einen zweiten Test, ähnlich dem ersten. Diesmal erhielten sie allerdings Zugriff auf einen Computer mit PowerShell ohne Internetzugang. Das Ergebnis des zweiten Tests zeigte einen großen Unterschied bei den Kenntnissen zwischen beiden Gruppen. Experten kennen nicht immer die Antworten, aber sie wissen, wie Sie die an die Antworten kommen können.

Worin bestand der Unterschied bei den Ergebnissen des ersten und zweiten Tests zwischen diesen beiden Gruppen?

Die in diesen beiden Tests beobachteten Unterschiede lagen darin, dass Experten sich nicht merken, wie Tausende von Befehlen in PowerShell verwendet werden. Sie lernen, wie Sie das Hilfesystem in PowerShell optimal verwenden.
Dies ermöglicht es Ihnen, bei Bedarf die erforderlichen Befehle zuerst zu finden und dann, nachdem Sie sie gefunden haben, ihre Verwendung zu ermitteln.

Ich habe Jeffrey Snover, den Erfinder der PowerShell, mehrmals eine ähnliche Geschichte erzählen gehört.

Das Beherrschen des Hilfesystems ist der Schlüssel zum Erfolg mit der PowerShell.

## <a name="discoverability"></a>Erkennbarkeit

Kompilierte Befehle in PowerShell werden als „Cmdlets“ bezeichnet. Cmdlet wird wie „Command-let“ (nicht CMD-let) ausgesprochen. Namen von Cmdlets weisen die Form von „Verb-Nomen“-Befehlen im Singular auf, damit Sie leicht auffindbar sind. Beispielsweise ist das Cmdlet zur Bestimmung, welche Prozesse ausgeführt werden, `Get-Process`, und das Cmdlet zum Abrufen einer Liste von Diensten und deren Status ist `Get-Service`. Es gibt andere Arten von Befehlen in PowerShell, wie z. B. Aliase und Funktionen, die später in diesem Buch behandelt werden. Der Begriff „PowerShell-Befehl“ ist ein allgemeiner Begriff, der häufig verwendet wird, um auf einen beliebigen Befehlstyp in PowerShell zu verweisen, unabhängig davon, ob es sich um ein Cmdlet, eine Funktion oder einen Alias handelt.

## <a name="the-three-core-cmdlets-in-powershell"></a>Die drei wesentlichen Cmdlets in PowerShell

- `Get-Command`
- `Get-Help`
- `Get-Member` (wird in Kapitel 3 behandelt)

Eine Frage, die mir häufig gestellt wird, ist, wie man herausfindet, was die Befehle in PowerShell sind? Sowohl `Get-Command` als auch `Get-Help` kann verwendet werden, um die Befehle zu ermitteln.

## <a name="get-help"></a>Get-Help

`Get-Help` ist ein multifunktionaler Befehl. `Get-Help` hilft Ihnen, zu erfahren, wie Befehle verwendet werden, nachdem Sie sie gefunden haben. `Get-Help` kann auch verwendet werden, um Befehle zu finden, funktioniert aber auf eine andere und eher indirekte Weise im Vergleich zu `Get-Command`.

Wenn `Get-Help` zum Suchen von Befehlen verwendet wird, sucht es zuerst nach Platzhalterübereinstimmungen von Befehlsnamen, basierend auf der bereitgestellten Eingabe. Wenn keine Entsprechung gefunden wird, werden die Hilfethemen selbst durchsucht, und wenn keine Übereinstimmung gefunden wird, wird ein Fehler zurückgegeben. Im Gegensatz zur weit verbreiteten Ansicht kann `Get-Help` verwendet werden, um Befehle zu suchen, zu denen es keine Hilfethemen gibt.

Das Erste, was Sie über das Hilfesystem in PowerShell wissen müssen, ist, wie Sie das Cmdlet `Get-Help` verwenden. Der folgende Befehl wird verwendet, um das Hilfethema für `Get-Help` anzuzeigen.

```powershell
Get-Help -Name Get-Help
```

```Outpout
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

Seit PowerShell, Version 3, wird die PowerShell-Hilfe nicht mehr zusammen mit dem Betriebssystem ausgeliefert. Wenn Sie `Get-Help` zum ersten Mal für einen Befehl ausführen, wird die vorherige Meldung angezeigt. Wenn anstelle des Cmdlets `Get-Help` die Funktion `help` oder der Alias `man` verwendet wird, erhalten Sie diese Eingabeaufforderung nicht.

Wenn Sie mithilfe von <kbd>Y</kbd> (Yes) mit „Ja“ antworten, wird das Cmdlet `Update-Help` ausgeführt, für das standardmäßig Internetzugriff erforderlich ist. `Y` kann als Groß- oder Kleinbuchstabe angegeben werden.

Nachdem die Hilfe heruntergeladen und das Update fertiggestellt wurde, wird das Hilfethema für den angegebenen Befehl zurückgegeben:

```powershell
Get-Help -Name Get-Help
```

Nehmen Sie sich einen Moment Zeit, um dieses Beispiel auf Ihrem Computer auszuführen, sehen Sie sich die Ausgabe an, und beachten Sie, wie die Informationen gruppiert sind:

- NAME
- ZUSAMMENFASSUNG
- SYNTAX
- DESCRIPTION
- VERWANDTE LINKS
- ANMERKUNGEN

Wie Sie sehen können, können Hilfethemen eine große Menge an Informationen enthalten, und das ist noch nicht einmal das gesamte Hilfethema.

Ein Parameter, wenn auch nicht spezifisch für PowerShell, ist eine Möglichkeit, um Eingaben an einen Befehl zu übergeben. `Get-Help` verfügt über zahlreiche Parameter, die angegeben werden können, um das gesamte Hilfethema oder nur einen Teil davon zurückzugeben.

Im Abschnitt „Syntax“ des Hilfethemas, das im vorherigen Resultset angezeigt wurde, werden alle Parameter für `Get-Help` aufgeführt. Auf den ersten Blick scheinen dieselben Parameter sechs Mal aufgeführt zu sein. Jeder dieser unterschiedlichen Blöcke im Abschnitt „Syntax“ ist ein Parametersatz. Dies bedeutet, dass das Cmdlet `Get-Help` sechs verschiedene Parametersätze aufweist. Wenn Sie sich diese näher ansehen, werden Sie feststellen, dass in jedem der Parametersätze mindestens ein Parameter unterschiedlich ist.

Parametersätze schließen sich gegenseitig aus. Sobald ein eindeutiger Parameter verwendet wird, der nur in einem der Parametersätze vorhanden ist, können nur die Parameter verwendet werden, die in diesem Parametersatz enthalten sind. Beispielsweise könnten die Parameter **Full** und **Detailed** nicht gleichzeitig angegeben werden, weil sie sich in verschiedenen Parametersätzen befinden.

Jeder der folgenden Parameter befindet sich in einem anderen Parametersatz:

- Vollständig
- Detailliert
- Beispiele
- Online
- Parameter
- ShowWindow

Alle kryptischen Teile der Syntax, z. B. eckige und spitze Klammern, im Abschnitt „Syntax“ haben eine Bedeutung, und werden in Anhang A dieses Buchs behandelt. Zwar ist das Erlernen der Bedeutung der kryptischen Syntax wichtig, doch fällt es Einsteigern bei PowerShell, die sie möglicherweise auch nicht täglich verwenden, häufig schwer, sich dies zu merken.

Weitere Informationen zum besseren Verständnis der kryptischen Syntax finden Sie in [Anhang A][].

Für Einsteiger gibt es eine einfachere Möglichkeit, um an dieselben Informationen zu kommen, nur dass sie in normaler Sprache verfasst sind.

Wenn der Parameter **Full** für `Get-Help` angegeben wird, wird das gesamte Hilfethema zurückgegeben.

```powershell
Get-Help -Name Get-Help -Full
```

Nehmen Sie sich einen Moment Zeit, um dieses Beispiel auf Ihrem Computer auszuführen, sehen Sie sich die Ausgabe an, und beachten Sie, wie die Informationen gruppiert sind:

- NAME
- ZUSAMMENFASSUNG
- SYNTAX
- DESCRIPTION
- PARAMETERS
- EINGABEN
- AUSGABEN
- HINWEISE
- BEISPIELE
- VERWANDTE LINKS

Beachten Sie, dass durch die Verwendung des Parameters **Full** mehrere zusätzliche Abschnitte zurückgegeben wurden, von denen einer der Abschnitt „PARAMETER“ ist, der mehr Informationen als der kryptisch Abschnitt „SYNTAX“ bereitstellt.

Der Parameter **Full** ist ein Switch-Parameter (Schalter). Ein Parameter, der keinen Wert erfordert, wird als Switch-Parameter bezeichnet. Wenn ein Switch-Parameter angegeben wird, ist sein Wert „true“, und er nicht angegeben wird, ist sein Wert „false“.

Wenn Sie dieses Kapitel in der PowerShell-Konsole durchgearbeitet haben, haben Sie bemerkt, dass der vorherige Befehl zum Anzeigen des vollständigen Hilfethemas für `Get-Help` auf dem Bildschirm durchgelaufen ist, ohne dass Sie die Möglichkeit hatten, es zu lesen. Es gibt eine bessere Möglichkeit.

`Help` ist eine Funktion, die `Get-Help` per Pipeline an eine Funktion namens `more` weiterleitet, bei der es sich um einen Wrapper für die ausführbare Datei `more.com` in Windows handelt. In der PowerShell-Konsole stellt `help` immer eine Seite der Hilfe zur Verfügung. In der ISE funktioniert der Befehl auf dieselbe Weise wie `Get-Help`. Meine Empfehlung ist es, die `help`-Funktion anstelle des `Get-Help`-Cmdlets zu verwenden, da sie eine bessere Erfahrung bietet, die Eingabe kürzer ist.

Kürzere Eingaben sind jedoch nicht immer eine gute Sache. Wenn Sie Ihre Befehle als Skript speichern oder mit einer anderen Person teilen möchten, achten Sie darauf, dass Sie die vollständigen Cmdlet- und Parameternamen verwenden. Die vollständigen Namen sind selbstdokumentierend, wodurch sie leichter verständlich werden. Denken Sie an die nächste Person, die Ihre Befehle lesen und verstehen muss. Das könnten Sie sein. Ihre Kollegen und Ihr zukünftiges Ich werden es Ihnen danken.

Versuchen Sie, die folgenden Befehle in der PowerShell-Konsole auf Ihrem Computer in der Windows 10-Laborumgebung auszuführen.

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

Haben Sie Unterschiede in der Ausgabe zu den zuvor aufgeführten Befehle bemerkt, als Sie diese auf Ihrem Computer in der Windows 10-Laborumgebung ausgeführt haben?

Es gibt keine Unterschiede, außer dass die letzten beiden Optionen die Ergebnisse seitenweise zurückgeben.
Die <kbd>Leertaste</kbd> wird zum Anzeigen der nächsten Inhaltsseite verwendet, wenn die `Help`-Funktion verwendet wird, und mit <kbd>STRG</kbd>+<kbd>C</kbd> werden Befehle abgebrochen, die in der PowerShell-Konsole ausgeführt werden.

Im ersten Beispiel wird das Cmdlet `Get-Help` verwendet, im zweiten wird die Funktion `Help` verwendet, und im dritten wird der Parameter **Name** bei Verwendung der Funktion `Help` ausgelassen. **Name** ist ein Positionsparameter und wird in diesem Beispiel positionell verwendet. Dies bedeutet, dass der Wert ohne Angabe des Parameternamens angegeben werden kann, solange der Wert selbst an der korrekten Position angegeben wird. Woher weiß ich, an welcher Position der Wert festgelegt werden muss? Indem Sie die Hilfe lesen, wie im folgenden Beispiel gezeigt.

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

Beachten Sie, dass im vorherigen Beispiel der Parameter **Parameter** mit der Help-Funktion verwendet wurde, um nur Informationen aus dem Hilfethema für den Parameter **Name** zurückzugeben. Dies ist sehr viel bündiger, als manuell durchzusehen, was manchmal wie ein hundertseitiges Hilfethema aussieht.

Basierend auf diesen Ergebnissen können Sie feststellen, dass der Parameter **Name** positionell ist und an Position Null (der ersten Position) angegeben werden muss, wenn er positionell verwendet wird. Die Reihenfolge, in der Parameter angegeben werden, spielt keine Rolle, wenn der Parametername angegeben wird.

Eine weitere wichtige Information ist, dass der Parameter **Name** erwartet, dass der Datentyp für seinen Wert eine einzelne Zeichenfolge ist, die durch `<String>` gekennzeichnet wird. Wenn mehrere Zeichenfolgen akzeptiert würden, würde der Datentyp als `<String[]>` aufgeführt.

Manchmal möchten Sie einfach nicht das gesamte Hilfethema für einen Befehl anzeigen. Neben **Full** gibt es eine Reihe weiterer Parameter, die mit `Get-Help` oder `Help` angegeben werden können. Versuchen Sie, die folgenden Befehle auf Ihrem Computer in der Windows 10-Laborumgebung auszuführen:

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

In der Regel verwende ich `help <command name>` mit dem Parameter **Full** oder **Online**. Wenn ich nur an den Beispielen interessiert bin, verwende ich den Parameter **Examples**, und wenn ich nur an einem bestimmten Parameter interessiert bin, verwende ich den Parameter **Parameter**. Der Parameter **ShowWindow** öffnet das Hilfethema in einem separaten, durchsuchbaren Fenster, das auf einem anderen Monitor angezeigt werden kann, wenn Sie über mehrere Monitore verfügen. Ich habe den Parameter **ShowWindow** vermieden, weil es einen bekannten Fehler gibt, durch den nicht das gesamte Hilfethema angezeigt wird.

Wenn Sie Hilfe in einem separaten Fenster anzeigen möchten, empfehle ich Ihnen, entweder den Parameter **Online** oder den Parameter **Full** zu verwenden und die Ergebnisse per Pipeline an `Out-GridView` weiterzuleiten, wie im folgenden Beispiel gezeigt.

```powershell
help Get-Command -Full | Out-GridView
```

Sowohl das Cmdlet `Out-GridView` als auch der Parameter **ShowWindow** des Cmdlets `Get-Help` erfordert ein Betriebssystem mit grafischer Benutzeroberfläche (GUI). Sie generieren eine Fehlermeldung, wenn Sie versuchen, eins davon unter Windows Server zu verwenden, das mit der Installationsoption „Server Core“ (ohne GUI) installiert wurde.

Wenn Sie `Get-Help` verwenden möchten, um Befehle zu suchen, verwenden Sie das Sternchen-Platzhalterzeichen (`*`) mit dem Parameter **Name**. Geben Sie einen Begriff, mit dem Sie nach Befehlen suchen, als Wert für den Parameter **Name**an, wie im folgenden Beispiel gezeigt.

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

Im vorherigen Beispiel sind die `*`-Platzhalterzeichen nicht erforderlich, und wenn Sie sie auslassen, erhalten Sie dasselbe Ergebnis. `Get-Help` fügt die Platzhalterzeichen automatisch im Hintergrund hinzu.

```powershell
help process
```

Der vorherige Befehl erzeugt dieselben Ergebnisse wie durch das Angeben des `*`-Platzhalterzeichens an jedem Ende des Prozesses.

Ich ziehe es vor, sie hinzuzufügen, da dies die Option ist, die immer konsistent funktioniert. Andernfalls sind sie in bestimmten Szenarien erforderlich und in anderen nicht. Sobald Sie ein Platzhalterzeichen in der Mitte des Werts hinzufügen, werden diese nicht mehr automatisch im Hintergrund dem von Ihnen angegebenen Wert hinzugefügt.

```powershell
help pr*cess
```

Von diesem Befehl werden keine Ergebnisse zurückgegeben, es sei denn, das `*`-Platzhalterzeichen wird am Anfang, am Ende oder sowohl am Anfang als auch am Ende von `pr*cess` hinzugefügt.

Wenn der angegebene Wert mit einem Bindestrich beginnt, wird ein Fehler generiert, da er von PowerShell als Parametername interpretiert wird und für das Cmdlet `Get-Help` kein solcher Parametername vorhanden ist.

```powershell
help -process
```

Wenn Sie versuchen, nach Befehlen zu suchen, die auf `-process` enden, müssen Sie das `*`-Platzhalterzeichen nur am Anfang des Werts hinzufügen.

```powershell
help *-process
```

Bei der Suche nach PowerShell-Befehlen mit `Get-Help` sollten Sie bei dem Gesuchten stattdessen etwas ungenauer sein, anstatt zu spezifisch.

Früher wurden bei der Suche nach `process` nur Befehle gefunden, die `process` im Namen des Befehls enthielten, sodass nur diese als Ergebnisse zurückgegeben wurden. Wenn `Get-Help` für die Suche nach `processes` verwendet wird, werden keine Übereinstimmungen für Befehlsnamen gefunden. Daher wird eine Suche in allen Hilfethemen in PowerShell auf Ihrem System durchgeführt, und alle gefundenen Übereinstimmungen werden zurückgegeben. Dadurch wird eine enorme Anzahl von Ergebnissen zurückgegeben.

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

Die Verwendung von `Help` für die Suche nach `process` hat 10 Ergebnisse zurückgegeben, und die Verwendung zur Suche nach `processes` hat 68 Ergebnisse zurückgegeben. Wenn nur ein Ergebnis gefunden wird, wird das Hilfethema selbst anstelle einer Liste von Befehlen angezeigt.

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

Doch entzaubern wir nun den Mythos, dass `Help` in PowerShell nur Befehle finden kann, zu denen es Hilfethemen gibt.

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

Beachten Sie im vorherigen Beispiel, dass `more` kein Hilfethema besitzt, und dass das `Help`-System in PowerShell dennoch in der Lage war, es zu finden. Es hat nur eine Übereinstimmung gefunden und die grundlegenden Syntaxinformationen zurückgegeben, die Ihnen angezeigt werden, wenn ein Befehl kein Hilfethema besitzt.

PowerShell enthält zahlreiche konzeptionelle („About“) Hilfethemen. Der folgende Befehl kann verwendet werden, um eine Liste aller **About**-Hilfethemen in Ihrem System zurückzugeben.

```powershell
help About_*
```

Wenn Sie die Ergebnisse auf ein einzelnes „About“-Hilfethema beschränken, wird das eigentliche Hilfethema angezeigt, anstatt eine Liste zurückzugeben.

```powershell
help about_Updatable_Help
```

Das Hilfesystem in PowerShell muss aktualisiert werden, damit die **About**-Hilfethemen vorhanden sind. Wenn die anfängliche Aktualisierung des Hilfesystems auf dem Computer aus irgendeinem Grund fehlgeschlagen ist, sind die Dateien erst verfügbar, wenn das Cmdlet `Update-Help` erfolgreich ausgeführt wurde.

## <a name="get-command"></a>Get-Command

`Get-Command` ist darauf ausgelegt, Ihnen beim Auffinden von Befehlen zu helfen. Wenn Sie `Get-Command` ohne Parameter ausführen, wird eine Liste aller Befehle auf Ihrem System zurückgegeben. Das folgende Beispiel veranschaulicht die Verwendung des Cmdlets `Get-Command`, um zu bestimmen, welche Befehle für das Arbeiten mit Prozessen vorhanden sind:

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

Beachten Sie, dass im vorherigen Beispiel, in dem `Get-Command` ausgeführt wurde, der Parameter **Noun** verwendet und `Process` als Wert für den Parameter **Noun** angegeben wird. Was ist, wenn Sie nicht wüssten, wie das Cmdlet `Get-Command` verwendet wird? Sie könnten `Get-Help` verwenden, um das Hilfethema für `Get-Command` anzuzeigen.

Die Parameter **Name**, **Noun** und **Verb** akzeptieren Platzhalter. Das folgende Beispiel illustriert die Verwendung von Platzhaltern mit dem Parameter **Name**:

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

Ich bin kein großer Freund der Verwendung von Platzhaltern mit dem Parameter **Name** von `Get-Command`, da er auch ausführbare Dateien zurückgibt, die keine nativen PowerShell-Befehle sind.

Wenn Sie Platzhalterzeichen mit dem Parameter **Name** verwenden möchten, empfehle ich, die Ergebnisse mit dem Parameter **CommandType** einzuschränken.

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

Eine bessere Option ist es, den Parameter **Verb** oder **Noun** oder beide zu verwenden, da nur PowerShell-Befehle sowohl Verben als auch Nomen aufweisen.

Haben Sie einen Fehler in einem Hilfethema gefunden? Die gute Nachricht ist, dass die Hilfethemen für PowerShell mittlerweile Open Source und somit im Repository [PowerShell-Docs][] auf GitHub verfügbar sind. Denken Sie an die Community, und korrigieren Sie die fehlerhaften Informationen nicht nur für sich, sondern auch für alle anderen. Forken Sie einfach das PowerShell-Dokumentationsrepository auf GitHub, aktualisieren Sie das Hilfethema, und reichen Sie eine Pull Request ein.
Nachdem die Pull Request akzeptiert wurde, steht die korrigierte Dokumentation jedem zur Verfügung.

## <a name="updating-help"></a>Aktualisieren der Hilfe

Die lokale Kopie der PowerShell-Hilfethemen wurde zuvor aktualisiert, als zum ersten Mal Hilfe zu einem Befehl angefordert wurde. Es wird empfohlen, das Hilfesystem regelmäßig zu aktualisieren, da von Zeit zu Zeit Aktualisierungen am Hilfeinhalt vorliegen können. Das Cmdlet `Update-Help` dient der Aktualisierung der Hilfethemen.
Es benötigt standardmäßig Internetzugriff, und Sie müssen PowerShell mit erhöhten Rechten als Administrator ausführen.

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : The value of the HelpInfoUri key in the module manifest must resolve to a
container or root URL on a website where the help files are stored. The HelpInfoUri
'https://technet.microsoft.com/en-us/library/dd819413.aspx' does not resolve to a
container.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

Einige der Module haben Fehler zurückgegeben, was nicht ungewöhnlich ist. Wenn der Computer über keinen Internetzugang verfügte, könnten Sie das Cmdlet `Save-Help` auf einem anderen Computer mit Internetzugang verwenden, um die aktualisierten Hilfeinformationen zuerst auf einer Dateifreigabe in Ihrem Netzwerk zu speichern, und dann den Parameter **SourcePath** von `Update-Help` verwenden, um diesen Netzwerkspeicherort für die Hilfethemen anzugeben.

Erwägen Sie, eine geplante Aufgabe einzurichten oder Ihrem Profilskript in PowerShell eine Logik hinzuzufügen, um den Hilfeinhalt auf Ihrem Computer regelmäßig zu aktualisieren. Profilskripts werden in einem der nächsten Kapitel behandelt.

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie erfahren, wie Sie mit `Get-Help` und `Get-Command` Befehle auffinden können. Sie haben gelernt, wie Sie das Hilfesystem verwenden, um herauszufinden, wie Sie Befehle verwenden können, nachdem Sie diese gefunden haben. Sie haben außerdem gelernt, wie Sie den Inhalt der Hilfethemen aktualisieren, wenn Aktualisierungen verfügbar sind.

Meine Herausforderung an Sie besteht darin, dass Sie jeden Tag einen PowerShell-Befehl lernen sollten.

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a>Überprüfung

1. Ist der Parameter **DisplayName** von `Get-Service` positionell?
1. Wie viele Parametersätze hat das Cmdlet `Get-Process`?
1. Welche PowerShell-Befehle gibt es für das Arbeiten mit Ereignisprotokollen?
1. Wie lautet der PowerShell-Befehl, um eine Liste der PowerShell-Prozesse zurückzugeben, die auf Ihrem Computer ausgeführt werden?
1. Wie aktualisieren Sie den auf Ihrem Computer gespeicherten PowerShell-Hilfeinhalt?

## <a name="recommended-reading"></a>Empfohlene Lektüre

Wenn Sie weitere Informationen zu den in diesem Kapitel behandelten Themen wünschen, empfehle ich Ihnen, die folgenden PowerShell-Hilfethemen zu lesen.

- [Get-Help][]
- [Get-Command][]
- [Update-Help][]
- [Save-Help][]
- [about_Updatable_Help][]
- [about_Command_Syntax][]

Im nächsten Kapitel erfahren Sie mehr über das Cmdlet `Get-Member` sowie über Objekte, Eigenschaften und Methoden.

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[Anhang A]: appendix-a.md
