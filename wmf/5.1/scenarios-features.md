---
title: Neue Szenarien und Features in WMF 5.1 (Preview)
ms.date: 2016-07-06
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: dcccf6880873c3f5c1b58fb1a8c546901b173879
ms.openlocfilehash: 9341b7fc3feea20cc2434065c3e512d1a8dd2b54

---

# Neue Szenarien und Features in WMF 5.1 (Preview) #

> Hinweis: Diese Dokumentation ist vorläufig und kann geändert werden.

## PowerShell-Editionen ##
Ab Version 5.1 steht PowerShell in verschiedenen Editionen zur Verfügung, die unterschiedliche Featuregruppen und Plattformkompatibilität bieten.

- **Desktop-Edition:** Diese Edition basiert auf .NET Framework und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter Vollversionen von Windows wie Server Core und Windows Desktop ausgeführt werden.
- **Core-Edition:** Diese Edition basiert auf .NET Core und bietet Kompatibilität mit Skripts und Modulen für Versionen von PowerShell, die unter funktionsreduzierten Versionen von Windows wie Nano Server und Windows IoT ausgeführt werden.

**Weitere Informationen zur Verwendung von PowerShell-Editionen**
- [Bestimmen der ausgeführten Edition von PowerShell]()
- [Deklarieren der Kompatibilität eines Moduls mit bestimmten Versionen von PowerShell]()
- [Der Filter „Get-Module“ hat „CompatiblePSEditions“ als Ergebnis]()
- [Verhindern der Ausführung von Skripts außer bei Ausführung in einer kompatiblen Edition von PowerShell]()

## Die Datei „ModuleAnalysisCache“ ##
Ab Version 5.1 bietet PowerShell Kontrolle über die Datei, die zum Zwischenspeichern von Daten zu einem Modul verwendet wird, z. B. der Befehle, die es exportiert.

Standardmäßig wird dieser Cache in der Datei `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` gespeichert.
Der Cache wird in der Regel beim Start der Suche nach einem Befehl gelesen und einige Zeit nach dem Import des Moduls in einem Hintergrundthread geschrieben.

Um den Standardspeicherort des Caches zu ändern, legen Sie die Umgebungsvariable „PSModuleAnalysisCachePath“ vor dem Starten von PowerShell fest. Änderungen an dieser Umgebungsvariablen betreffen nur untergeordnete Prozesse.
Der Wert muss einen vollständigen Pfad (samt Dateiname) definieren, in dem PowerShell die Berechtigung zum Erstellen und Schreiben von Dateien hat.
Zum Deaktivieren des Dateicaches kann dieser Wert auf einen ungültigen Speicherort festgelegt werden. Beispiel:

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Hiermit wird der Pfad auf ein ungültiges Gerät festgelegt. Wenn PowerShell nicht in den Pfad schreiben kann, wird keine Fehlermeldung zurückgegeben. Doch mithilfe eines Ablaufverfolgungstools können Sie einen Fehlerbericht anzeigen:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Bei der Ausgabe aus dem Cache sucht PowerShell nach Modulen, die nicht mehr vorhanden sind, um einen unnötig großen Cache zu vermeiden.
Mitunter sind diese Überprüfungen nicht wünschenswert, weshalb Sie sie deaktivieren können, indem Sie Folgendes festlegen:

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

Das Festlegen dieser Umgebungsvariablen wird im aktuellen Prozess sofort wirksam.

##Angeben der Modulversion

In WMF 5.1 verhält sich `using module` genauso wie andere modulbezogene Konstruktionen in PowerShell. Zuvor gab es keine Möglichkeit, eine bestimmte Modulversion anzugeben. Wenn mehrere Versionen vorhanden waren, führte dies zu einem Fehler.


In WMF 5.1:

* Sie können die `ModuleSpecification` [Hashtabelle](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx) verwenden. Diese Hashtabelle hat das gleiche Format wie `Get-Module -FullyQualifiedName`.

**Beispiel:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Wenn mehrere Versionen des Moduls vorhanden sind, verwendet PowerShell **dieselbe Auflösungslogik** wie `Import-Module` und gibt keinen Fehler zurück, was dem Verhalten von `Import-Module` und `Import-DscResource` entspricht.

## Verbesserungen an der PowerShell-Konsole

Die folgenden Änderungen sind in WMF 5.1 an Powershell.exe zum Verbessern der Konsolenumgebung erfolgt:

###Unterstützung von VT100

Windows 10 unterstützt nun [VT100-Escapesequenzen](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
Bei der Berechnung von Tabellenbreiten ignoriert PowerShell bestimmte VT100-Escapesequenzen für die Formatierung.

PowerShell bietet nun auch eine neue API, die in Formatierungscode verwendet werden kann, um festzustellen, ob VT100 unterstützt wird. Beispiel:

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
Es folgt ein vollständiges [Beispiel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7), das zum Hervorheben von Übereinstimmungen aus „Select-String“ verwendet werden kann.
Speichern Sie das Beispiel in einer Datei namens `MatchInfo.format.ps1xml`. Verwenden Sie sie in Ihrem Profil oder an anderer Stelle, und führen Sie `Update-FormatData -Prepend MatchInfo.format.ps1xml` aus.

Beachten Sie, dass VT100-Escapesequenzen erst ab dem Anniversary-Update für Windows 10 unterstützt werden. Von vorherigen Systemen werden sie nicht unterstützt.   

### Unterstützung des vi-Modus in PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) bietet nun Unterstützung den für vi-Modus. Führen Sie zur Verwendung des vi-Modus `Set-PSReadline -EditMode vi` aus.

### Umgeleitetes stdin mit interaktiver Eingabe 

In früheren Versionen war das Starten von PowerShell mit `powershell -File -` erforderlich, wenn stdin umgeleitet wurde und Sie Befehle interaktiv eingeben wollten.

Ab WMF 5.1 ist diese nur schwer auffindbare Option nicht mehr erforderlich. Sie können PowerShell ohne Optionen starten, z. B. `powershell`.

Beachten Sie, dass PSReadline derzeit umgeleitetes stdin nicht unterstützt und dass die integrierte Bearbeitungsumgebung für die Befehlszeile mit umgeleitetem sdtdin sehr eingeschränkt ist. Beispielsweise funktionieren die Pfeiltasten nicht.  In einer künftigen Version von PSReadline soll dieses Problem behoben werden.   

##Verbesserungen am PowerShell-Modul

Die folgenden Verbesserungen am PowerShell-Kernmodul wurden in WMF 5.1 implementiert:


## Leistung ##

In einigen wichtigen Bereichen wurde die Leistung verbessert:

- Start
- Das Pipelining zu Cmdlets wie „ForEach-Object“ und „Where-Object“ erfolgt ca. 50 % schneller. 

Einige Beispiele der Verbesserungen (Ergebnisse variieren je nach Hardware): 

| Szenario | Zeit (ms) in 5.0 | Zeit (ms) in 5.1 |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Erste Ausführung von PowerShell überhaupt: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Erstellung des Caches für die Befehlsanalyse: `powershell -command "Unknown-Command"` | 7000 | 520 |
| `1..1000000 | % { }` | 1400 | 750 |
  
> [!NOTE]  
> Eine Änderung im Zusammenhang mit dem Start kann sich möglicherweise auf einige (nicht unterstützte) Szenarien auswirken. PowerShell liest nicht mehr die Dateien des Typs `$pshome\*.ps1xml`. Diese Dateien wurden in C# konvertiert, um einen Teil des Datei- und CPU-Aufwands zum Verarbeiten der XML-Dateien zu vermeiden. Die Dateien sind zur Unterstützung der parallelen Verwendung von Version 2 noch vorhanden. Wenn Sie also den Inhalt der Dateien ändern, hat dies keine Auswirkung auf Version 5, sondern nur auf Version 2. Beachten Sie, dass das Ändern dieser Dateien zu keiner Zeit ein unterstütztes Szenario war.

Eine andere sichtbare Änderung ist, wie PowerShell die exportierten Befehle und andere Informationen für Module zwischenspeichert, die auf einem System installiert sind. Zuvor wurde dieser Cache im Verzeichnis `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` gespeichert. In WMF 5.1 befindet sich der Cache ausschließlich in der Datei `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Unter [analysis_cache.md]() finden Sie weitere Details.



## Fehlerkorrekturen ##

Die folgenden auffälligen Fehler wurden behoben:

### AutoErmittlung von Modulen vollständig berücksichtigt `$env:PSModulePath` ###

Die AutoErmittlung von Modulen (d. h. das automatische Laden von Modulen ohne explizites Ausführen von „Import-Module“ beim Aufrufen eines Befehls) wurde in WMF 3 eingeführt. Nach der Einführung suchte PowerShell nach Befehlen in `$PSHome\Modules`, bevor `$env:PSModulePath` verwendet wurde.

In WMF 5.1 ändert sich dieses Verhalten so, dass `$env:PSModulePath` vollständig berücksichtigt wird. Dadurch kann ein vom Benutzer erstelltes Modul, das von PowerShell bereitgestellte Befehle definiert (z. B. `Get-ChildItem`), automatisch geladen werden und den integrierten Befehl ordnungsgemäß überschreiben.

### Keine Hartcodierung mehr bei der Umleitung von Dateien `-Encoding Unicode` ###

In allen früheren Versionen von PowerShell konnte die vom Dateiumleitungsoperator, z. B. `get-childitem > out.txt`, verwendete Dateicodierung nicht gesteuert werden, da PowerShell `-Encoding Unicode` hinzugefügt hat.

Ab WMF 5.1 können Sie jetzt die Dateicodierung der Umleitung durch Festlegen von z. B. `$PSDefaultParameterValues` ändern.

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Korrektur einer Regression beim Zugriff auf Member von `System.Reflection.TypeInfo` ###

Durch eine in WMF 5.0 eingeführte Regression wurde der Zugriff auf Member von `System.Reflection.RuntimeType`, z. B. `[int].ImplementedInterfaces`, unterbrochen.
Dieser Fehler wurde in WMF 5.1 behoben.


### Korrektur einiger Probleme mit COM-Objekten ###

In WMF 5.0 wurde ein neuer COM-Binder zum Aufrufen von Methoden für COM-Objekte und den Zugriff auf Eigenschaften von COM-Objekten eingeführt.
Dieser neue Binder verbesserte die Leistung erheblich, verursachte jedoch auch einige Fehler, die in WMF 5.1 behoben wurden.

#### Argumentkonvertierungen erfolgten nicht immer ordnungsgemäß ####

Siehe das folgende Beispiel:

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

Die „SendKeys“-Methode erwartet eine Zeichenfolge, aber PowerShell konvertierte „char“ nicht in „string“, wodurch die Konvertierung in der „IDispatch::Invoke“-Methode verzögert wurde. Diese Methode verwendet „VariantChangeType“ zum Ausführen der Konvertierung, was bei diesem Beispiel zum Senden der Schlüssel „1“, „7“ und „3 anstelle des erwarteten Schlüssels „Volume.Mute“ geführt hat.

#### Die Verarbeitung aufzählbarer COM-Objekte erfolgte nicht immer ordnungsgemäß ####

PowerShell zählt normalerweise die meisten aufzählbaren Objekte auf. Doch eine in WMF 5.0 eingeführte Regression verhinderte die Aufzählung von COM-Objekten, die „IEnumerable“ implementieren.  Beispiel:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

Im obigen Beispiel schreibt WMF 5.0 „Scripting.Dictionary“ fälschlicherweise in die Pipeline, anstatt die Schlüssel-/Wert-Paare aufzuzählen.


### `[ordered]` war innerhalb von Klassen nicht zulässig. ###

In WMF 5 wurden Klassen mit einer in Klassen verwendeten Überprüfung von Typliteralen eingeführt.  `[ordered]` sieht wie ein Typliteral aus, ist jedoch kein echter .NET-Typ.  WMF 5 meldete fälschlicherweise einen Fehler für `[ordered]` innerhalb einer Klasse:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### Hilfe zu Themen mit mehreren Versionen funktioniert nicht ###

Wenn Sie vor WMF 5.1 über mehrere Versionen eines installierten Modus verfügt haben und es für alle nur ein Hilfethema gab, z. B. „about_PSReadline“, gab `help about_PSReadline` mehrere Themen zurück, ohne dass es eine erkennbare Möglichkeit gab, die tatsächliche Hilfe anzuzeigen.

In WMF 5.1 wurde dieser Fehler behoben, sodass nur die Hilfe für die neueste Version des Themas zurückgegeben wird.

„Get-Help“ bietet keine Möglichkeit anzugeben, für welche Version Sie Hilfe wünschen. Die Problemumgebung besteht darin, zum Verzeichnis „Modules“ zu navigieren und die Hilfe direkt mit einem Tool wie Ihrem bevorzugten Editor anzuzeigen. 

## Verbesserungen an OneGet
WMF 5.1 bietet verschiedene Korrekturen und Verbesserungen, um einige Probleme bei der Benutzererfahrung in der WMF-Version 5.0 zu beheben. 

###„-version“-Alias entfernt.

**Szenario**: Angenommen, Sie haben Version 1.0 und 2.0 des Pakets P1 auf Ihrem System installiert und möchten nun die Version 1.0 deinstallieren. Deshalb führen Sie „uninstall-package -name P1 -version 1.0“ aus. Sie erwarten, dass Version 1.0 nach dem Ausführen des Cmdlets deinstalliert wurde. Das Ergebnis ist jedoch, dass Version 2.0 deinstalliert wird. 
    
Dies passiert, weil der „-version“-Parameter ein Alias für den „-minimumversion“-Parameter ist. Wenn OneGet ein qualifiziertes Paket mit der Mindestversion 1.0 sucht, wird die neueste Version zurückgegeben. Dieses Verhalten wird normalerweise erwartet, da meistens die neueste Version gefunden werden soll. Für den Fall „uninstall-package“ sollte dies aber nicht gelten.
    
**Lösung**: In WMF 5.1 wurde der „-version“-Alias aus OneGet und PowerShellGet vollständig entfernt. 

###Mehrere Aufforderungen zum Bootstrapping des NuGet-Anbieters

**Szenario**: Wenn Sie „Find-Module“ oder „Install-Module“ oder andere OneGet-Cmdlets erstmals auf Ihrem Computer ausführen, versucht OneGet das Bootstrapping des NuGet-Anbieters. Das liegt daran, dass der PowerShellGet-Anbieter auch den NuGet-Anbieter verwendet, um PowerShell-Module herunterzuladen. OneGet fordert dann vom Benutzer die Berechtigung zum Installieren des NuGet-Anbieters an. Nachdem der Benutzer für das Bootstrapping „yes“ ausgewählt hat, wird die neueste Version des NuGet-Anbieters installiert. 
    
Wenn jedoch eine ältere Version des NuGet-Anbieters auf Ihrem Computer installiert ist, wird mitunter die ältere NuGet-Version zuerst in die PowerShell-Sitzung geladen (was die Racebedingung in OneGet ist). Damit PowerShellGet funktioniert, ist jedoch die neuere Version des NuGet-Anbieters erforderlich. Deshalb wird OneGet von PowerShellGet aufgefordert, für den NuGet-Anbieter erneut das Bootstrapping auszuführen. Dies führt zu mehreren Aufforderungen zum Bootstrapping des NuGet-Anbieters.

**Lösung**: In WMF 5.1 lädt OneGet nun die neueste Version des NuGet-Anbieters, um mehrere Aufforderungen zum Bootstrapping des NuGet-Anbieters zu vermeiden.

Es gibt auch eine Umgehung dieses Problems. Löschen Sie dazu manuell die alte Version des NuGet-Anbieters (NuGet-Anycpu.exe), sofern vorhanden, aus „$env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies“.


###Unterstützung für OneGet auf Computern mit ausschließlichem Intranetzugriff

**Szenario**: In WMF 5.0 hat OneGet keine Computer unterstützt, die nur auf das Intranet (aber nicht auf das Internet) zugreifen dürfen.

**Lösung**: In WMF 5.1 können Sie diese Schritte ausführen, um Intranetcomputern das Verwenden von OneGet zu erlauben:

1. Laden Sie den NuGet-Anbieter auf einem anderen Computer mit Internetverbindung mit dem Befehl „Install-PackageProvider NuGet“ herunter.

2. Den NuGet-Anbieter finden Sie entweder unter „$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget“ oder „$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget“. 

3. Kopieren Sie die Binärdateien in einen Ordner oder eine Netzwerkfreigabe, auf die der Intranetcomputer zugreifen kann, und installieren Sie den NuGet-Anbieter mit „Install-PackageProvider NuGet -Source <Path to folder>“.


###Verbesserungen bei der Ereignisprotokollierung

Wenn Sie Pakete installieren, ändern Sie den Status des Computers. In WMF 5.1 protokolliert OneGet jetzt beim Installieren, Deinstallieren und Speichern von Paketen Ereignisse im Windows-Ereignisprotokoll. Der Ereigniskanal ist identisch für PowerShell, d. h. Microsoft-Windows-PowerShell, Operational.

###Unterstützung für Standardauthentifizierung

In WMF 5.1 unterstützt OneGet das Suchen und Installieren von Paketen aus einem Repository, das Standardauthentifizierung erfordert. Sie können Ihre Anmeldeinformationen den Cmdlets „Find-Package“ und „Install-Package“ angeben. Beispiel:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
###Unterstützung der Verwendung von OneGet hinter einem Proxy

In WMF 5.1 verwendet OneGet die neuen Proxyparameter „-ProxyCredential“ und „-Proxy“. Mithilfe dieser Parameter können Sie die Proxy-URL und Anmeldeinformationen für OneGet-Cmdlets angeben. Standardmäßig werden die Proxyeinstellungen des Systems verwendet. Beispiel:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


