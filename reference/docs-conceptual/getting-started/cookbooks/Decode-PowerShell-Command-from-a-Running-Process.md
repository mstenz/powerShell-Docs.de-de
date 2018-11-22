---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Decodieren eines PowerShell-Befehls in einem laufenden Prozess
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619202"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="9f41d-103">Decodieren eines PowerShell-Befehls in einem laufenden Prozess</span><span class="sxs-lookup"><span data-stu-id="9f41d-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="9f41d-104">In einigen Fällen müssen Sie möglicherweise eine PowerShell Prozess ausgeführt wird, die eine große Menge an Ressourcen beansprucht.</span><span class="sxs-lookup"><span data-stu-id="9f41d-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="9f41d-105">Dieser Vorgang kann ausgeführt werden, im Kontext des eine [Aufgabenplanung][] Auftrag oder ein [SQL Server-Agent][] Auftrag.</span><span class="sxs-lookup"><span data-stu-id="9f41d-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="9f41d-106">Es sind mehrere PowerShell-Prozesse ausgeführt, kann es schwierig sein zu wissen, welcher Prozess das Problem darstellt.</span><span class="sxs-lookup"><span data-stu-id="9f41d-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="9f41d-107">In diesem Artikel zeigt, wie Sie einen Skriptblock zu decodieren, den ein PowerShell-Prozess derzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9f41d-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="9f41d-108">Erstellen Sie einen lang ausgeführten Vorgang</span><span class="sxs-lookup"><span data-stu-id="9f41d-108">Create a long running process</span></span>

<span data-ttu-id="9f41d-109">Um dieses Szenario zu veranschaulichen, öffnen Sie ein neues PowerShell-Fenster aus, und führen Sie den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="9f41d-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="9f41d-110">Sie führt einen PowerShell-Befehl, der eine Anzahl pro Minute für 10 Minuten ausgibt.</span><span class="sxs-lookup"><span data-stu-id="9f41d-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

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

## <a name="view-the-process"></a><span data-ttu-id="9f41d-111">Den Prozess anzeigen</span><span class="sxs-lookup"><span data-stu-id="9f41d-111">View the process</span></span>

<span data-ttu-id="9f41d-112">Der Text des Befehls die PowerShell ausgeführt wird befindet sich in der **CommandLine** Eigenschaft der [Win32_Process][] Klasse.</span><span class="sxs-lookup"><span data-stu-id="9f41d-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="9f41d-113">Wenn der Befehl ist ein [codierte-Befehl][], **CommandLine** -Eigenschaft enthält die Zeichenfolge "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="9f41d-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="9f41d-114">Mithilfe dieser Informationen kann die codierte Befehl entschleiert werden über den folgenden Prozess sein.</span><span class="sxs-lookup"><span data-stu-id="9f41d-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="9f41d-115">Starten Sie PowerShell als Administrator an.</span><span class="sxs-lookup"><span data-stu-id="9f41d-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="9f41d-116">Es unerlässlich ist, dass PowerShell als Administrator ausgeführt wird, werden andernfalls keine Ergebnisse zurückgegeben, wenn die ausgeführten Prozesse abgefragt.</span><span class="sxs-lookup"><span data-stu-id="9f41d-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="9f41d-117">Führen Sie den folgenden Befehl zum Abrufen aller die PowerShell-Prozesse, die einen codierten-Befehl:</span><span class="sxs-lookup"><span data-stu-id="9f41d-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="9f41d-118">Der folgende Befehl erstellt ein benutzerdefiniertes PowerShell-Objekt, das die Prozess-ID und den codierten Befehl enthält.</span><span class="sxs-lookup"><span data-stu-id="9f41d-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

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

<span data-ttu-id="9f41d-119">Jetzt kann die codierte Befehl decodiert werden.</span><span class="sxs-lookup"><span data-stu-id="9f41d-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="9f41d-120">Der folgende Codeausschnitt durchläuft das Details-Befehlsobjekt, decodiert den codierten Befehl und fügt den decodierten Befehl zurück an das Objekt zur weiteren Untersuchung.</span><span class="sxs-lookup"><span data-stu-id="9f41d-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

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

<span data-ttu-id="9f41d-121">Der decodierte-Befehl kann jetzt durch Auswahl der decodierte Command-Eigenschaft überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="9f41d-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

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
[codierte-Befehl]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
