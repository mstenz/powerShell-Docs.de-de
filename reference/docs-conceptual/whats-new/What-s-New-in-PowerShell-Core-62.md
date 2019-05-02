---
title: Neuerungen in PowerShell Core 6.2
description: Neue Funktionen und Änderungen in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058096"
---
# <a name="whats-new-in-powershell-core-62"></a>Neuerungen in PowerShell Core 6.2

Das Release PowerShell Core 6.2 konzentriert sich auf Leistungsverbesserungen, Fehlerbehebungen und kleinere Cmdlet- und Sprachverbesserungen, die die Qualität verbessern. Eine vollständige Liste der Verbesserungen finden Sie in unseren detaillierten [Änderungsprotokollen](https://github.com/PowerShell/PowerShell/releases) auf GitHub.

## <a name="experimental-features"></a>Experimentelle Features

Wir haben bereits früher die Unterstützung [Experimentelle Features][] aktiviert. Release 6.2 enthält vier experimentelle Features, die Sie ausprobieren können. Bitte geben Sie uns Feedback, damit wir Verbesserungen vornehmen und entscheiden können, ob das Feature allgemein verfügbar gemacht werden sollte.

Verwenden Sie `Get-ExperimentalFeature`, um eine Liste der verfügbaren experimentellen Features abzurufen. Sie können diese Features mit `Enable-ExperimentalFeature` und `Disable-ExperimentalFeature` aktivieren oder deaktivieren.

### <a name="command-not-found-suggestions"></a>„Befehl nicht gefunden“-Vorschläge

Dieses Feature sucht anhand von Fuzzyübereinstimmungen nach Vorschlägen für Befehle oder Cmdlets, bei denen Sie sich möglicherweise verschrieben haben.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Beispiel

In diesem Beispiel bestehen Fuzzyübereinstimmungen des falsch geschriebenen Cmdlet-Namens mit mehreren Vorschlägen, vom wahrscheinlichsten bis zum am wenigsten wahrscheinlichen.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Implizite Remoting-Batchverarbeitung

Bei Verwendung von [implizitem Remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in einer Pipeline behandelt PowerShell die Befehle in der Pipeline unabhängig voneinander. Objekte werden während der Ausführung der Pipeline wiederholt zwischen dem Client und dem Remotesystem serialisiert und `de-serialized`.

Mit diesem Feature analysiert PowerShell die Pipeline, um festzustellen, ob der Befehl sicher ausgeführt werden kann und auf dem Zielsystem vorhanden ist. Wenn „true“, führt PowerShell die gesamte Pipeline remote aus und serialisiert und `de-serializes` nur die Ergebnisse zurück an den Client.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Ein Test von `Get-Process | Sort-Object` in der realen Welt über Localhost wird von 10 bis 15 Sekunden auf 20 bis 30 **Millisekunden** reduziert. Dieses Feature muss nur auf dem Client aktiviert werden. Auf dem Server sind keine Änderungen erforderlich.

### <a name="temp-drive"></a>Temporäres Laufwerk

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Wenn Sie PowerShell Core auf verschiedenen Betriebssystemen verwenden, werden Sie feststellen, dass die Umgebungsvariable für die Suche nach dem temporären Verzeichnis unter Windows, macOS und Linux unterschiedlich ist! Mit diesem Feature erhalten Sie ein [PSDrive][] namens `Temp:`, dass automatisch dem temporären Ordner für das von Ihnen verwendete Betriebssystem zugeordnet ist.

#### <a name="example"></a>Beispiel

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

Beachten Sie, dass native Dateibefehle (z.B. `ls` unter Linux) nicht für PSDrives geeignet sind und dieses `Temp:`-Laufwerk nicht erkennen.

### <a name="abbreviation-expansion"></a>Erweiterung der Abkürzung

Von PowerShell-Cmdlets wird erwartet, dass sie beschreibende Namen haben. Dies führt zu langen, schwieriger einzugebenden Namen. Mit diesem Feature genügt es, wenn Sie nur die Großbuchstaben des Cmdlets eingeben und anhand der Vervollständigung mit der TAB-Taste eine Übereinstimmung suchen.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Beispiel

```powershell
PS> i-arsavsf
```

Wenn Sie das [Az](https://www.powershellgallery.com/packages/Az)-Modul von Azure PowerShell installiert haben und die TAB-Taste drücken, wird die automatische Vervollständigung ausgeführt:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Dieses Feature ist für die interaktive Verwendung vorgesehen. Abgekürzte Formen der Cmdlets können nicht ausgeführt werden.
> Dieses Feature ist kein Ersatz für Aliase.

## <a name="breaking-changes"></a>Wichtige Änderungen

- `-NoEnumerate`-Verhalten in `Write-Output` ist konsistent mit Windows PowerShell. (#9069)
- Das Ergebnis von `Join-String -InputObject 1,2,3` ist jetzt gleich dem Ergebnis von `1,2,3 | Join-String` (#8611) – vielen Dank an @sethvs!
- Hinzufügen von `-Stable` zu `Sort-Object` und zugehörige Tests (#7862) – vielen Dank an @KirkMunro!
- Verbesserung des `Start-Sleep`-Cmdlets, sodass es Bruchteile von Sekunden akzeptiert (#8537) – vielen Dank an @Prototyyppi!
- Ändern der Hashtabelle, sodass OrdinalIgnoreCase verwendet wird, damit die Tabelle in allen Kulturen `case-insensitive` ist (#8566)
- **LiteralPath** in `Import-Csv` wird an `Get-ChildItem`-Ausgabe gebunden (#8277) – vielen Dank an @iSazonov!
- Eine Spalte ohne Namen wird nicht mehr übersprungen, wenn in `Import-Csv` doppelte Anführungszeichen als Trennzeichen verwendet werden (#7899) – vielen Dank an @Topping!
- `Get-ExperimentalFeature` hat nicht mehr die Option `-ListAvailable` (#8318)
- Beim Debuggen von Parametern wird `$DebugPreference` jetzt auf **Continue** statt auf **Inquire** gesetzt (#8195) – vielen Dank an @KirkMunro!
- Beachtung von `-OutputFormat` bei Angabe in nicht interaktivem, umgeleitetem, codiertem Befehl, der mit PowerShell verwendet wird (#8115)
- Assembly wird vor dem Versuch, aus dem GAC geladen zu werden, aus dem Modulbasispfad geladen (#8073)
- Entfernen der Tilde aus Linux-Vorschaupaketen (#8244)
- Verschieben der Verarbeitung von `-WorkingDirectory` vor der Verarbeitung von Profilen (#8079)
- Kein Hinzufügen der `PATHEXT`-Umgebungsvariablen unter Unix (#7697) – vielen Dank an @iSazonov!

## <a name="known-issues"></a>Bekannte Probleme

- Beim Remoting tritt auf Windows IOT-ARM-Plattformen beim Laden von Modulen ein Problem auf. Siehe (#8053)

## <a name="general-updates-and-fixes"></a>Allgemeine Updates und Fixes

- Vervollständigung mit der TAB-Taste ohne Berücksichtigung der Groß-/Kleinschreibung für Dateien und Ordner im Groß-/Kleinschreibung berücksichtigenden Dateisystem (#8128)
- Öffentlich machen von PSVersionInfo.PSVersion und PSVersionInfo.PSEdition (#8054) – vielen Dank an @KirkMunro!
- Hinzufügen des Typrückschlusses für `$_` / `$PSItem` in `catch{ }`-Blöcken (#8020) – vielen Dank an @vexx32!
- Behoben: Typrückschluss bei Aufruf der statischen Methode (#8018) – vielen Dank an @SeeminglyScience!
- Erstellen von abgeleiteten Typen für `Select-Object`, `Group-Object`, **PSObject** und **Hashtabelle** (#7231) – vielen Dank an @powercode!
- Unterstützung des Methodenaufrufs mit `ByRef-like`-Typparametern (#7721)
- Behandeln des Falls, dass der Windows PowerShell-Modulpfad bereits im PSModulePath der Umgebung enthalten ist (#7727)
- Aktivieren von `SecureString`-Cmdlets für Nicht-Windows durch Speichern von Nur-Text (#9199)
- Verbesserte Fehlermeldung in Nicht-Windows beim Importieren von „clixml“ mit securestring (#7997)
- Hinzufügen des ReplyTo-Parameters zu `Send-MailMessage` (#8727) – vielen Dank an @replicaJunction!
- Hinzufügen der „Veraltet“-Nachricht zu `Send-MailMessage` (#9178)
- `Restart-Computer` funktioniert auf `localhost`, wenn WinRM nicht vorhanden ist (#9160)
- Veranlassen, dass `Start-Job` einen Fehler mit Abbruch auslöst, wenn PowerShell gehostet wird (#9128)
- Hinzufügen von Beschleunigern und Suffixen des C#-Formatvorlagentyps für ushort, uint, ulong und kurze Literale (#7813) – vielen Dank an @vexx32!
- Hinzufügen neuer Suffixe für numerische Literale – siehe [about_Numeric_Literals][] (#7901) – vielen Dank an @vexx32!
- Ordnungsgemäßes Melden des Schweregrads, wenn SupportsShouldProcess nicht auf „true“ festgelegt ist (#8209) – vielen Dank an @vexx32!
- Beheben von Problemen mit der Zeichensatzanforderung in Web-Cmdlets (#8742) – vielen Dank an @markekraus!
- Beheben des erwarteten `100-continue`-Problems mit Web-Cmdlets (#8679) – vielen Dank an @markekraus!
- Beheben des Dateiblockierungsproblems mit Web-Cmdlets (#7676) – vielen Dank an @Claustn!
- Beheben des Codeseitenanalyse-Problems in `Invoke-RestMethod` (#8694) – vielen Dank an @markekraus!
- Umgestalten von `ConvertTo-Json`, um JsonObject.ConvertToJson als öffentliche API verfügbar zu machen (#8682)
- Hinzufügen von konfigurierbarer maximaler Tiefe in `ConvertFrom-Json` mit „-Depth“ (#8199) – vielen Dank an @louistio!
- Hinzufügen des EscapeHandling-Parameters in `ConvertTo-Json`-Cmdlet (#7775) – vielen Dank an @iSazonov!
- Hinzufügen von `-CustomPipeName` zu PowerShell und `Enter-PSHostProcess` (#8889)
- Relative symbolische Verknüpfungen können mit `New-Item` unter Windows erstellt werden (#8783)
- Zulassen, das Windows-Benutzer im Entwicklermodus ohne Rechteerweiterung symbolische Verknüpfungen erstellen (#8534)
- `Write-Information` akzeptiert `$null` (#8774)
- Korrigieren von `Get-Help` für erweiterte Funktionen mit MAML-Hilfeinhalt (#8353)
- Beheben des `Get-Help`-PSTypeName-Problems mit „-Parameter“, wenn nur ein Parameter deklariert wird (#8754) – vielen Dank an @pougetat!
- Korrektur der Tokenberechnung für `Get-Help` ausgeführt auf ScriptBlock für Kommentarhilfe. (#8238) – vielen Dank an @hubuk!
- Änderung des `Get-Help` Cmdlet-Parameters „-Parameter“, sodass er Zeichenfolgenarrays akzeptiert (#8454) – vielen Dank an @sethvs!
- Korrektur bei PAGER für den Fall, dass der Pfad Leerzeichen enthält (#8571) – vielen Dank an @pougetat!
- Hinzufügen einer Eingabeaufforderung bei Verwendung von `less` in der Funktion „help“", um Benutzer anzuweisen, wie sie beenden sollen (#7998)
- Hinzufügen von Unterstützung für Enumerations- und Char-Datentyp in `Format-Hex`-Cmdlet (#8191) – vielen Dank an @iSazonov!
- Entfernen von ShouldProcess aus `Format-Hex` (#8178)
- Hinzufügen der neuen Parameter „Offset“ und „Count“ zu `Format-Hex` und Umgestalten des Cmdlets (#7877) – vielen Dank an @iSazonov!
- Zulassen von „name“ als Aliasschlüssel für „label“ in `ConvertTo-Html`, Zulassen des Eintrags „width“ als Ganzzahl (#8426) – vielen Dank an @mklement0!
- ScriptBlock-basierte berechnete Eigenschaften funktionieren wieder in `ConvertTo-Html` (#8427) – vielen Dank an @mklement0!
- Hinzufügen des Cmdlets `Join-String` zum Erstellen von Text aus der Pipelineeingabe (#7660) – vielen Dank an @powercode!
- Korrektur der FormatString-Parameterlogik des `Join-String`-Cmdlets (#8449) – vielen Dank an @sethvs!
- Änderung von `Clear-Host` zurück zur Verwendung von `$RAWUI` und Bereitmachen zur Arbeit mit Remoting (#8609)
- Änderung von `Clear-Host` in einfach aufgerufenes `[console]::clear` und Entfernen des clear-Alias aus Unix (#8603)
- LiteralPath in `Import-Csv` wird an `Get-ChildItem`-Ausgabe gebunden (#8277) – vielen Dank an @iSazonov!
- Hilfefunktion sollte Pager nicht für AliasHelpInfo verwenden (#8552)
- Hinzufügen von `-UseMinimalHeader` zu `Start-Transcript`, um Aufzeichnungsheader zu minimieren (#8402) – vielen Dank an @lukexjeremy!
- Hinzufügen der Cmdlets `Enable-ExperimentalFeature` und `Disable-ExperimentalFeature` (#8318)
- Verfügbar machen aller Cmdlets aus **PSDiagnostics**, wenn „logman.exe“ verfügbar ist (#8366)
- Entfernen des **Persist**-Parameters aus `New-PSDrive` auf der `non-Windows`-Plattform (#8291) – vielen Dank an @lukexjeremy!
- Hinzufügen von Unterstützung für `cd +` (#7206) – vielen Dank an @bergmeister!
- `Set-Location -LiteralPath` funktioniert mit Ordnern, die mit „-“ und „+“ benannt sind (#8089)
- `Test-Path` gibt `$false` zurück, wenn ein leerer oder `$null`-Pfadwert übergeben wird (#8080) – vielen Dank an @vexx32!
- Dynamische Parameter können auch dann zurückgegeben werden, wenn der Pfad mit keinem Anbieter übereinstimmt (#7957)
- Unterstützung von `Get-PSHostProcessInfo` und `Enter-PSHostProcess` auf Unix-Plattformen (#8232)
- Reduzieren der Zuordnungen im `Get-Content`-Cmdlet (#8103) – vielen Dank an @iSazonov!
- `Add-Content` kann den Lesezugriff beim Schreiben von Inhalt mit anderen Tools gemeinsam nutzen (#8091)
- Von `Get/Add-Content` bei Anwendung auf einen Container ausgelöste Fehlermeldungen wurden verbessert (#7823) – vielen Dank an @kvprasoon!
- Dem `Get-Culture`-Cmdlet wurden die Parameter `-Name`, `-NoUserOverrides` und `-ListAvailable` hinzugefügt. (#7702) – Vielen Dank an @iSazonov!
- Hinzufügen eines vereinheitlichten Attribut für die Vervollständigung des **Encoding**-Parameters. (#7732) – Vielen Dank an @ThreeFive-O!
- Zulassen von numerischen IDs und Namen registrierter Codepages in **Encoding**-Parametern (#7636) – vielen Dank an @iSazonov!
- Korrektur von `Rename-Item -Path` mit Platzhalterzeichen (#7398) – vielen Dank an @kwkam!
- Wenn bei Verwendung von `Start-Transcript` eine Datei vorhanden ist, Datei leeren statt löschen (#8131) – vielen Dank an @paalbra!
- `Add-Type` öffnet Quelldateien explizit mit **FileAccess.Read** und **FileShare.Read** (#7915) – vielen Dank an @IISResetMe!
- Korrektur von `Enter-PSSession -ContainerId` für aktuelle Windows-Version (#7883)
- Sicherstellen, dass **NestedModules**-Eigenschaft durch `Test-ModuleManifest` aufgefüllt wird (#7859)
- Hinzufügen des `%F`-Falls zu `Get-Date` -UFormat (#7630) – vielen Dank an @britishben!
- Korrektur von `Set-Service -Status Stopped` zum Beenden von Diensten mit Abhängigkeiten (#5525) – vielen Dank an @zhenggu!

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentelle Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
