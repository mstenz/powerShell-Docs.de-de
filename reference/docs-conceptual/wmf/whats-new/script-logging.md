---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Ablaufverfolgung und Protokollierung von Skripts
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147800"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="5e120-103">Ablaufverfolgung und Protokollierung von Skripts</span><span class="sxs-lookup"><span data-stu-id="5e120-103">Script Tracing and Logging</span></span>

<span data-ttu-id="5e120-104">Während PowerShell bereits über die Gruppenrichtlinieneinstellung **LogPipelineExecutionDetails** verfügt, um den Aufruf von Cmdlets zu protokollieren, bietet die PowerShell-Skriptsprache mehrere Features, die Sie ggf. protokollieren und überwachen möchten.</span><span class="sxs-lookup"><span data-stu-id="5e120-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="5e120-105">Das neue Feature zur detaillierten Ablaufverfolgung von Skripts stellt eine detaillierte Nachverfolgung und Analyse der Verwendung von PowerShell-Skriptaktivitäten auf einem System bereit.</span><span class="sxs-lookup"><span data-stu-id="5e120-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="5e120-106">Nachdem Sie die detaillierte Ablaufverfolgung von Skripts aktiviert haben, protokolliert PowerShell alle Skriptblöcke im ETW-Ereignisprotokoll **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="5e120-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="5e120-107">Wenn ein Skriptblock einen anderen Skriptblock erzeugt, z. B. durch Aufrufen von `Invoke-Expression`, wird der aufgerufene Skriptblock ebenfalls protokolliert.</span><span class="sxs-lookup"><span data-stu-id="5e120-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="5e120-108">Die Protokollierung wird über die Gruppenrichtlinieneinstellung **Protokollierung von PowerShell-Skriptblöcken aktivieren** (**Administrative Vorlagen** -> **Windows-Komponenten** -> **Windows PowerShell**) aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5e120-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="5e120-109">Die Ereignisse sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="5e120-109">The events are:</span></span>

| <span data-ttu-id="5e120-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5e120-110">Channel</span></span> |                               <span data-ttu-id="5e120-111">Betriebsbereit</span><span class="sxs-lookup"><span data-stu-id="5e120-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="5e120-112">Ebene</span><span class="sxs-lookup"><span data-stu-id="5e120-112">Level</span></span>   | <span data-ttu-id="5e120-113">Ausführlich</span><span class="sxs-lookup"><span data-stu-id="5e120-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="5e120-114">Opcode</span><span class="sxs-lookup"><span data-stu-id="5e120-114">Opcode</span></span>  | <span data-ttu-id="5e120-115">Erstellen</span><span class="sxs-lookup"><span data-stu-id="5e120-115">Create</span></span>                                                                  |
| <span data-ttu-id="5e120-116">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="5e120-116">Task</span></span>    | <span data-ttu-id="5e120-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="5e120-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="5e120-118">Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="5e120-118">Keyword</span></span> | <span data-ttu-id="5e120-119">Runspace</span><span class="sxs-lookup"><span data-stu-id="5e120-119">Runspace</span></span>                                                                |
| <span data-ttu-id="5e120-120">Ereignis-ID</span><span class="sxs-lookup"><span data-stu-id="5e120-120">EventId</span></span> | <span data-ttu-id="5e120-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="5e120-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="5e120-122">Meldung</span><span class="sxs-lookup"><span data-stu-id="5e120-122">Message</span></span> | <span data-ttu-id="5e120-123">Skriptblocktext (%1 von %2) wird erstellt:</span><span class="sxs-lookup"><span data-stu-id="5e120-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="5e120-124">%3</span><span class="sxs-lookup"><span data-stu-id="5e120-124">%3</span></span> </br> <span data-ttu-id="5e120-125">ScriptBlock-ID: %4</span><span class="sxs-lookup"><span data-stu-id="5e120-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="5e120-126">Der in der Meldung eingebettete Text gibt das Ausmaß des kompilierten Skriptblocks an.</span><span class="sxs-lookup"><span data-stu-id="5e120-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="5e120-127">Die ID ist eine GUID, die für die Gültigkeitsdauer des Skriptblocks beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="5e120-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="5e120-128">Wenn Sie die ausführlichen Protokollierung aktivieren, schreibt das Feature die Markierungen „begin“ und „end“:</span><span class="sxs-lookup"><span data-stu-id="5e120-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="5e120-129">Kanal</span><span class="sxs-lookup"><span data-stu-id="5e120-129">Channel</span></span> |                                 <span data-ttu-id="5e120-130">Betriebsbereit</span><span class="sxs-lookup"><span data-stu-id="5e120-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="5e120-131">Ebene</span><span class="sxs-lookup"><span data-stu-id="5e120-131">Level</span></span>   | <span data-ttu-id="5e120-132">Ausführlich</span><span class="sxs-lookup"><span data-stu-id="5e120-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="5e120-133">Opcode</span><span class="sxs-lookup"><span data-stu-id="5e120-133">Opcode</span></span>  | <span data-ttu-id="5e120-134">Öffnen/Schließen</span><span class="sxs-lookup"><span data-stu-id="5e120-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="5e120-135">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="5e120-135">Task</span></span>    | <span data-ttu-id="5e120-136">CommandStart/CommandStop</span><span class="sxs-lookup"><span data-stu-id="5e120-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="5e120-137">Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="5e120-137">Keyword</span></span> | <span data-ttu-id="5e120-138">Runspace</span><span class="sxs-lookup"><span data-stu-id="5e120-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="5e120-139">Ereignis-ID</span><span class="sxs-lookup"><span data-stu-id="5e120-139">EventId</span></span> | <span data-ttu-id="5e120-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="5e120-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="5e120-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) /</span><span class="sxs-lookup"><span data-stu-id="5e120-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="5e120-142">Message</span><span class="sxs-lookup"><span data-stu-id="5e120-142">Message</span></span> | <span data-ttu-id="5e120-143">Der Aufruf der ScriptBlock-ID wurde gestartet/abgeschlossen: %1</span><span class="sxs-lookup"><span data-stu-id="5e120-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="5e120-144">Runspace-ID: %2</span><span class="sxs-lookup"><span data-stu-id="5e120-144">Runspace ID: %2</span></span> |

<span data-ttu-id="5e120-145">Die ID ist die GUID, die den Skriptblock darstellt (der mit der Ereignis-ID 0x1008 korreliert werden kann). Die Runspace-ID stellt den Runspace dar, in dem dieser Skriptblock ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="5e120-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="5e120-146">Prozentzeichen in der Aufrufmeldung stellen strukturierte ETW-Eigenschaften dar.</span><span class="sxs-lookup"><span data-stu-id="5e120-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="5e120-147">Wenngleich sie im Meldungstext durch die tatsächlichen Werte ersetzt werden, empfiehlt sich für den Zugriff darauf eher das Abrufen der Meldung mit dem Cmdlet „Get-WinEvent“ und dann das Untersuchen des Bereichs **Eigenschaften** der Meldung.</span><span class="sxs-lookup"><span data-stu-id="5e120-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="5e120-148">Hier ist ein Beispiel, wie diese Funktionalität helfen kann, einen böswilligen Versuch zum Verschlüsseln und Verschleiern eines Skripts zu erkennen:</span><span class="sxs-lookup"><span data-stu-id="5e120-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

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

<span data-ttu-id="5e120-149">Bei Ausführen dieses Befehls werden die folgenden Einträge generiert:</span><span class="sxs-lookup"><span data-stu-id="5e120-149">Running this generates the following log entries:</span></span>

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

Wenn die Länge eines Skriptblocks größer als die Kapazität eines einzelnen Ereignisses ist, teilt PowerShell das Skript in mehrere Teile auf. <span data-ttu-id="5e120-151">Hier ist Beispielcode für das erneute Zusammenzusetzen der Protokollmeldungen eines Skripts:</span><span class="sxs-lookup"><span data-stu-id="5e120-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="5e120-152">Wie alle Protokollierungssysteme, die einen begrenzten Aufbewahrungspuffer haben, besteht eine Angriffsmöglichkeit auf diese Infrastruktur darin, dass Protokoll mit gefälschten Ereignissen zu überfluten, um ein früheres Vorkommen zu vertuschen.</span><span class="sxs-lookup"><span data-stu-id="5e120-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="5e120-153">Um sich vor diesen Angriffen zu schützen, stellen Sie sicher, dass Sie eine Form der Ereignisprotokollerfassung eingerichtet haben, z. B. Windows-Ereignisweiterleitung.</span><span class="sxs-lookup"><span data-stu-id="5e120-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="5e120-154">Weitere Informationen finden Sie unter [Ermitteln des Angreifers mit Überwachung des Windows-Ereignisprotokolls](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span><span class="sxs-lookup"><span data-stu-id="5e120-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>