---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ablaufverfolgung und Protokollierung von Skripts
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147800"
---
# <a name="script-tracing-and-logging"></a>Ablaufverfolgung und Protokollierung von Skripts

Während PowerShell bereits über die Gruppenrichtlinieneinstellung **LogPipelineExecutionDetails** verfügt, um den Aufruf von Cmdlets zu protokollieren, bietet die PowerShell-Skriptsprache mehrere Features, die Sie ggf. protokollieren und überwachen möchten. Das neue Feature zur detaillierten Ablaufverfolgung von Skripts stellt eine detaillierte Nachverfolgung und Analyse der Verwendung von PowerShell-Skriptaktivitäten auf einem System bereit. Nachdem Sie die detaillierte Ablaufverfolgung von Skripts aktiviert haben, protokolliert PowerShell alle Skriptblöcke im ETW-Ereignisprotokoll **Microsoft-Windows-PowerShell/Operational**. Wenn ein Skriptblock einen anderen Skriptblock erzeugt, z. B. durch Aufrufen von `Invoke-Expression`, wird der aufgerufene Skriptblock ebenfalls protokolliert.

Die Protokollierung wird über die Gruppenrichtlinieneinstellung **Protokollierung von PowerShell-Skriptblöcken aktivieren** (**Administrative Vorlagen** -> **Windows-Komponenten** -> **Windows PowerShell**) aktiviert.

Die Ereignisse sind wie folgt:

| Channel |                               Bei Betrieb                               |
| ------- | ----------------------------------------------------------------------- |
| Ebene   | Ausführlich                                                                 |
| Opcode  | Erstellen                                                                  |
| Aufgabe    | CommandStart                                                            |
| Schlüsselwort | Runspace                                                                |
| EventId | Engine_ScriptBlockCompiled (0x1008 = 4104)                              |
| `Message` | Skriptblocktext (%1 von %2) wird erstellt: </br> %3 </br> ScriptBlock-ID: %4 |


Der in der Meldung eingebettete Text gibt das Ausmaß des kompilierten Skriptblocks an. Die ID ist eine GUID, die für die Gültigkeitsdauer des Skriptblocks beibehalten wird.

Wenn Sie die ausführlichen Protokollierung aktivieren, schreibt das Feature die Markierungen „begin“ und „end“:

| Channel |                                 Bei Betrieb                                |
| ------- | -------------------------------------------------------------------------- |
| Ebene   | Ausführlich                                                                    |
| Opcode  | Öffnen/Schließen                                                               |
| Aufgabe    | CommandStart/CommandStop                                                 |
| Schlüsselwort | Runspace                                                                   |
| EventId | ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) / </br> ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) / |
| `Message` | Der Aufruf der ScriptBlock-ID wurde gestartet/abgeschlossen: %1 </br> Runspace-ID: %2 |

Die ID ist die GUID, die den Skriptblock darstellt (der mit der Ereignis-ID 0x1008 korreliert werden kann). Die Runspace-ID stellt den Runspace dar, in dem dieser Skriptblock ausgeführt wurde.

Prozentzeichen in der Aufrufmeldung stellen strukturierte ETW-Eigenschaften dar. Wenngleich sie im Meldungstext durch die tatsächlichen Werte ersetzt werden, empfiehlt sich für den Zugriff darauf eher das Abrufen der Meldung mit dem Cmdlet „Get-WinEvent“ und dann das Untersuchen des Bereichs **Eigenschaften** der Meldung.

Hier ist ein Beispiel, wie diese Funktionalität helfen kann, einen böswilligen Versuch zum Verschlüsseln und Verschleiern eines Skripts zu erkennen:

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

Bei Ausführen dieses Befehls werden die folgenden Einträge generiert:

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

Wenn die Länge eines Skriptblocks größer als die Kapazität eines einzelnen Ereignisses ist, teilt PowerShell das Skript in mehrere Teile auf. Hier ist Beispielcode für das erneute Zusammenzusetzen der Protokollmeldungen eines Skripts:

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

Wie alle Protokollierungssysteme, die einen begrenzten Aufbewahrungspuffer haben, besteht eine Angriffsmöglichkeit auf diese Infrastruktur darin, dass Protokoll mit gefälschten Ereignissen zu überfluten, um ein früheres Vorkommen zu vertuschen. Um sich vor diesen Angriffen zu schützen, stellen Sie sicher, dass Sie eine Form der Ereignisprotokollerfassung eingerichtet haben, z. B. Windows-Ereignisweiterleitung. Weitere Informationen finden Sie unter [Ermitteln des Angreifers mit Überwachung des Windows-Ereignisprotokolls](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).