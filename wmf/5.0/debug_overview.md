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
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="5049e-102">Verbesserungen beim Debuggen von PowerShell-Skripts</span><span class="sxs-lookup"><span data-stu-id="5049e-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="5049e-103">Für PowerShell 5.0 wurden zahlreiche Verbesserungen vorgenommen, um das Debuggen zu verbessern:</span><span class="sxs-lookup"><span data-stu-id="5049e-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="5049e-104">Alle unterbrechen</span><span class="sxs-lookup"><span data-stu-id="5049e-104">Break All</span></span>

<span data-ttu-id="5049e-105">Die PowerShell-Konsole und Windows PowerShell ISE ermöglichen Ihnen nun bei der Ausführung von Skripts, den Debugger zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="5049e-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="5049e-106">Dies funktioniert in lokalen und Remotesitzungen.</span><span class="sxs-lookup"><span data-stu-id="5049e-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="5049e-107">Drücken Sie in der Konsole **STRG+UNTBR**.</span><span class="sxs-lookup"><span data-stu-id="5049e-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="5049e-108">Drücken Sie in der ISE **STRG+B,**, oder verwenden Sie den Menübefehl **Debuggen -> Alle unterbrechen**.</span><span class="sxs-lookup"><span data-stu-id="5049e-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="5049e-109">Remotedebuggen und Remotedateibearbeitung in der Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="5049e-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="5049e-110">Die Windows PowerShell ISE ermöglicht nun das Öffnen und Bearbeiten von Dateien in einer Remotesitzung, indem der Befehl „PSEdit“ ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5049e-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="5049e-111">Sie können z. B. eine Datei zur Bearbeitung in der Befehlszeile in einer Remotesitzung wie folgt öffnen:</span><span class="sxs-lookup"><span data-stu-id="5049e-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="5049e-112">Darüber hinaus können Sie nun Bearbeitungen vornehmen und Änderungen in einer Remotedatei speichern, die in Windows PowerShell ISE automatisch geöffnet wird, wenn ein Haltepunkt erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="5049e-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="5049e-113">Sie können nun eine Skriptdatei debuggen, die auf einem Remotecomputer ausgeführt wird, die Datei bearbeiten, um einen Fehler zu beheben, und dann das geänderte Skript erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="5049e-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="5049e-114">Erweitertes Skriptdebugging</span><span class="sxs-lookup"><span data-stu-id="5049e-114">Advanced Script Debugging</span></span>

<span data-ttu-id="5049e-115">Es gibt neue, erweiterte Debugfunktionen, die an beliebige lokale Computerprozesse angefügt werden können, für die Windows PowerShell geladen ist, und beliebige Runspaces im jeweiligen Prozess debuggen.</span><span class="sxs-lookup"><span data-stu-id="5049e-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="5049e-116">Debuggen von Runspaces</span><span class="sxs-lookup"><span data-stu-id="5049e-116">Runspace Debugging</span></span>

<span data-ttu-id="5049e-117">Neue Cmdlets wurden hinzugefügt, mit denen Sie aktuelle Runspaces in einem Prozess auflisten und die Windows PowerShell-Konsole oder ISE-Debugger an den jeweiligen Runspace zum Debuggen von Skripts anfügen können:</span><span class="sxs-lookup"><span data-stu-id="5049e-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="5049e-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="5049e-118">Get-Runspace</span></span>
-   <span data-ttu-id="5049e-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="5049e-119">Debug-Runspace</span></span>
-   <span data-ttu-id="5049e-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5049e-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="5049e-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5049e-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="5049e-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="5049e-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="5049e-123">Anfügen an den Prozess, der PowerShell hostet</span><span class="sxs-lookup"><span data-stu-id="5049e-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="5049e-124">Nun ist ein Anfügen an jeden Computerprozess möglich, für den Windows PowerShell geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="5049e-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="5049e-125">Starten Sie dazu eine interaktive Sitzung mit dem Prozess ähnlich dem Starten einer interaktiven Remotesitzung, indem Sie das Cmdlet „Enter-PSSession“ ausführen:</span><span class="sxs-lookup"><span data-stu-id="5049e-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="5049e-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="5049e-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="5049e-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="5049e-127">Exit-PSHostProcess</span></span>

