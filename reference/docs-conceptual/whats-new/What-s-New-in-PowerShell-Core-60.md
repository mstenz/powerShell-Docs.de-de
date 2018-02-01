# <a name="whats-new-in-powershell-core-60"></a>Neuigkeiten in PowerShell Core 6.0

[PowerShell Core 6.0][github] ist eine neue plattformübergreifende (Windows, macOS und Linux) Open Source-Edition von PowerShell, die für heterogene Umgebungen und die Cloud entwickelt wurde.

## <a name="moved-from-net-framework-to-net-core"></a>Aus .NET Framework in .NET Core übernommen

In PowerShell Core wird [.NET Core 2.0][] als Runtime verwendet.
Dank .NET Core 2.0 funktioniert PowerShell Core auf verschiedenen Plattformen (Windows, macOS und Linux).
PowerShell Core macht auch die .NET Core 2.0-APIs verfügbar, die in PowerShell-Cmdlets und -Skripts verwendet werden.

In Windows PowerShell wurde das PowerShell-Modul mithilfe der .NET Framework Runtime gehostet.
Windows PowerShell macht also die .NET Framework-APIs verfügbar.

Die von .NET Core und .NET Framework gemeinsam genutzten APIs sind als Teil von [.NET Standard 2.0][] definiert.

Weitere Informationen dazu, wie sich dies auf die Kompatibilität von Modulen und Skripts in PowerShell Core und Windows PowerShell auswirkt, finden Sie unter [Abwärtskompatibilität mit Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Unterstützung für macOS und Linux

PowerShell unterstützt jetzt offiziell macOS und Linux, einschließlich:

- Windows 7, 8.1 und 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Halbjährlicher Kanal von Windows Server][semi-annual]
- Ubuntu 14.04, 16.04 und 17.04
- Debian 8.7 und höher sowie Debian 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12 und höher

Unsere Community hat außerdem Pakete für die folgenden Plattformen beigetragen, die jedoch nicht offiziell unterstützt werden:

- Arch Linux
- Kali Linux
- AppImage (funktioniert auf verschiedenen Linux-Plattformen)

Für die folgenden Plattformen gibt es experimentelle (nicht unterstützte) Releases:

- Windows unter ARM32/ARM64
- Raspbian (Stretch)

In PowerShell Core 6.0 wurden einige Änderungen vorgenommen, um die Funktionsweise auf Nicht-Windows-Systemen zu verbessern.
Einige davon sind sehr wichtig und gelten auch für Windows.
Andere betreffen nur Nicht-Windows-Installationen von PowerShell Core.

- Unterstützung der nativen Verwendung von Platzhaltern in Befehlen auf Unix-Plattformen
- Die `more`-Funktionalität respektiert `$PAGER` von Linux und entspricht standardmäßig `less`.
  Jetzt können Sie also Platzhalter mit nativen Binärdateien bzw. Befehlen verwenden, z.B. `ls *.txt`. (#3463)
- Der abschließende umgekehrte Schrägstrich wird bei nativen Befehlsargumenten automatisch mit einem Escapezeichen versehen. (#4965)
- Der Schalter `-ExecutionPolicy` wird bei der Ausführung von PowerShell auf Nicht-Windows-Plattformen ignoriert, da das Signieren von Skripts derzeit nicht unterstützt wird. (#3481)
- ConsoleHost berücksichtigt auf Unix-Plattformen jetzt `NoEcho`. (#3801)
- `Get-Help` unterstützt nun Mustervergleiche auf Unix-Plattformen, bei denen die Groß- und Kleinschreibung nicht beachtet wird. (#3852)
- `powershell`-Manpage wurde zum Paket hinzugefügt.

### <a name="logging"></a>Protokollierung

Unter macOS verwendet PowerShell native `os_log`-APIs zur Anmeldung beim [einheitlichen Protokollierungssystem][os_log] von Apple.
Unter Linux verwendet PowerShell [Syslog][], eine weit verbreitete Protokollierungslösung.

### <a name="filesystem"></a>Dateisystem

Unter macOS und Linux wurden einige Änderungen vorgenommen, damit für Dateinamen, die früher unter Windows nicht unterstützt wurden, nun Unterstützung angeboten wird:

- Pfade, die an Cmdlets übergeben werden, sind jetzt schrägstrichagnostisch, d.h., dass sowohl „/“ als auch „\“ als Verzeichnistrennzeichen akzeptiert werden.
- Die XDG Base Directory-Spezifikation wird eingehalten und standardmäßig verwendet:
  - Der Linux/macOS-Profilpfad lautet `~/.config/powershell/profile.ps1`
  - Der Speicherpfad für den Verlauf lautet `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Der Benutzermodulpfad lautet `~/.local/share/powershell/Modules`
- Unterstützung für Datei- und Ordnernamen mit Doppelpunkt unter Unix. (#4959)
- Unterstützung für Skriptnamen oder vollständige Pfade, die Kommas enthalten. (#4136) (Vielen Dank an @TimCurwick)
- Es wird erkannt, wann mit `-LiteralPath` die Platzhaltererweiterung für Navigations-Cmdlets unterdrückt wird. (#5038)
- `Get-ChildItem` wurde in der Funktionsweise an `ls -R` in *nix und native `DIR /S`-Windows-Befehle angeglichen.
  `Get-ChildItem` gibt jetzt die symbolischen Links zurück, die bei einer rekursiven Suche gefunden wurden, und sucht nicht in den Verzeichnissen, zu denen die Links führen. (#3780)

### <a name="case-sensitivity"></a>Unterscheidung nach Groß-/Kleinschreibung

Unter Linux und macOS wird die Groß-/Kleinschreibung im Gegensatz zu Windows meist beachtet, während unter Windows die Groß-/Kleinschreibung beibehalten wird.
PowerShell unterscheidet nicht nach Groß-/Kleinschreibung.

Bei Umgebungsvariablen wird unter macOS und Linux z.B. nach Groß-/Kleinschreibung unterschieden. Daher wurde die Groß-/Kleinschreibung der Umgebungsvariable `PSModulePath` standardisiert. (#3255) Bei `Import-Module` wird die Groß-/Kleinschreibung beachtet, wenn der Modulname mit einem Dateipfad bestimmt werden soll. (#5097)

## <a name="support-for-side-by-side-installations"></a>Unterstützung für parallele Installationen

PowerShell Core wird separat von Windows PowerShell installiert, konfiguriert und ausgeführt.
Außerdem enthält PowerShell Core ein „portables“ ZIP-Paket,
mit dem Sie beliebig viele Versionen an einem beliebigen Speicherort auf dem Datenträger installieren können, auch lokal für eine Anwendung, die PowerShell als Abhängigkeit verwendet.
Eine parallele Installation erleichtert das Testen neuer PowerShell-Versionen und die Migration vorhandener Skripts.
Sie ermöglicht außerdem Abwärtskompatibilität, da Skripts an bestimmte Versionen angeheftet werden können, die sie benötigen.

> [!NOTE]
> Der MSI-basierte Installer unter Windows führt standardmäßig eine direkte Updateinstallation aus.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>`powershell(.exe)` in `pwsh(.exe)` umbenannt

Der binäre Name für PowerShell Core wurde von `powershell(.exe)` in `pwsh(.exe)` geändert.
So können Benutzer PowerShell Core deterministisch auf Computern ausführen, um parallele Windows PowerShell- und PowerShell Core-Installationen zu unterstützen.
`pwsh` ist außerdem viel kürzer und lässt sich einfacher eingeben.

Weitere Änderungen in `pwsh(.exe)` im Vergleich zu `powershell.exe`:

- Der erste positionelle Parameter wurde von `-Command` in `-File` geändert.
  `#!`, auch Shebang genannt, wird damit nicht mehr in PowerShell-Skripts benötigt, die über Nicht-PowerShell-Shells auf Nicht-Windows-Plattformen ausgeführt werden.
  Damit können Sie auch Befehle wie `pwsh foo.ps1` oder `pwsh fooScript` ausführen, ohne `-File` anzugeben.
  Beim Versuch, einen Befehl wie `pwsh.exe -Command Get-Command` auszuführen, muss für diese Änderung jedoch `-c` oder `-Command` explizit angegeben werden. (#4019)
- PowerShell Core akzeptiert den Schalter `-i` (oder `-Interactive`), um eine interaktive Shell anzugeben. (#3558) Daher kann PowerShell als Standard-Shell auf Unix-Plattformen verwendet werden.
- Die Parameter `-importsystemmodules` und `-psconsoleFile` wurden aus `pwsh.exe` entfernt. (#4995)
- `pwsh -version` wurde geändert, und Hilfe für `pwsh.exe` bei der Ausrichtung an anderen nativen Tools wurde integriert. (#4958 & #4931) (Vielen Dank an @iSazonov)
- Ungültige Argument-Fehlermeldungen für `-File` und `-Command` und mit den Unix-Standards konsistente Exitcodes (#4573)
- Parameter `-WindowStyle` unter Windows hinzugefügt. (#4573) Paketbasierte Installationsupdates auf Nicht-Windows-Plattformen werden direkt installiert.

## <a name="backwards-compatibility-with-windows-powershell"></a>Abwärtskompatibilität mit Windows PowerShell

Das Ziel von PowerShell Core ist die höchstmögliche Kompatibilität mit Windows PowerShell.
PowerShell Core verwendet [.NET Standard 2.0][], um binäre Kompatibilität mit vorhandenen .NET-Assemblys bereitzustellen.
Viele PowerShell-Module hängen von diesen Assemblys (häufig DLL-Dateien) ab. Daher lässt .NET Standard zu, dass sie weiterhin .NET Core nutzen.
PowerShell Core enthält auch eine Heuristik, mit der in bekannten Ordnern wie dem üblichen Speicherort des globalen Assemblycache auf dem Datenträger nach .NET Framework-DLL-Abhängigkeiten gesucht wird.

Weitere Informationen zu .NET Standard finden Sie auf dem [.NET-Blog][], in diesem [YouTube-Video][] und in diesen [Häufig gestellte Fragen][] auf GitHub.

Die PowerShell-Sprache und die „integrierten“ Module (z.B. `Microsoft.PowerShell.Management` und `Microsoft.PowerShell.Utility`) sollten genauso funktionieren wie in Windows PowerShell.
In vielen Fällen haben wir mit der Hilfe der Community Fehlerkorrekturen und neue Funktionen für diese Cmdlets eingebaut.
In einigen Fällen wurde Funktionalität aufgrund einer fehlenden Abhängigkeit in zugrunde liegenden .NET Ebenen entfernt oder ist nicht verfügbar.

Die meisten der in Windows enthaltenen Module (z.B. `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage` usw.) und andere Microsoft-Produkte, einschließlich Azure und Office, wurden noch nicht *explizit* auf .NET Core portiert.
Das PowerShell-Team arbeitet mit diesen Produktgruppen und -teams, um ihre vorhandenen Module zu überprüfen und in PowerShell Core zu portieren.
Mit .NET Standard und [CDXML][] scheinen viele dieser herkömmliche Windows PowerShell-Module in PowerShell Core zu funktionieren. Dies wurde bisher jedoch noch nicht formal validiert, und sie werden nicht offiziell unterstützt.

Durch die Installation des Moduls [`WindowsPSModulePath`][windowspsmodulepath] können Sie Windows PowerShell-Module durch Anfügen von `PSModulePath` aus Windows PowerShell an `PSModulePath` aus PowerShell Core verwenden.

Installieren Sie zunächst das `WindowsPSModulePath`-Modul aus dem PowerShell-Katalog:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Führen Sie nach der Installation dieses Moduls das `Add-WindowsPSModulePath`-Cmdlet aus, um `PSModulePath` aus Windows PowerShell zu PowerShell Core hinzuzufügen:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-Unterstützung

PowerShell Core enthält Unterstützung für Docker-Container für alle wichtigen Plattformen, die wir unterstützen, einschließlich mehrerer Linux-Distributionen, Windows Server Core und Nano Server.

Eine vollständige Liste finden Sie unter „Tags“ unter [`microsoft/powershell` im Docker-Hub][docker-hub].
Weitere Informationen zu Docker und PowerShell Core finden Sie unter [Docker][] auf GitHub.

## <a name="ssh-based-powershell-remoting"></a>SSH-basiertes PowerShell-Remoting

Das PowerShell-Remoting-Protokoll (PSRP) funktioniert jetzt nicht nur mit dem herkömmlichen WinRM-basierten PSRP, sondern auch mit dem Secure Shell-Protokoll (SSH).

Sie können also Cmdlets wie `Enter-PSSession` und `New-PSSession` verwenden und sich mithilfe von SSH authentifizieren.
Dazu müssen Sie PowerShell nur als Subsystem mit einem OpenSSH-basierten SSH-Server registrieren. Anschließend können Sie Ihre vorhandene SSH-basierte Authentifizierung (z.B. Kennwörter oder private Schlüssel) mit der herkömmlichen `PSSession`-Semantik verwenden.

Weitere Informationen zum Konfigurieren und Verwenden von SSH-basiertem Remoting finden Sie unter [PowerShell Remoting Over SSH (PowerShell-Remoting über SSH)][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom"></a>Standardcodierung ist UTF-8 ohne eine BOM

Früher haben Windows PowerShell-Cmdlets wie `Get-Content` und `Set-Content` unterschiedliche Codierungen wie ASCII und UTF-16 verwendet.
Dadurch kam es beim Kombinieren von Cmdlets ohne Angabe einer Codierung immer wieder zu Problemen.

Nicht-Windows-Plattformen verwenden normalerweise UTF-8 ohne eine Bytereihenfolge-Marke (BOM) als Standardcodierung für Textdateien.
Viele Windows-Anwendungen und -Tools kehren UTF-16 jedoch den Rücken und nutzen die BOM-freie UTF-8-Codierung.
Daher wurde die Standardcodierung in PowerShell Core geändert, damit sie der des größeren Ökosystems entspricht.

Dies bedeutet, dass alle integrierten-Cmdlets, die den Parameter `-Encoding` verwenden, auch standardmäßig den Wert `UTF8NoBOM` nutzen.
Die folgenden Cmdlets sind von dieser Änderung betroffen:

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- New-ModuleManifest
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

Diese Cmdlets wurden auch aktualisiert, sodass der Parameter `-Encoding` universell `System.Text.Encoding` akzeptiert.

Der Standardwert von `$OutputEncoding` wurde auch in UTF-8 geändert.

Es hat sich bewährt, Codierungen in Skripts mithilfe des Parameters `-Encoding` explizit festzulegen, um plattformübergreifend deterministisches Verhalten hervorzurufen.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Unterstützung eines kaufmännischen Und-Zeichens (`&`) am Ende einer Pipeline (#3360)

Wenn Sie ein `&` am Ende einer Pipeline einfügen, wird die Pipeline als PowerShell-Auftrag ausgeführt.
In diesem Fall wird ein Auftragsobjekt zurückgegeben.
Wird die Pipeline als Auftrag ausgeführt, kann sie mithilfe aller Standard-`*-Job`-Cmdlets verwaltet werden.
Die in der Pipeline verwendeten Variablen (außer der prozessspezifischen) werden automatisch in den Auftrag kopiert, sodass `Copy-Item $foo $bar &` funktioniert.
Der Auftrag wird auch im aktuellen Verzeichnis statt im Basisverzeichnis des Benutzers ausgeführt.
Weitere Informationen zu PowerShell-Aufträgen finden Sie unter [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Semantische Versionsverwaltung

- `SemanticVersion` ist nun mit `SemVer 2.0` kompatibel. (#5037) (Vielen Dank an @iSazonov)
- Standard-`ModuleVersion` in `New-ModuleManifest` zu `0.0.1` geändert, um SemVer zu entsprechen. (#4842) (Vielen Dank an @LDSpits)
- `semver` wurde als Typaccelerator für `System.Management.Automation.SemanticVersion` hinzugefügt. (#4142) (Vielen Dank an @oising)
- Der Vergleich zwischen einer `SemanticVersion`- und einer `Version`-Instanz, der nur mit `Major`- und `Minor`-Versionswerten erstellt wurde, wurde aktiviert.

## <a name="language-updates"></a>Sprachupdates

- Die Analyse von Unicode-Escapesequenzen wurde implementiert, sodass Benutzer Unicode-Zeichen als Argumente, Zeichenfolgen oder Variablennamen verwenden können. (#3958) (Vielen Dank an @rkeithhill)
- Es wurde ein neues Escapezeichen für die ESC-TASTE hinzugefügt: `` `e``.
- Es wurde Unterstützung für das Konvertieren von Enumerationen in Zeichenfolgen hinzugefügt. (#4318) (Vielen Dank an @KirkMunro)
- Probleme bei der Umwandlung eines Arrays mit einem einzigen Element in eine generische Auflistung wurden behoben. (#3170)
- Dem `..`-Operator wurde eine Überladung des Zeichenbereichs hinzugefügt, sodass `'a'..'z'` Buchstaben von „a“ bis „z“ zurückgibt. (#5026) (Vielen Dank an @IISResetMe)
- Schreibgeschützte Variablen werden bei der Variablenzuweisung nicht mehr überschrieben.
- Lokale Variablen werden beim Dot-Sourcing von Skript-Cmdlets automatisch per Push an „DottedScopes“ übertragen. (#4709)
- Die Optionen „Singleline“ und „Multiline“ können jetzt im Split-Operator verwendet werden. (#4721) (Vielen Dank an @iSazonov)

## <a name="engine-updates"></a>Modulupdates

- `$PSVersionTable` hat vier neue Eigenschaften:
  - `PSEdition`: Dieser Wert ist unter PowerShell Core auf `Core` festgelegt und unter Windows PowerShell auf `Desktop`.
  - `GitCommitId`: Dies ist die Git-Commit-ID des Git-Branchs oder -Tags, in dem PowerShell erstellt wurde.
    Bei veröffentlichten Builds ist sie wahrscheinlich mit `PSVersion` identisch.
  - `OS`: Dies ist eine von `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription` zurückgegebene Betriebssystem-Versionszeichenfolge.
  - `Platform`: Dieser Wert wird von `[System.Environment]::OSVersion.Platform` zurückgegeben. Unter Windows ist er auf `Win32NT`, unter macOS auf `MacOSX` und unter Linux auf `Unix` festgelegt.
- Die `BuildVersion`-Eigenschaft wurde aus `$PSVersionTable` entfernt.
  Diese Eigenschaft war stark an die Windows-Buildversion gebunden.
  Stattdessen wird empfohlen, die genaue Version von PowerShell Core mit `GitCommitId` abzurufen. (#3877) (Vielen Dank an @iSazonov)
- Die Eigenschaft `ClrVersion` wurde aus `$PSVersionTable` entfernt.
  Diese Eigenschaft ist für .NET Core irrelevant und wurde nur für die Abwärtskompatibilität in bestimmten Fällen beibehalten, die nicht für PowerShell gelten.
- Es wurden die drei automatischen Variablen `$IsWindows`, `$IsMacOs` und `$IsLinux` hinzugefügt, mit denen festgestellt werden kann, ob PowerShell unter einem bestimmten Betriebssystem ausgeführt wird.
- `GitCommitId` wurde dem PowerShell Core-Banner hinzugefügt.
  Nun müssen Sie beim Start von PowerShell nicht `$PSVersionTable` ausführen, um die Version zu erhalten. (#3916) (Vielen Dank an @iSazonov)
- Es wurde eine JSON-Konfigurationsdatei namens `PowerShellProperties.json` in `$PSHome` hinzugefügt, in der einige Einstellungen vor der Startzeit gespeichert werden (z.B. `ExecutionPolicy`).
- Es werden keine Pipelines bei der Ausführung von ausführbaren Windows-Dateien blockiert.
- Die Enumeration von COM-Auflistungen wurde aktiviert. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet-Updates

### <a name="new-cmdlets"></a>Neue Cmdlets

- `Get-Uptime` wurde `Microsoft.PowerShell.Utility` hinzugefügt.
- Der Befehl `Remove-Alias` wurde hinzugefügt. (#5143) (Vielen Dank an @PowershellNinja)
- Dem Verwaltungsmodul wurde `Remove-Service` hinzugefügt. (#4858) (Vielen Dank an @joandrsn)

### <a name="web-cmdlets"></a>Web-Cmdlets

- Unterstützung für die Zertifikatauthentifizierung wurde hinzugefügt. (#4646) (Vielen Dank an @markekraus)
- Unterstützung für Inhaltsheader wurde hinzugefügt. (#4494 & #4640) (Vielen Dank an @markekraus)
- Unterstützung für Header mit mehreren Links wurde hinzugefügt. (#5265) (Vielen Dank an @markekraus)
- Unterstützung für die Linkheader-Paginierung (#3828)
  - Wenn die Antwort einen Linkheader enthält, wird für `Invoke-WebRequest` eine RelationLink-Eigenschaft als Wörterbuch erstellt, das die URLs und `rel`-Attribute darstellt. Um die Verwendung zu erleichtern, wird außerdem sichergestellt, dass die URLs absolut sind.
  - Wir machen für `Invoke-RestMethod` einen `-FollowRelLink`-Schalter verfügbar, wenn die Antwort einen Linkheader enthält, der automatisch `next` `rel`-Links folgt, bis sie nicht mehr vorhanden sind, oder sobald der optionale Parameterwert `-MaximumFollowRelLink` erreicht wird.
- Der Parameter `-CustomMethod` wurde hinzugefügt, um die Verwendung nicht standardmäßiger Methodenverben zu ermöglichen. (#3142) (Vielen Dank an @Lee303)
- Unterstützung für `SslProtocol` wurde hinzugefügt. (#5329) (Vielen Dank an @markekraus)
- Mehrteilige Unterstützung wurde hinzugefügt. (#4782) (Vielen Dank an @markekraus)
- `-NoProxy` wurde Web-Cmdlets hinzugefügt, damit sie die systemweite Proxyeinstellung ignorieren. (#3447) (Vielen Dank an @TheFlyingCorpse)
- Der Benutzer-Agent von Web-Cmdlets meldet nun die Betriebssystemplattform. (#4937) (Vielen Dank an @LDSpits)
- Der `-SkipHeaderValidation`-Schalter wurde hinzugefügt, um das Hinzufügen von Headern ohne Überprüfung des Headerwerts zu unterstützen. (#4085)
- Falls erforderlich, können Sie festlegen, dass Web-Cmdlets das HTTPS-Zertifikat auf dem Server nicht überprüfen sollen.
- Es wurden Authentifizierungsparameter hinzugefügt. (#5052) (Vielen Dank an @markekraus)
  - Es wurde `-Authentication` mit den drei Optionen „Basic“, „OAuth“ und „Bearer“ hinzugefügt.
  - Es wurde `-Token` hinzugefügt, um das Bearer-Token für die Optionen „OAuth“ und „Bearer“ zu erhalten.
  - Es wurde `-AllowUnencryptedAuthentication` hinzugefügt, um die Authentifizierung zu umgehen, die für alle Transportschemas außer HTTPS bereitgestellt wird.
- `-ResponseHeadersVariable` wurde `Invoke-RestMethod` hinzugefügt, um die Erfassung von Antwortheadern zu aktivieren. (#4888) (Vielen Dank an @markekraus)
- Web-Cmdlets enthalten nun die HTTP-Antwort in der Ausnahme, wenn der Statuscode der Antwort nicht erfolgreich ist. (#3201)
- Der `UserAgent` von Web-Cmdlets wurde von `WindowsPowerShell` in `PowerShell` geändert. (#4914) (Vielen Dank an @markekraus)
- `Invoke-RestMethod` wurde explizite `ContentType`-Erkennung hinzugefügt. (#4692)
- `-SkipHeaderValidation` von Web-Cmdlets funktioniert jetzt mit nicht standardmäßigen User-Agent-Headern. (#4479 & #4512) (Vielen Dank an @markekraus)

### <a name="json-cmdlets"></a>JSON-Cmdlets

- `ConvertFrom-Json` wurde `-AsHashtable` hinzugefügt, sodass stattdessen ein `Hashtable` zurückgegeben wird. (#5043) (Vielen Dank an @bergmeister)
- Für die `ConvertTo-Json`-Ausgabe wird ein ansprechenderer Formatierer verwendet. (#2787) (Vielen Dank an @kittholland)
- `ConvertTo-Json` wurde Unterstützung für die `Jobject`-Serialisierung hinzugefügt. (#5141)
- `ConvertFrom-Json` deserialisiert nun ein Array von Zeichenfolgen aus der Pipeline, die zusammen eine vollständige JSON-Zeichenfolge bilden,
  d.h., Zeilenumbrüche verursachen keine Fehler bei der JSON-Analyse mehr. (#3823)
- Der für `System.Array` definierte `AliasProperty "Count"` wurde entfernt.
  Dadurch wird die nicht wichtige `Count`-Eigenschaft aus einigen `ConvertFrom-Json`-Ausgaben entfernt. (#3231) (Vielen Dank an @PetSerAl)

### <a name="csv-cmdlets"></a>CSV-Cmdlets

- `PSTypeName`-Unterstützung wurde für `Import-Csv` und `ConvertFrom-Csv` hinzugefügt. (#5389) (Vielen Dank an @markekraus)
- `Import-Csv` unterstützt nun `CR`, `LF` und `CRLF` als Zeilentrennzeichen. (#5363) (Vielen Dank an @iSazonov)
- `-NoTypeInformation` ist nun der Standard für `Export-Csv` und `ConvertTo-Csv`. (#5164) (Vielen Dank an @markekraus)

### <a name="service-cmdlets"></a>Dienst-Cmdlets

- Den von `Get-Service` zurückgegebenen `ServiceController`-Objekten wurden die Eigenschaften `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName` und `StartupType` hinzugefügt. (#4907) (Vielen Dank an @joandrsn)
- Es wurden Funktionen zum Festlegen von Anmeldeinformationen für den `Set-Service`-Befehl hinzugefügt. (#4844) (Vielen Dank an @joandrsn)

### <a name="other-cmdlets"></a>Weitere Cmdlets

- `Get-ChildItem` wurde ein Parameter namens `-FollowSymlink` hinzugefügt, der bedarfsgesteuert symbolische Verknüpfungen mit Prüfungen auf Linkschleifen durchläuft. (#4020)
- `Add-Type` wurde aktualisiert und unterstützt nun `CSharpVersion7`. (#3933) (Vielen Dank an @iSazonov)
- Das `Microsoft.PowerShell.LocalAccounts`-Modul wurde aufgrund der Verwendung von nicht unterstützten APIs entfernt, bis eine bessere Lösung verfügbar ist. (#4302)
- `*-Counter`-Cmdlets wurden aufgrund der Verwendung von nicht unterstützten APIs aus `Microsoft.PowerShell.Diagnostics` entfernt, bis eine bessere Lösung verfügbar ist. (#4303)
- Support für `Invoke-Item -Path <folder>` wurde hinzugefügt. (#4262)
- `Split-Path` wurden die Schalter `-Extension` und `-LeafBase` hinzugefügt, sodass Pfade zwischen der Dateierweiterung und dem Rest des Dateinamens aufgeteilt werden können. (#2721) (Vielen Dank an @powercode)
- `Sort-Object` wurden die Parameter `-Top` und `-Bottom` für die Sortierung „Top/Bottom N“ hinzugefügt.
- Der übergeordnete Prozess eines Prozesses wurde durch Hinzufügen von `CodeProperty "Parent"` zu `System.Diagnostics.Process` verfügbar gemacht. (#2850) (Vielen Dank an @powercode)
- Für Speicherspalten von `Get-Process` werden MB statt KB verwendet.
- Der Schalter `-NoNewLine` wurde `Out-String` hinzugefügt. (#5056) (Vielen Dank an @raghav710)
- Das Cmdlet `Move-Item` berücksichtigt nun die Parameter `-Include`, `-Exclude` und `-Filter`. (#3878)
- `*` kann jetzt in Registrierungspfaden für `Remove-Item` verwendet werden. (#4866)
- `-Title` wurde `Get-Credential` hinzugefügt und die Benutzeroberfläche bei Aufforderungen plattformübergreifend vereinheitlicht.
- Der Parameter `-TimeOut` wurde `Test-Connection` hinzugefügt. (#2492)
- `Get-AuthenticodeSignature`-Cmdlets können nun Dateisignatur-Zeitstempel erhalten. (#4061)
- Der nicht unterstützte `-ShowWindow`-Schalter wurde aus `Get-Help` entfernt. (#4903)
- `Get-Content -Delimiter` enthält nun nicht mehr das von den Arrayelementen zurückgegebene Trennzeichen. (#3706) (Vielen Dank an @mklement0)
- `ConvertTo-HTML` wurden die Parameter `Meta`, `Charset` und `Transitional` hinzugefügt. (#4184) (Vielen Dank an @ergo3114)
- Dem `Get-ComputerInfo`-Ergebnis wurden die Eigenschaften `WindowsUBR` und `WindowsVersion` hinzugefügt.
- `-Group` wurde der `Get-Verb`-Parameter hinzugefügt.
- `New-FileCatalog` und `Test-FileCatalog` wurde Unterstützung für `ShouldProcess` hinzugefügt (behebt `-WhatIf` und `-Confirm`). (#3074) (Vielen Dank an @iSazonov)
- Dem Cmdlet `Start-Process` wurde der `-WhatIf`-Schalter hinzugefügt. (#4735) (Vielen Dank an @sarithsutha)
- Vielen vorhandenen Parametern wurde `ValidateNotNullOrEmpty` hinzugefügt.

## <a name="tab-completion"></a>Registerkartenvervollständigung

- Der Typrückschluss bei der Vervollständigung mit der TAB-TASTE wurde basierend auf den Variablenwerten der Common Language Runtime verbessert. (#2744) (Vielen Dank an @powercode) Dadurch funktioniert die Vervollständigung mit der TAB-TASTE z.B. in folgendem Fall:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Die Hashtabellen-Vervollständigung mit der TAB-TASTE wurde bei `-Property` von `Select-Object` hinzugefügt. (#3625) (Vielen Dank an @powercode)
- Die automatische Argumentvervollständigung wurde für `-ExcludeProperty` und `-ExpandProperty` von `Select-Object` hinzugefügt. (#3443) (Vielen Dank an @iSazonov)
- `native.exe --<tab>` ruft bei der Vervollständigung mit der TAB-TASTE den nativen Vervollständiger auf. (#3633) (Vielen Dank an @powercode)

## <a name="breaking-changes"></a>Wichtige Änderungen

Wir haben einige wichtige Änderungen in PowerShell Core 6.0 eingeführt.
Weitere Informationen finden Sie unter [Breaking Changes for PowerShell 6.0 (Wichtige Änderungen in PowerShell 6.0)][breaking-changes].

## <a name="debugging"></a>Debuggen

- Unterstützung für die Möglichkeit, das Remotedebuggen von `Invoke-Command -ComputerName` schrittweise zu durchlaufen. (#3015)
- Die Binderdebugprotokollierung wurde in PowerShell Core aktiviert.

## <a name="filesystem-updates"></a>Dateisystemupdates

- Der Dateisystemanbieter kann jetzt über einen UNC-Pfad verwendet werden. ($4998)
- `Split-Path` funktioniert nun mit UNC-Stämmen.
- `cd` ohne Argumente verhält sich nun wie `cd ~`.
- In PowerShell Core dürfen nun Pfade mit mehr als 260 Zeichen verwendet werden. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Fehlerbehebungen und Leistungsverbesserungen

Wir haben *viele* Leistungsverbesserungen in PowerShell vorgenommen, z.B. bei der Startzeit, bei verschiedenen integrierten Cmdlets sowie bei der Interaktion mit nativen Binärdateien.

Außerdem wurden einige Fehler in PowerShell Core behoben.
Eine vollständige Liste der Korrekturen und Änderungen finden Sie unter [Changelog (Änderungsprotokoll)][] auf GitHub.

## <a name="telemetry"></a>Telemetrie

- In PowerShell Core 6.0 wurde dem Konsolenhost Telemetrie hinzugefügt, um zwei Werte zu melden (#3620):
  - die Betriebssystemplattform (`$PSVersionTable.OSDescription`)
  - die genaue PowerShell-Version (`$PSVersionTable.GitCommitId`)

Wenn Sie diese Telemetriedaten nicht senden möchten, löschen Sie einfach `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY`.
Dadurch wird das Senden von Telemetriedaten bereits vor der ersten Ausführung von PowerShell unterbunden.
Diese Telemetriedaten und die Erkenntnisse, die wir daraus ziehen, sollen auf dem [Community-Dashboard][community-dashboard] veröffentlicht werden.
Weitere Informationen dazu, wie wir diese Daten verwenden, finden Sie [in diesem Blogbeitrag][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/en-us/dotnet/core/
[.NET Standard 2.0]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[Changelog (Änderungsprotokoll)]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET-Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube-Video]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[Häufig gestellte Fragen]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/en-us/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[Docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
