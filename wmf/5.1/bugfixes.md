---
title: Fehlerbehebungen in WMF 5.1 (Vorschau)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: d851b0cc9300b9afb027fe9ceb122f246a17e418
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="bug-fixes-in-wmf-51-preview"></a>Fehlerbehebungen in WMF 5.1 (Vorschau)#

## <a name="bug-fixes"></a>Fehlerkorrekturen ##

Die folgenden auffälligen Fehler wurden in WMF 5.1 behoben:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>AutoErmittlung von Modulen vollständig berücksichtigt `$env:PSModulePath` ###

Die AutoErmittlung von Modulen (d. h. das automatische Laden von Modulen ohne explizites Ausführen von „Import-Module“ beim Aufrufen eines Befehls) wurde in WMF 3 eingeführt. Nach der Einführung suchte PowerShell nach Befehlen in `$PSHome\Modules`, bevor `$env:PSModulePath` verwendet wurde.

In WMF 5.1 ändert sich dieses Verhalten so, dass `$env:PSModulePath` vollständig berücksichtigt wird. Dadurch kann ein vom Benutzer erstelltes Modul, das von PowerShell bereitgestellte Befehle definiert (z. B. `Get-ChildItem`), automatisch geladen werden und den integrierten Befehl ordnungsgemäß überschreiben.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Keine Hartcodierung mehr bei der Umleitung von Dateien `-Encoding Unicode` ###

In allen früheren Versionen von PowerShell konnte die vom Dateiumleitungsoperator, z. B. `Get-ChildItem > out.txt`, verwendete Dateicodierung nicht gesteuert werden, da PowerShell `-Encoding Unicode` hinzugefügt hat.

Ab WMF 5.1 können Sie jetzt die Dateicodierung der Umleitung durch Festlegen von `$PSDefaultParameterValues` ändern.

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Korrektur einer Regression beim Zugriff auf Member von `System.Reflection.TypeInfo` ###

Durch eine in WMF 5.0 eingeführte Regression wurde der Zugriff auf Member von `System.Reflection.RuntimeType`, z. B. `[int].ImplementedInterfaces`, unterbrochen.
Dieser Fehler wurde in WMF 5.1 behoben.


### <a name="fixed-some-issues-with-com-objects"></a>Korrektur einiger Probleme mit COM-Objekten ###

In WMF 5.0 wurde ein neuer COM-Binder zum Aufrufen von Methoden für COM-Objekte und den Zugriff auf Eigenschaften von COM-Objekten eingeführt. Dieser neue Binder verbesserte die Leistung erheblich, verursachte jedoch auch einige Fehler, die in WMF 5.1 behoben wurden.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argumentkonvertierungen erfolgten nicht immer ordnungsgemäß ####

Siehe das folgende Beispiel:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

Die „SendKeys“-Methode erwartet eine Zeichenfolge, aber PowerShell konvertierte „char“ nicht in „string“, wodurch die Konvertierung in der „IDispatch::Invoke“-Methode verzögert wurde. Diese Methode verwendet „VariantChangeType“ zum Ausführen der Konvertierung, was bei diesem Beispiel zum Senden der Schlüssel „1“, „7“ und „3 anstelle des erwarteten Schlüssels „Volume.Mute“ geführt hat.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Die Verarbeitung aufzählbarer COM-Objekte erfolgte nicht immer ordnungsgemäß ####

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

Im obigen Beispiel schreibt WMF 5.0 fälschlicherweise „Scripting.Dictionary“ in die Pipeline, anstatt die Schlüssel-Wert-Paare aufzuzählen.

Diese Änderung betrifft auch das [Problem 1752224 auf Microsoft Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224).

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` war innerhalb von Klassen nicht zulässig. ###

In WMF 5.0 wurden Klassen mit einer in Klassen verwendeten Überprüfung von Typliteralen eingeführt.  
`[ordered]` sieht wie ein Typliteral aus, ist jedoch kein echter .NET-Typ. WMF 5.0 meldete fälschlicherweise einen Fehler für `[ordered]` innerhalb einer Klasse:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Hilfe zu Themen mit mehreren Versionen funktioniert nicht ###

Wenn Sie vor WMF 5.1 über mehrere Versionen eines installierten Modus verfügt haben und es für alle nur ein Hilfethema gab, z. B. „about_PSReadline“, gab `help about_PSReadline` mehrere Themen zurück, ohne dass es eine erkennbare Möglichkeit gab, die tatsächliche Hilfe anzuzeigen.

In WMF 5.1 wurde dieser Fehler behoben, sodass nur die Hilfe für die neueste Version des Themas zurückgegeben wird.

`Get-Help` bietet keine Möglichkeit anzugeben, für welche Version Sie Hilfe wünschen. Die Problemumgebung besteht darin, zum Verzeichnis „Modules“ zu navigieren und die Hilfe direkt mit einem Tool wie Ihrem bevorzugten Editor anzuzeigen. 
