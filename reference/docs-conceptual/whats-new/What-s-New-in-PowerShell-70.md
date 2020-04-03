---
title: Neuerungen in PowerShell 7.0
description: In PowerShell 7.0 veröffentlichte neue Features und Änderungen
ms.date: 03/04/2020
ms.openlocfilehash: 84631d9fa169c8d1b4cd4dd23eb3d7c1bca120bb
ms.sourcegitcommit: b0966d61293e28ecdb929c5065be9760884e4e7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/25/2020
ms.locfileid: "80263134"
---
# <a name="whats-new-in-powershell-70"></a>Neuerungen in PowerShell 7.0

PowerShell 7.0 ist eine plattformübergreifende Open-Source-Edition (Windows, macOS und Linux) von PowerShell, die für die Verwaltung heterogener Umgebungen und Hybrid Clouds entwickelt wurde.

In diesem Release haben wir eine Reihe neuer Features eingeführt, einschließlich:

- Parallelisierung von Pipelines mit `ForEach-Object -Parallel`
- Neue Operatoren:
  - Ternärer Operator: `a ? b : c`
  - Pipeline-Kettenoperatoren: `||` und `&&`
  - Bedingte NULL-Operatoren: `??` und `??=`
- Eine vereinfachte und dynamische Fehleransicht und das Cmdlet `Get-Error` für eine einfachere Untersuchung von Fehlern
- Eine Kompatibilitätsebene, die es Benutzern ermöglicht, Module in eine implizite Windows PowerShell-Sitzung zu importieren
- Automatische Benachrichtigung zu neuen Versionen
- Die Möglichkeit zum direkten Aufrufen von DSC-Ressourcen in PowerShell 7 (experimentell)

Eine vollständige Liste der Features und Korrekturen finden Sie in den [Änderungsprotokollen](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md).

## <a name="where-can-i-install-powershell"></a>Wo kann ich PowerShell installieren?

PowerShell 7 unterstützt derzeit die folgenden x64-Betriebssysteme:

- Windows 8.1 und 10
- Windows Server 2012, 2012 R2, 2016, und 2019
- macOS ab 10.13
- Red Hat Enterprise Linux (RHEL)/CentOS 7
- Fedora ab 30
- Debian 9
- Ubuntu LTS ab 16.04
- Alpine Linux ab 3.8

Zusätzlich unterstützt PowerShell 7.0 die ARM32- und ARM64-Varianten von Debian, Ubuntu und ARM64 Alpine Linux.

Prüfen Sie die Installationsanweisungen für Ihr bevorzugtes Betriebssystem: [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) oder [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).

Wenngleich nicht offiziell unterstützt, hat die Community auch Pakete für [Arch](https://aur.archlinux.org/packages/powershell/) und Kali Linux bereitgestellt.

> [!NOTE]
> Debian 10 und CentOS 8 unterstützen zurzeit nicht WinRM-Remoting. Einzelheiten zum Einrichten von SSH-basiertem Remoting finden Sie unter [PowerShell-Remoting über SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).

Weitere aktuelle Informationen zu unterstützten Betriebssystemen und zum Supportlebenszyklus finden Sie unter [PowerShell-Supportlebenszyklus](/powershell/scripting/powershell-support-lifecycle?view=powershell-7).

## <a name="running-powershell-7"></a>Ausführen von PowerShell 7

PowerShell 7 wird in ein neues Verzeichnis installiert und parallel mit Windows PowerShell 5.1 ausgeführt. Für PowerShell Core 6.x ist PowerShell 7 ein direktes Upgrade, durch das PowerShell Core 6.x entfernt wird.

- PowerShell 7 wird in `%programfiles%\PowerShell\7` installiert.
- Der Ordner `%programfiles%\PowerShell\7` wird `$env:PATH` hinzugefügt.

Das Installationsprogramm von PowerShell 7 aktualisiert frühere Versionen von PowerShell Core 6.x:

- PowerShell Core 6. x unter Windows: `%programfiles%\PowerShell\6` wird durch `%programfiles%\PowerShell\7` ersetzt.
- Linux: `/opt/microsoft/powershell/6` wird durch `/opt/microsoft/powershell/7` ersetzt.
- macOS: `/usr/local/microsoft/powershell/6` wird durch `/usr/local/microsoft/powershell/7` ersetzt.

> [!NOTE]
> In Windows PowerShell heißt die ausführbare Datei zum Starten von PowerShell `powershell.exe`. Ab Version 6 wurde die ausführbare Datei so geändert, dass die parallele Ausführung unterstützt wird. Die neue ausführbare Datei zum Starten von PowerShell 7 ist `pwsh.exe`. Vorschaubuilds bleiben als `pwsh-preview` anstelle von `pwsh` im Verzeichnis „7-preview“ erhalten.

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>Verbesserte Abwärtskompatibilität mit Windows PowerShell

PowerShell 7.0 markiert einen Wechsel zu .NET Core 3.1, wodurch eine wesentlich bessere Abwärtskompatibilität mit vorhandenen Windows PowerShell-Modulen ermöglicht wird. Dazu gehören viele Module unter Windows, die GUI-Funktionalität benötigen, wie `Out-GridView` und `Show-Command`, sowie viele Rollenverwaltungsmodule, die Teil von Windows sind.

Für Windows wurde `Import-Module` der neue Schalterparameter **UseWindowsPowerShell** hinzugefügt. Dieser Schalter erstellt in PowerShell 7 ein Proxymodul, das einen lokalen Windows PowerShell-Prozess verwendet, um alle in diesem Modul enthaltenen Cmdlets implizit auszuführen. Weitere Informationen finden Sie unter [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).

Weitere Informationen dazu, welche Microsoft-Module mit PowerShell 7.0 funktionieren, finden Sie in der [Tabelle zur Modulkompatibilität](https://aka.ms/PSModuleCompat).

## <a name="parallel-execution-added-to-foreach-object"></a>Parallele Ausführung zu ForEach-Object hinzugefügt

Das Cmdlet `ForEach-Object`, das Elemente in einer Sammlung iteriert, zeichnet sich nun dank des neuen Parameters **Parallel** durch integrierte Parallelität aus.

Standardmäßig verwenden parallele Skriptblöcke das aktuelle Arbeitsverzeichnis des Aufrufers, der die parallelen Aufgaben gestartet hat.

In diesem Beispiel werden 50.000 Protokolleinträge aus 5 Systemprotokollen auf einem lokalen Windows-Computer abgerufen:

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

Der Parameter **Parallel** gibt den Skriptblock an, der für jeden Eingabeprotokollnamen parallel ausgeführt wird.

Der neue Parameter **ThrottleLimit** begrenzt die Anzahl der zu einer bestimmten Zeit parallel ausgeführten Skriptblöcke. Der Standardwert ist 5.

Verwenden Sie die Variable `$_`, um das aktuelle Eingabeobjekt im Skriptblock darzustellen. Verwenden Sie den Bereich `$using:`, um Variablenverweise an den ausgeführten Skriptblock zu übergeben.

Weitere Informationen finden Sie unter [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).

## <a name="ternary-operator"></a>Ternärer Operator

PowerShell 7.0 führt einen ternären Operator ein, der sich wie eine vereinfachte `if-else`-Anweisung verhält.
Der ternäre Operator von PowerShell ist eng an die Syntax des ternären Operators in C# angelehnt:

```
<condition> ? <if-true> : <if-false>
```

Der Bedingungsausdruck wird stets ausgewertet und sein Ergebnis in einen **booleschen Wert** konvertiert, um zu bestimmen, welcher Zweig als Nächstes ausgewertet wird:

- Der Ausdruck `<if-true>` wird ausgeführt, wenn der Ausdruck `<condition>` TRUE ist.
- Der Ausdruck `<if-false>` wird ausgeführt, wenn der Ausdruck `<condition>` FALSE ist.

Beispiel:

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

Wenn in diesem Beispiel der Pfad vorhanden ist, wird **Pfad vorhanden** angezeigt. Wenn der Pfad nicht vorhanden ist, wird **Pfad nicht gefunden** angezeigt.

Weitere Informationen finden Sie unter [Informationen zu „If“](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).

## <a name="pipeline-chain-operators"></a>Pipeline-Kettenoperatoren

PowerShell 7 implementiert die Operatoren `&&` und `||`, um Pipelines bedingt zu verketten. Diese Operatoren werden in PowerShell als „Pipeline-Kettenoperatoren“ bezeichnet und ähneln AND- und OR-Listen in Shells wie **Bash** und **Zsh** sowie bedingten Verarbeitungssymbolen in der Windows-Befehlsshell (**cmd.exe**).

Der Operator `&&` führt die rechte Pipeline aus, wenn die linke Pipeline erfolgreich war. Dagegen führt der Operator `||` die rechte Pipeline aus, wenn die linke Pipeline fehlgeschlagen ist.

> [!NOTE]
> Diese Operatoren verwenden die Variablen `$?` und `$LASTEXITCODE`, um zu bestimmen, ob eine Pipeline fehlgeschlagen ist. Dadurch können Sie sie mit nativen Befehlen und nicht bloß mit Cmdlets oder Funktionen verwenden.

Hier ist der erste Befehl erfolgreich, und der zweite Befehl wird ausgeführt:

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

Hier schlägt der erste Befehl fehl, der zweite wird nicht ausgeführt:

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

Hier ist der erste Befehl erfolgreich, der zweite Befehl wird nicht ausgeführt:

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

Hier schlägt der erste Befehl fehl, sodass der zweite Befehl ausgeführt wird:

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

Weitere Informationen zu finden Sie unter [Informationen zu Pipeline-Kettenoperatoren](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).

## <a name="null-coalescing-assignment-and-conditional-operators"></a>NULL-Sammeloperator, Zuweisung und bedingte Operatoren

PowerShell 7 bietet den NULL-Sammeloperator `??`, die Zuweisung mit NULL-Bedingung `??=` sowie die Zugriffsoperatoren `?.` und `?[]` für Member mit NULL-Bedingung.

### <a name="null-coalescing-operator-"></a>NULL-Sammeloperator ??

Der NULL-Sammeloperator `??` gibt den Wert seines linken Operanden zurück, wenn er nicht NULL ist.
Andernfalls wertet er den rechten Operanden aus und gibt sein Ergebnis zurück. Der Operator `??` wertet seinen rechten Operanden nicht aus, wenn der linke Operand mit ungleich NULL auswertet wird.

```powershell
$x = $null
$x ?? 100
100
```

Im folgenden Beispiel wird der rechte Operand nicht ausgewertet:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Zuweisungsoperator mit NULL-Bedingung ??=

Der Zuweisungsoperator mit NULL-Bedingung `??=` weist den Wert seines rechten Operanden dem linken Operanden nur zu, wenn der linke Operand mit NULL ausgewertet wird. Der Operator `??=` wertet seinen rechten Operanden nicht aus, wenn der linke Operand mit ungleich NULL auswertet wird.

```powershell
$x = $null
$x ??= 100
$x
100
```

Im folgenden Beispiel wird der rechte Operand nicht ausgewertet:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Zugriffsoperatoren für Member mit NULL-Bedingung ?. und ?[] (experimentell)

> [!NOTE]
> Dies ist ein experimentelles Feature mit dem Namen **PSNullConditionalOperators**. Weitere Informationen finden Sie unter [Informationen zu experimentellen Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

Ein bedingter NULL-Operator erlaubt den Memberzugriff (`?.`) oder Elementzugriff (`?[]`) auf seinen Operanden nur dann, wenn dieser Operand mit ungleich NULL ausgewertet wird. Andernfalls gibt er NULL zurück.

> [!NOTE]
> Da PowerShell erlaubt, dass `?` Teil des Variablennamens ist, ist für die Verwendung dieser Operatoren die formale Angabe des Variablennamens erforderlich. Daher ist es nötig, `{}` um die Variablennamen herum zu platzieren, wie z. B. `${a}` oder wenn `?` Teil des Variablennamens `${a?}` ist.

Im folgenden Beispiel wird der Wert der Membereigenschaft **Status** zurückgegeben:

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

Das folgende Beispiel gibt NULL zurück, ohne dass versucht wird, auf den Membernamen **Status** zuzugreifen:

```powershell
$service = $Null
${Service}?.status
```

Analog wird bei Verwendung von `?[]` der Wert des Elements zurückgegeben:

```powershell
$a = 1..10
${a}?[0]
1
```

Wenn der Operand NULL ist, wird nicht auf das Element zugegriffen und NULL zurückgegeben:

```powershell
$a = $null
${a}?[0]
```

Weitere Informationen finden Sie unter [Informationen zu Operatoren](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7).

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>Neue Ansicht ConciseView und neues Cmdlet Get-Error

Die Anzeige von Fehlermeldungen wurde verbessert, um die Lesbarkeit von Interaktions- und Skriptfehlern mithilfe einer neuen Standardansicht namens **ConciseView** zu verbessern. Die Ansichten sind vom Benutzer über die Einstellungsvariable `$ErrorView` auswählbar.

Wenn bei **ConciseView** ein Fehler nicht von einem Skript- oder Parserfehler herrührt, handelt es sich um eine einzeilige Fehlermeldung:

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

Wenn der Fehler während der Skriptausführung auftritt oder ein Analysefehler ist, gibt PowerShell eine mehrzeilige Fehlermeldung zurück. Diese enthält den Fehler, einen Zeiger und eine Fehlermeldung, die angibt, wo der Fehler in dieser Zeile vorliegt. Wenn das Terminal keine farbigen Escapesequenzen nach ANSI (VT100) unterstützt, werden keine Farben angezeigt.

![Fehleranzeige in einem Skript](./media/What-s-New-in-PowerShell-70/myscript-error.png)

Die Standardansicht in PowerShell 7 ist **ConciseView**. Die vorherige Standardansicht war **NormalView**, die vom Benutzer durch Festlegen der Einstellungsvariablen `$ErrorView` ausgewählt werden kann.

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> Die neue Eigenschaft **ErrorAccentColor** wird zu `$Host.PrivateData` hinzugefügt, um die Änderung der Akzentfarbe der Fehlermeldung zu unterstützen.

Das neue Cmdlet `Get-Error` bietet auf Wunsch eine vollständige Detailansicht des vollqualifizierten Fehlers.
Standardmäßig zeigt das Cmdlet die vollständigen Details, einschließlich innerer Ausnahmen, des zuletzt aufgetretenen Fehlers an.

![Anzeige aus Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

Das Cmdlet `Get-Error` unterstützt die Eingabe aus der Pipeline unter Verwendung der integrierten Variablen `$Error`.
`Get-Error` zeigt alle weitergeleiteten Fehler an.

```powershell
$Error | Get-Error
```

Das Cmdlet `Get-Error` unterstützt den Parameter **Newest**, mit dem Sie angeben können, wie viele Fehler aus der aktuellen Sitzung angezeigt werden sollen.

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

Weitere Informationen finden Sie unter [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).

## <a name="new-version-notification"></a>Benachrichtigung zu neuen Versionen

PowerShell 7 verwendet Updatebenachrichtigungen, um Benutzer über das Vorhandensein von Updates für PowerShell zu informieren.
Einmal pro Tag fragt PowerShell einen Onlinedienst ab, um zu prüfen, ob eine neuere Version verfügbar ist.

> [!NOTE]
> Die Prüfung auf Updates erfolgt während der ersten Sitzung innerhalb eines bestimmten 24-stündigen Zeitraums. Aus Leistungsgründen beginnt die Prüfung auf Updates 3 Sekunden nach Beginn der Sitzung. Die Benachrichtigung wird nur zu Beginn nachfolgender Sitzungen angezeigt.

Standardmäßig abonniert PowerShell je nach Version/Branch einen von zwei verschiedenen Benachrichtigungskanälen. Unterstützte, allgemein verfügbare (GA-) Versionen von PowerShell geben nur für aktualisierte GA-Releases Benachrichtigungen zurück. Vorschau- und Release Candidate-Releases (RC) benachrichtigen über Updates für Vorschau-, RC- und GA-Releases.

Das Verhalten der Updatebenachrichtigung kann mithilfe der Umgebungsvariablen `$Env:POWERSHELL_UPDATECHECK` geändert werden. Die folgenden Werte werden unterstützt:

- **Default** entspricht der Nichtangabe von `$Env:POWERSHELL_UPDATECHECK`.
  - GA-Releases benachrichtigen zu Updates von GA-Releases.
  - Vorschau-/RC-Releases benachrichtigen zu Updates von GA- und Vorschau-Releases.
- **Off** deaktiviert das Feature zur Updatebenachrichtigung.
- **LTS** benachrichtigt nur zu Updates für LTS GA-Releases (Long-Term-Servicing).

> [!NOTE]
> Die Umgebungsvariable `$Env:POWERSHELL_UPDATECHECK` ist erst vorhanden, nachdem sie zum ersten Mal festgelegt wurde.

So legen Sie die Versionsbenachrichtigung nur für `LTS`-Releases fest

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

So legen Sie die Versionsbenachrichtigung auf das `Default`-Verhalten fest

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

Weitere Informationen finden Sie unter [Informationen zu Updatebenachrichtigungen](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>Unterstützung für neue DSC-Ressourcen mit Invoke-DSCResource (experimentell)

> [!NOTE]
> Dies ist ein experimentelles Feature mit dem Namen **PSDesiredStateConfiguration.InvokeDscResource**. Weitere Informationen finden Sie unter [Informationen zu experimentellen Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

Mit dem Cmdlet `Invoke-DscResource` wird eine Methode einer angegebenen PowerShell DSC-Ressource (Desired State Configuration) ausgeführt.

Dieses Cmdlet ruft eine DSC-Ressource direkt auf, ohne ein Konfigurationsdokument zu erstellen. Mit diesem Cmdlet können Konfigurationsverwaltungsprodukte Windows oder Linux mithilfe von DSC-Ressourcen verwalten. Dieses Cmdlet ermöglicht auch das Debuggen von Ressourcen, wenn die DSC-Engine mit aktiviertem Debuggen ausgeführt wird.

Dieser Befehl ruft die **Set**-Methode einer Ressource namens „Log“ auf und gibt eine **Message**-Eigenschaft an.

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

Weitere Informationen finden Sie unter [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).

## <a name="breaking-changes-and-improvements"></a>Breaking Changes und Verbesserungen

### <a name="breaking-changes"></a>Aktuelle Änderungen

- Bewirken, dass Updatebenachrichtigungen LTS und Standardkanäle unterstützen (#11132)
- Aktualisierung von Test-Connection, damit das Cmdlet mehr wie in Windows PowerShell funktioniert (#10697) (vielen Dank an @vexx32!)
- Beibehaltung von $? für ParenExpression, SubExpression und ArrayExpression (#11040)
- Festlegung des Arbeitsverzeichnisses auf das aktuelle Verzeichnis in Start-Job (#10920) (vielen Dank an @iSazonov!)
- Veranlassen, dass $PSCulture Veränderungen der Kultur innerhalb der Sitzung konsistent widerspiegelt (#10138) (vielen Dank an @iSazonov!)

### <a name="engine-updates-and-fixes"></a>Engineupdates und Fixes

- Verbesserungen bei Haltepunkt-APIs für Remoteszenarien (#11312)
- Korrektur des Entweichens von PowerShell-Klassendefinition in einen anderen Runspace (#11273)
- Korrektur einer Regression in der Formatierung, die durch die in 7.0.0-Preview1 hinzugefügte Primitive FirstOrDefault verursacht wurde (#11258)
- Zusätzliche in PS7-Telemetrie nachzuverfolgende Microsoft-Module (#10751)
- Festlegung genehmigter Features als nicht experimentell (#11303)
- Aktualisierung von ConciseView für die Verwendung von TargetObject, falls zutreffend (#11075)
- Korrektur von NullReferenceException in öffentlichen CompletionCompleters-Methoden (#11274)
- Korrektur der Überprüfung des Status des Apartment-Threads auf Nicht-Windows-Plattformen (#11301)
- Aktualisierung der Einstellung PSModulePath dergestalt, dass Prozess- und Computerumgebungsvariablen verkettet werden (#11276)
- Aktualisierung von .NET Core auf 3.1.0 (#11260)
- Korrektur der Erkennung von $PSHOME vor $env:PATH (#11141)
- Zulassen, dass pwsh $env:PSModulePath erbt, und ermöglichen, dass powershell.exe ordnungsgemäß gestartet wird (#11057)
- Umstieg auf .NET Core 3.1 Preview 1 (#10798)
- Umgestaltung von Tagprüfungen nach erneuter Analyse in Dateisystemanbieter (#10431) (vielen Dank an @iSazonov!)
- Ersetzung von Wagenrücklauf- und Zeilenvorschubzeichen (CR und LF) durch das Zeichen 0x23CE in Skriptprotokollierung (#10616)
- Korrektur eines Ressourcenlecks durch Aufheben der Registrierung des Ereignisbehandlers in AppDomain.CurrentDomain.ProcessExit (#10626)
- Hinzufügung von Unterstützung für ActionPreference.break, um den Debugger anzuhalten, wenn Debug-, Fehler-, Informations-, Status-, ausführliche oder Warnmeldungen generiert werden (#8205) (vielen Dank an @KirkMunro!)
- Aktivierung des Starts von Systemsteuerungs-Add-Ins in PowerShell Core ohne Angabe der CPL-Erweiterung. (#9828)
- Unterstützung negativer Zahlen im Operator -split (#8960) (vielen Dank an @ece-jacob-scott!)

### <a name="general-cmdlet-updates-and-fixes"></a>Allgemeine Cmdletupdates und Korrekturen

- Korrektur für Problem in Raspbian beim Festlegen des Datums von Dateiänderungen im experimentellen Feature UnixStat (#11313)
- Hinzufügung von -AsPlainText zu ConvertFrom-SecureString (#11142)
- Prüfung der WindowsPS-Version für WinCompat hinzugefügt (#11148)
- Korrektur der Fehlerberichterstellung in einigen WinCompat-Szenarien (#11259)
- Hinzufügung von nativem binären Konfliktlöser (#11032) (vielen Dank an@iSazonov!)
- Aktualisierung der Berechnung der Zeichenbreite unter vollständiger Berücksichtigung von CJK-Zeichen (#11262)
- Hinzufügung von Unblock-File für macOS (#11137)
- Korrektur von Regression in Get-PSCallStack (#11210) (vielen Dank an @iSazonov!)
- Entfernung des automatischen Ladens des Moduls ScheduledJob bei Verwendung von Job-Cmdlets (#11194)
- Hinzufügung von OutputType zum Cmdlet Get-Error und Beibehaltung ursprünglicher Typnamen (#10856)
- Korrektur des NULL-Verweises in der Eigenschaft SupportsVirtualTerminal (#11105)
- Hinzufügung der Grenzwertprüfung in Get-WinEvent (#10648) (vielen Dank an @iSazonov!)
- Korrektur der Befehlslaufzeit dahingehend, dass StopUpstreamCommandsException in -ErrorVariable nicht aufgefüllt wird (#10840)
- Festlegung der Ausgabecodierung auf [Console]::OutputEncoding für native Befehle (#10824)
- Unterstützung mehrzeiliger Codeblöcke in Beispielen (#10776) (vielen Dank an @Greg-Smulko!)
- Hinzufügung des Culture-Parameters zum Cmdlet Select-String (#10943) (vielen Dank an @iSazonov!)
- Korrektur des Arbeitsverzeichnispfads von Start-Job mit nachgestelltem Rückwärtsschrägstrich (#11041)
- ConvertFrom-Json: Standardmäßiges Aufheben des Umbruchs in Sammlungen (#10861) (vielen Dank an @danstur!)
- Unterscheidung von Groß-/Kleinschreibung für das Cmdlet Group-Object mit den Schaltern -CaseSensitive und -AsHashtable (#11030) (vielen Dank an @vexx32!)
- Behandlung der Ausnahme, wenn die Aufzählung von Dateien beim Neuerstellen des Pfads fehlschlägt, um die richtige Schreibweise zu erhalten (#11014)
- Korrektur von ConciseView zur Anzeige von Activity statt myCommand (#11007)
- Zulassen, dass Web-Cmdlets HTTP-Fehlerstatus ignorieren (#10466) (vielen Dank an @vdamewood!)
- Korrektur der Weiterleitung von mehr als einer CommandInfo an Get-Command (#10929)
- Wiederhinzufügung des Cmdlets Get-Counter für Windows (#10933)
- Veranlassen, dass ConvertTo-Json [AutomationNull]::Value und [NullString]::Value als $null behandelt (#10957)
- Entfernung von Klammern aus der IPv6-Adresse für SSH-Remoting (#10968)
- Kein Absturz mehr, wenn der an pwsh gesendete Befehl nur aus Leerzeichen besteht (#10977)
- Plattformübergreifende Cmdlets Get-Clipboard und Set-Clipboard hinzugefügt (#10340)
- Korrektur der Festlegung des Ursprungspfads eines Dateisystemobjekts dahingehend, dass es keinen zusätzlichen nachstehenden Schrägstrich aufweist (#10959)
- Unterstützung von $null für ConvertTo-Json (#10947)
- Wiederhinzufügung des Befehls Out-Printer für Windows (#10906)
- Korrektur von -WorkingDirectory für Start-Job mit Leerzeichen (#10951)
- Rückgabe des Standardwerts, wenn für eine Einstellung in PSConfiguration.cs der Wert NULL abgerufen wird (#10963) (vielen Dank an @iSazonov!)
- Behandlung von E/A-Ausnahme als nicht beendend (#10950)
- Hinzufügung der Assembly GraphicalHost zur Aktivierung von Out-GridView, Show-Command und Get-Help -ShowWindow (#10899)
- Verwenden von ComputerName über Pipeline in Get-HotFix (#10852) (vielen Dank an @kvprasoon!)
- Korrektur der Vervollständigung per TAB-TASTE für Parameter dergestalt, dass allgemeine Parameter als verfügbar angezeigt werden (#10850)
- Korrektur von GetCorrectCasedPath(), um vor dem Aufruf von First() zunächst zu prüfen, ob Systemdateieinträge zurückgegeben werden (#10930)
- Festlegung des Arbeitsverzeichnisses auf das aktuelle Verzeichnis in Start-Job (#10920) (vielen Dank an @iSazonov!)
- Ändern von TabExpansion2 dahingehend, dass -CursorColumn nicht erforderlich ist und als $InputScript.Length behandelt wird (#10849)
- Behandeln des Falls, bei dem Host möglicherweise keine Zeilen oder Spalten des Bildschirms zurückgibt (#10938)
- Korrektur der Verwendung von Akzentfarben für Hosts, die diese nicht unterstützen (#10937)
- Wiederhinzufügung des Befehls Update-List (#10922)
- Aktualisierung von FWLink Id für Clear-RecycleBin (#10925)
- Überspringen der Datei während der Vervollständigung per TAB-TASTE, wenn Dateiattribute nicht gelesen werden können (#10910)
- Wiederhinzufügung von Clear-RecycleBin für Windows (#10909)
- Hinzufügung von `$env:__SuppressAnsiEscapeSequences` zum Steuern, ob bei der Ausgabe eine VT-Escapesequenz verwendet werden soll (#10814)
- Hinzufügung des Parameters -NoEmphasize zur farbigen Darstellung der Ausgabe von Select-String (#8963) (vielen Dank an @derek-xia!)
- Wiederhinzufügung des Cmdlets Get-HotFix (#10740)
- Ermöglichung des Verwendens von Add-Type in Anwendungen, die PowerShell hosten (#10587)
- Verwendung einer effektiveren Auswertungsreihenfolge in LanguagePrimitives.IsNullLike() (#10781) (vielen Dank an @vexx32!)
- Verbesserung der Handhabung gemischter Sammlungen von weitergeleiteten Eingaben und weitergeleiteten Datenströmen in Format-Hex (#8674) (vielen Dank an @vexx32!)
- Verwendung der Typkonvertierung in Hashtabellen für SSHConnection, wenn der Wert nicht dem erwarteten Typ entspricht (#10720) (vielen Dank an @SeeminglyScience!)
- Korrektur des Verhaltens von Get-Content -ReadCount 0, wenn -TotalCount festgelegt ist (#10749) (vielen Dank an @eugenesmlv!)
- Umformulierung der Fehlermeldung des Typs „Zugriff verweigert“ in Get-WinEvent (#10639) (vielen Dank an @iSazonov!)
- Aktivierung der Vervollständigung per TAB-TASTE zur Variablenzuweisung bei Einschränkung von Enumeration oder Typ (#10646)
- Entfernung der nicht verwendeten Remotingeigenschaft SourceLength, die Formatierungsprobleme verursacht (#10765)
- Hinzufügung des Parameters -Delimiter zu ConvertFrom-StringData (#10665) (vielen Dank an @steviecoaster!)
- Hinzufügung von Positionsparameter für ScriptBlock bei Verwendung von Invoke-Command mit SSH (#10721) (vielen Dank an @machgo!)
- Anzeige von Zeilenkontextinformationen bei mehreren Zeilen, aber keinen Skriptnamen für ConciseView (#10746)
- Hinzufügung von Unterstützung für Pfade des Typs \\wsl$\ zu Dateisystemanbieter (#10674)
- Hinzufügung des fehlenden Tokentexts für TokenKind.QuestionMark im Parser (#10706)
- Festlegung des aktuellen Arbeitsverzeichnisses jedes ausgeführten Skripts des Typs ForEach-Object -Parallel auf einen Ort, der mit dem aufrufenden Skript identisch ist. (#10672)
- Ersetzung von api-ms-win-core-file-l1-2-2.dll durch Kernell32.dll für die APIs FindFirstStreamW und FindNextStreamW (#10680) (vielen Dank an @iSazonov!)
- Optimierung des Hilfeformatierungsskripts, um toleranter gegenüber StrictMode zu sein (#10563)
- Hinzufügen des Parameters -SecurityDescriptorSDDL zu New-Service (#10483) (vielen Dank an @kvprasoon!)
- Entfernung von Informationsausgaben, Konsolidierung der Nutzung von Ping in Test-Connection (#10478) (vielen Dank an @vexx32!)
- Lesen spezieller Analysepunkte, ohne auf sie zuzugreifen (#10662) (vielen Dank an @iSazonov!)
- Direkte Clear-Host-Ausgabe an Terminal (#10681) (vielen Dank an @iSazonov!)
- Wiederhinzufügung eines Zeilenvorschubzeichens für Gruppierung mit Format-Table und -Property (#10653)
- Entfernung von [ValidateNotNullOrEmpty] aus -InputObject für Get-Random, um eine leere Zeichenfolge zuzulassen (#10644)
- Keine Unterscheidung von Groß-/Kleinschreibung für Entfernungsalgorithmus in Zeichenfolgen des Vorschlagsystems (#10549) (vielen Dank an@iSazonov!)
- Korrektur von NULL-Verweisausnahme in Eingabeverarbeitung für ForEach-Object -Parallel (#10577)
- Hinzufügung von PowerShell Core-Gruppenrichtliniendefinitionen (#10468)
- Aktualisierung des Konsolenhosts zur Unterstützung von XTPUSHSGR/XTPOPSGR VT-Steuersequenzen, die in Zusammensetzbarkeitsszenarien verwendet werden. (#10208)
- Hinzufügung des Parameters WorkingDirectory zu Start-Job (#10324) (vielen Dank an @davinci26!)
- Entfernung des Ereignishandlers, der dazu geführt hat, dass Änderungen an Haltepunkten fälschlicherweise in den Runspacedebugger des Hosts repliziert wurden (#10503) (vielen Dank an @KirkMunro!)
- Austausch von api-ms-win-core-job-12-1-0.dll durch Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke-API (#10417) (vielen Dank an @iSazonov!)
- Korrektur der falschen Ausgabe für New-Service bei der Variablenzuweisung und -OutVariable (#10444) (vielen Dank an @kvprasoon!)
- Korrektur globaler Toolprobleme bei Exitcode, Befehlszeilenparameter und Pfad mit Leerzeichen (#10461)
- Korrektur der Rekursion in OneDrive: Ändern Sie FindFirstFileEx() so, dass der SafeFindHandle-Typ verwendet wird (#10405)
- Überspringen des automatischen Ladens von PSReadLine unter Windows, wenn die NVDA-Sprachausgabe aktiv ist (#10385)
- Erhöhung der built-with-PowerShell-Modulversionen auf 7.0.0.0 (#10356)
- Hinzufügen des Auslösens eines Fehlers in Add-Type, wenn ein Typ mit dem gleichen Namen bereits existiert (#9609) (vielen Dank an @iSazonov!)

### <a name="performance"></a>Leistung

- Vermeidung der Verwendung des Abschlusses in Parser.SaveError (#11006)
- Verbesserung des Zwischenspeicherns beim Erstellen neuer RegEx-Instanzen (#10657) (vielen Dank an @iSazonov!)
- Verbesserte Verarbeitung der in PowerShell integrierten Typdaten aus types.ps1xml, typesV3.ps1xml und GetEvent.types.ps1xml (#10898)
- Aktualisierung von PSConfiguration.ReadValueFromFile, um es schneller und speichereffizienter zu machen (#10839)
- Hinzufügung kleinerer Leistungsverbesserungen für die Initialisierung von Runspaces (#10569) (Thanks @iSazonov!)
- Beschleunigung von ForEach-Object in häufig verwendeten Szenarien (#10454) und Behebung des Leistungsproblems mit ForEach-Object -Parallel in vielen Runspaces (#10455)

### <a name="code-cleanup"></a>Codebereinigung

- Änderung von Kommentaren und Elementtexten gemäß Microsoft-Standards (#11304)
- Bereinigung von Stilproblemen in Compiler.cs (#10368) (vielen Dank an @iSazonov!)
- Entfernung des nicht verwendeten Typkonverters für CommaDelimitedStringCollection (#11000) (vielen Dank an @iSazonov!)
- Bereinigung des Stils in InitialSessionState.cs (#10865) (Thanks @iSazonov!)
- Codebereinigung für PSSession-Klasse (#11001)
- Entfernung des nicht funktionierenden Features „Update-Help in Get-Help ausführen, wenn Get-Help zum ersten Mal ausgeführt wird“ (#10974)
- Behebung von Stilproblemen (#10998) (vielen Dank an @iSazonov!)
- Bereinigung: Verwenden Sie den integrierten Typalias. (#10882) (vielen Dank an @iSazonov!)
- Entfernung des nicht verwendeten Einstellungsschlüssels ConsolePrompting und Vermeidung der unnötigen Zeichenfolgenerstellung beim Abfragen der Einstellung ExecutionPolicy (#10985)
- Deaktivieren der Updatebenachrichtigungsprüfung für tägliche Builds (#10903) (vielen Dank an @bergmeister!)
- Reaktivierung der in #10338 verloren gegangenen Debug-API (#10808)
- Entfernung des WorkflowJobSourceAdapter-Verweises, der nicht mehr verwendet wird (#10326) (vielen Dank an @KirkMunro!)
- Bereinigung von COM-Schnittstellen im Sprunglistencode durch Korrektur von PreserveSig-Attributen (#9899) (vielen Dank an @weltkante!)
- Hinzufügung eines Kommentars, der beschreibt, warum -ia nicht der Alias für den allgemeinen Parameter -InformationAction ist (#10703) (vielen Dank an @KirkMunro!)
- Umbenennung von InvokeCommandCmdlet.cs in InvokeExpressionCommand.cs (#10659) (vielen Dank an @kilasuit!)
- Hinzufügung geringfügiger Codebereinigungen im Zusammenhang mit Updatebenachrichtigungen (#10698)
- Entfernung veralteter Workflowlogik aus den Skripts für das Remotesetup (#10320) (vielen Dank an @KirkMunro!)
- Aktualisierung des Hilfeformats in die Verwendung der richtigen Schreibweise (#10678) (vielen Dank an @tnieto88!)
- Bereinigung von CodeFactor-Stilproblemen bei Commits im letzten Monat (#10591) (vielen Dank an @iSazonov!)
- Korrektur eines Tippfehlers in der Beschreibung des experimentellen Features PSTernaryOperator (#10586) (vielen Dank an @bergmeister!)
- Konvertierung des Enumerationswerts ActionPreference.suspend in einen nicht unterstützten, reservierten Zustand und Aufhebung der Einschränkung für die Verwendung von ActionPreference.Ignore in Einstellungsvariablen (#10317) (vielen Dank an @KirkMunro!)
- Austausch von ArrayList durch List<T>, um besser lesbaren und zuverlässigeren Code zu erhalten, ohne Funktionalität zu ändern (#10333) (vielen Dank an @iSazonov!)
- Korrekturen am Codestil für TestConnectionCommand (#10439) (vielen Dank an @vexx32!)
- Bereinigung von AutomationEngine und Entfernung des zusätzlichen Aufrufs der SetSessionStateDrive-Methode (#10416) (vielen Dank an @iSazonov!)
- Umbenennung der Standardeinstellung ParameterSetName zurück in Delimiter für ConvertTo-Csv und ConvertFrom-Csv (#10425)

### <a name="tools"></a>Tools

- Hinzufügung einer Standardeinstellung für die SDKToUse-Eigenschaft für Builds in VS (#11085)
- Install-Powershell.ps1: Hinzufügung eines Parameters, um die MSI-Installation zu verwenden (#10921) (vielen Dank an @MJECloud!)
- Hinzufügung einfacher Beispiele für install-powershell.ps1 (#10914) (vielen Dank an @kilasuit!)
- Veranlassen, dass Install-PowerShellRemoting.ps1 eine leere Zeichenfolge im PowerShellHome-Parameter behandelt (#10526) (vielen Dank an @Orca88!)
- Wechsel von /etc/lsb-release zu /etc/os-release in install-powershell.sh (#10773) (vielen Dank an @Himura2la!)
- Überprüfung von pwsh.exe und pwsh in täglicher Version unter Windows (#10738) (vielen Dank an @centreboard!)
- Entfernen von unnötigem Tippen aus installpsh-osx.sh (#10752)
- Aktualisierung von install-powershell.ps1 zur Überprüfung auf bereits installierte tägliche Builds (#10489)

### <a name="tests"></a>Tests

- Unzuverlässigen DSC-Test ausstehend gestalten (#11131)
- Korrektur des Tests von Zeichenfolgendaten für die ordnungsgemäße Validierung von Schlüsseln von Hashtabellen (#10810)
- Entladung von Testmodulen (#11061) (vielen Dank an @iSazonov!)
- Verlängerung der Zeit zwischen Wiederholungen der Test-URL (#11015)
- Aktualisieren vom Tests, um Testaktionen genau zu beschreiben. (#10928) (vielen Dank an @romero126!)
- Temporäres Überspringen des unzuverlässigen Tests TestAppDomainProcessExitEvenHandlerNotLeaking (#10827)
- Stabilisierung des Ereignishandlertests auf Lecks (#10790)
- Synchronisieren der Großbeschreibung in CI YAML (#10767) (vielen Dank an @RDIL!)
- Hinzufügung eines Tests für die Korrektur des Ereignishandlerlecks (#10768)
- Hinzufügung eines Tests von Get-ChildItem (#10507) (vielen Dank an @iSazonov!)
- Ersetzung mehrdeutiger Sprache für Tests von Schalter zu Parameter für Genauigkeit (#10666) (vielen Dank an @romero126!)
- Hinzufügung einer experimentellen Prüfung zu Tests von ForEach-Object -Parallel (#10354) (vielen Dank an @KirkMunro!)
- Aktualisierung von Tests für Alpine-Validierung (#10428)

### <a name="build-and-package-improvements"></a>Verbesserungen von Build- und Packvorgängen

- Korrektur der Signierung von NuGet-Paketen für den Coordinated Package-Build (#11316)
- Aktualisierung von Abhängigkeiten in PowerShell-Katalog und NuGet (#11323)
- Aktualisierung von Microsoft.ApplicationInsights von 2.11.0 auf 2.12.0 (#11305)
- Aktualisierung vonMicrosoft.CodeAnalysis.CSharp von 3.3.1 auf 3.4.0 (#11265)
- Aktualisierung von Paketen für Debian 10 und 11 (#11236)
- Ausschließliches Aktivieren experimenteller Funktionen vor RC (#11162)
- Aktualisierung der Mindestversion von macOS (#11163)
- Aktualisierung von NJsonSchema von 10.0.27 auf 10.0.28 (#11170)
- Aktualisierung von Links in README.md und metadata.json für Preview.5 (#10854)
- Auswählen der Dateien für Konformitätstests, die im Besitz von PowerShell sind (#10837)
- Ermöglichung des Erstellens eines win7x86-msix-Pakets. (10515 intern)
- Zulassen, dass semantische Versionen an die Funktion NormalizeVersion übergeben werden (#11087)
- Aktualisierung von .NET Core-Framework auf 3.1-preview.3 (#11079)
- Aktualisierung von PSReadLine von 2.0.0-beta5 auf 2.0.0-beta6 in /src/Modules (#11078)
- Aktualisierung von Newtonsoft.Json von 12.0.2 auf 12.0.3 (#11037) (#11038)
- Hinzufügung von Debian 10-, 11-und CentOS 8-Paketen (#11028)
- Hochladen von JSON-Datei mit Build-Info mit dem Feld ReleaseDate (#10986)
- Aktualisierung von .NET Core-Framework auf 3.1-preview.2 (#10993)
- Aktivierung des Builds des x86-MSIX-Pakets (#10934)
- Aktualisierung der URL des .SDK-Installationsskripts in build.psm1 (#10927)
- Aktualisierung von Markdig.Signed von 0.17.1 auf 0.18.0 (#10887)
- Aktualisierung von ThreadJob von 2.0.1 auf 2.0.2 (#10886)
- Aktualisierung von AppX Manifest und des Packaging-Moduls entsprechend den Microsoft Store-Anforderungen (#10878)
- Aktualisierung des Paketverweises für das PowerShell SDK in preview.5 (10295 intern)
- Aktualisierung von ThirdPartyNotices.txt (#10834)
- Aktualisierung von Microsoft.PowerShell.Native auf 7.0.0-preview.3 (#10826)
- Aktualisierung von Microsoft.ApplicationInsights von 2.10.0 auf 2.11.0 (#10608)
- Aktualisierung von NJsonSchema von 10.0.24 auf 10.0.27 (#10756)
- Hinzufügung der Unterstützung von MacPorts zum Buildsystem (#10736) (vielen Dank an @Lucius-Q-User!)
- Aktualisierung von PackageManagement von 1.4.4 auf 1.4.5 (#10728)
- Aktualisierung von NJsonSchema von 10.0.23 auf 10.0.24 (#10635)
- Hinzufügung einer Umgebungsvariablen zur Unterscheidung von Client-/Servertelemetrie in MSI (#10612)
- Aktualisierung von PSDesiredStateConfiguration von 2.0.3 auf 2.0.4 (#10603)
- Aktualisierung vonMicrosoft.CodeAnalysis.CSharp von 3.2.1 auf 3.3.1 (#10607)
- Aktualisierung von .Net Core 3.0 RTM (#10604) (vielen Dank an @bergmeister!)
- Aktualisierung der Erstellung von MSIX-Paketen entsprechend den Microsoft Store-Anforderungen (#10588)
- Aktualisierung der PowerShellGet-Version von 2.2 auf 2.2.1 (#10382)
- Aktualisierung der PackageManagement-Version von 1.4.3 auf 1.4.4 (#10383)
- Aktualisierung von README.md und metadata.json für 7.0.0-preview.4 (10011 intern)
- Aktualisierung der .Net Core 3.0-Version von Preview 9 auf RC1 (#10552) (vielen Dank an @bergmeister!)
- Korrektur der Listengenerierung für ExperimentalFeature (intern 9996)
- Aktualisierung der PSReadLine-Version von 2.0.0-beta4 auf 2.0.0-beta5 (#10536)
- Korrektur des Releasebuildskripts zum Festlegen des Releasetags
- Aktualisierung von Microsoft.PowerShell.Native auf 7.0.0-preview.2 (#10519)
- Aktualisierung auf Netcoreapp3.0 preview9 (#10484) (vielen Dank an @bergmeister!)
- Sicherstellung, dass der täglich koordinierte Build weiß, dass es sich um einen täglichen Build handelt (#10464)
- Aktualisierung des kombinierten Paketbuilds dahingehend, dass die täglichen Builds freigegeben werden (#10449)
- Entfernung des Verweises auf appveyor (#10445) (vielen Dank an @RDIL!)
- Aktualisierung von NJsonSchema von 10.0.22 auf 10.0.23 (#10421)
- Entfernung der Löschung des Buildordners linux-x64, da einige Abhängigkeiten für Alpine ihn benötigen (#10407)

### <a name="documentation-and-help-content"></a>Dokumentation und Inhalt der Hilfe

- Umgestaltung von Änderungsprotokollen in ein Protokoll pro Release (#11165)
- Korrektur von FWLinks für Onlinehilfedokumente für PowerShell 7 (#11071)
- Aktualisierung von CONTRIBUTING.MD (#11096) (vielen Dank an @mklement0!)
- Korrektur von Links zu Installationsdokumenten in README.MD (#11083)
- Hinzufügung von Beispielen zum Skript install-powershell.ps1 (#11024) (vielen Dank an @kilasuit!)
- Korrektur für Hervorhebung von Select-String und Import-DscResource in CHANGELOG.md (#10890)
- Entfernung des veralteten Links aus powershell-beginners-guide.md (#10926)
- Merge stabiler Branches und Wartung von Änderungsprotokollen (#10527)
- Aktualisierung der verwendeten .NET-Version in Builddokumenten (#10775) (vielen Dank an @Greg-Smulko!)
- Austausch von Links aus MSDN zu docs.microsoft.com in powershell-beginners-guide.md (#10778) (vielen Dank an @iSazonov!)
- Korrektur eines fehlerhaften Links zur DSC-Übersicht (#10702)
- Aktualisierung von Support_Question.md mit einem Link zu Stack Overflow als weitere Communityressource (#10638) (vielen Dank an @mklement0!)
- Hinzufügung der Prozessorarchitektur zur Verteilungsanforderungsvorlage (#10661)
- Hinzufügung eines neuen PowerShell MoL-Buchs zu Dokumenten zum Erlernen von PowerShell (#10602)
- Aktualisierung von README.md und Metadaten für v6.1.6 and v6.2.3 (#10523)
- Korrektur eines Tippfehlers in README.md (#10465) (vielen Dank an @vedhasp!)
- Hinzufügung eines Verweises auf das Modul PSKoans zur Dokumentation für Lernressourcen (#10369) (vielen Dank an @vexx32!)
- Aktualisierung von README.md und metadata.json für 7.0.0-preview.3 (#10393)
