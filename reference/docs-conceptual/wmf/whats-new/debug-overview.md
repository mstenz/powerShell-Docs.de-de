---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Verbesserungen beim Debuggen von PowerShell-Skripts
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147810"
---
# <a name="improvements-in-powershell-script-debugging"></a>Verbesserungen beim Debuggen von PowerShell-Skripts

PowerShell 5.0 enthält mehrere Verbesserungen, die die Debugerfahrung erweitern.

## <a name="break-all"></a>Alle unterbrechen

Die PowerShell-Konsole und PowerShell ISE ermöglichen Ihnen nun bei der Ausführung von Skripts, den Debugger zu unterbrechen. Dies funktioniert in lokalen und Remotesitzungen.

Drücken Sie in der Konsole <kbd>STRG</kbd>+<kbd>UNTBR</kbd>.

Drücken Sie in der ISE <kbd>STRG</kbd>+<kbd>B</kbd>, oder verwenden Sie den Menübefehl **Debuggen -> Alle unterbrechen**.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Remotedebuggen und Remotedateibearbeitung in der PowerShell ISE

Die PowerShell ISE ermöglicht nun das Öffnen und Bearbeiten von Dateien in einer Remotesitzung, indem der Befehl „PSEdit“ ausgeführt wird.
Sie können z. B. eine Datei zur Bearbeitung in der Befehlszeile in einer Remotesitzung wie folgt öffnen:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Darüber hinaus können Sie nun Bearbeitungen vornehmen und Änderungen in einer Remotedatei speichern, die in PowerShell ISE automatisch geöffnet wird, wenn ein Haltepunkt erreicht wird. Sie können nun eine Skriptdatei debuggen, die auf einem Remotecomputer ausgeführt wird, die Datei bearbeiten, um einen Fehler zu beheben, und dann das geänderte Skript erneut ausführen.

## <a name="advanced-script-debugging"></a>Erweitertes Skriptdebugging

Es gibt neue, erweiterte Debugfunktionen, die an beliebige lokale Computerprozesse angefügt werden können, für die PowerShell geladen ist, und beliebige Runspaces im jeweiligen Prozess debuggen.

### <a name="runspace-debugging"></a>Debuggen von Runspaces

Neue Cmdlets wurden hinzugefügt, mit denen Sie aktuelle Runspaces in einem Prozess auflisten und die PowerShell-Konsole oder PowerShell ISE-Debugger an den jeweiligen Runspace zum Debuggen von Skripts anfügen können:

- Get-Runspace
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Anfügen an den Prozess, der PowerShell hostet

Nun ist ein Anfügen an jeden Computerprozess möglich, für den PowerShell geladen wurde. Hierzu starten Sie eine interaktive Sitzung mit dem Hostprozess. Weitere Informationen finden Sie unter:

- [Enter-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Exit-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
