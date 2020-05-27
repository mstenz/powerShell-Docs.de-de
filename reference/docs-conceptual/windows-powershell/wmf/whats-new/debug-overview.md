---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Verbesserungen beim Debuggen von PowerShell-Skripts
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808946"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="f413a-103">Verbesserungen beim Debuggen von PowerShell-Skripts</span><span class="sxs-lookup"><span data-stu-id="f413a-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="f413a-104">PowerShell 5.0 enthält mehrere Verbesserungen, die die Debugerfahrung erweitern.</span><span class="sxs-lookup"><span data-stu-id="f413a-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="f413a-105">Alle unterbrechen</span><span class="sxs-lookup"><span data-stu-id="f413a-105">Break All</span></span>

<span data-ttu-id="f413a-106">Die PowerShell-Konsole und PowerShell ISE ermöglichen Ihnen nun bei der Ausführung von Skripts, den Debugger zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="f413a-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="f413a-107">Dies funktioniert in lokalen und Remotesitzungen.</span><span class="sxs-lookup"><span data-stu-id="f413a-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="f413a-108">Drücken Sie in der Konsole <kbd>STRG</kbd>+<kbd>UNTBR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f413a-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="f413a-109">Drücken Sie in der ISE <kbd>STRG</kbd>+<kbd>B</kbd>, oder verwenden Sie den Menübefehl **Debuggen -> Alle unterbrechen**.</span><span class="sxs-lookup"><span data-stu-id="f413a-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="f413a-110">Remotedebuggen und Remotedateibearbeitung in der PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f413a-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="f413a-111">Die PowerShell ISE ermöglicht nun das Öffnen und Bearbeiten von Dateien in einer Remotesitzung, indem der Befehl „PSEdit“ ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f413a-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="f413a-112">Sie können z. B. eine Datei zur Bearbeitung in der Befehlszeile in einer Remotesitzung wie folgt öffnen:</span><span class="sxs-lookup"><span data-stu-id="f413a-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="f413a-113">Darüber hinaus können Sie nun Bearbeitungen vornehmen und Änderungen in einer Remotedatei speichern, die in PowerShell ISE automatisch geöffnet wird, wenn ein Haltepunkt erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="f413a-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="f413a-114">Sie können nun eine Skriptdatei debuggen, die auf einem Remotecomputer ausgeführt wird, die Datei bearbeiten, um einen Fehler zu beheben, und dann das geänderte Skript erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="f413a-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="f413a-115">Erweitertes Skriptdebugging</span><span class="sxs-lookup"><span data-stu-id="f413a-115">Advanced Script Debugging</span></span>

<span data-ttu-id="f413a-116">Es gibt neue, erweiterte Debugfunktionen, die an beliebige lokale Computerprozesse angefügt werden können, für die PowerShell geladen ist, und beliebige Runspaces im jeweiligen Prozess debuggen.</span><span class="sxs-lookup"><span data-stu-id="f413a-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="f413a-117">Debuggen von Runspaces</span><span class="sxs-lookup"><span data-stu-id="f413a-117">Runspace Debugging</span></span>

<span data-ttu-id="f413a-118">Neue Cmdlets wurden hinzugefügt, mit denen Sie aktuelle Runspaces in einem Prozess auflisten und die PowerShell-Konsole oder PowerShell ISE-Debugger an den jeweiligen Runspace zum Debuggen von Skripts anfügen können:</span><span class="sxs-lookup"><span data-stu-id="f413a-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="f413a-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="f413a-119">Get-Runspace</span></span>
- <span data-ttu-id="f413a-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="f413a-120">Debug-Runspace</span></span>
- <span data-ttu-id="f413a-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f413a-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="f413a-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f413a-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="f413a-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f413a-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="f413a-124">Anfügen an den Prozess, der PowerShell hostet</span><span class="sxs-lookup"><span data-stu-id="f413a-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="f413a-125">Nun ist ein Anfügen an jeden Computerprozess möglich, für den PowerShell geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="f413a-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="f413a-126">Hierzu starten Sie eine interaktive Sitzung mit dem Hostprozess.</span><span class="sxs-lookup"><span data-stu-id="f413a-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="f413a-127">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="f413a-127">For more information, see:</span></span>

- [<span data-ttu-id="f413a-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f413a-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="f413a-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f413a-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
