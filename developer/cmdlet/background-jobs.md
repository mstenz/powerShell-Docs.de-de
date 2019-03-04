---
title: Hintergrundaufträge | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: 9aff23647e55e8c9c41c54e5b62cedc15fb28a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857166"
---
# <a name="background-jobs"></a><span data-ttu-id="fcf29-102">Hintergrundaufträge</span><span class="sxs-lookup"><span data-stu-id="fcf29-102">Background Jobs</span></span>

<span data-ttu-id="fcf29-103">Cmdlets können ihre Aktion ausführen, intern oder als ein Windows PowerShell*Hintergrundauftrag*.</span><span class="sxs-lookup"><span data-stu-id="fcf29-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="fcf29-104">Wenn ein Cmdlet als Hintergrundauftrag ausgeführt wird, wird die Arbeit asynchron in einem eigenen Thread getrennt von der Pipeline-Thread durchgeführt, die mit dem-Cmdlet verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="fcf29-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="fcf29-105">Aus der Perspektive des Benutzers Wenn ein Cmdlet als Hintergrundauftrag ausgeführt wird die Eingabeaufforderung wird sofort zurückgegeben auch, wenn der Auftrag einen erweiterten Zeitraum nimmt abgeschlossen und der Benutzer ohne Unterbrechung weiterhin während der Auftrag ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fcf29-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="fcf29-106">Hintergrundaufträge, untergeordneten Aufträge und die Auftragsrepository</span><span class="sxs-lookup"><span data-stu-id="fcf29-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="fcf29-107">Das Objekt, das von den Cmdlets zurückgegeben wird, die Unterstützung von Hintergrundaufträgen definiert den Auftrag.</span><span class="sxs-lookup"><span data-stu-id="fcf29-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="fcf29-108">(Die [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) Cmdlet gibt auch ein Auftragsobjekt zurück.) Der Name des Auftrags und ein Bezeichner, der verwendet wird, um den Auftrag, Informationen über den Zustand und die untergeordneten Aufträge angeben, sind in dieser Definition enthalten.</span><span class="sxs-lookup"><span data-stu-id="fcf29-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="fcf29-109">Der Auftrag führt keiner arbeiten.</span><span class="sxs-lookup"><span data-stu-id="fcf29-109">The job does not perform any of the work.</span></span> <span data-ttu-id="fcf29-110">Jeden Hintergrundauftrag verfügt über mindestens einen untergeordneten Auftrag aus, da der untergeordnete Auftrag die eigentliche Arbeit ausführt.</span><span class="sxs-lookup"><span data-stu-id="fcf29-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="fcf29-111">Wenn Sie ein Cmdlet ausgeführt, sodass die Arbeit als Hintergrundauftrag ausgeführt wird, das Cmdlet muss hinzufügen den Auftrag und die untergeordneten Aufträge auf einem gemeinsamen Repository, um genannte der *auftragsrepository*.</span><span class="sxs-lookup"><span data-stu-id="fcf29-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>
<span data-ttu-id="fcf29-112">Das Objekt, das von den Cmdlets zurückgegeben wird, die Unterstützung von Hintergrundaufträgen definiert den Auftrag.</span><span class="sxs-lookup"><span data-stu-id="fcf29-112">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="fcf29-113">(Die [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) Cmdlet gibt auch ein Auftragsobjekt zurück.) Der Name des Auftrags und ein Bezeichner, der verwendet wird, um den Auftrag, Informationen über den Zustand und die untergeordneten Aufträge angeben, sind in dieser Definition enthalten.</span><span class="sxs-lookup"><span data-stu-id="fcf29-113">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="fcf29-114">Der Auftrag führt keiner arbeiten.</span><span class="sxs-lookup"><span data-stu-id="fcf29-114">The job does not perform any of the work.</span></span> <span data-ttu-id="fcf29-115">Jeden Hintergrundauftrag verfügt über mindestens einen untergeordneten Auftrag aus, da der untergeordnete Auftrag die eigentliche Arbeit ausführt.</span><span class="sxs-lookup"><span data-stu-id="fcf29-115">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="fcf29-116">Wenn Sie ein Cmdlet ausgeführt, sodass die Arbeit als Hintergrundauftrag ausgeführt wird, das Cmdlet muss hinzufügen den Auftrag und die untergeordneten Aufträge auf einem gemeinsamen Repository, um genannte der *auftragsrepository*.</span><span class="sxs-lookup"><span data-stu-id="fcf29-116">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="fcf29-117">Weitere Informationen zur Behandlung von Hintergrundaufträgen in der Befehlszeile finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="fcf29-117">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="fcf29-118">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="fcf29-118">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="fcf29-119">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="fcf29-119">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="fcf29-120">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="fcf29-120">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="fcf29-121">Schreiben eines Cmdlets, die als Hintergrundauftrag ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fcf29-121">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="fcf29-122">Um ein Cmdlet zu schreiben, die als Hintergrundauftrag ausgeführt werden können, müssen Sie die folgenden Aufgaben ausführen:</span><span class="sxs-lookup"><span data-stu-id="fcf29-122">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="fcf29-123">Definieren einer `asJob` switch-Parameter, damit der Benutzer entscheiden, ob das Cmdlet als Hintergrundauftrag ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="fcf29-123">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="fcf29-124">Erstellen Sie ein Objekt, das von abgeleitet ist die [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Klasse.</span><span class="sxs-lookup"><span data-stu-id="fcf29-124">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="fcf29-125">Dieses Objekt kann sein, ein benutzerdefiniertes Job-Objekt oder ein Job-Objekt, das von Windows PowerShell bereitgestellt wurde, z. B. eine [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) Objekt.</span><span class="sxs-lookup"><span data-stu-id="fcf29-125">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="fcf29-126">Fügen Sie in einem Datensatz Verarbeitungsmethode ein `if` -Anweisung, die erkennt, ob das Cmdlet als Hintergrundauftrag ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="fcf29-126">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="fcf29-127">Implementieren Sie für benutzerdefinierte Auftragstypen-Objekte die Auftragsklasse.</span><span class="sxs-lookup"><span data-stu-id="fcf29-127">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="fcf29-128">Zurückgeben der entsprechenden Objekte, abhängig davon, ob das Cmdlet als Hintergrundauftrag ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fcf29-128">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="fcf29-129">Ein Codebeispiel finden Sie unter [wie Unterstützung Aufträge](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="fcf29-129">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="fcf29-130">Auftragsbezogene Hintergrund-APIs</span><span class="sxs-lookup"><span data-stu-id="fcf29-130">Background Job-Related APIs</span></span>

<span data-ttu-id="fcf29-131">Die folgenden APIs werden von Windows PowerShell zum Verwalten von Hintergrundaufträgen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="fcf29-131">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="fcf29-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) benutzerdefinierte Auftragsobjekte abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="fcf29-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="fcf29-133">Dies ist eine abstrakte Klasse.</span><span class="sxs-lookup"><span data-stu-id="fcf29-133">This is an abstract class.</span></span>

<span data-ttu-id="fcf29-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) verwaltet und bietet Informationen zum aktuellen aktiven Hintergrundaufträge.</span><span class="sxs-lookup"><span data-stu-id="fcf29-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="fcf29-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definiert den Status des Hintergrundauftrags.</span><span class="sxs-lookup"><span data-stu-id="fcf29-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="fcf29-136">Der Zustände enthalten, gestartet, ausgeführt und beendet.</span><span class="sxs-lookup"><span data-stu-id="fcf29-136">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="fcf29-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) enthält Informationen zum Status eines Auftrags im Hintergrund und, wenn der letzte Zustand geändert wurde aufgrund eines Fehlers, der Grund, die der Auftrag angenommen hat, den aktuellen Zustand verursacht.</span><span class="sxs-lookup"><span data-stu-id="fcf29-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="fcf29-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) stellt die Argumente für ein Ereignis, das ausgelöst wird, wenn ein Hintergrundauftrag Zustand ändert.</span><span class="sxs-lookup"><span data-stu-id="fcf29-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="fcf29-139">Windows PowerShell-Job-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fcf29-139">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="fcf29-140">Die folgenden Cmdlets werden von Windows PowerShell zum Verwalten von Hintergrundaufträgen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="fcf29-140">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="fcf29-141">Get-Job</span><span class="sxs-lookup"><span data-stu-id="fcf29-141">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="fcf29-142">Ruft Windows PowerShell-Hintergrundaufträge ab, die in der aktuellen Sitzung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="fcf29-142">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="fcf29-143">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="fcf29-143">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="fcf29-144">Ruft die Ergebnisse der Windows PowerShell-Hintergrundaufträge in der aktuellen Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="fcf29-144">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="fcf29-145">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="fcf29-145">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="fcf29-146">Löscht einen Windows PowerShell-Hintergrundauftrag.</span><span class="sxs-lookup"><span data-stu-id="fcf29-146">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="fcf29-147">Start-Job</span><span class="sxs-lookup"><span data-stu-id="fcf29-147">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="fcf29-148">Startet einen Windows PowerShell-Hintergrundauftrag.</span><span class="sxs-lookup"><span data-stu-id="fcf29-148">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="fcf29-149">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="fcf29-149">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="fcf29-150">Beendet einen Windows PowerShell-Hintergrundauftrag.</span><span class="sxs-lookup"><span data-stu-id="fcf29-150">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="fcf29-151">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="fcf29-151">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="fcf29-152">Unterdrückt die Eingabeaufforderung, bis ein oder alle der in der Sitzung ausgeführten Windows PowerShell-Hintergrundaufträge abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="fcf29-152">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcf29-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fcf29-153">See Also</span></span>

[<span data-ttu-id="fcf29-154">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fcf29-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
