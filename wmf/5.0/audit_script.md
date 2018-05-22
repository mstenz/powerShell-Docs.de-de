---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2627b9d02788bd31a5384587406df533faf2cfaf
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="632d3-102">Ablaufverfolgung und Protokollierung von Skripts</span><span class="sxs-lookup"><span data-stu-id="632d3-102">Script Tracing and Logging</span></span>

<span data-ttu-id="632d3-103">Während Windows PowerShell bereits über die Gruppenrichtlinieneinstellung **LogPipelineExecutionDetails** verfügt, um den Aufruf von Cmdlets zu protokollieren, bietet die PowerShell-Skriptsprache viele Features, die Sie ggf. protokollieren und/oder überwachen möchten.</span><span class="sxs-lookup"><span data-stu-id="632d3-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="632d3-104">Das neue Feature zur detaillierten Ablaufverfolgung von Skripts ermöglicht eine detaillierte Nachverfolgung und Analyse der Verwendung von Windows PowerShell-Skripts auf einem System.</span><span class="sxs-lookup"><span data-stu-id="632d3-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="632d3-105">Nachdem Sie die detaillierte Ablaufverfolgung von Skripts aktiviert haben, protokolliert Windows PowerShell alle Skriptblöcke im ETW-Ereignisprotokoll **Microsoft-Windows-PowerShell/Operational**.</span><span class="sxs-lookup"><span data-stu-id="632d3-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="632d3-106">Wenn ein Skriptblock einen anderen Skriptblock erstellt (ein Skript z. B. das Cmdlet „Invoke-Expression“ für eine Zeichenfolge aufruft), wird dieser resultierende Skriptblock ebenfalls protokolliert.</span><span class="sxs-lookup"><span data-stu-id="632d3-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="632d3-107">Die Protokollierung dieser Ereignisse kann über die Gruppenrichtlinieneinstellung **Protokollierung von PowerShell-Skriptblöcken aktivieren** (Administrative Vorlagen -> Windows-Komponenten -> Windows PowerShell) aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="632d3-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="632d3-108">Die Ereignisse sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="632d3-108">The events are:</span></span>

| <span data-ttu-id="632d3-109">Kanal</span><span class="sxs-lookup"><span data-stu-id="632d3-109">Channel</span></span> | <span data-ttu-id="632d3-110">Betriebsbereit</span><span class="sxs-lookup"><span data-stu-id="632d3-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="632d3-111">Ebene</span><span class="sxs-lookup"><span data-stu-id="632d3-111">Level</span></span>   | <span data-ttu-id="632d3-112">Ausführlich</span><span class="sxs-lookup"><span data-stu-id="632d3-112">Verbose</span></span>                                     |
| <span data-ttu-id="632d3-113">Opcode</span><span class="sxs-lookup"><span data-stu-id="632d3-113">Opcode</span></span>  | <span data-ttu-id="632d3-114">Erstellen</span><span class="sxs-lookup"><span data-stu-id="632d3-114">Create</span></span>                                      |
| <span data-ttu-id="632d3-115">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="632d3-115">Task</span></span>    | <span data-ttu-id="632d3-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="632d3-116">CommandStart</span></span>                                |
| <span data-ttu-id="632d3-117">Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="632d3-117">Keyword</span></span> | <span data-ttu-id="632d3-118">Runspace</span><span class="sxs-lookup"><span data-stu-id="632d3-118">Runspace</span></span>                                    |
| <span data-ttu-id="632d3-119">Ereignis-ID</span><span class="sxs-lookup"><span data-stu-id="632d3-119">EventId</span></span> | <span data-ttu-id="632d3-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="632d3-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="632d3-121">Meldung</span><span class="sxs-lookup"><span data-stu-id="632d3-121">Message</span></span> | <span data-ttu-id="632d3-122">Skriptblocktext (%1 von %2) wird erstellt:</span><span class="sxs-lookup"><span data-stu-id="632d3-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="632d3-123">%3</span><span class="sxs-lookup"><span data-stu-id="632d3-123">%3</span></span> </br> <span data-ttu-id="632d3-124">ScriptBlock-ID: %4</span><span class="sxs-lookup"><span data-stu-id="632d3-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="632d3-125">Der in der Meldung eingebettete Text gibt das Ausmaß des kompilierten Skriptblocks an.</span><span class="sxs-lookup"><span data-stu-id="632d3-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="632d3-126">Die ID ist eine GUID, die für die Gültigkeitsdauer des Skriptblocks beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="632d3-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="632d3-127">Wenn Sie die ausführlichen Protokollierung aktivieren, schreibt das Feature die Markierungen „begin“ und „end“:</span><span class="sxs-lookup"><span data-stu-id="632d3-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="632d3-128">Kanal</span><span class="sxs-lookup"><span data-stu-id="632d3-128">Channel</span></span> | <span data-ttu-id="632d3-129">Betriebsbereit</span><span class="sxs-lookup"><span data-stu-id="632d3-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="632d3-130">Ebene</span><span class="sxs-lookup"><span data-stu-id="632d3-130">Level</span></span>   | <span data-ttu-id="632d3-131">Ausführlich</span><span class="sxs-lookup"><span data-stu-id="632d3-131">Verbose</span></span>                                                |
| <span data-ttu-id="632d3-132">Opcode</span><span class="sxs-lookup"><span data-stu-id="632d3-132">Opcode</span></span>  | <span data-ttu-id="632d3-133">Öffnen (/ Schließen)</span><span class="sxs-lookup"><span data-stu-id="632d3-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="632d3-134">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="632d3-134">Task</span></span>    | <span data-ttu-id="632d3-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="632d3-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="632d3-136">Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="632d3-136">Keyword</span></span> | <span data-ttu-id="632d3-137">Runspace</span><span class="sxs-lookup"><span data-stu-id="632d3-137">Runspace</span></span>                                               |
| <span data-ttu-id="632d3-138">Ereignis-ID</span><span class="sxs-lookup"><span data-stu-id="632d3-138">EventId</span></span> | <span data-ttu-id="632d3-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="632d3-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="632d3-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) /</span><span class="sxs-lookup"><span data-stu-id="632d3-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="632d3-141">Message</span><span class="sxs-lookup"><span data-stu-id="632d3-141">Message</span></span> | <span data-ttu-id="632d3-142">Der Aufruf der ScriptBlock-ID wurde gestartet (/ abgeschlossen: %1</span><span class="sxs-lookup"><span data-stu-id="632d3-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="632d3-143">Runspace-ID: %2</span><span class="sxs-lookup"><span data-stu-id="632d3-143">Runspace ID: %2</span></span> |

<span data-ttu-id="632d3-144">Die ID ist die GUID, die den Skriptblock darstellt (der mit der Ereignis-ID 0x1008 korreliert werden kann). Die Runspace-ID stellt den Runspace dar, in dem dieser Skriptblock ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="632d3-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="632d3-145">Prozentzeichen in der Aufrufmeldung stellen strukturierte ETW-Eigenschaften dar.</span><span class="sxs-lookup"><span data-stu-id="632d3-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="632d3-146">Wenngleich sie im Meldungstext durch die tatsächlichen Werte ersetzt werden, empfiehlt sich für den Zugriff darauf eher das Abrufen der Meldung mit dem Cmdlet „Get-WinEvent“ und dann das Untersuchen des Bereichs **Eigenschaften** der Meldung.</span><span class="sxs-lookup"><span data-stu-id="632d3-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="632d3-147">Hier ist ein Beispiel, wie diese Funktionalität helfen kann, einen böswilligen Versuch zum Verschlüsseln und Verschleiern eines Skripts zu erkennen:</span><span class="sxs-lookup"><span data-stu-id="632d3-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
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

<span data-ttu-id="632d3-148">Bei Ausführen dieses Befehls werden die folgenden Einträge generiert:</span><span class="sxs-lookup"><span data-stu-id="632d3-148">Running this generates the following log entries:</span></span>

```
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

Wenn die Länge eines Skriptblocks größer als das Maximum ist, das ETW in einem einzelnen Ereignis zulässt, teilt Windows PowerShell das Skript in mehrere Teile auf. <span data-ttu-id="632d3-150">Hier ist Beispielcode für das erneute Zusammenzusetzen der Protokollmeldungen eines Skripts:</span><span class="sxs-lookup"><span data-stu-id="632d3-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="632d3-151">Wie alle Protokollierungssysteme, die einen begrenzten Aufbewahrungspuffer haben (wie z. B. ETW-Protokolle), besteht ein Angriff auf diese Infrastruktur darin, dass Protokoll mit gefälschten Ereignissen zu überfluten, um ein früheres Vorkommen zu vertuschen.</span><span class="sxs-lookup"><span data-stu-id="632d3-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="632d3-152">Um sich vor einem solchen Angriff zu schützen, stellen Sie sicher, dass Sie eine Form der Ereignisprotokollsammlung eingerichtet haben (z. B. Windows-Ereignisweiterleitung, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf) [Erkennen des Gegners mithilfe der Überwachung des Windows-Ereignisprotokolls]), um Ereignisprotokolle so schnell wie möglich vom Computer zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="632d3-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf)) to move event logs off of the computer as soon as possible.</span></span>
