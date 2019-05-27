---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Fehlerkorrekturen in WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855495"
---
# <a name="bug-fixes-in-wmf-51"></a>Fehlerkorrekturen in WMF 5.1

## <a name="bug-fixes"></a>Fehlerkorrekturen

Die folgenden auffälligen Fehler wurden in WMF 5.1 behoben:

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>AutoErmittlung von Modulen berücksichtigt PSModulePath vollständig

Die AutoErmittlung von Modulen (d. h. das automatische Laden von Modulen ohne explizites Ausführen von „Import-Module“ beim Aufrufen eines Befehls) wurde in WMF 3 eingeführt. Nach der Einführung suchte PowerShell nach Befehlen in `$PSHome\Modules`, bevor `$env:PSModulePath` verwendet wurde.

In WMF 5.1 ändert sich dieses Verhalten so, dass `$env:PSModulePath` vollständig berücksichtigt wird. Dadurch kann ein vom Benutzer erstelltes Modul, das von PowerShell bereitgestellte Befehle definiert (z. B. `Get-ChildItem`), automatisch geladen werden und den integrierten Befehl ordnungsgemäß überschreiben.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Keine Hartcodierung mehr von „-Encoding Unicode“ bei der Umleitung von Dateien

In allen früheren Versionen von PowerShell konnte die vom Dateiumleitungsoperator verwendete Dateicodierung nicht gesteuert werden.

Ab WMF 5.1 können Sie jetzt die Dateicodierung der Umleitung durch Festlegen von `$PSDefaultParameterValues` ändern.

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Korrektur einer Regression beim Zugriff auf Member von System.Reflection.TypeInfo

Durch eine in WMF 5.0 eingeführte Regression wurde der Zugriff auf Member von `System.Reflection.RuntimeType`, z. B. `[int].ImplementedInterfaces`, unterbrochen. Dieser Fehler wurde in WMF 5.1 behoben.

### <a name="fixed-some-issues-with-com-objects"></a>Korrektur einiger Probleme mit COM-Objekten

In WMF 5.0 wurde ein neuer COM-Binder zum Aufrufen von Methoden für COM-Objekte und den Zugriff auf Eigenschaften von COM-Objekten eingeführt. Dieser neue Binder verbesserte die Leistung erheblich, verursachte jedoch auch einige Fehler, die in WMF 5.1 behoben wurden.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argumentkonvertierungen erfolgten nicht immer ordnungsgemäß

Siehe das folgende Beispiel:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

Die **SendKeys**-Methode erwartet eine Zeichenfolge, aber PowerShell konvertierte „char“ nicht in „string“, wodurch die Konvertierung in der **IDispatch::Invoke**-Methode verzögert wurde. Diese Methode verwendet **VariantChangeType** zum Ausführen der Konvertierung. In diesem Beispiel hat dies zum Senden der Schlüssel „1“, „7“ und „3 anstelle des erwarteten Schlüssels **Volume.Mute** geführt.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Die Verarbeitung aufzählbarer COM-Objekte erfolgte nicht immer ordnungsgemäß

PowerShell zählt normalerweise die meisten aufzählbaren Objekte auf. Doch eine in WMF 5.0 eingeführte Regression verhinderte die Aufzählung von COM-Objekten, die „IEnumerable“ implementieren. Beispiel:

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

Im obigen Beispiel schreibt WMF 5.0 fälschlicherweise **Scripting.Dictionary** in die Pipeline, anstatt die Schlüssel-Wert-Paare aufzuzählen.

### <a name="ordered-was-not-allowed-inside-classes"></a>[ordered] war innerhalb von Klassen nicht zulässig.

In WMF 5.0 wurden Klassen mit einer in Klassen verwendeten Überprüfung von Typliteralen eingeführt. `[ordered]` sieht wie ein Typliteral aus, ist jedoch kein echter .NET-Typ. WMF 5.0 meldete fälschlicherweise einen Fehler für `[ordered]` innerhalb einer Klasse:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Hilfe zu Themen mit mehreren Versionen funktioniert nicht

Wenn Sie vor WMF 5.1 über mehrere Versionen eines installierten Modus verfügt haben und es für alle nur ein Hilfethema gab, z. B. „about_PSReadline“, gab `help about_PSReadline` mehrere Themen zurück, ohne dass es eine erkennbare Möglichkeit gab, die tatsächliche Hilfe anzuzeigen.

In WMF 5.1 wurde dieser Fehler behoben, sodass nur die Hilfe für die neueste Version des Themas zurückgegeben wird.

`Get-Help` bietet keine Möglichkeit anzugeben, für welche Version Sie Hilfe wünschen. Die Problemumgebung besteht darin, zum Verzeichnis „Modules“ zu navigieren und die Hilfe direkt mit einem Tool wie Ihrem bevorzugten Editor anzuzeigen.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>„powershell.exe“ wird beim Lesen aus STDIN beendet

Kunden verwenden `powershell -command -` aus nativen Apps heraus zum Ausführen von PowerShell; die Übergabe im Skript über STDIN ist leider aufgrund anderer Änderungen am Konsolenhost fehlerhaft.

Dies wurde für Version 5.1 im Windows 10 Anniversary Update behoben.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>„powerShell.exe“ führt beim Start zu einer Spitze in der CPU-Auslastung

PowerShell überprüft mithilfe einer WMI-Abfrage, ob der Start über die Gruppenrichtlinie erfolgt ist, um Verzögerung bei der Anmeldung zu vermeiden. Am Ende der WMI-Abfrage wird „tzres.mui.dll“ in jeden Prozess auf dem System hinzugefügt, da die Klasse **WMI-Win32_Process** versucht, lokale Zeitzoneninformationen abzurufen. Dies führt zu einer großen CPU-Spitze in **wmiprvse** (dem WMI-Anbieterhost). Lösung: Verwenden Sie Win32-API-Aufrufe anstelle von WMI, um die gleichen Informationen abzurufen.
