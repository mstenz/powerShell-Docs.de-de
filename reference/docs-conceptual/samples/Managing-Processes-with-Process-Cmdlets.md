---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwalten von Prozessen mit „Process“-Cmdlets
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401196"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="43a1f-103">Verwalten von Prozessen mit „Process“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="43a1f-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="43a1f-104">Sie können die „Process“-Cmdlets in Windows PowerShell verwenden, um lokale und Remoteprozesse in Windows PowerShell zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="43a1f-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="43a1f-105">Abrufen von Prozessen (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="43a1f-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="43a1f-106">Um die Prozesse abzurufen, die auf dem lokalen Computer ausgeführt werden, führen Sie **Get-Process** ohne Parameter aus.</span><span class="sxs-lookup"><span data-stu-id="43a1f-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="43a1f-107">Sie können bestimmte Prozesse abrufen, indem Sie deren Prozessnamen oder Prozess-IDs angeben.</span><span class="sxs-lookup"><span data-stu-id="43a1f-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="43a1f-108">Der folgende Befehl ruft den Prozess „Idle“ ab:</span><span class="sxs-lookup"><span data-stu-id="43a1f-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="43a1f-109">Obwohl es für Cmdlets normal ist, dass sie in einigen Fällen keine Daten zurückgeben, generiert **Get-Process** einen Fehler, wenn Sie einen Prozess über seine Prozess-ID (ProcessId) angeben, das Cmdlet aber keine Übereinstimmung finden kann. Dies ist darin begründet, dass die eigentliche Absicht ist, dass ein bekannter aktiver Prozess abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="43a1f-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="43a1f-110">Gibt es keinen Prozess mit dieser ID, ist es sehr wahrscheinlich, dass die ID falsch ist oder der Prozess bereits beendet wurde:</span><span class="sxs-lookup"><span data-stu-id="43a1f-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="43a1f-111">Sie können den „Name“-Parameter des Cmdlets „Get-Process“ verwenden, um anhand des Prozessnamens eine Teilmenge von Prozessen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="43a1f-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="43a1f-112">Der „Name“-Parameter akzeptiert mehrere Namen in einer durch Kommas getrennten Liste und unterstützt die Verwendung von Platzhaltern, sodass Sie Namensmuster eingeben können.</span><span class="sxs-lookup"><span data-stu-id="43a1f-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="43a1f-113">Beispielsweise ruft der folgende Befehl Prozesse ab, deren Namen mit „ex“ beginnen.</span><span class="sxs-lookup"><span data-stu-id="43a1f-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="43a1f-114">Weil die .NET-Klasse „System.Diagnostics.Process“ die Grundlage für Windows PowerShell-Prozesse ist, gelten für diese einige der Konventionen, die von „System.Diagnostics.Process“ verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="43a1f-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="43a1f-115">Eine dieser Konventionen ist, dass der Prozessname für eine ausführbare Datei nie das „.exe“ am Ende des Namens der ausführbaren Datei enthält.</span><span class="sxs-lookup"><span data-stu-id="43a1f-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="43a1f-116">**Get-Process** akzeptiert auch mehrere Werte für den „Name“-Parameter.</span><span class="sxs-lookup"><span data-stu-id="43a1f-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="43a1f-117">Sie können den „ComputerName“-Parameter von „Get-Process“ verwenden, um Prozesse auf Remotecomputern abzurufen.</span><span class="sxs-lookup"><span data-stu-id="43a1f-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="43a1f-118">Beispielsweise ruft der folgende Befehl die PowerShell-Prozesse auf dem lokalen Computer (dargestellt durch „localhost“) und auf zwei Remotecomputern ab.</span><span class="sxs-lookup"><span data-stu-id="43a1f-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="43a1f-119">Die Computernamen sind in dieser Anzeige nicht zu sehen, sie sind aber in der „MachineName“-Eigenschaft der Prozessobjekte gespeichert, die „Get-Process“ zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="43a1f-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="43a1f-120">Im folgenden Befehl wird das Cmdlet „Format-Table“ verwendet, um die Eigenschaften Prozess-„ID“, „ProcessName“ und „MachineName“ (ComputerName) der Prozessobjekte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="43a1f-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="43a1f-121">In diesem komplexeren Befehl wird der standardmäßigen „Get-Process“-Anzeige die „MachineName“-Eigenschaft hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="43a1f-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="43a1f-122">Beenden von Prozessen (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="43a1f-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="43a1f-123">Windows PowerShell gibt Ihnen die Flexibilität zum Auflisten von Prozessen, aber wie sieht es mit dem Beenden eines Prozesses aus?</span><span class="sxs-lookup"><span data-stu-id="43a1f-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="43a1f-124">Das Cmdlet **Stop-Process** akzeptiert einen Namen oder eine ID als Angabe für den Prozess, den Sie beenden möchten.</span><span class="sxs-lookup"><span data-stu-id="43a1f-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="43a1f-125">Inwieweit Sie Prozesse beenden können, hängt von Ihren Berechtigungen ab.</span><span class="sxs-lookup"><span data-stu-id="43a1f-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="43a1f-126">Einige Prozesse können nicht beendet werden.</span><span class="sxs-lookup"><span data-stu-id="43a1f-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="43a1f-127">Wenn Sie beispielsweise versuchen, den Prozess „idle“ zu beenden, erhalten Sie einen Fehler:</span><span class="sxs-lookup"><span data-stu-id="43a1f-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="43a1f-128">Mit dem **Force**-Parameter können Sie auch eine Eingabeaufforderung erzwingen.</span><span class="sxs-lookup"><span data-stu-id="43a1f-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="43a1f-129">Dieser Parameter ist insbesondere nützlich, wenn Sie für die Angabe des Prozessnamens einen Platzhalter verwenden, denn möglicherweise ergibt sich versehentlich eine Übereinstimmung für einige Prozesse, die Sie nicht beenden möchten:</span><span class="sxs-lookup"><span data-stu-id="43a1f-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="43a1f-130">Komplexe Prozessverarbeitung ist möglich, indem Sie einige der Cmdlets zur Objektfilterung verwenden.</span><span class="sxs-lookup"><span data-stu-id="43a1f-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="43a1f-131">Weil ein Prozessobjekt eine „Responding“-Eigenschaft hat, die gleich „false“ ist, wenn das Prozessobjekt nicht mehr reagiert, können Sie alle nicht reagierenden Anwendungen mit dem folgenden Befehl beenden:</span><span class="sxs-lookup"><span data-stu-id="43a1f-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="43a1f-132">Sie können die gleiche Vorgehensweise in anderen Situationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="43a1f-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="43a1f-133">Nehmen Sie beispielsweise an, dass automatisch eine sekundäre Anwendung für den Infobereich ausgeführt wird, wenn der Benutzer eine andere Anwendung startet.</span><span class="sxs-lookup"><span data-stu-id="43a1f-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="43a1f-134">Sie stellen möglicherweise fest, dass dies in Terminaldienstesitzungen nicht ordnungsgemäß funktioniert, aber Sie möchten es in Sitzungen beibehalten, die in der Konsole des physischen Computers ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="43a1f-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="43a1f-135">Sitzungen, die mit dem Desktop eines physischen Computers verbunden sind, haben immer die Sitzungs-ID „0“, also können Sie alle Instanzen des Prozesses, die sich in anderen Sitzungen befinden, beenden, indem Sie **Where-Object** und die Prozesssitzungs-ID (**SessionId**) verwenden:</span><span class="sxs-lookup"><span data-stu-id="43a1f-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="43a1f-136">Das Cmdlet „Stop-Process“ hat keinen ComputerName-Parameter.</span><span class="sxs-lookup"><span data-stu-id="43a1f-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="43a1f-137">Daher müssen Sie, wenn Sie auf einem Remotecomputer einen Befehl zum Beenden eines Prozesses ausführen möchten, das Cmdlet „Invoke-Command“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="43a1f-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="43a1f-138">Wenn Sie beispielsweise den PowerShell-Prozess auf dem Remotecomputer „Server01“ beenden möchten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="43a1f-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="43a1f-139">Beenden alle anderen Windows PowerShell-Sitzungen</span><span class="sxs-lookup"><span data-stu-id="43a1f-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="43a1f-140">Gelegentlich kann es nützlich sein, alle aktiven Windows PowerShell-Sitzungen mit Ausnahme der aktuellen Sitzung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="43a1f-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="43a1f-141">Wenn eine Sitzung zu viele Ressourcen verwendet, oder wenn nicht mehr auf sie zugegriffen werden kann (sie wird möglicherweise remote oder in einer anderen Desktopsitzung ausgeführt), kann es sein, dass Sie sie nicht direkt beenden können.</span><span class="sxs-lookup"><span data-stu-id="43a1f-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="43a1f-142">Wenn Sie aber versuchen, alle aktiven Sitzungen zu beenden, wird möglicherweise stattdessen die aktuelle Sitzung beendet.</span><span class="sxs-lookup"><span data-stu-id="43a1f-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="43a1f-143">Jede Windows PowerShell-Sitzung hat die Umgebungsvariable PID, die die ID des jeweiligen Windows PowerShell-Prozesses enthält.</span><span class="sxs-lookup"><span data-stu-id="43a1f-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="43a1f-144">Sie können die $PID mit der ID jeder Sitzung abgleichen und nur die Windows PowerShell-Sitzungen beenden, die eine andere ID haben. Im folgenden Pipelinebefehl wird dies ausgeführt und die Liste der beendeten Sitzungen zurückgegeben (weil der **PassThru**-Parameter verwendet wird):</span><span class="sxs-lookup"><span data-stu-id="43a1f-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="43a1f-145">Starten und Debuggen von Prozessen sowie Warten auf Prozesse</span><span class="sxs-lookup"><span data-stu-id="43a1f-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="43a1f-146">Zu Windows PowerShell gehören auch Cmdlets zum Starten (oder Neustarten) eines Prozesses, zum Debuggen eines Prozesses sowie zum Warten, bis ein Prozess abgeschlossen ist, bevor ein Befehl ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="43a1f-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="43a1f-147">Informationen zu diesen Cmdlets finden Sie im Cmdlet-Hilfethema für jedes Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43a1f-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="43a1f-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="43a1f-148">See Also</span></span>

- <span data-ttu-id="43a1f-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="43a1f-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="43a1f-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="43a1f-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="43a1f-151">Start-Process</span><span class="sxs-lookup"><span data-stu-id="43a1f-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="43a1f-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="43a1f-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="43a1f-153">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="43a1f-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="43a1f-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="43a1f-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
