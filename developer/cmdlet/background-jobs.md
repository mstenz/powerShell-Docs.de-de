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
ms.openlocfilehash: ff4fe159eedc47fc69f4d783cd90d2b0e888c0d5
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794704"
---
# <a name="background-jobs"></a><span data-ttu-id="7ea79-102">Hintergrundaufträge</span><span class="sxs-lookup"><span data-stu-id="7ea79-102">Background Jobs</span></span>

<span data-ttu-id="7ea79-103">Cmdlets können ihre Aktion ausführen, intern oder als ein Windows PowerShell*Hintergrundauftrag*.</span><span class="sxs-lookup"><span data-stu-id="7ea79-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="7ea79-104">Wenn ein Cmdlet als Hintergrundauftrag ausgeführt wird, wird die Arbeit asynchron in einem eigenen Thread getrennt von der Pipeline-Thread durchgeführt, die mit dem-Cmdlet verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7ea79-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="7ea79-105">Aus der Perspektive des Benutzers Wenn ein Cmdlet als Hintergrundauftrag ausgeführt wird die Eingabeaufforderung wird sofort zurückgegeben auch, wenn der Auftrag einen erweiterten Zeitraum nimmt abgeschlossen und der Benutzer ohne Unterbrechung weiterhin während der Auftrag ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7ea79-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="7ea79-106">Hintergrundaufträge, untergeordneten Aufträge und die Auftragsrepository</span><span class="sxs-lookup"><span data-stu-id="7ea79-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="7ea79-107">Das Objekt, das von den Cmdlets zurückgegeben wird, die Unterstützung von Hintergrundaufträgen definiert den Auftrag.</span><span class="sxs-lookup"><span data-stu-id="7ea79-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="7ea79-108">(Die [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) Cmdlet gibt auch ein Auftragsobjekt zurück.) Der Name des Auftrags und ein Bezeichner, der verwendet wird, um den Auftrag, Informationen über den Zustand und die untergeordneten Aufträge angeben, sind in dieser Definition enthalten.</span><span class="sxs-lookup"><span data-stu-id="7ea79-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="7ea79-109">Der Auftrag führt keiner arbeiten.</span><span class="sxs-lookup"><span data-stu-id="7ea79-109">The job does not perform any of the work.</span></span> <span data-ttu-id="7ea79-110">Jeden Hintergrundauftrag verfügt über mindestens einen untergeordneten Auftrag aus, da der untergeordnete Auftrag die eigentliche Arbeit ausführt.</span><span class="sxs-lookup"><span data-stu-id="7ea79-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="7ea79-111">Wenn Sie ein Cmdlet ausgeführt, sodass die Arbeit als Hintergrundauftrag ausgeführt wird, das Cmdlet muss hinzufügen den Auftrag und die untergeordneten Aufträge auf einem gemeinsamen Repository, um genannte der *auftragsrepository*.</span><span class="sxs-lookup"><span data-stu-id="7ea79-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="7ea79-112">Weitere Informationen zur Behandlung von Hintergrundaufträgen in der Befehlszeile finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="7ea79-112">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="7ea79-113">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="7ea79-113">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="7ea79-114">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="7ea79-114">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="7ea79-115">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="7ea79-115">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="7ea79-116">Schreiben eines Cmdlets, die als Hintergrundauftrag ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7ea79-116">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="7ea79-117">Um ein Cmdlet zu schreiben, die als Hintergrundauftrag ausgeführt werden können, müssen Sie die folgenden Aufgaben ausführen:</span><span class="sxs-lookup"><span data-stu-id="7ea79-117">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="7ea79-118">Definieren einer `asJob` switch-Parameter, damit der Benutzer entscheiden, ob das Cmdlet als Hintergrundauftrag ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="7ea79-118">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="7ea79-119">Erstellen Sie ein Objekt, das von abgeleitet ist die [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Klasse.</span><span class="sxs-lookup"><span data-stu-id="7ea79-119">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="7ea79-120">Dieses Objekt kann sein, ein benutzerdefiniertes Job-Objekt oder ein Job-Objekt, das von Windows PowerShell bereitgestellt wurde, z. B. eine [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) Objekt.</span><span class="sxs-lookup"><span data-stu-id="7ea79-120">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="7ea79-121">Fügen Sie in einem Datensatz Verarbeitungsmethode ein `if` -Anweisung, die erkennt, ob das Cmdlet als Hintergrundauftrag ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="7ea79-121">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="7ea79-122">Implementieren Sie für benutzerdefinierte Auftragstypen-Objekte die Auftragsklasse.</span><span class="sxs-lookup"><span data-stu-id="7ea79-122">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="7ea79-123">Zurückgeben der entsprechenden Objekte, abhängig davon, ob das Cmdlet als Hintergrundauftrag ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7ea79-123">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="7ea79-124">Ein Codebeispiel finden Sie unter [wie Unterstützung Aufträge](./how-to-support-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="7ea79-124">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="7ea79-125">Auftragsbezogene Hintergrund-APIs</span><span class="sxs-lookup"><span data-stu-id="7ea79-125">Background Job-Related APIs</span></span>

<span data-ttu-id="7ea79-126">Die folgenden APIs werden von Windows PowerShell zum Verwalten von Hintergrundaufträgen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7ea79-126">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="7ea79-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) benutzerdefinierte Auftragsobjekte abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="7ea79-127">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="7ea79-128">Dies ist eine abstrakte Klasse.</span><span class="sxs-lookup"><span data-stu-id="7ea79-128">This is an abstract class.</span></span>

<span data-ttu-id="7ea79-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) verwaltet und bietet Informationen zum aktuellen aktiven Hintergrundaufträge.</span><span class="sxs-lookup"><span data-stu-id="7ea79-129">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="7ea79-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) definiert den Status des Hintergrundauftrags.</span><span class="sxs-lookup"><span data-stu-id="7ea79-130">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="7ea79-131">Der Zustände enthalten, gestartet, ausgeführt und beendet.</span><span class="sxs-lookup"><span data-stu-id="7ea79-131">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="7ea79-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) enthält Informationen zum Status eines Auftrags im Hintergrund und, wenn der letzte Zustand geändert wurde aufgrund eines Fehlers, der Grund, die der Auftrag angenommen hat, den aktuellen Zustand verursacht.</span><span class="sxs-lookup"><span data-stu-id="7ea79-132">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="7ea79-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) stellt die Argumente für ein Ereignis, das ausgelöst wird, wenn ein Hintergrundauftrag Zustand ändert.</span><span class="sxs-lookup"><span data-stu-id="7ea79-133">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="7ea79-134">Windows PowerShell-Job-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="7ea79-134">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="7ea79-135">Die folgenden Cmdlets werden von Windows PowerShell zum Verwalten von Hintergrundaufträgen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7ea79-135">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="7ea79-136">Get-Job</span><span class="sxs-lookup"><span data-stu-id="7ea79-136">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="7ea79-137">Ruft Windows PowerShell-Hintergrundaufträge ab, die in der aktuellen Sitzung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="7ea79-137">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="7ea79-138">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="7ea79-138">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="7ea79-139">Ruft die Ergebnisse der Windows PowerShell-Hintergrundaufträge in der aktuellen Sitzung ab.</span><span class="sxs-lookup"><span data-stu-id="7ea79-139">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="7ea79-140">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="7ea79-140">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="7ea79-141">Löscht einen Windows PowerShell-Hintergrundauftrag.</span><span class="sxs-lookup"><span data-stu-id="7ea79-141">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7ea79-142">Start-Job</span><span class="sxs-lookup"><span data-stu-id="7ea79-142">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="7ea79-143">Startet einen Windows PowerShell-Hintergrundauftrag.</span><span class="sxs-lookup"><span data-stu-id="7ea79-143">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7ea79-144">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="7ea79-144">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="7ea79-145">Beendet einen Windows PowerShell-Hintergrundauftrag.</span><span class="sxs-lookup"><span data-stu-id="7ea79-145">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="7ea79-146">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="7ea79-146">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="7ea79-147">Unterdrückt die Eingabeaufforderung, bis ein oder alle der in der Sitzung ausgeführten Windows PowerShell-Hintergrundaufträge abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="7ea79-147">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ea79-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7ea79-148">See Also</span></span>

[<span data-ttu-id="7ea79-149">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="7ea79-149">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
