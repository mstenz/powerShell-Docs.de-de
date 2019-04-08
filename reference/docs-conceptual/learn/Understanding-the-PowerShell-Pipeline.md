---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: Grundlegendes zu PowerShell-Modulen
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 05ab98b7261f4d41ade1788a924193eccda6318c
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623958"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="60fba-103">Grundlegendes zu Pipelines</span><span class="sxs-lookup"><span data-stu-id="60fba-103">Understanding pipelines</span></span>

<span data-ttu-id="60fba-104">Eine Pipeline fungiert als eine Reihe von verbundenen Segmenten eines Rohrs.</span><span class="sxs-lookup"><span data-stu-id="60fba-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="60fba-105">Elemente, die durch die Pipeline geleitet werden, durchlaufen jedes Segment.</span><span class="sxs-lookup"><span data-stu-id="60fba-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="60fba-106">Um eine Pipeline in PowerShell zu erstellen, verbinden Sie Befehle mit dem Pipeoperator „|“.</span><span class="sxs-lookup"><span data-stu-id="60fba-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="60fba-107">Die Ausgabe eines Befehls wird als Eingabe des nächsten Befehls verwendet.</span><span class="sxs-lookup"><span data-stu-id="60fba-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="60fba-108">Die Notation für Pipelines ist der Notation in anderen Shells ähnlich.</span><span class="sxs-lookup"><span data-stu-id="60fba-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="60fba-109">Auf den ersten Blick ist es möglicherweise nicht offensichtlich, wie sich Pipelines in PowerShell unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="60fba-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="60fba-110">Obwohl Text auf dem Bildschirm angezeigt wird, leitet PowerShell Objekte und keinen Text zwischen Befehlen weiter.</span><span class="sxs-lookup"><span data-stu-id="60fba-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="60fba-111">Die PowerShell-Pipeline</span><span class="sxs-lookup"><span data-stu-id="60fba-111">The PowerShell pipeline</span></span>

<span data-ttu-id="60fba-112">Pipelines sind wohl das wertvollste Konzept, das Befehlszeilenschnittstellen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="60fba-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="60fba-113">Bei richtigem Einsatz verringern Pipelines den Aufwand durch die Verwendung von komplexen Befehlen und erleichtern es, den Ablauf der Befehle zu sehen.</span><span class="sxs-lookup"><span data-stu-id="60fba-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="60fba-114">Jeder Befehl in einer Pipeline (wird als Pipelineelement bezeichnet) übergibt seine Ausgabe elementweise an den nächsten Befehl in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="60fba-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="60fba-115">Befehle müssen jeweils nur ein Element zurzeit verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="60fba-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="60fba-116">Das Ergebnis ist eine verringerte Ressourcennutzung und die Möglichkeit, die Ausgabe unmittelbar zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="60fba-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="60fba-117">Wenn Sie beispielsweise das Cmdlet `Out-Host` zum Erzwingen einer seitenweisen Anzeige der Ausgabe eines anderen Befehls verwenden, sieht die Ausgabe wie der normale auf dem Bildschirm gezeigte Text aus, der in Seiten unterteilt ist:</span><span class="sxs-lookup"><span data-stu-id="60fba-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

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

<span data-ttu-id="60fba-118">Durch die Einteilung in Seiten wird auch die CPU-Auslastung reduziert, da die Verarbeitung an das Cmdlet `Out-Host` übertragen wird, wenn eine vollständige Seite für die Anzeige bereit ist.</span><span class="sxs-lookup"><span data-stu-id="60fba-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="60fba-119">Die Cmdlets, die sich in der Pipeline davor befinden, unterbrechen die Ausführung, bis die nächste Seite der Ausgabe verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="60fba-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="60fba-120">Sie können den Unterschied im Windows Task-Manager überprüfen, indem Sie die CPU- und Arbeitsspeicherauslastung durch PowerShell überwachen.</span><span class="sxs-lookup"><span data-stu-id="60fba-120">You can see the difference Windows Task Manager to monitor CPU and memory used by PowerShell.</span></span> <span data-ttu-id="60fba-121">Führen Sie den folgenden Befehl aus: `Get-ChildItem C:\Windows -Recurse`.</span><span class="sxs-lookup"><span data-stu-id="60fba-121">Run the following command: `Get-ChildItem C:\Windows -Recurse`.</span></span> <span data-ttu-id="60fba-122">Vergleichen die CPU- und Arbeitsspeicherauslastung mit diesem Befehl: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span><span class="sxs-lookup"><span data-stu-id="60fba-122">Compare the CPU and memory usage to this command: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span></span>

> [!NOTE]
> <span data-ttu-id="60fba-123">Der **Paging**-Parameter wird nicht von allen PowerShell-Hosts unterstützt.</span><span class="sxs-lookup"><span data-stu-id="60fba-123">The **Paging** parameter is not supported by all PowerShell hosts.</span></span> <span data-ttu-id="60fba-124">Wenn Sie z.B. versuchen, den **Paging**-Parameter in der PowerShell-ISE zu verwenden, wird folgende Fehlermeldung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="60fba-124">For example, when you try to use the **Paging** parameter in the PowerShell ISE, you see the following error:</span></span>
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="60fba-125">Objekte in der Pipeline</span><span class="sxs-lookup"><span data-stu-id="60fba-125">Objects in the pipeline</span></span>

<span data-ttu-id="60fba-126">Wenn Sie ein Cmdlet in PowerShell ausführen, sehen Sie eine Textausgabe, da es erforderlich ist, Objekte in einem Konsolenfenster als Text darzustellen.</span><span class="sxs-lookup"><span data-stu-id="60fba-126">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="60fba-127">Die Textausgabe enthält möglicherweise nicht alle Eigenschaften des Objekts, das ausgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="60fba-127">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="60fba-128">Betrachten Sie beispielsweise das Cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="60fba-128">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="60fba-129">Bei der Ausführung von `Get-Location`, während Ihr aktueller Speicherort der Stamm von Laufwerk C: ist, sehen Sie die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="60fba-129">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="60fba-130">Die Textausgabe ist eine Zusammenfassung der Informationen, keine vollständige Darstellung des Objekts, das von `Get-Location` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="60fba-130">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="60fba-131">Die Überschrift in der Ausgabe wird durch den Prozess hinzugefügt, der die Daten für die Anzeige auf dem Bildschirm formatiert.</span><span class="sxs-lookup"><span data-stu-id="60fba-131">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="60fba-132">Wenn Sie die Ausgabe an das Cmdlet `Get-Member` weiterleiten, erhalten Sie Informationen über das Objekt, das von `Get-Location` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="60fba-132">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
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

<span data-ttu-id="60fba-133">`Get-Location` gibt ein **PathInfo**-Objekt zurück, das den aktuellen Pfad und andere Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="60fba-133">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
