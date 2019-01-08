---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: Grundlegendes zu PowerShell-Modulen
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: fc7c7f57bdce458185a0f5bdb8bc1fbbd81d0d61
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401217"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="e2dd6-103">Grundlegendes zu Pipelines</span><span class="sxs-lookup"><span data-stu-id="e2dd6-103">Understanding pipelines</span></span>

<span data-ttu-id="e2dd6-104">Eine Pipeline fungiert als eine Reihe von verbundenen Segmenten eines Rohrs.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="e2dd6-105">Elemente, die durch die Pipeline geleitet werden, durchlaufen jedes Segment.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="e2dd6-106">Um eine Pipeline in PowerShell zu erstellen, verbinden Sie Befehle mit dem Pipeoperator „|“.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="e2dd6-107">Die Ausgabe eines Befehls wird als Eingabe des nächsten Befehls verwendet.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="e2dd6-108">Die Notation für Pipelines ist der Notation in anderen Shells ähnlich.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="e2dd6-109">Auf den ersten Blick ist es möglicherweise nicht offensichtlich, wie sich Pipelines in PowerShell unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="e2dd6-110">Obwohl Text auf dem Bildschirm angezeigt wird, leitet PowerShell Objekte und keinen Text zwischen Befehlen weiter.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="e2dd6-111">Die PowerShell-Pipeline</span><span class="sxs-lookup"><span data-stu-id="e2dd6-111">The PowerShell pipeline</span></span>

<span data-ttu-id="e2dd6-112">Pipelines sind wohl das wertvollste Konzept, das Befehlszeilenschnittstellen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="e2dd6-113">Bei richtigem Einsatz verringern Pipelines den Aufwand durch die Verwendung von komplexen Befehlen und erleichtern es, den Ablauf der Befehle zu sehen.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="e2dd6-114">Jeder Befehl in einer Pipeline (wird als Pipelineelement bezeichnet) übergibt seine Ausgabe elementweise an den nächsten Befehl in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="e2dd6-115">Befehle müssen jeweils nur ein Element zurzeit verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="e2dd6-116">Das Ergebnis ist eine verringerte Ressourcennutzung und die Möglichkeit, die Ausgabe unmittelbar zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="e2dd6-117">Wenn Sie beispielsweise das Cmdlet `Out-Host` zum Erzwingen einer seitenweisen Anzeige der Ausgabe eines anderen Befehls verwenden, sieht die Ausgabe wie der normale auf dem Bildschirm gezeigte Text aus, der in Seiten unterteilt ist:</span><span class="sxs-lookup"><span data-stu-id="e2dd6-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="e2dd6-118">Durch die Einteilung in Seiten wird auch die CPU-Auslastung reduziert, da die Verarbeitung an das Cmdlet `Out-Host` übertragen wird, wenn eine vollständige Seite für die Anzeige bereit ist.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="e2dd6-119">Die Cmdlets, die sich in der Pipeline davor befinden, unterbrechen die Ausführung, bis die nächste Seite der Ausgabe verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="e2dd6-120">Sie können den Unterschied im Windows Task-Manager überprüfen, indem Sie die CPU- und Arbeitsspeicherauslastung durch PowerShell überwachen.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-120">You can see the difference Windows Task Manager to monitor CPU and memory used by PowerShell.</span></span> <span data-ttu-id="e2dd6-121">Führen Sie den folgenden Befehl aus: `Get-ChildItem C:\Windows -Recurse`.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-121">Run the following command: `Get-ChildItem C:\Windows -Recurse`.</span></span> <span data-ttu-id="e2dd6-122">Vergleichen die CPU- und Arbeitsspeicherauslastung mit diesem Befehl: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-122">Compare the CPU and memory usage to this command: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span></span>

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="e2dd6-123">Objekte in der Pipeline</span><span class="sxs-lookup"><span data-stu-id="e2dd6-123">Objects in the pipeline</span></span>

<span data-ttu-id="e2dd6-124">Wenn Sie ein Cmdlet in PowerShell ausführen, sehen Sie eine Textausgabe, da es erforderlich ist, Objekte in einem Konsolenfenster als Text darzustellen.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="e2dd6-125">Die Textausgabe enthält möglicherweise nicht alle Eigenschaften des Objekts, das ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="e2dd6-126">Betrachten Sie beispielsweise das Cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="e2dd6-127">Bei der Ausführung von `Get-Location`, während Ihr aktueller Speicherort der Stamm von Laufwerk C: ist, sehen Sie die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="e2dd6-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="e2dd6-128">Die Textausgabe ist eine Zusammenfassung der Informationen, keine vollständige Darstellung des Objekts, das von `Get-Location` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="e2dd6-129">Die Überschrift in der Ausgabe wird durch den Prozess hinzugefügt, der die Daten für die Anzeige auf dem Bildschirm formatiert.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="e2dd6-130">Wenn Sie die Ausgabe an das Cmdlet `Get-Member` weiterleiten, erhalten Sie Informationen über das Objekt, das von `Get-Location` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
PS> Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="e2dd6-131">`Get-Location` gibt ein **PathInfo**-Objekt zurück, das den aktuellen Pfad und andere Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="e2dd6-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
