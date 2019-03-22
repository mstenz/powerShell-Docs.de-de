---
ms.date: 05/17/2018
keywords: powershell,core
title: Breaking Changes in PowerShell Core 6.0
ms.openlocfilehash: 975c978629f81f0f13a235c3d304e5ec03bae6d0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795690"
---
# <a name="breaking-changes-for-powershell-60"></a>Breaking Changes in PowerShell Core 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Nicht mehr verfügbare Features in PowerShell Core

### <a name="powershell-workflow"></a>PowerShell-Workflow

Der [PowerShell-Workflow][workflow] ist ein Feature in Windows PowerShell, das auf [Windows Workflow Foundation (WF)][workflow-foundation] basiert und die Erstellung von stabilen Runbooks für lang andauernde oder parallelisierte Aufgaben ermöglicht.

Da Windows Workflow Foundation in .NET Core nicht unterstützt wird, wird der PowerShell-Workflow in PowerShell Core nicht mehr unterstützt.

Zukünftig soll die native Parallelität in der PowerShell-Sprache ohne Notwendigkeit des PowerShell-Workflows ermöglicht werden.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Benutzerdefinierte Snap-Ins

[PowerShell-Snap-Ins][snapin] sind die Vorgänger von PowerShell-Modulen und sind in der PowerShell-Community nicht weit verbreitet.

Aufgrund der Komplexität der unterstützenden Snap-Ins und der zu geringen Verwendung in der Community werden benutzerdefinierte Snap-Ins in PowerShell Core nicht mehr unterstützt.

Dadurch funktionieren die Module `ActiveDirectory` und `DnsClient` unter Windows und Windows Server nicht mehr.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1-Cmdlets

Aufgrund der Komplexität der beiden unterstützenden WMI-basierten Module wurden die WMI v1-Cmdlets aus PowerShell Core entfernt:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

Es wird empfohlen, dass Sie stattdessen die CIM-Cmdlets (d.h. WMI v2) verwenden, die die gleichen Funktionen sowie neue Funktionen und eine überarbeitete Syntax bereitstellen:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

Aufgrund der Verwendung von nicht unterstützten APIs wurde `Microsoft.PowerShell.LocalAccounts` aus PowerShell Core entfernt, bis eine bessere Lösung gefunden wird.

### <a name="-counter-cmdlets"></a>`*-Counter`-Cmdlets

Aufgrund der Verwendung von nicht unterstützten APIs wurde `*-Counter` aus PowerShell Core entfernt, bis eine bessere Lösung gefunden wird.

### <a name="-eventlog-cmdlets"></a>`*-EventLog`-Cmdlets

Aufgrund der Verwendung von nicht unterstützten APIs wurde `*-EventLog` aus PowerShell Core entfernt, bis eine bessere Lösung gefunden wird. Unter Windows stehen `Get-WinEvent` und `Create-WinEvent` zum Abrufen und Erstellen von Ereignissen zur Verfügung.

## <a name="enginelanguage-changes"></a>Änderungen an der Engine bzw. Sprache

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Umbenennung von `powershell.exe` in `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Damit Benutzern eine deterministische Möglichkeit bereitgestellt werden kann, PowerShell Core unter Windows (im Gegensatz zu Windows PowerShell) aufzurufen, wurde die PowerShell Core-Binärdatei unter Windows in `pwsh.exe` und auf anderen Plattformen als Windows in `pwsh` geändert.

Der abgekürzte Name ist ebenfalls mit der Benennung von Shells in anderen Plattformen als Windows konsistent.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Fügen Sie keine Zeilenumbrüche in die Ausgabe ein (außer bei Tabellen) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Zuvor wurde die Ausgabe an die Breite der Konsole angebracht, und Zeilenumbrüche wurden zur Endbreite der Konsole hinzugefügt. Das bedeutet, dass die Ausgabe nicht wie erwartet neu formatiert wurde, wenn die Größe des Terminals geändert wurde. Diese Änderung wurde nicht auf Tabellen angewendet, da Zeilenumbrüche notwendig sind, um die Spalten auszurichten.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Überspringen der Überprüfung auf NULL-Elemente für Sammlungen mit einem Werttyp [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Überspringen Sie beim Parameter `Mandatory` und bei den Attributen `ValidateNotNull` und `ValidateNotNullOrEmpty` die Überprüfung auf NULL-Elemente, wenn der Elementtyp der Sammlung ein Werttyp ist.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Ändern von `$OutputEncoding`, um die `UTF-8 NoBOM`-Codierung statt ASCII zu verwenden [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

Die vorherige Codierung (ASCII, 7 Bit) würde in manchen Fällen zu falschen Änderungen der Ausgabe führen. Durch diese Änderung soll die `UTF-8 NoBOM`-Codierung standardmäßig verwendet werden. Dadurch wird die Unicode-Ausgabe mit einer Codierung beibehalten, die von den meisten Tools und Betriebssystemen unterstützt wird.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Entfernen von `AllScope` aus den meisten Standardaliasen [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

`AllScope` wurde aus den meisten Standardaliasen entfernt, um die Erstellung von Bereichen zu beschleunigen. In einigen häufig verwendeten Aliasen, in denen die Suche schneller ist, wurde `AllScope` beibehalten.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` und `-Debug` überschreiben `$ErrorActionPreference` nicht mehr [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Zuvor wurde das Verhalten von `$ErrorActionPreference` überschrieben, wenn `-Verbose` oder `-Debug` angegeben wurden. Durch diese Änderung wirken `-Verbose` und `-Debug` sich nicht mehr auf das Verhalten von `$ErrorActionPreference` aus.

## <a name="cmdlet-changes"></a>Änderungen an Cmdlets

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>„Invoke-RestMethod“ gibt keine nützlichen Informationen zurück, wenn keine Daten zurückgegeben werden [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Wenn eine API nur `null` zurückgibt, hat Invoke-RestMethod dies als die Zeichenfolge `"null"` statt `$null` serialisiert. Diese Änderung korrigiert die Logik in `Invoke-RestMethod`, um das gültige JSON-Literal mit Einzelwert `null` ordnungsgemäß als `$null` zu serialisieren.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Entfernung von `-ComputerName` aus `*-Computer`-Cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Aufgrund von Problemen mit dem RPC-Remoting in CoreFX (insbesondere auf anderen Plattformen als Windows) und zur Gewährleistung einer konsistenten Remotingumgebung in PowerShell wurde der Parameter `-ComputerName` aus den `\*-Computer`-Cmdlets entfernt. Verwenden Sie stattdessen `Invoke-Command`, um Cmdlets remote auszuführen.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Entfernung von `-ComputerName` aus `*-Service`-Cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Der Parameter `-ComputerName` wurde aus `*-Service`-Cmdlets entfernt, um die konsistente Verwendung von PSRP zu fördern.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Korrigieren von `Get-Item -LiteralPath a*b`, wenn `a*b` nicht vorhanden ist, um Fehler zurückzugeben [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Zuvor wurde ein `-LiteralPath`-Cmdlet im Hintergrund beendet, wenn ein Platzhalter es wie `-Path` behandelt und dieser keine Dateien findet. Korrekterweise sollte `-LiteralPath` ein Literal sein, sodass ein Fehler angezeigt wird, wenn die Datei nicht vorhanden ist. Die Änderung besteht darin, dass Platzhalter, die mit `-Literal` verwendet werden, als Literal behandelt werden.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` sollte `PSTypeNames` beim Import anwenden, wenn die Typinformationen in der CSV-Datei vorhanden sind [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Zuvor behielten exportierte Objekte, die `Export-CSV` mit `TypeInformation` verwenden und mit `ConvertFrom-Csv` importiert wurden, die Typinformationen nicht bei. Durch diese Änderung werden die Typinformationen zum Member `PSTypeNames` hinzugefügt, wenn Sie in der CSV-Datei vorhanden sind.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` sollte standardmäßig auf `Export-Csv` festgelegt sein [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Diese Änderung wurde als Reaktion auf Kundenfeedback zum Standardverhalten von `Export-CSV` durchgeführt, indem Typinformationen eingefügt wurden.

Zuvor gab das Cmdlet einen Kommentar als erste Zeile aus, der den Typnamen des Objekts enthielt. Durch diese Änderung wird dies standardmäßig unterdrückt, da es von den meisten Tools nicht interpretiert werden kann. Verwenden Sie `-IncludeTypeInformation`, um das vorherigen Verhalten beizubehalten.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Web-Cmdlets sollten eine Warnung ausgeben, wenn `-Credential` über nicht verschlüsselte Verbindungen gesendet wird [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Bei der Verwendung von HTTP werden Inhalte mit Kennwörtern als Klartext gesendet. Durch diese Änderung wird dies standardmäßig nicht zugelassen, außerdem wird ein Fehler zurückgegeben, wenn Anmeldeinformationen auf unsichere Weise weitergeleitet werden. Die Benutzer können dies umgehen, indem Sie den Parameter `-AllowUnencryptedAuthentication` verwenden.

## <a name="api-changes"></a>Änderungen an der API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Entfernung der `AddTypeCommandBase`-Klasse [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

Die `AddTypeCommandBase`-Klasse wurde aus `Add-Type` entfernt, um die Leistung zu verbessern. Diese Klasse wird nur vom Cmdlet „Add-Type“ verwendet, sodass es keine Auswirkungen auf die Benutzer geben sollte.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Vereinheitlichung von Cmdlets mit dem Parameter `-Encoding` vom Typ `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

Der `-Encoding`-Wert `Byte` wurde aus den Cmdlets des Dateisystemanbieters entfernt. Der neue Parameter `-AsByteStream` wird nun verwendet, um anzugeben, dass ein Bytestream als Eingabe erforderlich ist oder dass die Ausgabe ein Bytestream ist.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Verbesserte Fehlermeldung, wenn der `-UFormat`-Parameter leer oder NULL ist [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Zuvor wurde eine Fehlermeldung angezeigt, die nicht nützlich war, wenn eine leere Formatzeichenfolge an `-UFormat` übergeben wurde. Eine Fehlermeldung mit verbesserter Beschreibung wurde hinzugefügt.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Bereinigung des Konsolencodes [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

Folgende Features wurden entfernt, da sie in PowerShell Core nicht unterstützt werden und die Unterstützung nicht geplant ist, da diese nur aus Legacygründen in Windows PowerShell vorhanden sind: der `-psconsolefile`-Parameter und -Code, der `-importsystemmodules`-Parameter und -Code sowie Code zum Ändern der Schriftart.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Entfernung der Unterstützung von `RunspaceConfiguration` [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Zuvor konnten Sie bei der programmgesteuerten Erstellung eines PowerShell-Runspaces mithilfe der API die veraltete Klasse [`RunspaceConfiguration`][runspaceconfig] oder die neuere Klasse [`InitialSessionState`][iss] verwenden. Durch diese Änderung wurde die Unterstützung für `RunspaceConfiguration` entfernt, sodass nur noch `InitialSessionState` unterstützt wird.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` bindet Argumente an `$input` anstatt an `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Die falsche Position eines Parameters führte dazu, dass die Argumente als Eingabe statt als Argumente übergeben wurden.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Der nicht unterstützte `-showwindow`-Parameter wurde aus `Get-Help` entfernt [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` basiert auf WPF. Dies wird auf CoreCLR nicht unterstützt.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>* kann jetzt in Registrierungspfaden für `Remove-Item` verwendet werden [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Zuvor wurde ein `-LiteralPath`-Cmdlet im Hintergrund beendet, wenn ein Platzhalter es wie `-Path` behandelt und dieser keine Dateien findet. Korrekterweise sollte `-LiteralPath` ein Literal sein, sodass ein Fehler angezeigt wird, wenn die Datei nicht vorhanden ist. Die Änderung besteht darin, dass Platzhalter, die mit `-Literal` verwendet werden, als Literal behandelt werden.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Behebung eines fehlgeschlagenen Tests für `Set-Service` [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Zuvor wurde `foo` ignoriert, wenn `New-Service -StartupType foo` verwendet wurde, und der Dienst wurde mit Standardstarttypen erstellt. Durch diese Änderung soll für ungültige Starttypen explizit ein Fehler ausgelöst werden.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Umbenennung von `$IsOSX` in `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

Die Benennung in PowerShell sollte konsistent mit unserer Benennung und mit der Verwendung von macOS statt OSX (Apple) konform sein. Aus Gründen der Lesbarkeit und Konsistenz wird jedoch die Groß- und Kleinschreibung von Pascal beibehalten.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Fehlermeldungen sollten konsistent sein, wenn ein ungültiges Skript an „-File“ übergeben wird; Fehlermeldungen beim Übergeben eines mehrdeutigen Arguments sollten verbessert werden [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Änderung der Exitcodes von `pwsh.exe` für eine Übereinstimmung mit Unix-Konventionen

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Entfernung von `LocalAccount` und Cmdlets aus `Diagnostics`-Modulen [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Aufgrund von nicht unterstützten APIs wurden das `LocalAccounts`-Modul und die `Counter`-Cmdlets aus dem `Diagnostics`-Modul entfernt, bis eine bessere Lösung gefunden wird.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Das Ausführen des PowerShell-Skripts mit booleschen Parametern funktioniert nicht [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Zuvor wurde bei der Verwendung von **powershell.exe** (jetzt **pwsh.exe**), um ein PowerShell-Skript mithilfe von `-File` auszuführen, keine Möglichkeit bereitgestellt, `$true`/`$false` als Parameterwert zu übergeben. Die Unterstützung für `$true`/`$false` als analysierte Werte für Parameter wurde hinzugefügt. Parameterwerte werden ebenfalls unterstützt, da die derzeit dokumentierte Syntax nicht funktioniert.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Entfernung der `ClrVersion`-Eigenschaft aus `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

Die `ClrVersion`-Eigenschaft von `$PSVersionTable` ist in CoreCLR nicht nützlich, und Endbenutzer sollten diesen Wert nicht verwenden, um die Kompatibilität zu ermitteln.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Änderung des positionellen Parameters für `powershell.exe` von `-Command` in `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Die Verwendung von Shebang in PowerShell auf anderen Plattformen als Windows wird ermöglicht. Das bedeutet, dass Sie auf Unix-basierten Systemen ein Skript ausführen können, das PowerShell automatisch aufruft, anstatt `pwsh` explizit aufzurufen. Dies bedeutet ebenfalls, dass Sie `powershell foo.ps1` oder `powershell fooScript` durchführen können, ohne `-File` anzugeben. Durch diese Änderung ist es jedoch erforderlich, dass Sie explizit `-c` oder `-Command` angeben, wenn Sie z.B. versuchen, `powershell.exe Get-Command` durchzuführen.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Implementierung der Analyse von Unicode-Escapesequenzen [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` oder `` `u{####}`` wird in das entsprechende Unicode-Zeichen konvertiert. Verwenden Sie das Hochkommazeichen (``` ``u```), um ein Literal (`` `u``) auszugeben.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Änderung der `New-ModuleManifest`-Codierung in `UTF8NoBOM` auf anderen Plattformen als Windows [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Zuvor hat `New-ModuleManifest` PSD1-Manifeste in UTF-16 mit Bytereihenfolge-Marken erstellt, wodurch ein Problem für Linux-Tools entstand. Durch diese Änderung wird die Codierung auf anderen Plattformen als Windows von `New-ModuleManifest` in UTF (ohne Bytereihenfolge-Marken) geändert.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Verhindern, dass `Get-ChildItem` symbolische Links rekursiv durchläuft (#1875) [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Durch diese Änderung wird `Get-ChildItem` besser auf `ls -r` unter Unix sowie auf die nativen `dir /s`-Befehle unter Windows abgestimmt. Wie die genannten Befehle zeigt das Cmdlet symbolische Links zu Verzeichnissen an, die während der Rekursion gefunden werden. Diese werden jedoch nicht rekursiv durchlaufen.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>`Get-Content -Delimiter` sollte kein Trennzeichen in den zurückgegebenen Zeilen enthalten [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Zuvor war die Ausgabe bei der Verwendung von `Get-Content -Delimiter` inkonsistent und unpraktisch, da weitere Verarbeitung der Daten erforderlich ist, um das Trennzeichen zu entfernen. Durch diese Änderung wird das Trennzeichen aus den zurückgegebenen Zeilen entfernt.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Implementierung von „Format-Hex“ in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

Der Parameter `-Raw` ist nun kein Vorgang mehr (d.h. er führt keine Aktion aus). Zukünftig wird die gesamte Ausgabe als richtige Darstellung der Zahlen angezeigt, die alle Bytes für den Typ enthält. Vor der Änderung war dies die formale Aufgabe des `-Raw`-Parameters.

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell funktioniert nicht als Standardshell mit dem Skriptbefehl [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

Unter Unix ist es Konvention, dass Shells `-i` für eine inaktive Shell akzeptieren und viele Tools dieses Verhalten erwarten (z.B. `script` und wenn PowerShell als Standardshell festgelegt wird) und die Shell mit dem Parameter `-i` aufrufen. Dies ist ein Breaking Change, da `-i` zuvor einfach verwendet werden konnte, um mit `-inputformat` übereinzustimmen. Nun muss hierfür `-in` verwendet werden.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Behebung eines Tippfehlers im Eigenschaftenname von Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` wurde fälschlicherweise als `BiosSeralNumber` geschrieben und wurde in die richtige Schreibweise geändert.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Hinzufügung der `Get-StringHash`- und `Get-FileHash`-Cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Diese Änderung besteht darin, dass einige Hashalgorithmen von CoreFX nicht unterstützt werden und deshalb nicht mehr verfügbar sind.

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Hinzufügung der Überprüfung von `Get-*`-Cmdlets, wenn mein Übergeben von „$null“ alle Objekte statt eines Fehlers zurückgegeben werden [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Das Übergeben von `$null` an eines der folgenden Cmdlets löst nun einen Fehler aus:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Hinzufügung der Unterstützung für das erweiterte W3C-Protokolldateiformat in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Zuvor konnte das Cmdlet `Import-Csv` nicht verwendet werden, um die Protokolldateien direkt im erweiterten W3C-Protokollformat zu importieren. Hierfür waren zusätzliche Aktionen erforderlich. Durch diese Änderung wird das erweiterte W3C-Protokollformat unterstützt.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Problem mit der Bindung von Parametern mit `ValueFromRemainingArguments` in PowerShell-Funktionen [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` gibt nun die Werte als Array statt als Einzelwert, der ein Array darstellt, zurück.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>Entfernung von `BuildVersion` aus `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Die `BuildVersion`-Eigenschaft wurde aus `$PSVersionTable` entfernt. Diese Eigenschaft war an die Windows-Buildversion gebunden. Stattdessen wird empfohlen, die genaue Version von PowerShell Core mit `GitCommitId` abzurufen.

### <a name="changes-to-web-cmdlets"></a>Änderungen an Web-Cmdlets

Die zugrunde liegende .NET-API der Web-Cmdlets wurde in `System.Net.Http.HttpClient` geändert. Diese Änderung bietet viele Vorteile. Diese Änderung führte jedoch zusammen mit der mangelnden Interoperabilität mit Internet Explorer dazu, dass einige Breaking Changes in `Invoke-WebRequest` und `Invoke-RestMethod` auftraten.

- `Invoke-WebRequest` unterstützt nun ausschließlich die grundlegende HTML-Analyse. `Invoke-WebRequest` gibt immer ein `BasicHtmlWebResponseObject`-Objekt zurück. Die Eigenschaften `ParsedHtml` und `Forms` wurden entfernt.
- Die `BasicHtmlWebResponseObject.Headers`-Werte entsprechen nun `String[]` statt `String`.
- `BasicHtmlWebResponseObject.BaseResponse` ist nun ein `System.Net.Http.HttpResponseMessage`-Objekt.
- Die `Response`-Eigenschaft von Web-Cmdlet-Ausnahmen ist nun ein `System.Net.Http.HttpResponseMessage`-Objekt.
- Die strenge RFC-Headeranalyse wird nun standardmäßig für den `-Headers`- und `-UserAgent`-Parameter durchgeführt. Dies kann mit `-SkipHeaderValidation` umgangen werden.
- Die URI-Schemas `file://` und `ftp://` werden nicht mehr unterstützt.
- Die `System.Net.ServicePointManager`-Einstellungen werden nicht mehr berücksichtigt.
- Derzeit ist keine zertifikatbasierte Authentifizierung unter macOS verfügbar.
- Das Verwenden eines `-Credential`- statt einem `http://`-URI führt zu einem Fehler. Verwenden Sie einen `https://`-URI, oder geben Sie den `-AllowUnencryptedAuthentication`-Parameter an, um den Fehler zu unterdrücken.
- `-MaximumRedirection` erzeugt nun einen Fehler mit Abbruch, wenn Umleitungsversuche die angegebene Grenze überschreiten, anstatt die Ergebnisse der letzten Umleitung zurückzugeben.
