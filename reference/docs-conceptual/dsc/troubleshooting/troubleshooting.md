---
ms.date: 10/30/2018
keywords: dsc,powershell,configuration,setup
title: Problembehandlung bei DSC
ms.openlocfilehash: 2a0d2138f30573b9ae6cf52d8b106a05f1193407
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954617"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="7bb5b-103">Problembehandlung bei DSC</span><span class="sxs-lookup"><span data-stu-id="7bb5b-103">Troubleshooting DSC</span></span>

<span data-ttu-id="7bb5b-104">_Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="7bb5b-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="7bb5b-105">Dieses Thema beschreibt die Problembehandlung für DSC.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="7bb5b-106">WinRM-Abhängigkeit</span><span class="sxs-lookup"><span data-stu-id="7bb5b-106">WinRM Dependency</span></span>

<span data-ttu-id="7bb5b-107">Windows PowerShell DSC (Desired State Configuration) hängt von WinRM ab.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="7bb5b-108">Unter Windows Server 2008 R2 und Windows 7 ist WinRM nicht standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="7bb5b-109">Führen Sie zum Aktivieren von WinRM in einer Windows PowerShell-Sitzung mit erhöhten Benutzerrechten `Set-WSManQuickConfig` aus.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="7bb5b-110">Verwenden von „Get-DscConfigurationStatus“</span><span class="sxs-lookup"><span data-stu-id="7bb5b-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="7bb5b-111">Das Cmdlet [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) ruft Informationen zum Konfigurationsstatus von einem Zielknoten ab.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="7bb5b-112">Ein umfangreiches Objekt wird zurückgegeben, das ausführliche Informationen dazu enthält, ob die Ausführung der Konfiguration erfolgreich war oder nicht.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="7bb5b-113">Sie können das Objekt eingehender untersuchen, um Details zur Ausführung der Konfiguration zu ermitteln, wie z. B.:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="7bb5b-114">Alle fehlerhaften Ressourcen</span><span class="sxs-lookup"><span data-stu-id="7bb5b-114">All of the resources that failed</span></span>
- <span data-ttu-id="7bb5b-115">Alle Ressourcen, die ein Neustart erfordern</span><span class="sxs-lookup"><span data-stu-id="7bb5b-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="7bb5b-116">Metakonfigurationseinstellungen zum Zeitpunkt der Konfigurationsausführung</span><span class="sxs-lookup"><span data-stu-id="7bb5b-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="7bb5b-117">usw.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-117">Etc.</span></span>

<span data-ttu-id="7bb5b-118">Die folgende Parametergruppe gibt die Statusinformationen zur letzten Konfigurationsausführung zurück:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="7bb5b-119">Die folgende Parametergruppe gibt die Statusinformationen zu allen vorherigen Konfigurationsausführungen zurück:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="7bb5b-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7bb5b-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ResourceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="7bb5b-121">Mein Skript wird nicht ausgeführt: Verwenden von DSC-Protokollen für die Diagnose von Skriptfehlern</span><span class="sxs-lookup"><span data-stu-id="7bb5b-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="7bb5b-122">Wie alle Windows-Softwareprogramme erfasst DSC Fehler und Ereignisse in [Protokollen](/windows/desktop/EventLog/about-event-logging), die Sie in der [Ereignisanzeige](https://support.microsoft.com/hub/4338813/windows-help) anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="7bb5b-123">Die Durchsicht dieser Protokolle kann Ihnen dabei helfen herauszufinden, warum ein bestimmter Vorgang fehlgeschlagen ist und wie Sie Fehler in Zukunft vermeiden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="7bb5b-124">Das Schreiben von Konfigurationsskripts ist nicht ganz einfach. Sie sollten daher den Fortschritt der Konfiguration im Ereignisprotokoll der DSC-Analyse mithilfe der DSC-Protokollressource verfolgen, um Fehler bei der Erstellung leichter aufspüren zu können.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="7bb5b-125">Wo befinden sich die DSC-Ereignisprotokolle?</span><span class="sxs-lookup"><span data-stu-id="7bb5b-125">Where are DSC event logs?</span></span>

<span data-ttu-id="7bb5b-126">In der Ereignisanzeige befinden sich DSC-Ereignisse unter: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="7bb5b-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="7bb5b-127">Die können auch das entsprechende PowerShell-Cmdlet [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) ausführen, um die Ereignisprotokolle anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="7bb5b-128">Wie oben gezeigt, lautet der primäre Protokollname von DSC **Microsoft > Windows > DSC** (andere Protokollnamen unter Windows werden hier aus Gründen der Übersichtlichkeit nicht dargestellt).</span><span class="sxs-lookup"><span data-stu-id="7bb5b-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="7bb5b-129">Der primäre Name wird an den Namen des Kanals angefügt. Daraus ergibt sich der vollständige Protokollname.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="7bb5b-130">Die DSC-Engine schreibt hauptsächlich in drei Arten von Protokollen: [Betriebs-, Analyse- und Debugprotokolle](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="7bb5b-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="7bb5b-131">Da die analytischen Protokolle und die Debugprotokolle standardmäßig deaktiviert sind, sollten Sie sie in der Ereignisanzeige aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="7bb5b-132">Öffnen Sie dazu die Ereignisanzeige, indem Sie in Windows PowerShell „Show-EventLog“ eingeben. Oder klicken Sie auf die Schaltfläche **Start** und dann auf **Systemsteuerung**, **Verwaltung** und **Ereignisanzeige**.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="7bb5b-133">Klicken Sie in der Ereignisanzeige im Menü **Ansicht** auf **Analytische und Debugprotokolle einblenden**.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="7bb5b-134">Der Name des für den analytischen Kanal lautet **Microsoft-Windows-Dsc/Analytic**, und der Debugkanal heißt **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="7bb5b-135">Außerdem können Sie zum Aktivieren der Protokolle das Hilfsprogramm [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) verwenden, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="7bb5b-136">Was ist in den DSC-Protokollen enthalten?</span><span class="sxs-lookup"><span data-stu-id="7bb5b-136">What do DSC logs contain?</span></span>

<span data-ttu-id="7bb5b-137">DSC-Protokolle werden, basierend auf der Wichtigkeit der Meldung, auf die drei Protokollkanäle verteilt.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="7bb5b-138">Das Betriebsprotokoll in DSC enthält alle Fehlermeldungen und kann verwendet werden, um ein Problem zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="7bb5b-139">Das analytische Protokoll enthält eine größere Anzahl von Ereignissen und dient dazu zu ermitteln, wo ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="7bb5b-140">Dieser Kanal enthält auch ausführliche Meldungen (falls vorhanden).</span><span class="sxs-lookup"><span data-stu-id="7bb5b-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="7bb5b-141">Das Debugprotokoll enthält Protokolle, die Ihnen helfen zu verstehen, wie der Fehler entstanden ist.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="7bb5b-142">DSC-Ereignismeldungen sind so aufgebaut, dass jede Ereignismeldung mit eine Auftrags-ID beginnt, die einen DSC-Vorgang eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="7bb5b-143">Im folgenden Beispiel wird versucht, die Meldung über das erste Ereignis abzurufen, das im DSC-Betriebsprotokoll protokolliert wurde.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="7bb5b-144">DSC-Ereignisse werden in einer bestimmten Struktur protokolliert, das dem Benutzer ermöglicht, Ereignisse eines DSC-Auftrags zusammenzufassen.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="7bb5b-145">Die Struktur sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="7bb5b-146">Sammeln von Ereignissen zu einem einzelnen DSC-Vorgang</span><span class="sxs-lookup"><span data-stu-id="7bb5b-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="7bb5b-147">DSC-Ereignisprotokolle enthalten Ereignisse, die mithilfe verschiedener DSC-Vorgänge generiert wurden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="7bb5b-148">Allerdings sind in der Regel nur die Details zu einem bestimmten Vorgang von Interesse für Sie.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="7bb5b-149">Alle DSC-Protokolle können nach der Auftrags-ID-Eigenschaft gruppiert werden, die für jeden DSC-Vorgang eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="7bb5b-150">Die Auftrags-ID wird in allen DSC-Ereignissen als erster Eigenschaftswert angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="7bb5b-151">Die folgenden Schritte erläutern, wie Sie alle Ereignisse in einer gruppierten Arraystruktur sammeln.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="7bb5b-152">Hier enthält die Variable `$SeparateDscOperations` nach den Auftrags-IDs gruppierte Protokolle.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="7bb5b-153">Jedes Arrayelement dieser Variablen stellt eine Gruppe von Ereignissen dar, die von einem anderen DSC-Vorgang protokolliert wurden, und ermöglicht den Zugriff auf weitere Informationen zu den Protokollen .</span><span class="sxs-lookup"><span data-stu-id="7bb5b-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="7bb5b-154">Sie können die Daten in der Variablen `$SeparateDscOperations` mit [Where-Object](/powershell/module/microsoft.powershell.core/where-object) extrahieren.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="7bb5b-155">In den folgenden fünf Szenarien ist es beispielsweise sinnvoll, Daten für die Problembehandlung bei DSC zu extrahieren:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="7bb5b-156">1: Fehler bei Vorgängen</span><span class="sxs-lookup"><span data-stu-id="7bb5b-156">1: Operations failures</span></span>

<span data-ttu-id="7bb5b-157">Alle Ereignisse verfügen über [Schweregrade](/windows/desktop/WES/defining-severity-levels).</span><span class="sxs-lookup"><span data-stu-id="7bb5b-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="7bb5b-158">Diese Informationen kann verwendet werden, um die Fehlerereignisse zu identifizieren:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="7bb5b-159">2: Details zu Vorgängen, die in der letzten halben Stunde ausgeführt wurden</span><span class="sxs-lookup"><span data-stu-id="7bb5b-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="7bb5b-160">`TimeCreated`, eine Eigenschaft jedes Windows-Ereignisses, gibt den Zeitpunkt an, zu dem das Ereignis erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="7bb5b-161">Durch Vergleichen dieser Eigenschaft mit einem bestimmten Datum/Uhrzeit-Objekt können Sie alle Ereignisse filtern:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="7bb5b-162">3: Meldungen zum aktuellen Vorgang</span><span class="sxs-lookup"><span data-stu-id="7bb5b-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="7bb5b-163">Der aktuelle Vorgang wird im ersten Index der Arraygruppe `$SeparateDscOperations` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="7bb5b-164">Durch Abfragen der Meldungen der Gruppe für den Index 0 werden alle Meldungen für den aktuellen Vorgang zurückgegeben:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="7bb5b-165">4: Fehlermeldungen, die für die letzten fehlgeschlagenen Vorgänge protokolliert wurden</span><span class="sxs-lookup"><span data-stu-id="7bb5b-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="7bb5b-166">`$SeparateDscOperations[0].Group` enthält eine Reihe von Ereignissen für den aktuellen Vorgang.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="7bb5b-167">Führen Sie das Cmdlet `Where-Object` aus, um die Ereignisse basierend auf dem Schweregrad/Anzeigenamen zu filtern.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="7bb5b-168">Die Ergebnisse werden in der Variablen `$myFailedEvent` gespeichert. Diese kann weiter zerlegt werden, um die Ereignismeldung zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="7bb5b-169">5: Alle Ereignisse, die für eine bestimmte Auftrags-ID generiert wurden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="7bb5b-170">`$SeparateDscOperations` ist ein Array von Gruppen, die jeweils den Namen als eindeutige Auftrags-ID aufweisen.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="7bb5b-171">Durch Ausführen des Cmdlets `Where-Object` können Sie die Gruppen von Ereignissen mit einer bestimmten Auftrags-ID extrahieren:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="7bb5b-172">Verwenden von „xDscDiagnostics“ zum Analysieren von DSC-Protokollen</span><span class="sxs-lookup"><span data-stu-id="7bb5b-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="7bb5b-173">**xDscDiagnostics** ist ein PowerShell-Modul, das aus mehreren Funktionen besteht, die bei der Analyse von DSC-Fehlern auf dem Computer helfen können.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="7bb5b-174">Diese Funktionen können Ihnen helfen, alle lokalen Ereignisse der letzten DSC-Vorgänge oder DSC-Ereignisse auf Remotecomputern (mit gültigen Anmeldeinformationen) zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="7bb5b-175">Hier wird der Begriff „DSC-Vorgang“ verwendet, um eine einzelne eindeutige DSC-Ausführung von Anfang bis Ende zu definieren.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="7bb5b-176">`Test-DscConfiguration` wäre z. B. ein separater DSC-Vorgang.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="7bb5b-177">Auf ähnliche Weise kann jedes andere Cmdlet in DSC (z. B. `Get-DscConfiguration`, `Start-DscConfiguration` usw.) jeweils als separater DSC-Vorgang identifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="7bb5b-178">Die Funktionen werden unter [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics) erläutert.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="7bb5b-179">Hilfe ist durch Ausführen von `Get-Help <cmdlet name>` verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="7bb5b-180">Abrufen von Details der DSC-Vorgänge</span><span class="sxs-lookup"><span data-stu-id="7bb5b-180">Getting details of DSC operations</span></span>

<span data-ttu-id="7bb5b-181">Mit der Funktion `Get-xDscOperation` können Sie die Ergebnisse der DSC-Vorgänge suchen, die auf einem oder mehreren Computern ausgeführt werden. Die Funktion gibt außerdem ein Objekt zurück, das die Sammlung der von den einzelnen DSC-Vorgängen erzeugten Ereignisse enthält.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="7bb5b-182">In der folgenden Ausgabe wurden beispielsweise drei Befehle ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="7bb5b-183">Der erste wurde erfolgreich ausgeführt, bei den beiden anderen sind Fehler aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="7bb5b-184">Die Ergebnisse sind in der Ausgabe von `Get-xDscOperation` zusammengefasst.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="7bb5b-185">Durch Verwendung des Parameters `Newest` können Sie angeben, dass nur die Ergebnisse der aktuellsten Vorgänge ausgegeben werden sollen:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="7bb5b-186">Abrufen von Details der DSC-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="7bb5b-186">Getting details of DSC events</span></span>

<span data-ttu-id="7bb5b-187">Das Cmdlet `Trace-xDscOperation` gibt ein Objekt zurück, das eine Sammlung von Ereignissen, deren Ereignistypen und die von einem bestimmten DSC-Vorgang generierte Meldungsausgabe enthält.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="7bb5b-188">Wenn Sie mit `Get-xDscOperation` in einem der Vorgänge einen Fehler finden, würden Sie diesen Vorgang normalerweise verfolgen, um herauszufinden, welches Ereignis den Fehler verursacht hat.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="7bb5b-189">Verwenden Sie den Parameter `SequenceID`, um die Ereignisse eines bestimmten Vorgangs auf einem bestimmten Computer abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="7bb5b-190">Wenn Sie beispielsweise für `SequenceID` „9“ angeben, ruft `Trace-xDscOperaion` die Verfolgung des neuntletzten DSC-Vorgangs ab:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="7bb5b-191">Übergeben Sie die einem bestimmten DSC-Vorgang zugeordnete **GUID** (wie vom Cmdlet `Get-xDscOperation` zurückgegeben), um die Ereignisdetails für diesen DSC-Vorgang abzurufen:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="7bb5b-192">Beachten Sie Folgendes: Da `Trace-xDscOperation` Ereignisse aus den analytischen Protokollen, den Debugprotokollen und den Betriebsprotokollen aggregiert, werden Sie aufgefordert, diese Protokolle wie oben beschrieben zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="7bb5b-193">Informationen zu den Ereignissen können Sie alternativ auch sammeln, indem Sie die Ausgabe von `Trace-xDscOperation` in einer Variablen speichern.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="7bb5b-194">Verwenden Sie die folgenden Befehle, um alle Ereignisse für einen bestimmten DSC-Vorgang anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="7bb5b-195">Dadurch werden gleichen Ergebnisse wie durch das Cmdlet `Get-WinEvent` in der unten stehenden Ausgabe angezeigt:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="7bb5b-196">Im Idealfall würden Sie zuerst `Get-xDscOperation` verwenden, um die letzten DSC-Konfigurationsausführungen auf Ihren Computern aufzulisten.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="7bb5b-197">Im Anschluss können Sie jeden einzelnen Vorgang (anhand der Sequenz-ID oder der Auftrags-ID) mit `Trace-xDscOperation` untersuchen, um zu ermitteln, was im Hintergrund geschehen ist.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="7bb5b-198">Abrufen von Ereignissen für einen Remotecomputer</span><span class="sxs-lookup"><span data-stu-id="7bb5b-198">Getting events for a remote computer</span></span>

<span data-ttu-id="7bb5b-199">Verwenden Sie den Parameter `ComputerName` des Cmdlets `Trace-xDscOperation`, um Details von Ereignissen abzurufen, die auf einem Remotecomputer auftreten.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="7bb5b-200">Zuvor müssen Sie eine Firewallregel erstellen, um die Remoteverwaltung auf dem Remotecomputer zu erlauben:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="7bb5b-201">Nun können Sie diesen Computer angeben, wenn Sie `Trace-xDscOperation` aufrufen:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="7bb5b-202">Meine Ressourcen werden nicht aktualisiert: Zurücksetzen des Caches</span><span class="sxs-lookup"><span data-stu-id="7bb5b-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="7bb5b-203">Die DSC-Engine speichert Ressourcen zwischen, die aus Effizienzgründen als PowerShell-Engine implementiert wurden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="7bb5b-204">Dies kann jedoch Probleme verursachen, wenn Sie eine Ressource erstellen und gleichzeitig testen, da DSC die zwischengespeicherte Version lädt, solange der Vorgang nicht neu gestartet wurde.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="7bb5b-205">Die einzige Möglichkeit, DSC zu veranlassen, die neuere Version zu laden, besteht darin, den Prozess, der die DSC-Engine hostet, explizit zu beenden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="7bb5b-206">Ähnliches gilt, wenn Sie `Start-DscConfiguration` nach dem Hinzufügen und Ändern einer benutzerdefinierten Ressource ausführen. Die Änderung kann dann möglicherweise nicht ausgeführt werden, bis der Computer neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="7bb5b-207">Grund hierfür ist, dass DSC im WMI-Anbieterhostprozess (WmiPrvSE) ausgeführt wird, und in der Regel mehrere Instanzen von WmiPrvSE gleichzeitig ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="7bb5b-208">Beim Neustart wird der Hostprozess neu gestartet und der Cache geleert.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="7bb5b-209">Um die Konfiguration erfolgreich zu recyceln und den Cache zu löschen, ohne einen Neustart auszuführen, müssen Sie den Hostprozess beenden und neu starten.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="7bb5b-210">Dazu können Sie den Prozess auf Instanzebene identifizieren, beenden und neu starten.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="7bb5b-211">Sie können auch `DebugMode` verwenden, wie nachfolgend gezeigt, um die PowerShell DSC-Ressource erneut zu laden.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="7bb5b-212">Um zu identifizieren, welcher Prozess die DSC-Engine hostet, und diesen auf Instanzebene zu beenden, können Sie die Prozess-ID des WmiPrvSE-Prozesses auflisten, der die DSC-Engine hostet.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="7bb5b-213">Beenden Sie den WmiPrvSE-Prozess dann mithilfe der unten aufgeführten Befehle, um den Anbieter zu aktualisieren, und führen Sie anschließend **Start-DscConfiguration** erneut aus.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="7bb5b-214">Verwenden von DebugMode</span><span class="sxs-lookup"><span data-stu-id="7bb5b-214">Using DebugMode</span></span>

<span data-ttu-id="7bb5b-215">Sie können den lokalen Konfigurations-Manager (LCM) von DSC für die Verwendung von `DebugMode` konfigurieren, damit der Cache bei jedem Neustart des Hostprozesses neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="7bb5b-216">Indem Sie den Debugmodus verwenden (auf **TRUE** festlegen), lädt die Engine die PowerShell DSC-Ressource immer neu.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="7bb5b-217">Sobald Sie mit dem Schreiben Ihrer Ressource fertig sind, können Sie den Debugmodus wieder deaktivieren (auf **FALSE** festlegen), um zum alten Verhalten zurückzukehren und die Module wieder zwischenzuspeichern.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="7bb5b-218">In der folgenden Demonstration wird verdeutlicht, wie `DebugMode` den Cache automatisch aktualisieren kann.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="7bb5b-219">Betrachten wir zunächst die Standardkonfiguration:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="7bb5b-220">Sie sehen, dass `DebugMode` auf **None** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="7bb5b-221">Zum Einrichten der `DebugMode`-Demo verwenden Sie die folgenden PowerShell-Ressource:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="7bb5b-222">Nun erstellen Sie eine Konfiguration mit der oben stehenden Ressource namens `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="7bb5b-223">Die Inhalte der Datei zeigen, dass `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` **1** beträgt.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="7bb5b-224">Aktualisieren Sie nun den Anbietercode mithilfe des folgenden Skripts:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-224">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="7bb5b-225">Dieses Skript generiert eine Zufallszahl und aktualisiert den Anbietercode entsprechend.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="7bb5b-226">Ist `DebugMode` auf „false“ festgelegt, wird der Inhalt der Datei „ **$env:SystemDrive\OutputFromTestProviderDebugMode.txt**“ nie geändert.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="7bb5b-227">Legen Sie `DebugMode` in Ihrem Konfigurationsskript jetzt auf **ForceModuleImport** fest:</span><span class="sxs-lookup"><span data-stu-id="7bb5b-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="7bb5b-228">Wenn Sie das oben stehende Skript erneut ausführen, sehen Sie, dass der Inhalt der Datei jedes Mal anders ist.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="7bb5b-229">(Zum Überprüfen können Sie `Get-DscConfiguration` ausführen).</span><span class="sxs-lookup"><span data-stu-id="7bb5b-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="7bb5b-230">Im Folgenden wird das Ergebnis von zwei weiteren Ausführungen angezeigt (Ihre Ergebnisse können sich nach Ausführen des Skripts von diesem Ergebnis unterscheiden):</span><span class="sxs-lookup"><span data-stu-id="7bb5b-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="dsc-returns-unexpected-response-code-internalservererror-when-registering-with-windows-pull-server"></a><span data-ttu-id="7bb5b-231">DSC gibt bei der Registrierung bei Windows-Pullserver „Unerwarteter Antwortcode – InternalServerError“ zurück.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-231">DSC returns "unexpected response code InternalServerError" when registering with Windows Pull Server</span></span>

<span data-ttu-id="7bb5b-232">Wenn eine Metakonfiguration auf einen Server angewendet wird, um ihn bei einer Instanz von Windows-Pullserver zu registrieren, wird möglicherweise der folgende Fehler angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-232">When applying a metaconfiguration to a server to register it with an instance of Windows Pull Server, you might encounter the following error.</span></span>

```PowerShell
Registration of the Dsc Agent with the server https://<serverfqdn>:8080/PSDSCPullServer.svc failed. The underlying error is: The attempt to register Dsc Agent with AgentId <ID> with the server 
https://<serverfqdn>:8080/PSDSCPullServer.svc/Nodes(AgentId='<ID>') returned unexpected response code InternalServerError. .
    + CategoryInfo          : InvalidResult: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : RegisterDscAgentUnsuccessful,Microsoft.PowerShell.DesiredStateConfiguration.Commands.RegisterDscAgentCommand
    + PSComputerName        : <computername>
```

<span data-ttu-id="7bb5b-233">Er kann auftreten, wenn das Zertifikat, das auf dem Server zum Verschlüsseln von Datenverkehr verwendet wird, einen allgemeinen Namen (Common Name, CN) hat, der anders als der DNS-Name ist, der vom Knoten zum Auflösen der URL verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-233">This can occur when the certificate used on the server to encrypt traffic has a common name (CN) that is different than the DNS name used by the node to resolve the URL.</span></span>
<span data-ttu-id="7bb5b-234">Aktualisieren Sie die Windows-Pullserver-Instanz, sodass ein Zertifikat mit einem korrigierten Namen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7bb5b-234">Update the Windows Pull Server instance to use a certificate with a corrected name.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bb5b-235">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7bb5b-235">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="7bb5b-236">Konzepte</span><span class="sxs-lookup"><span data-stu-id="7bb5b-236">Concepts</span></span>

- [<span data-ttu-id="7bb5b-237">Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="7bb5b-237">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="7bb5b-238">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="7bb5b-238">Other Resources</span></span>

- [<span data-ttu-id="7bb5b-239">Windows PowerShell DSC-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="7bb5b-239">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)
