---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Überwachung und Berichterstellung zu JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "70017791"
---
# <a name="auditing-and-reporting-on-jea"></a><span data-ttu-id="2ad23-103">Überwachung und Berichterstellung zu JEA</span><span class="sxs-lookup"><span data-stu-id="2ad23-103">Auditing and Reporting on JEA</span></span>

<span data-ttu-id="2ad23-104">Nachdem Sie JEA bereitgestellt haben, muss die JEA-Konfiguration regelmäßig überwacht werden.</span><span class="sxs-lookup"><span data-stu-id="2ad23-104">After you've deployed JEA, you need to regularly audit the JEA configuration.</span></span> <span data-ttu-id="2ad23-105">Dadurch können Sie leichter beurteilen, ob die Benutzer, die auf den JEA-Endpunkt zugreifen, dazu berechtigt sind und ob die ihnen zugewiesenen Rollen noch geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="2ad23-105">Auditing helps you assess that the correct people have access to the JEA endpoint and their assigned roles are still appropriate.</span></span>

## <a name="find-registered-jea-sessions-on-a-machine"></a><span data-ttu-id="2ad23-106">Ermitteln von registrierten JEA-Sitzungen auf einem Computer</span><span class="sxs-lookup"><span data-stu-id="2ad23-106">Find registered JEA sessions on a machine</span></span>

<span data-ttu-id="2ad23-107">Verwenden Sie das [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet, um zu überprüfen, welche JEA-Sitzungen auf einem Computer registriert sind.</span><span class="sxs-lookup"><span data-stu-id="2ad23-107">To check which JEA sessions are registered on a machine, use the [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.</span></span>

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

<span data-ttu-id="2ad23-108">Die jeweils gültigen Rechte für den Endpunkt werden in der Eigenschaft **Berechtigung** aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="2ad23-108">The effective rights for the endpoint are listed in the **Permission** property.</span></span> <span data-ttu-id="2ad23-109">Diese Benutzer sind berechtigt, mit dem JEA-Endpunkt eine Verbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="2ad23-109">These users have the right to connect to the JEA endpoint.</span></span> <span data-ttu-id="2ad23-110">Auf welche Rollen und Befehle sie jedoch Zugriff haben, richtet sich nach der Eigenschaft **RoleDefinitions** in der [Sitzungskonfigurationsdatei](session-configurations.md), die beim Registrieren des Endpunkts verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="2ad23-110">However, the roles and commands they have access to is determined by the **RoleDefinitions** property in the [session configuration file](session-configurations.md) that was used to register the endpoint.</span></span> <span data-ttu-id="2ad23-111">Erweitern Sie die Eigenschaft **RoleDefinitions**, um die Rollenzuordnungen in einem registrierten JEA-Endpunkt zu bewerten.</span><span class="sxs-lookup"><span data-stu-id="2ad23-111">Expand the **RoleDefinitions** property to evaluate the role mappings in a registered JEA endpoint.</span></span>

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a><span data-ttu-id="2ad23-112">Ermitteln verfügbarer Rollenfunktionen auf dem Computer</span><span class="sxs-lookup"><span data-stu-id="2ad23-112">Find available role capabilities on the machine</span></span>

<span data-ttu-id="2ad23-113">JEA ruft die im Ordner `.psrc`RoleCapabilities**gespeicherten**-Dateien innerhalb eines PowerShell-Moduls ab.</span><span class="sxs-lookup"><span data-stu-id="2ad23-113">JEA gets role capabilities from the `.psrc` files stored in the **RoleCapabilities** folder inside a PowerShell module.</span></span> <span data-ttu-id="2ad23-114">Mit der folgenden Funktion können Sie alle auf einem Computer verfügbaren Rollenfunktionen ermitteln:</span><span class="sxs-lookup"><span data-stu-id="2ad23-114">The following function finds all role capabilities available on a computer.</span></span>

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> <span data-ttu-id="2ad23-115">Die Reihenfolge der Ergebnisse dieser Funktion entspricht nicht zwangsläufig der Reihenfolge, in der die Rollenfunktionen ausgewählt werden, wenn mehrere Rollenfunktionen den gleichen Namen haben.</span><span class="sxs-lookup"><span data-stu-id="2ad23-115">The order of results from this function is not necessarily the order in which the role capabilities will be selected if multiple role capabilities share the same name.</span></span>

## <a name="check-effective-rights-for-a-specific-user"></a><span data-ttu-id="2ad23-116">Überprüfen gültiger Berechtigungen für einen bestimmten Benutzer</span><span class="sxs-lookup"><span data-stu-id="2ad23-116">Check effective rights for a specific user</span></span>

<span data-ttu-id="2ad23-117">Mit dem Cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) werden alle für den JEA-Endpunkt verfügbaren Befehle basierend auf den Mitgliedschaften einer Benutzergruppe aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="2ad23-117">The [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet enumerates all the commands available on a JEA endpoint based on a user's group memberships.</span></span>
<span data-ttu-id="2ad23-118">Die Ausgabe von `Get-PSSessionCapability` ist identisch mit dem angegebenen Benutzerkonto, das `Get-Command -CommandType All` in einer JEA-Sitzung ausführt.</span><span class="sxs-lookup"><span data-stu-id="2ad23-118">The output of `Get-PSSessionCapability` is identical to that of the specified user running `Get-Command -CommandType All` in a JEA session.</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

<span data-ttu-id="2ad23-119">Wenn Ihre Benutzer keine ständigen Mitglieder von Gruppen sind, die ihnen zusätzliche JEA-Rechte erteilen, entspricht dieses Cmdlet möglicherweise nicht den zusätzlichen Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="2ad23-119">If your users aren't permanent members of groups that would grant them additional JEA rights, this cmdlet may not reflect those extra permissions.</span></span> <span data-ttu-id="2ad23-120">Dies ist der Fall, wenn Just-in-Time-Systeme für Privileged Access Management verwendet werden, um Benutzern vorübergehend die Aufnahme in eine Sicherheitsgruppe zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2ad23-120">This happens when using just-in-time privileged access management systems to allow users to temporarily belong to a security group.</span></span> <span data-ttu-id="2ad23-121">Gehen Sie bei der Bewertung der Zuordnung von Benutzern zu Rollen und Funktionen sorgfältig vor, um den einzelnen Benutzern nur die für eine erfolgreiche Verrichtung ihrer Arbeit erforderliche Zugriffsebene zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="2ad23-121">Carefully evaluate the mapping of users to roles and capabilities to ensure that users only get the level of access needed to do their jobs successfully.</span></span>

## <a name="powershell-event-logs"></a><span data-ttu-id="2ad23-122">PowerShell-Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="2ad23-122">PowerShell event logs</span></span>

<span data-ttu-id="2ad23-123">Wenn Sie die Protokollierung von Modul- oder Skriptblöcken für das System aktivieren, enthalten die Windows-Ereignisprotokolle Ereignisse für jeden Befehl, den ein Benutzer in einer JEA-Sitzung ausführt.</span><span class="sxs-lookup"><span data-stu-id="2ad23-123">If you enabled module or script block logging on the system, you can see events in the Windows event logs for each command a user runs in a JEA session.</span></span> <span data-ttu-id="2ad23-124">Öffnen Sie für die Suche nach diesen Ereignissen das Ereignisprotokoll **Microsoft-Windows-PowerShell/Operational**, und suchen Sie nach Ereignissen mit der Ereignis-ID **4104**.</span><span class="sxs-lookup"><span data-stu-id="2ad23-124">To find these events, open **Microsoft-Windows-PowerShell/Operational** event log and look for events with event ID **4104**.</span></span>

<span data-ttu-id="2ad23-125">Jeder Eintrag im Ereignisprotokoll enthält Informationen über die Sitzung, in der der Befehl ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="2ad23-125">Each event log entry includes information about the session in which the command was run.</span></span> <span data-ttu-id="2ad23-126">Bei JEA-Sitzungen enthält das Ereignis Informationen zu **ConnectedUser** und **RunAsUser**.</span><span class="sxs-lookup"><span data-stu-id="2ad23-126">For JEA sessions, the event includes information about the **ConnectedUser** and the **RunAsUser**.</span></span> <span data-ttu-id="2ad23-127">**ConnectedUser** ist der Benutzer, der die JEA-Sitzung tatsächlich erstellt hat.</span><span class="sxs-lookup"><span data-stu-id="2ad23-127">The **ConnectedUser** is the actual user who created the JEA session.</span></span> <span data-ttu-id="2ad23-128">**RunAsUser** ist das Konto, mit dem JEA den Befehl ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="2ad23-128">The **RunAsUser** is the account JEA used to execute the command.</span></span>

<span data-ttu-id="2ad23-129">Die Anwendungsereignisprotokolle enthalten Änderungen, die von **RunAsUser** vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="2ad23-129">Application event logs show changes being made by the **RunAsUser**.</span></span> <span data-ttu-id="2ad23-130">Die Modul- und Skriptprotokollierung muss also aktiviert sein, um einen bestimmten Befehlsaufruf zu **ConnectedUser** zurückzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="2ad23-130">So having module and script logging enabled is required to trace a specific command invocation back to the **ConnectedUser**.</span></span>

## <a name="application-event-logs"></a><span data-ttu-id="2ad23-131">Anwendungsereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="2ad23-131">Application event logs</span></span>

<span data-ttu-id="2ad23-132">In einer JEA-Sitzung ausgeführte Befehle, die mit externen Anwendungen oder Diensten interagieren, protokollieren möglicherweise Ereignisse in ihren eigenen Ereignisprotokollen.</span><span class="sxs-lookup"><span data-stu-id="2ad23-132">Commands run in a JEA session that interact with external applications or services may log events to their own event logs.</span></span> <span data-ttu-id="2ad23-133">Im Gegensatz zu PowerShell-Protokollen und -Aufzeichnungen erfassen andere Protokollierungsmechanismen nicht den verbundenen Benutzer der JEA-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="2ad23-133">Unlike PowerShell logs and transcripts, other logging mechanisms don't capture the connected user of the JEA session.</span></span> <span data-ttu-id="2ad23-134">Stattdessen protokollieren diese Anwendungen nur den virtuellen ausführenden Benutzer.</span><span class="sxs-lookup"><span data-stu-id="2ad23-134">Instead, those applications only log the virtual run-as user.</span></span>
<span data-ttu-id="2ad23-135">Überprüfen Sie zur Bestimmung, wer den Befehl ausgeführt hat, eine [Sitzungsaufzeichnung](#session-transcripts), oder korrelieren Sie PowerShell-Ereignisprotokolle mit dem Zeitpunkt und Benutzer, die im Anwendungsereignisprotokoll angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2ad23-135">To determine who ran the command, you need to consult a [session transcript](#session-transcripts) or correlate PowerShell event logs with the time and user shown in the application event log.</span></span>

<span data-ttu-id="2ad23-136">Mit dem WinRM-Protokoll können Sie in einem Anwendungsereignisprotokoll ebenfalls ausführende Benutzer mit dem Benutzer korrelieren, der eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="2ad23-136">The WinRM log can also help you correlate run-as users to the connecting user in an application event log.</span></span> <span data-ttu-id="2ad23-137">Mit der Ereignis-ID **193** im Protokoll **Microsoft-Windows-Windows Remote Management/Operational** werden bei jeder neuen JEA-Sitzung die Sicherheits-ID (SID) und der Kontoname sowohl des Benutzers, der eine Verbindung herstellt, als auch des ausführenden Benutzers erfasst.</span><span class="sxs-lookup"><span data-stu-id="2ad23-137">Event ID **193** in the **Microsoft-Windows-Windows Remote Management/Operational** log records the security identifier (SID) and account name for both the connecting user and run as user for every new JEA session.</span></span>

## <a name="session-transcripts"></a><span data-ttu-id="2ad23-138">Sitzungsaufzeichnungen</span><span class="sxs-lookup"><span data-stu-id="2ad23-138">Session transcripts</span></span>

<span data-ttu-id="2ad23-139">Wenn Sie JEA für die Erstellung einer Aufzeichnung bei jeder Benutzersitzung konfiguriert haben, wird eine Textkopie für die Aktionen aller Benutzer im angegebenen Ordner gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2ad23-139">If you configured JEA to create a transcript for each user session, a text copy of every user's actions are stored in the specified folder.</span></span>

<span data-ttu-id="2ad23-140">Mit dem folgenden Befehl können Sie (als Administrator) nach allen Aufzeichnungsverzeichnissen suchen.</span><span class="sxs-lookup"><span data-stu-id="2ad23-140">The following command (as an administrator) finds all transcript directories.</span></span>

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

<span data-ttu-id="2ad23-141">Jede Aufzeichnung beginnt mit Informationen über den Zeitpunkt, zu dem die Sitzung gestartet wurde, welche Benutzer eine Verbindung mit der Sitzung hergestellt haben und welche JEA-Identität ihnen zugewiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="2ad23-141">Each transcript starts with information about the time the session started, which user connected to the session, and which JEA identity was assigned to them.</span></span>

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

<span data-ttu-id="2ad23-142">Der Hauptteil der Aufzeichnung enthält Informationen zu jedem vom Benutzer aufgerufenen Befehl.</span><span class="sxs-lookup"><span data-stu-id="2ad23-142">The body of the transcript contains information about each command the user invoked.</span></span> <span data-ttu-id="2ad23-143">Die genaue Syntax des verwendeten Befehls ist für JEA-Sitzungen aufgrund der Transformationsart von Befehlen für PowerShell-Remoting nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2ad23-143">The exact syntax of the command used is unavailable in JEA sessions because of the way commands are transformed for PowerShell remoting.</span></span> <span data-ttu-id="2ad23-144">Der tatsächlich ausgeführte Befehl kann jedoch weiterhin ermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="2ad23-144">However, you can still determine the effective command that was executed.</span></span> <span data-ttu-id="2ad23-145">Im Folgenden finden Sie ein Beispiel für einen Aufzeichnungsausschnitt eines Benutzers, der in einer JEA-Sitzung `Get-Service Dns` ausgeführt hat:</span><span class="sxs-lookup"><span data-stu-id="2ad23-145">Below is an example transcript snippet from a user running `Get-Service Dns` in a JEA session:</span></span>

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

<span data-ttu-id="2ad23-146">Für jeden von einem Benutzer ausgeführten Befehl wird eine **CommandInvocation**-Zeile geschrieben.</span><span class="sxs-lookup"><span data-stu-id="2ad23-146">A **CommandInvocation** line is written for each command a user runs.</span></span> <span data-ttu-id="2ad23-147">Mit **ParameterBindings** werden alle Parameter und Werte erfasst, die für den Befehl angegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="2ad23-147">**ParameterBindings** record each parameter and value supplied with the command.</span></span> <span data-ttu-id="2ad23-148">Im vorherigen Beispiel wird für das Cmdlet **der Parameter**Name**mit dem Wert**Dns`Get-Service` angegeben.</span><span class="sxs-lookup"><span data-stu-id="2ad23-148">In the previous example, you can see that the parameter **Name** was supplied the with value **Dns** for the `Get-Service` cmdlet.</span></span>

<span data-ttu-id="2ad23-149">Die Ausgabe jedes Befehls löst außerdem **CommandInvocation** aus, in der Regel zu `Out-Default`.</span><span class="sxs-lookup"><span data-stu-id="2ad23-149">The output of each command also triggers a **CommandInvocation**, usually to `Out-Default`.</span></span> <span data-ttu-id="2ad23-150">**InputObject** von `Out-Default` stellt das vom Befehl zurückgegebene PowerShell-Objekt dar.</span><span class="sxs-lookup"><span data-stu-id="2ad23-150">The **InputObject** of `Out-Default` is the PowerShell object returned from the command.</span></span> <span data-ttu-id="2ad23-151">Die Details des Objekts einige Zeilen darunter bilden täuschend ähnlich das nach, was der Benutzer gesehen hätte.</span><span class="sxs-lookup"><span data-stu-id="2ad23-151">The details of that object are printed a few lines below, closely mimicking what the user would have seen.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ad23-152">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2ad23-152">See also</span></span>

[<span data-ttu-id="2ad23-153">*PowerShell ♥ the Blue Team (PowerShell ♥ das Blue Team)* – Blogbeitrag zum Thema Sicherheit</span><span class="sxs-lookup"><span data-stu-id="2ad23-153">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
