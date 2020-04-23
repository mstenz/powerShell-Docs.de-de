---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Decodieren eines PowerShell-Befehls in einem laufenden Prozess
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "66470969"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Decodieren eines PowerShell-Befehls in einem laufenden Prozess

Gelegentlich wird möglicherweise ein PowerShell-Prozess ausgeführt, der eine große Menge an Ressourcen beansprucht.
Dieser Prozess kann im Rahmen eines [Aufgabenplanung][]-Auftrags oder eines [SQL Server-Agent][]-Auftrags ausgeführt werden. Wenn mehrere PowerShell-Prozesse ausgeführt werden, kann eine Identifizierung schwierig sein, welcher Prozess das Problem darstellt. Dieser Artikel zeigt, wie Sie einen Skriptblock decodieren, der aktuell von einem PowerShell-Prozess ausgeführt wird.

## <a name="create-a-long-running-process"></a>Erstellen eines zeitintensiven Prozesses

Um dieses Szenario zu veranschaulichen, öffnen Sie ein neues PowerShell-Fenster und führen den folgenden Code aus. Es führt einen PowerShell-Befehl aus, der 10 Minuten lang jede Minute eine Zahl ausgibt.

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

## <a name="view-the-process"></a>Anzeigen des Prozesses

Der Textkörper des Befehls, den PowerShell ausführt, wird in der Eigenschaft **CommandLine** der Klasse [Win32_Process][] gespeichert. Wenn der Befehl ein codierter Befehl ist, enthält die **CommandLine**-Eigenschaft die Zeichenfolge „EncodedCommand“. Mithilfe dieser Informationen kann der codierte Befehl über den folgenden Prozess entschleiert werden.

Starten Sie PowerShell als Administrator. Es ist unerlässlich, dass PowerShell als Administrator ausgeführt wird, da andernfalls bei der Abfrage der ausgeführten Prozesse keine Ergebnisse zurückgegeben werden.

Führen Sie den folgenden Befehl aus, um alle PowerShell-Prozesse abzurufen, die über einen codierten Befehl verfügen:

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

Jetzt kann der codierte Befehl decodiert werden. Der folgende Codeausschnitt iteriert durch das Befehlsdetailobjekt, decodiert den codierten Befehl und fügt den decodierten Befehl zur weiteren Untersuchung dem Objekt erneut hinzu.

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

Der decodierte Befehl kann jetzt durch Auswählen der decodierten Befehlseigenschaft überprüft werden.

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
