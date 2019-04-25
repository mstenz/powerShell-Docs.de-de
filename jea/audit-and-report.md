---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Überwachung und Berichterstellung zu JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084078"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="bfb7f-103">Überwachung und Berichterstellung zu JEA</span><span class="sxs-lookup"><span data-stu-id="bfb7f-103">Auditing and Reporting on JEA</span></span>

> <span data-ttu-id="bfb7f-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="bfb7f-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="bfb7f-105">Nachdem Sie JEA bereitgestellt haben, sollten Sie die JEA-Konfiguration regelmäßig überwachen.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-105">After you've deployed JEA, you will want to regularly audit the JEA configuration.</span></span>
<span data-ttu-id="bfb7f-106">Auf diese Weise können Sie leichter beurteilen, ob die Benutzer, die auf den JEA-Endpunkt zugreifen, dazu autorisiert sind und ob die ihnen zugewiesenen Rollen noch geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-106">This will help you assess if the correct people have access to the JEA endpoint and if their assigned roles are still appropriate.</span></span>

<span data-ttu-id="bfb7f-107">Dieses Thema beschreibt die verschiedenen Methoden zur Überwachung eines JEA-Endpunkts.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-107">This topic describes the various ways you can audit a JEA endpoint.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="bfb7f-108">Ermitteln von registrierten JEA-Sitzungen auf einem Computer</span><span class="sxs-lookup"><span data-stu-id="bfb7f-108">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="bfb7f-109">Verwenden Sie das [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet, um zu überprüfen, welche JEA-Sitzungen auf einem Computer registriert sind.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-109">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="bfb7f-110">Die jeweils gültigen Rechte für den Endpunkt werden in der Eigenschaft „Berechtigung“ aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-110">The effective rights for the endpoint are listed in the "Permission" property.</span></span>
<span data-ttu-id="bfb7f-111">Diese Benutzer sind berechtigt, eine Verbindung mit dem JEA-Endpunkt herzustellen. Auf welche Rollen (und im weiteren Sinne Befehle) sie jedoch Zugriff haben, richtet sich nach dem Feld „RoleDefinitions“ in der [Sitzungskonfigurationsdatei](session-configurations.md), die beim Registrieren des Endpunkts verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-111">These users have the right to connect to the JEA endpoint, but which roles (and, by extension, commands) they have access to is determined by the "RoleDefinitions" field in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span>

<span data-ttu-id="bfb7f-112">Sie können die Rollenzuordnungen in einem registrierten JEA-Endpunkt bewerten, indem Sie die Daten in der Eigenschaft „RoleDefinitions“ erweitern.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-112">You can evaluate the role mappings in a registered JEA endpoint by expanding the data in the "RoleDefinitions" property.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="bfb7f-113">Ermitteln verfügbarer Rollenfunktionen auf dem Computer</span><span class="sxs-lookup"><span data-stu-id="bfb7f-113">Find available role capabilities on the machine</span></span>

<span data-ttu-id="bfb7f-114">Rollenfunktionsdateien werden nur dann von JEA verwendet, wenn sie in einem Ordner „RoleCapabilities“ in einem gültigen PowerShell-Modul gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-114">Role capability files will only be used by JEA if they are stored in a "RoleCapabilities" folder inside a valid PowerShell module.</span></span>
<span data-ttu-id="bfb7f-115">Sie erhalten alle verfügbaren Rollenfunktionen, indem Sie die Liste verfügbarer Module durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-115">You can find all role capabilities available on a computer by searching the list of available modules.</span></span>

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="bfb7f-116">Die Reihenfolge der Ergebnisse dieser Funktion entspricht nicht zwangsläufig der Reihenfolge, in der die Rollenfunktionen ausgewählt werden, wenn mehrere Rollenfunktionen den gleichen Namen haben.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-116">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="bfb7f-117">Überprüfen gültiger Berechtigungen für einen bestimmten Benutzer</span><span class="sxs-lookup"><span data-stu-id="bfb7f-117">Check effective rights for a specific user</span></span>

<span data-ttu-id="bfb7f-118">Nachdem Sie einen JEA-Endpunkt eingerichtet haben, sollten Sie überprüfen, welche Befehle in einer JEA-Sitzung für einen bestimmten Benutzer verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-118">Once you have set up a JEA endpoint, you may want to check which commands are available to a specific user in a JEA session.</span></span>
<span data-ttu-id="bfb7f-119">Sie können [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) zum Auflisten aller Befehle verwenden, die für Benutzer gelten, die eine JEA-Sitzung mit ihren aktuellen Gruppenmitgliedschaften starten.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-119">You can use [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) to enumerate all of the commands applicable to a user if they were to start a JEA session with their current group memberships.</span></span>
<span data-ttu-id="bfb7f-120">Die Ausgabe von `Get-PSSessionCapability` ist identisch mit dem angegebenen Benutzerkonto, das `Get-Command -CommandType All` in einer JEA-Sitzung ausführt.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-120">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="bfb7f-121">Wenn Ihre Benutzer keine ständigen Mitglieder von Gruppen sind, die ihnen zusätzliche JEA-Rechte erteilen, spiegelt dieses Cmdlet möglicherweise nicht die zusätzlichen Berechtigungen wider.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-121">If your users are not permanent members of groups which would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span>
<span data-ttu-id="bfb7f-122">Dies ist i.d.R. der Fall, wenn Just-in-Time-Privileged Access Management-Systeme verwendet werden, um Benutzern vorübergehend die Aufnahme in eine Sicherheitsgruppe zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-122">This is typically the case when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span>
<span data-ttu-id="bfb7f-123">Überprüfen Sie daher stets sorgfältig die Zuordnung von Benutzern zu Rollen und den Inhalt der einzelnen Rollen, um sicherzustellen, dass Benutzer nur Zugriff auf jene Befehle habe, die sie zur Erfüllung ihrer Aufgaben unbedingt benötigen.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-123">Always carefully evaluate the mapping of users to roles and the contents of each role to ensure users are only getting access to the least amount of commands needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="bfb7f-124">PowerShell-Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="bfb7f-124">PowerShell event logs</span></span>

<span data-ttu-id="bfb7f-125">Wenn Sie die Modul- und/oder Skriptblockprotokollierung im System aktivieren, enthalten die Windows-Ereignisprotokolle Ereignisse für jeden Befehl, den Benutzer in ihren JEA-Sitzungen ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-125">If you enabled module and/or script block logging on the system, you will be able to find events in the Windows event logs for each command a user ran in their JEA sessions.</span></span>
<span data-ttu-id="bfb7f-126">Um diese Ereignisse zu finden, öffnen Sie die Windows-Ereignisanzeige, navigieren Sie zum Ereignisprotokoll **Microsoft-Windows-PowerShell/Operational** Ereignisprotokoll, und suchen Sie nach Ereignissen mit der Ereignis-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-126">To find these events, open the Windows Event Viewer, navigate to the **Microsoft-Windows-PowerShell/Operational** event log, and look for events with event ID **4104**.</span></span>

<span data-ttu-id="bfb7f-127">Jeder Eintrag im Ereignisprotokoll enthält Informationen über die Sitzung, in der der Befehl ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-127">Each event log entry will include information about the session in which the command was run.</span></span>
<span data-ttu-id="bfb7f-128">Bei JEA-Sitzungen handelt es sich dabei um wichtige Informationen zum **ConnectedUser**, also dem tatsächlichen Benutzer, der die JEA-Sitzung erstellt hat, als auch zum Parameter **RunAsUser**, der das JEA-Konto angibt, das zum Ausführen des Befehls verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-128">For JEA sessions, this includes important information about the **ConnectedUser**, which is the actual user who created the JEA session, as well as the **RunAsUser** which identifies the account JEA used to execute the command.</span></span>
<span data-ttu-id="bfb7f-129">Anwendungsereignisprotokolle zeigen Änderungen durch RunAsUser. Die Aufzeichnungs- bzw Modul-/Skriptprotokollierung sollte daher unbedingt aktiviert sein, um einen bestimmten Befehlsaufruf zu einem Benutzer zurückverfolgen zu können.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-129">Application event logs will show changes being made by the RunAsUser, so having transcripts or module/script logging enabled is crucial to be able to trace a specific command invocation back to a user.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="bfb7f-130">Anwendungsereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="bfb7f-130">Application event logs</span></span>

<span data-ttu-id="bfb7f-131">Wenn Sie einen Befehl in einer JEA-Sitzung ausführen, die mit einer externen Anwendung oder einem externen Dienst interagiert, können diese Anwendungen Ereignisse in ihren eigenen Ereignisprotokollen protokollieren.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-131">When you run a command in a JEA session that interacts with an external application or service, those applications may log events to their own event logs.</span></span>
<span data-ttu-id="bfb7f-132">Im Gegensatz zu PowerShell-Protokollen und Aufzeichnungen erfassen andere Protokollierungsmechanismen nicht den Benutzer, der eine Verbindung zur JEA-Sitzung aufbaut. Stattdessen wird nur das Konto des virtuellen, ausführenden Benutzers bzw. des gruppenverwalteten Dienstkontos protokolliert.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-132">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the connected user of the JEA session, and will instead only log the virtual run-as user or group managed service account.</span></span>
<span data-ttu-id="bfb7f-133">Um zu bestimmen, wer den Befehl ausgeführt hat, überprüfen Sie eine [Sitzungsaufzeichnung](#session-transcripts), oder korrelieren Sie PowerShell-Ereignisprotokolle mit dem Zeitpunkt und den Benutzern, die im Anwendungsereignisprotokoll angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-133">In order to determine who ran the command, you will need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="bfb7f-134">Das WinRM-Protokoll kann ebenfalls hilfreich sein, wenn Sie ausführende Benutzer in einem Anwendungsereignisprotokoll mit dem Benutzer korrelieren möchten, der eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-134">The WinRM log can also help you correlate run as users in an application event log with the connecting user.</span></span>
<span data-ttu-id="bfb7f-135">Die Ereignis-ID **193** im Protokoll **Microsoft-Windows-Windows Remote Management/Operational** erfasst bei jeder Erstellung einer JEA-Sitzung die Sicherheits-ID (SID) und den Kontonamen sowohl des Benutzers, der eine Verbindung herstellt, als auch des ausführenden Benutzers.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-135">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user every time a JEA session is created.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="bfb7f-136">Sitzungsaufzeichnungen</span><span class="sxs-lookup"><span data-stu-id="bfb7f-136">Session transcripts</span></span>

<span data-ttu-id="bfb7f-137">Wenn Sie JEA für die Erstellung einer Aufzeichnung bei jeder Benutzersitzung konfiguriert haben, wird eine Textkopie für die Aktionen aller Benutzer im angegebenen Ordner gespeichert.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-137">If you configured JEA to create a transcript for each user session, a text copy of every user's actions will be stored in the specified folder.</span></span>

<span data-ttu-id="bfb7f-138">Sie finden sämtliche Aufzeichnungsverzeichnisse, indem Sie den folgenden Befehl als Administrator auf dem mit JEA konfigurierten Computer ausführen:</span><span class="sxs-lookup"><span data-stu-id="bfb7f-138">To find all transcript directories, run the following command as an administrator on the computer configured with JEA:</span></span>

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="bfb7f-139">Jede Aufzeichnung beginnt mit Informationen über den Zeitpunkt, zu dem die Sitzung gestartet wurde, welche Benutzer eine Verbindung mit der Sitzung hergestellt haben und welche JEA-Identität ihnen zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-139">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="bfb7f-140">Der Hauptteil der Aufzeichnung enthält Informationen zu jedem Befehl, den der Benutzer aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-140">In the body of the transcript, information is logged about each command the user invoked.</span></span>
<span data-ttu-id="bfb7f-141">Die genaue Syntax des durch den Benutzer ausgeführten Befehls ist in JEA-Sitzungen nicht verfügbar. Dies ist auf die Art und Weise zurückzuführen, in der Befehle für PowerShell-Remoting verarbeitet werden. Der tatsächlich ausgeführt Befehl kann jedoch weiterhin ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-141">The exact syntax of the command the user ran is unavailable in JEA sessions due to the way commands are transformed for PowerShell remoting, however you can still determine the effective command that was executed.</span></span>
<span data-ttu-id="bfb7f-142">Im Folgenden finden Sie ein Beispiel für einen Aufzeichnungsausschnitt eines Benutzers, der in einer JEA-Sitzung `Get-Service Dns` ausgeführt hat:</span><span class="sxs-lookup"><span data-stu-id="bfb7f-142">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="bfb7f-143">Für jeden Befehl, den der Benutzer ausführt, wird eine Zeile „CommandInvocation“ geschrieben. Sie beschreibt das Cmdlet bzw. die Funktion, das bzw. die der Benutzer aufgerufen hat.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-143">For each command a user runs, a "CommandInvocation" line will be written, describing the cmdlet or function the user invoked.</span></span>
<span data-ttu-id="bfb7f-144">Auf jede Zeile „CommandInvocation“ folgt „ParameterBindings“ mit Information über jeden Parameter und Wert, der für den Befehl angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-144">ParameterBindings follow each CommandInvocation to tell you about each parameter and value that was supplied with the command.</span></span>
<span data-ttu-id="bfb7f-145">Im voranstehenden Beispiel sehen Sie, dass für den Parameter „Name“ der Wert „Dns“ für das Cmdlet „Get-Service“ angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-145">In the above example, you can see that the parameter "Name" was supplied the value "Dns" for the "Get-Service" cmdlet.</span></span>

<span data-ttu-id="bfb7f-146">Die Ausgabe jedes Befehls löst außerdem eine „CommandInvocation“ aus, in der Regel nach „Out-Default“.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-146">The output of each command will also trigger a CommandInvocation, usually to Out-Default.</span></span>
<span data-ttu-id="bfb7f-147">Das vom Befehl zurückgegebene PowerShell-Objekt fungiert als InputObject für„InputObject“ von „Out-Default“.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-147">The InputObject of Out-Default is the PowerShell object returned from the command.</span></span>
<span data-ttu-id="bfb7f-148">Die Details des Objekts einige Zeilen darunter bilden täuschend ähnlich das nach, was der Benutzer gesehen hätte.</span><span class="sxs-lookup"><span data-stu-id="bfb7f-148">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfb7f-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bfb7f-149">See also</span></span>

- [<span data-ttu-id="bfb7f-150">*PowerShell ♥ the Blue Team (PowerShell ♥ das Blue Team)* – Blogbeitrag zum Thema Sicherheit</span><span class="sxs-lookup"><span data-stu-id="bfb7f-150">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
