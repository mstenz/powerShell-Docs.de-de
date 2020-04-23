---
ms.date: 02/03/2020
keywords: powershell,core
title: Bekannte Probleme bei PowerShell 6.0
ms.openlocfilehash: e9550e3db53865cfc2713d1d80665cced6f0d47a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "76996102"
---
# <a name="known-issues-for-powershell-60"></a>Bekannte Probleme bei PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Bekannte Probleme bei PowerShell auf anderen Plattformen als Windows

Die Alphareleases von PowerShell sind unter Linux und macOS überwiegend funktionsfähig, weisen jedoch einige wichtige Einschränkungen und Probleme bei der Verwendung auf. Die Betareleases von PowerShell sind unter Linux und macOS überwiegend funktionsfähiger und stabiler als die Alphareleases, können aber Fehler aufweisen. Außerdem sind einige Features möglicherweise nicht enthalten. In einigen Fällen handelt es sich bei diesen Problemen um bisher ungelöste Fehler. In anderen Fällen (z.B. mit den Standardaliasen für ls, cp usw.) benötigen wir zu unseren Entscheidungen Feedback aus der Community.

Hinweis: Aufgrund der Ähnlichkeiten vieler zugrunde liegender Subsysteme weist PowerShell unter Linux und macOS üblicherweise die gleichen Features und Fehler auf. Wenn nicht anders angegeben, gelten die Probleme in diesem Abschnitt für beide Betriebssysteme.

### <a name="case-sensitivity-in-powershell"></a>Groß-/Kleinschreibung in PowerShell

Bisher wurde die Groß- und Kleinschreibung in PowerShell mit wenigen Ausnahmen generell nicht berücksichtigt. Auf UNIX-ähnlichen Betriebssystemen wird die Groß- und Kleinschreibung vom Dateisystem jedoch überwiegend berücksichtigt, sodass PowerShell sich nach dem Standard des Dateisystems richtet. Dies wird durch einige offensichtliche und nicht offensichtliche Möglichkeiten verdeutlicht.

#### <a name="directly"></a>Direkt

- Wenn Sie eine Datei in PowerShell angeben, muss die korrekte Groß-/Kleinschreibung verwendet werden.

#### <a name="indirectly"></a>Indirekt

- Wenn ein Skript versucht, ein Modul zu laden, und die Groß- und Kleinschreibung des Moduls nicht korrekt ist, tritt beim Laden des Moduls ein Fehler auf. Dies kann zu Problemen mit vorhandenen Skripts führen, wenn der Name, mit dem auf das Modul verwiesen wird, nicht mit dem tatsächlichen Dateinamen übereinstimmt.
- Die automatische Vervollständigung mithilfe der TAB-Taste funktioniert nicht, wenn die Groß- und Kleinschreibung des Dateinamens nicht korrekt ist. Die Groß- und Kleinschreibung des abzuschließenden Fragments muss korrekt sein. (Die Groß- und Kleinschreibung wird bei der Vervollständigung von Typnamen und Typmembers nicht berücksichtigt.)

### <a name="ps1-file-extensions"></a>PS1-Dateierweiterungen

PowerShell-Skripts müssen auf `.ps1` enden, damit der Interpreter weiß, wie diese im aktuellen Prozess geladen und ausgeführt werden müssen. Das Ausführen von Skripts im aktuellen Prozess wird als übliches Verhalten für PowerShell vorausgesetzt. Die magische Zahl `#!` kann einem Skript ohne die Erweiterung `.ps1` hinzugefügt werden, dadurch wird das Skript jedoch in einer neuen PowerShell-Instanz ausgeführt, und das Austauschen von Objekten funktioniert nicht ordnungsgemäß. (Hinweis: Dabei kann es sich um das erwünschte Verhalten handeln, wenn ein PowerShell-Skript über `bash` oder eine andere Shell ausgeführt wird.)

### <a name="missing-command-aliases"></a>Fehlende Befehlsaliase

Unter Linux und macOS wurden die einfach verwendbaren Aliase für die grundlegenden Befehle `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount` und `ps` entfernt. Unter Windows stellt PowerShell einige Aliase bereit, die den Linux-Befehlsnamen zugeordnet sind und die Benutzerfreundlichkeit erhöhen. Diese Aliase wurden aus der Standardversion von PowerShell unter Linux- und macOS-Verteilungen entfernt, wodurch die native ausführbare Datei ausgeführt werden kann, ohne einen Pfad anzugeben.

Diese Vorgehensweise hat Vor- und Nachteile. Durch das Entfernen der Aliase werden die nativen Befehle dem PowerShell-Benutzer zur Verfügung gestellt, allerdings wird die Funktionalität der Shell reduziert, da die nativen Befehle Zeichenfolgen statt Objekte zurückgeben.

> [!NOTE]
> Zu diesem Thema benötigt das PowerShell-Team weiteres Feedback. Welche Lösung wird bevorzugt?
> Soll dies beibehalten werden, oder sollen die einfach verwendbaren Aliase wieder hinzugefügt werden? Weitere Informationen finden Sie unter [Issue #929 (Problem #929)](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Fehlende Unterstützung für Platzhalter

Derzeit unterstützt PowerShell nur Platzhaltererweiterungen für integrierte Cmdlets unter Windows sowie für externe Befehle bzw. Binärdateien und Cmdlets unter Linux. Das bedeutet, dass bei einem Befehl wie `ls
*.txt` ein Fehler auftritt, da das Sternchen nicht erweitert wird, um mit den Dateinamen übereinzustimmen. Sie können dies umgehen, indem Sie `ls (gci *.txt | % name)` oder einfach `gci *.txt` mithilfe dem in PowerShell integrierten Äquivalent für `ls` verwenden.

Besuchen Sie [#954](https://github.com/PowerShell/PowerShell/issues/954), um uns Feedback zu geben, wie die Verwendung von Platzhaltern unter Linux und macOS verbessert werden kann.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework und .NET Core Framework im Vergleich

PowerShell unter Linux und macOS verwendet .NET Core. Dabei handelt es sich um eine Teilmenge des vollständigen .NET Frameworks unter Microsoft Windows. Das ist wichtig, da PowerShell den direkten Zugriff auf die zugrunde liegenden Frameworktypen, Methoden und vieles mehr bereitstellt. Folglich können Skripts, die unter Windows ausgeführt werden, nicht auf anderen Plattformen als Windows ausgeführt werden, da die Frameworks sich unterscheiden. Weitere Informationen zum .NET Core-Framework finden Sie unter [dotnetfoundation.org](https://dotnetfoundation.org/).

Mit der Einführung von [.NET Standard 2.0](https://devblogs.microsoft.com/dotnet/introducing-net-standard/) sind viele der herkömmlichen Typen und Methoden aus dem vollständigen .NET Framework wieder in .NET Core 2.0 verfügbar. Das bedeutet, dass PowerShell Core viele herkömmliche Windows PowerShell-Module ohne Änderungen laden kann. Unsere Arbeit an .NET Standard 2.0 können Sie [hier](https://github.com/PowerShell/PowerShell/projects/4) verfolgen.

### <a name="redirection-issues"></a>Umleitungsprobleme

Die Umleitung von Eingaben wird von PowerShell auf keiner Plattform unterstützt.
[Issue #1629 (Problem #1629)](https://github.com/PowerShell/PowerShell/issues/1629)

Verwenden Sie `Get-Content`, um die Inhalte einer Datei in die Pipeline zu schreiben.

Die umgeleitete Ausgabe enthält die Bytereihenfolge-Marke (Byte Order Mark, BOM) in Unicode, wenn die UTF-8-Standardcodierung verwendet wird. Die Bytereihenfolge-Marke verursacht Probleme, wenn mit Hilfsprogrammen gearbeitet wird, die dies nicht erwarten, oder wenn sie einer Datei angefügt wird. Verwenden Sie `-Encoding Ascii`, um ASCII-Text zu schreiben, der keine BOM enthält.

> [!Note]
> Geben Sie uns unter [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) Feedback, damit die Codierung für PowerShell Core für alle Plattformen verbessert werden kann. Es wird daran gearbeitet, UTF-8 ohne Bytereihenfolge-Marke zu unterstützen und die Standardcodierung für verschiedene Cmdlets plattformübergreifend zu ändern.

### <a name="job-control"></a>Auftragssteuerung

Es gibt keine Unterstützung für die Auftragssteuerung in PowerShell unter Linux und macOS.
Die Befehle `fg` und `bg` sind nicht verfügbar.

Derzeit können Sie [PowerShell-Aufträge](/powershell/module/microsoft.powershell.core/about/about_jobs) verwenden, die auf allen Plattformen funktionieren.

### <a name="remoting-support"></a>Unterstützung für das Remoting

Derzeit unterstützt PowerShell Core das PowerShell-Remoting (PSRP) unter macOS und Linux mit einer Standardauthentifizierung über WSMan. Unter Linux wird ebenfalls die NTLM-basierte Authentifizierung unterstützt. (Die Kerberos-basierte Authentifizierung wird nicht unterstützt.)

Das WSMan-basierte Remoting wird über das Repository [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) durchgeführt.

PowerShell Core unterstützt das PowerShell-Remoting (PSRP) ebenfalls auf allen Plattformen (Windows, macOS, Linux) über SSH. Dies wird derzeit nicht in der Produktion unterstützt, [hier](../learn/remoting/SSH-Remoting-in-PowerShell-Core.md) können Sie jedoch mehr über die Einrichtung erfahren.

### <a name="just-enough-administration-jea-support"></a>Unterstützung für Just Enough Administration (JEA)

Derzeit können keine eingeschränkten JEA-Remoting-Endpunkte in PowerShell unter Linux und macOS erstellt werden. Dieses Feature ist derzeit nicht für Version 6.0 geplant, sondern für spätere Versionen, da dafür wichtige Entwurfsarbeit erforderlich ist.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec` und PowerShell

Da PowerShell (wie Python oder Ruby) die meisten Befehle im Arbeitsspeicher ausführt, können Sie sudo nicht direkt mit integrierten PowerShell-Features verwenden. (Sie können `pwsh` selbstverständlich über sudo ausführen.) Wenn es erforderlich ist, ein PowerShell-Cmdlet innerhalb von PowerShell mit sudo auszuführen, z.B. im Fall von `sudo Set-Date 8/18/2016`, sollten Sie `sudo pwsh Set-Date 8/18/2016` verwenden. Gleichermaßen können Sie integrierte PowerShell-Features nicht direkt ausführen. Stattdessen müssen Sie `exec pwsh item_to_exec` verwenden.

Dieses Problem wird unter [#3232](https://github.com/PowerShell/PowerShell/issues/3232) nachverfolgt.

### <a name="missing-cmdlets"></a>Fehlende Cmdlets

Viele Befehle (Cmdlets), die normalerweise in PowerShell verfügbar sind, sind unter Linux und macOS nicht verfügbar. In vielen Fällen sind diese Befehle auf diesen Plattformen überflüssig, z.B. Befehle für Windows-spezifische Features wie die Registrierung. Andere Befehle wie die zur Steuerung von Diensten (Get/Start/Stop-Service) sind vorhanden, aber nicht funktionsfähig. Diese Probleme werden vielleicht in zukünftigen Releases behoben, indem die fehlerhaften Cmdlets korrigiert und neue hinzugefügt werden.

### <a name="command-availability"></a>Verfügbarkeit von Befehlen

In der folgenden Tabelle werden die Befehle aufgeführt, die bekanntermaßen nicht in PowerShell unter Linux und macOS funktionieren.

|Befehle|Betriebsstatus|Notizen|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Nicht verfügbar.|Diese Befehle werden nicht erkannt. Dies wird in einem zukünftigen Release behoben.|
|`Get-Acl`, `Get-AuthenticodeSignature`, `Get-CmsMessage`, `New-FileCatalog`, `Protect-CmsMessage`, `Set-Acl`, `Set-AuthenticodeSignature`, `Test-FileCatalog`, `Unprotect-CmsMessage`|Nicht verfügbar.|Diese Befehle werden nicht erkannt. Dies wird in einem zukünftigen Release behoben.|
|`Wait-Process`|Dieser Befehl ist verfügbar, funktioniert jedoch nicht ordnungsgemäß. |`Start-Process gvim -PassThru | Wait-Process` funktioniert beispielsweise nicht. Beim Warten auf den Prozess tritt ein Fehler auf.|
|`Connect-PSSession`, `Disable-PSRemoting`, `Disable-PSSessionConfiguration`, `Disconnect-PSSession`, `Enable-PSRemoting`, `Enable-PSSessionConfiguration`, `Get-PSSessionCapability`, `Get-PSSessionConfiguration`, `New-PSSessionConfigurationFile`, `Receive-PSSession`, `Register-PSSessionConfiguration`, `Set-PSSessionConfiguration`, `Test-PSSessionConfigurationFile`, `Unregister-PSSessionConfiguration`|Nicht verfügbar.|Diese Befehle werden nicht erkannt. Dies wird in einem zukünftigen Release behoben.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Remove-Event`, `Unregister-Event`|Diese Befehle sind verfügbar, es gibt jedoch keine Ereignisquellen.|Die PowerShell-Befehle für Ereignisse sind vorhanden, allerdings sind die meisten Ereignisquellen, die mit den Befehlen verwendet werden (z.B. „ System.Timers.Timer“), nicht unter Linux verfügbar. Dadurch sind die Befehle im Alpharelease unnötig.|
|`Set-ExecutionPolicy`|Dieser Befehl ist verfügbar, funktioniert jedoch nicht.|Eine Meldung wird zurückgegeben, die angibt, dass der Befehl auf dieser Plattform nicht unterstützt wird. Die Ausführungsrichtlinie stellt eine benutzerorientierte Sicherheitsmaßnahme dar, die verhindert, dass der Benutzer schwere Fehler begeht. Dabei handelt es sich nicht um eine Sicherheitsgrenze.|
|`New-PSSessionOption`, `New-PSTransportOption`|Dieser Befehl ist verfügbar, `New-PSSession` funktioniert jedoch nicht.|Es wurde nicht überprüft, ob `New-PSSessionOption` und `New-PSTransportOption` funktionieren, nachdem nun `New-PSSession` funktioniert.|
