---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Informationsdatenstrom
ms.openlocfilehash: 39cb3c36a70530b3ff9777edc74b88d276cbbb7c
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808926"
---
# <a name="information-stream"></a>Informationsdatenstrom

PowerShell 5.0 fügt einen neuen strukturierten **Informations**datenstrom hinzu, um strukturierte Daten zwischen einem Skript und seinem Host zu übertragen. `Write-Host` wurde auch so aktualisiert, dass seine Ausgabe in **den Informations**datenstrom erfolgt, in dem Sie sie nun erfassen oder unterdrücken können. Das neue Cmdlet `Write-Information`, wenn es zusammen mit den allgemeinen Parametern **InformationVariable** und **InformationAction** verwendet wird, bietet mehr Flexibilität und Funktionalität.

Die folgende Funktion verwendet Cmdlets, die den neuen **Informations**datenstrom nutzen.

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

Die folgenden Beispiele zeigen die Ergebnisse der Ausführung dieser Funktion.

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

Die Variable `$r` hat die Prozessinformationen in der Skriptvariablen `$p` erfasst.

```powershell
$r.Id
4008
```

Im Gegensatz zum Cmdlet `Write-Host` ermöglicht Ihnen die Verwendung des Parameters **InformationVariable** von `Write-Information` die Erfassung der Ausgabe in einer Variablen. Mithilfe des **Tag**s können Sie getrennte Kanäle für die an den **Informations**datenstrom gesendete Nachricht erstellen.

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

Beim Senden einer Nachricht an den **Informations**datenstrom mit einem Tag, wird diese Nachricht nicht in der Hostanwendung angezeigt, kann aber mithilfe des Tagnamens abgerufen werden. Beispiel:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```
