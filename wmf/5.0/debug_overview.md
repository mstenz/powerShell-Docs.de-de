---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: aaf1809277f072c82e5a1a862ea64b75586e32d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="improvements-in-powershell-script-debugging" class="xliff"></a>
# Verbesserungen beim Debuggen von PowerShell-Skripts

Für PowerShell 5.0 wurden zahlreiche Verbesserungen vorgenommen, um das Debuggen zu verbessern:

<a id="break-all" class="xliff"></a>
## Alle unterbrechen

Die PowerShell-Konsole und Windows PowerShell ISE ermöglichen Ihnen nun bei der Ausführung von Skripts, den Debugger zu unterbrechen. Dies funktioniert in lokalen und Remotesitzungen.

Drücken Sie in der Konsole **STRG+UNTBR**.

Drücken Sie in der ISE **STRG+B,**, oder verwenden Sie den Menübefehl **Debuggen -> Alle unterbrechen**.

<a id="remote-debugging-and-remote-file-editing-in-windows-powershell-ise" class="xliff"></a>
## Remotedebuggen und Remotedateibearbeitung in der Windows PowerShell ISE

Die Windows PowerShell ISE ermöglicht nun das Öffnen und Bearbeiten von Dateien in einer Remotesitzung, indem der Befehl „PSEdit“ ausgeführt wird.
Sie können z. B. eine Datei zur Bearbeitung in der Befehlszeile in einer Remotesitzung wie folgt öffnen:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Darüber hinaus können Sie nun Bearbeitungen vornehmen und Änderungen in einer Remotedatei speichern, die in Windows PowerShell ISE automatisch geöffnet wird, wenn ein Haltepunkt erreicht wird.
Sie können nun eine Skriptdatei debuggen, die auf einem Remotecomputer ausgeführt wird, die Datei bearbeiten, um einen Fehler zu beheben, und dann das geänderte Skript erneut ausführen.

<a id="advanced-script-debugging" class="xliff"></a>
## Erweitertes Skriptdebugging

Es gibt neue, erweiterte Debugfunktionen, die an beliebige lokale Computerprozesse angefügt werden können, für die Windows PowerShell geladen ist, und beliebige Runspaces im jeweiligen Prozess debuggen.

<a id="runspace-debugging" class="xliff"></a>
### Debuggen von Runspaces

Neue Cmdlets wurden hinzugefügt, mit denen Sie aktuelle Runspaces in einem Prozess auflisten und die Windows PowerShell-Konsole oder ISE-Debugger an den jeweiligen Runspace zum Debuggen von Skripts anfügen können:

-   Get-Runspace
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

<a id="attach-to-process-hosting-powershell" class="xliff"></a>
### Anfügen an den Prozess, der PowerShell hostet

Nun ist ein Anfügen an jeden Computerprozess möglich, für den Windows PowerShell geladen wurde. Starten Sie dazu eine interaktive Sitzung mit dem Prozess ähnlich dem Starten einer interaktiven Remotesitzung, indem Sie das Cmdlet „Enter-PSSession“ ausführen:

-   Enter-PSHostProcess
-   Exit-PSHostProcess

