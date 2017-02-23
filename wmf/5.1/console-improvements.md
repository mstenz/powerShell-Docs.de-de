---
title: Verbesserungen an der Konsole in WMF 5.1
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: fc0c78f59a2c4cda5c6aad625a5eaf5121485bad
ms.sourcegitcommit: 26f4e52f3dd008b51b7eae7b634f0216eec6200e
translationtype: HT
---
# <a name="console-improvements-in-wmf-51"></a>Verbesserungen an der Konsole in WMF 5.1#

## <a name="powershell-console-improvements"></a>Verbesserungen an der PowerShell-Konsole

Die folgenden Änderungen wurden in WMF 5.1 an powershell.exe vorgenommen, um die Konsolenumgebung zu verbessern:

###<a name="vt100-support"></a>Unterstützung von VT100

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

### <a name="vi-mode-support-in-psreadline"></a>Unterstützung des vi-Modus in PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) bietet nun Unterstützung den für vi-Modus. Führen Sie zur Verwendung des vi-Modus `Set-PSReadlineOption -EditMode Vi` aus.

### <a name="redirected-stdin-with-interactive-input"></a>Umgeleitetes stdin mit interaktiver Eingabe 

In früheren Versionen war das Starten von PowerShell mit `powershell -File -` erforderlich, wenn stdin umgeleitet wurde und Sie Befehle interaktiv eingeben wollten.

Bei WMF 5.1 ist diese schwer zu findende Option nicht mehr erforderlich. Sie können PowerShell ohne Optionen starten, z. B. mit `powershell`.

Beachten Sie, dass PSReadline derzeit umgeleitetes stdin nicht unterstützt und dass die integrierte Bearbeitungsumgebung für die Befehlszeile mit umgeleitetem stdin sehr eingeschränkt ist. Beispielsweise funktionieren die Pfeiltasten nicht. In einer künftigen Version von PSReadline soll dieses Problem behoben werden.   
