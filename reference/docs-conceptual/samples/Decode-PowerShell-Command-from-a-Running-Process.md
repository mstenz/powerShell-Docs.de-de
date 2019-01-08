---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Decodieren eines PowerShell-Befehls in einem laufenden Prozess
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401235"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Decodieren eines PowerShell-Befehls in einem laufenden Prozess

In einigen Fällen müssen Sie möglicherweise eine PowerShell Prozess ausgeführt wird, die eine große Menge an Ressourcen beansprucht.
Dieser Vorgang kann ausgeführt werden, im Kontext des eine [Aufgabenplanung][] Auftrag oder ein [SQL Server-Agent][] Auftrag. Es sind mehrere PowerShell-Prozesse ausgeführt, kann es schwierig sein zu wissen, welcher Prozess das Problem darstellt. In diesem Artikel zeigt, wie Sie einen Skriptblock zu decodieren, den ein PowerShell-Prozess derzeit ausgeführt wird.

## <a name="create-a-long-running-process"></a>Erstellen Sie einen lang ausgeführten Vorgang

Um dieses Szenario zu veranschaulichen, öffnen Sie ein neues PowerShell-Fenster aus, und führen Sie den folgenden Code. Sie führt einen PowerShell-Befehl, der eine Anzahl pro Minute für 10 Minuten ausgibt.

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

## <a name="view-the-process"></a>Den Prozess anzeigen

Der Text des Befehls die PowerShell ausgeführt wird befindet sich in der **CommandLine** Eigenschaft der [Win32_Process][] Klasse. Wenn der Befehl ist ein [codierte-Befehl][], **CommandLine** -Eigenschaft enthält die Zeichenfolge "EncodedCommand". Mithilfe dieser Informationen kann die codierte Befehl entschleiert werden über den folgenden Prozess sein.

Starten Sie PowerShell als Administrator an. Es unerlässlich ist, dass PowerShell als Administrator ausgeführt wird, werden andernfalls keine Ergebnisse zurückgegeben, wenn die ausgeführten Prozesse abgefragt.

Führen Sie den folgenden Befehl zum Abrufen aller die PowerShell-Prozesse, die einen codierten-Befehl:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

Der folgende Befehl erstellt ein benutzerdefiniertes PowerShell-Objekt, das die Prozess-ID und den codierten Befehl enthält.

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

Jetzt kann die codierte Befehl decodiert werden. Der folgende Codeausschnitt durchläuft das Details-Befehlsobjekt, decodiert den codierten Befehl und fügt den decodierten Befehl zurück an das Objekt zur weiteren Untersuchung.

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

Der decodierte-Befehl kann jetzt durch Auswahl der decodierte Command-Eigenschaft überprüft werden.

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
[SQL Server-Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[codierte-Befehl]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
