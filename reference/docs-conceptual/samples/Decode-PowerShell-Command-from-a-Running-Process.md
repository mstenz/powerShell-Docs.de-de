---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Decodieren eines PowerShell-Befehls in einem laufenden Prozess
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "66470969"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="a632c-103">Decodieren eines PowerShell-Befehls in einem laufenden Prozess</span><span class="sxs-lookup"><span data-stu-id="a632c-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="a632c-104">Gelegentlich wird möglicherweise ein PowerShell-Prozess ausgeführt, der eine große Menge an Ressourcen beansprucht.</span><span class="sxs-lookup"><span data-stu-id="a632c-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="a632c-105">Dieser Prozess kann im Rahmen eines [Aufgabenplanung][]-Auftrags oder eines [SQL Server-Agent][]-Auftrags ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a632c-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="a632c-106">Wenn mehrere PowerShell-Prozesse ausgeführt werden, kann eine Identifizierung schwierig sein, welcher Prozess das Problem darstellt.</span><span class="sxs-lookup"><span data-stu-id="a632c-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="a632c-107">Dieser Artikel zeigt, wie Sie einen Skriptblock decodieren, der aktuell von einem PowerShell-Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a632c-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="a632c-108">Erstellen eines zeitintensiven Prozesses</span><span class="sxs-lookup"><span data-stu-id="a632c-108">Create a long running process</span></span>

<span data-ttu-id="a632c-109">Um dieses Szenario zu veranschaulichen, öffnen Sie ein neues PowerShell-Fenster und führen den folgenden Code aus.</span><span class="sxs-lookup"><span data-stu-id="a632c-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="a632c-110">Es führt einen PowerShell-Befehl aus, der 10 Minuten lang jede Minute eine Zahl ausgibt.</span><span class="sxs-lookup"><span data-stu-id="a632c-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="a632c-111">Anzeigen des Prozesses</span><span class="sxs-lookup"><span data-stu-id="a632c-111">View the process</span></span>

<span data-ttu-id="a632c-112">Der Textkörper des Befehls, den PowerShell ausführt, wird in der Eigenschaft **CommandLine** der Klasse [Win32_Process][] gespeichert.</span><span class="sxs-lookup"><span data-stu-id="a632c-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="a632c-113">Wenn der Befehl ein codierter Befehl ist, enthält die **CommandLine**-Eigenschaft die Zeichenfolge „EncodedCommand“.</span><span class="sxs-lookup"><span data-stu-id="a632c-113">If the command is an encoded command, the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="a632c-114">Mithilfe dieser Informationen kann der codierte Befehl über den folgenden Prozess entschleiert werden.</span><span class="sxs-lookup"><span data-stu-id="a632c-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="a632c-115">Starten Sie PowerShell als Administrator.</span><span class="sxs-lookup"><span data-stu-id="a632c-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="a632c-116">Es ist unerlässlich, dass PowerShell als Administrator ausgeführt wird, da andernfalls bei der Abfrage der ausgeführten Prozesse keine Ergebnisse zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a632c-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="a632c-117">Führen Sie den folgenden Befehl aus, um alle PowerShell-Prozesse abzurufen, die über einen codierten Befehl verfügen:</span><span class="sxs-lookup"><span data-stu-id="a632c-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="a632c-118">Der folgende Befehl erstellt ein benutzerdefiniertes PowerShell-Objekt, das die Prozess-ID und den codierten Befehl enthält.</span><span class="sxs-lookup"><span data-stu-id="a632c-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="a632c-119">Jetzt kann der codierte Befehl decodiert werden.</span><span class="sxs-lookup"><span data-stu-id="a632c-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="a632c-120">Der folgende Codeausschnitt iteriert durch das Befehlsdetailobjekt, decodiert den codierten Befehl und fügt den decodierten Befehl zur weiteren Untersuchung dem Objekt erneut hinzu.</span><span class="sxs-lookup"><span data-stu-id="a632c-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="a632c-121">Der decodierte Befehl kann jetzt durch Auswählen der decodierten Befehlseigenschaft überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="a632c-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Aufgabenplanung]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server-Agent]: /sql/ssms/agent/sql-server-agent
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
