---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Informationsdatenstrom
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147610"
---
# <a name="information-stream"></a><span data-ttu-id="2f7e1-103">Informationsdatenstrom</span><span class="sxs-lookup"><span data-stu-id="2f7e1-103">Information Stream</span></span>

<span data-ttu-id="2f7e1-104">PowerShell 5.0 fügt einen neuen strukturierten **Informations**datenstrom hinzu, um strukturierte Daten zwischen einem Skript und seinem Host zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-104">PowerShell 5.0 adds a new structured **Information** stream to transmit structured data between a script and its host.</span></span> <span data-ttu-id="2f7e1-105">`Write-Host` wurde auch so aktualisiert, dass seine Ausgabe in **den Informations**datenstrom erfolgt, in dem Sie sie nun erfassen oder unterdrücken können.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-105">`Write-Host` has also been updated to emit its output to the **Information** stream where you can now capture or silence it.</span></span> <span data-ttu-id="2f7e1-106">Das neue Cmdlet `Write-Information`, wenn es zusammen mit den allgemeinen Parametern **InformationVariable** und **InformationAction** verwendet wird, bietet mehr Flexibilität und Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-106">The new `Write-Information` cmdlet used with **InformationVariable** and **InformationAction** common parameters enables more flexibility and capability.</span></span>

<span data-ttu-id="2f7e1-107">Die folgende Funktion verwendet Cmdlets, die den neuen **Informations**datenstrom nutzen.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-107">The following function uses cmdlets that take advantage of the new **Information** stream.</span></span>

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

<span data-ttu-id="2f7e1-108">Die folgenden Beispiele zeigen die Ergebnisse der Ausführung dieser Funktion.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-108">The following examples show the results of running this function.</span></span>

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

<span data-ttu-id="2f7e1-109">Die Variable `$r` hat die Prozessinformationen in der Skriptvariablen `$p` erfasst.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-109">The `$r` variable has captured the process information in the script variable `$p`.</span></span>

```powershell
$r.Id
4008
```

<span data-ttu-id="2f7e1-110">Im Gegensatz zum Cmdlet `Write-Host` ermöglicht Ihnen die Verwendung des Parameters **InformationVariable** von `Write-Information` die Erfassung der Ausgabe in einer Variablen.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-110">Unlike the `Write-Host` cmdlet, using the **InformationVariable** parameter of `Write-Information` allows you to capture the output in a variable.</span></span> <span data-ttu-id="2f7e1-111">Mithilfe des **Tag**s können Sie getrennte Kanäle für die an den **Informations**datenstrom gesendete Nachricht erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-111">Using the **Tag**, you can create separate channels for message sent to the **Information** stream.</span></span>

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

<span data-ttu-id="2f7e1-112">Beim Senden einer Nachricht an den **Informations**datenstrom mit einem Tag, wird diese Nachricht nicht in der Hostanwendung angezeigt, kann aber mithilfe des Tagnamens abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2f7e1-112">When you send a message to the **Information** stream with a tag, that message is not displayed in the host application but can be retrieved using the tag name.</span></span> <span data-ttu-id="2f7e1-113">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="2f7e1-113">For example:</span></span>

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```