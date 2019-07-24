---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA-Sitzungskonfigurationen
ms.openlocfilehash: 650d0d11ef13605847d0822249e29e3491180629
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726548"
---
# <a name="jea-session-configurations"></a><span data-ttu-id="b7964-103">JEA-Sitzungskonfigurationen</span><span class="sxs-lookup"><span data-stu-id="b7964-103">JEA Session Configurations</span></span>

<span data-ttu-id="b7964-104">Ein JEA-Endpunkt wird in einem System durch Erstellen und Registrieren einer PowerShell-Sitzungskonfigurationsdatei registriert.</span><span class="sxs-lookup"><span data-stu-id="b7964-104">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file.</span></span> <span data-ttu-id="b7964-105">Sitzungskonfigurationen definieren, welche Benutzer den JEA-Endpunkt verwenden können und auf welche Rollen sie Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="b7964-105">Session configurations define who can use the JEA endpoint and which roles they have access to.</span></span> <span data-ttu-id="b7964-106">Sie legen außerdem globale Einstellungen fest, die für alle Benutzer der JEA-Sitzung gelten.</span><span class="sxs-lookup"><span data-stu-id="b7964-106">They also define global settings that apply to all users of the JEA session.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="b7964-107">Erstellen einer Sitzungskonfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="b7964-107">Create a session configuration file</span></span>

<span data-ttu-id="b7964-108">Sie müssen zunächst angeben, wie der JEA-Endpunkt konfiguriert ist, bevor Sie ihn registrieren können.</span><span class="sxs-lookup"><span data-stu-id="b7964-108">To register a JEA endpoint, you must specify how that endpoint is configured.</span></span> <span data-ttu-id="b7964-109">Dafür gibt es zahlreiche Optionen.</span><span class="sxs-lookup"><span data-stu-id="b7964-109">There are many options to consider.</span></span> <span data-ttu-id="b7964-110">Folgende Fragen sind dabei entscheidend:</span><span class="sxs-lookup"><span data-stu-id="b7964-110">The most important options are:</span></span>

- <span data-ttu-id="b7964-111">Wer soll auf den JEA-Endpunkt zugreifen können?</span><span class="sxs-lookup"><span data-stu-id="b7964-111">Who has access to the JEA endpoint</span></span>
- <span data-ttu-id="b7964-112">Welche Rollen sollen den Benutzern zugewiesen werden?</span><span class="sxs-lookup"><span data-stu-id="b7964-112">Which roles they be assigned</span></span>
- <span data-ttu-id="b7964-113">Welche Identität wird von JEA im Hintergrund verwendet?</span><span class="sxs-lookup"><span data-stu-id="b7964-113">Which identity JEA uses under the covers</span></span>
- <span data-ttu-id="b7964-114">Welchen Namen soll der JEA-Endpunkt erhalten?</span><span class="sxs-lookup"><span data-stu-id="b7964-114">The name of the JEA endpoint</span></span>

<span data-ttu-id="b7964-115">Diese Optionen werden in einer PowerShell-Datendatei mit der Erweiterung `.pssc`, auch PowerShell-Sitzungskonfigurationsdatei genannt, definiert.</span><span class="sxs-lookup"><span data-stu-id="b7964-115">These options are defined in a PowerShell data file with a `.pssc` extension known as a PowerShell session configuration file.</span></span> <span data-ttu-id="b7964-116">Sie können die Sitzungskonfigurationsdatei mit einem beliebigen Text-Editor bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="b7964-116">The session configuration file can be edited using any text editor.</span></span>

<span data-ttu-id="b7964-117">Führen Sie den folgenden Befehl aus, um eine leere Vorlagenkonfigurationsdatei zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="b7964-117">Run the following command to create a blank template configuration file.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="b7964-118">Standardmäßig enthält die Vorlagendatei nur die häufigsten Konfigurationsoptionen.</span><span class="sxs-lookup"><span data-stu-id="b7964-118">Only the most common configuration options are included in the template file by default.</span></span> <span data-ttu-id="b7964-119">Verwenden Sie den `-Full`-Switch, um alle anwendbaren Einstellungen in die generierte PSSC-Datei einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="b7964-119">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="b7964-120">Das Feld `-SessionType RestrictedRemoteServer` gibt an, dass die Sitzungskonfiguration von JEA für eine sichere Verwaltung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b7964-120">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration is used by JEA for secure management.</span></span> <span data-ttu-id="b7964-121">Sitzungen dieses Typs arbeiten im Modus **NoLanguage** und können nur auf die folgenden Standardbefehle (und Aliase) zugreifen:</span><span class="sxs-lookup"><span data-stu-id="b7964-121">Sessions of this type operate in **NoLanguage** mode and only have access to the following default commands (and aliases):</span></span>

- <span data-ttu-id="b7964-122">Clear-Host (cls, löschen)</span><span class="sxs-lookup"><span data-stu-id="b7964-122">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="b7964-123">Exit-PSSession (exsn, beenden)</span><span class="sxs-lookup"><span data-stu-id="b7964-123">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="b7964-124">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="b7964-124">Get-Command (gcm)</span></span>
- <span data-ttu-id="b7964-125">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="b7964-125">Get-FormatData</span></span>
- <span data-ttu-id="b7964-126">"Get-Help "</span><span class="sxs-lookup"><span data-stu-id="b7964-126">Get-Help</span></span>
- <span data-ttu-id="b7964-127">Measure-Object (messen)</span><span class="sxs-lookup"><span data-stu-id="b7964-127">Measure-Object (measure)</span></span>
- <span data-ttu-id="b7964-128">Out-Default</span><span class="sxs-lookup"><span data-stu-id="b7964-128">Out-Default</span></span>
- <span data-ttu-id="b7964-129">Select-Object (auswählen)</span><span class="sxs-lookup"><span data-stu-id="b7964-129">Select-Object (select)</span></span>

<span data-ttu-id="b7964-130">Weder PowerShell-Anbieter noch externe Programme (ausführbare Dateien oder Skripts) stehen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="b7964-130">No PowerShell providers are available, nor are any external programs (executables or scripts).</span></span>

<span data-ttu-id="b7964-131">Weitere Informationen zu Sprachmodi finden Sie unter [About_Language_Modes (Informationen zu Sprachmodi)](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span><span class="sxs-lookup"><span data-stu-id="b7964-131">For more information about language modes, see [about_Language_modes](/powershell/module/microsoft.powershell.core/about/about_language_modes).</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="b7964-132">Wählen der JEA-Identität</span><span class="sxs-lookup"><span data-stu-id="b7964-132">Choose the JEA identity</span></span>

<span data-ttu-id="b7964-133">JEA benötigt ein Identitätskonto im Hintergrund, wenn die Befehle eines Benutzers ausgeführt werden, der die Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="b7964-133">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="b7964-134">Sie legen fest, welche Identität von JEA in der Sitzungskonfigurationsdatei verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b7964-134">You define which identity JEA uses in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="b7964-135">Lokales virtuelles Konto</span><span class="sxs-lookup"><span data-stu-id="b7964-135">Local Virtual Account</span></span>

<span data-ttu-id="b7964-136">Die Verwendung eines lokalen virtuellen Kontos ist geeignet für Fälle, in denen alle für diesen JEA-Endpunkt definierten Rollen für die Verwaltung des lokalen Computers eingesetzt werden und ein lokales Administratorkonto ausreicht, um die Befehle erfolgreich auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b7964-136">Local virtual accounts are useful when all roles defined for the JEA endpoint are used to manage the local machine and a local administrator account is sufficient to run the commands successfully.</span></span>
<span data-ttu-id="b7964-137">Virtuelle Konten sind temporäre Konten, die für einen bestimmten Benutzer eindeutig sind und nur für die Dauer seiner PowerShell-Sitzung gültig sind.</span><span class="sxs-lookup"><span data-stu-id="b7964-137">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span> <span data-ttu-id="b7964-138">Virtuelle Konten auf einem Mitgliedsserver oder einer Arbeitsstation gehören zur Gruppe der **Administratoren** des lokalen Computers.</span><span class="sxs-lookup"><span data-stu-id="b7964-138">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group.</span></span> <span data-ttu-id="b7964-139">Auf einem Active Directory-Domänencontroller gehören virtuelle Konten zur Gruppe der **Domänen-Admins** der Domäne.</span><span class="sxs-lookup"><span data-stu-id="b7964-139">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="b7964-140">Wenn die durch die Sitzungskonfiguration definierten Rollen keine vollständigen Administratorrechte benötigen, können Sie die Sicherheitsgruppen angeben, zu denen das virtuelle Konto gehören soll.</span><span class="sxs-lookup"><span data-stu-id="b7964-140">If the roles defined by the session configuration don't require full administrative privilege, you can specify the security groups to which the virtual account will belong.</span></span> <span data-ttu-id="b7964-141">Auf einem Mitgliedsserver oder einer Arbeitsstation müssen die angegebenen Sicherheitsgruppen lokale Gruppen sein. Es darf sich nicht um Gruppen aus einer Domäne handeln.</span><span class="sxs-lookup"><span data-stu-id="b7964-141">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="b7964-142">Wird mindestens eine Sicherheitsgruppe angegeben, wird das virtuelle Konto nicht der lokalen Gruppe oder der Gruppe der Domänenadministratoren zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="b7964-142">When one or more security groups are specified, the virtual account isn't assigned to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

> [!NOTE]
> <span data-ttu-id="b7964-143">Virtuellen Konten wird die Anmeldung als Dienst direkt in der Sicherheitsrichtlinie für den lokalen Server gewährt.</span><span class="sxs-lookup"><span data-stu-id="b7964-143">Virtual accounts are temporarily granted the Logon as a service right in the local server security policy.</span></span> <span data-ttu-id="b7964-144">Wenn einer angegebenen Gruppe von virtuellen Konten bereits diese Berechtigung in der Richtlinie gewährt wurde, wird das individuelle virtuelle Konto nicht mehr hinzugefügt, und es wird aus der Richtlinie entfernt.</span><span class="sxs-lookup"><span data-stu-id="b7964-144">If one of the VirtualAccountGroups specified has already been granted this right in the policy, the individual virtual account will no longer be added and removed from the policy.</span></span> <span data-ttu-id="b7964-145">Dies kann sich beispielsweise bei Domänencontrollern als nützlich erweisen, bei denen Änderungen an der Sicherheitsrichtlinie für Domänencontroller genau überwacht werden.</span><span class="sxs-lookup"><span data-stu-id="b7964-145">This can be useful in scenarios such as domain controllers where revisions to the domain controller security policy are closely audited.</span></span> <span data-ttu-id="b7964-146">Dies ist nur in Windows Server 2016 mit dem Rollup vom November 2018 oder höher und Windows Server 2019 mit dem Rollup vom Januar 2019 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b7964-146">This is only available in Windows Server 2016 with the November 2018 or later rollup and Windows Server 2019 with the January 2019 or later rollup.</span></span>

#### <a name="group-managed-service-account"></a><span data-ttu-id="b7964-147">Gruppenverwaltetes Dienstkonto</span><span class="sxs-lookup"><span data-stu-id="b7964-147">Group-managed service account</span></span>

<span data-ttu-id="b7964-148">Für Szenarios, in denen JEA-Benutzer Zugriff auf Netzwerkressourcen wie Dateifreigaben und Webdienste benötigen, eignet sich als Identität ein gruppenverwaltetes Dienstkonto (Group Managed Service Account, gMSA).</span><span class="sxs-lookup"><span data-stu-id="b7964-148">A group-managed service account (GMSA) is the appropriate identity to use when JEA users need to access network resources such as file shares and web services.</span></span> <span data-ttu-id="b7964-149">Ein gMSA-Konto bietet Ihnen eine Domänenidentität zur Authentifizierung bei Ressourcen auf einem beliebigen Computer innerhalb der Domäne.</span><span class="sxs-lookup"><span data-stu-id="b7964-149">GMSAs give you a domain identity that is used to authenticate with resources on any machine within the domain.</span></span> <span data-ttu-id="b7964-150">Die mit einem gMSA-Konto einhergehenden Rechte werden durch die Ressourcen bestimmt, auf die Sie zugreifen.</span><span class="sxs-lookup"><span data-stu-id="b7964-150">The rights that a GMSA provides are determined by the resources you're accessing.</span></span> <span data-ttu-id="b7964-151">Administratorrechte für einen beliebigen Computer oder Dienste besitzen Sie nur dann, wenn der Computer- bzw. Dienstadministrator dem gMSA-Konto diese Rechte explizit erteilt hat.</span><span class="sxs-lookup"><span data-stu-id="b7964-151">You don't have admin rights on any machines or services unless the machine or service administrator has explicitly granted those rights to the GMSA.</span></span>

```powershell
# Configure JEA sessions to use the GMSA in the local computer's domain
# with the sAMAccountName of 'MyJEAGMSA'
GroupManagedServiceAccount = 'Domain\MyJEAGMSA'
```

<span data-ttu-id="b7964-152">gMSA-Konten sollten nur verwendet werden, wenn es wirklich nötig ist:</span><span class="sxs-lookup"><span data-stu-id="b7964-152">GMSAs should only be used when necessary:</span></span>

- <span data-ttu-id="b7964-153">Mit einem gMSA-Konto können Aktionen nur schwer zu einem Benutzer zurückverfolgt werden –</span><span class="sxs-lookup"><span data-stu-id="b7964-153">It's difficult to trace back actions to a user when using a GMSA.</span></span> <span data-ttu-id="b7964-154">jeder Benutzer besitzt dieselbe ausführende Identität.</span><span class="sxs-lookup"><span data-stu-id="b7964-154">Every user shares the same run-as identity.</span></span> <span data-ttu-id="b7964-155">Sie müssen PowerShell-Sitzungsaufzeichnungen und -protokolle überprüfen, um einzelne Benutzer mit ihren Aktionen abzugleichen.</span><span class="sxs-lookup"><span data-stu-id="b7964-155">You must review PowerShell session transcripts and logs to correlate individual users with their actions.</span></span>

- <span data-ttu-id="b7964-156">Ein gMSA-Konto besitzt möglicherweise Zugriff auf zahlreiche Netzwerkressourcen, auf die der Benutzer, der eine Verbindung herstellt, keinen Zugriff benötigt.</span><span class="sxs-lookup"><span data-stu-id="b7964-156">The GMSA may have access to many network resources that the connecting user doesn't need access to.</span></span> <span data-ttu-id="b7964-157">Versuchen Sie immer, effektive Berechtigungen in einer JEA-Sitzung zu beschränken und damit das Prinzip der geringsten Rechte anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="b7964-157">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="b7964-158">Gruppenverwaltete Dienstkonten sind nur auf Computern unter PowerShell 5.1 oder höher verfügbar, die einer Domäne angehören.</span><span class="sxs-lookup"><span data-stu-id="b7964-158">Group managed service accounts are only available on domain-joined machines using PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="b7964-159">Weitere Informationen zum Sichern einer JEA-Sitzung finden Sie im Artikel [JEA-Sicherheitsüberlegungen](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="b7964-159">For more information about securing a JEA session, see the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="b7964-160">Sitzungsaufzeichnungen</span><span class="sxs-lookup"><span data-stu-id="b7964-160">Session transcripts</span></span>

<span data-ttu-id="b7964-161">Es wird empfohlen, einen JEA-Endpunkt zu konfigurieren, um Aufzeichnungen von Benutzersitzungen automatisch zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="b7964-161">It's recommended that you configure a JEA endpoint to automatically record transcripts of users' sessions.</span></span> <span data-ttu-id="b7964-162">PowerShell-Sitzungsaufzeichnungen enthalten Informationen zu Benutzern, die eine Verbindung herstellen, die ihnen zugewiesene ausführende Identität und die vom Benutzer ausgeführten Befehle.</span><span class="sxs-lookup"><span data-stu-id="b7964-162">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span> <span data-ttu-id="b7964-163">Diese Informationen können für ein Überwachungsteam nützlich sein, um herauszufinden, welcher Benutzer eine bestimmte Änderung in einem System vorgenommen hat.</span><span class="sxs-lookup"><span data-stu-id="b7964-163">They can be useful to an auditing team who needs to understand who made a specific change to a system.</span></span>

<span data-ttu-id="b7964-164">Geben Sie einen Pfad zu einem Ordner an, in dem die Aufzeichnungen gespeichert werden sollen, um eine automatische Protokollierung in der Sitzungskonfigurationsdatei festzulegen.</span><span class="sxs-lookup"><span data-stu-id="b7964-164">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="b7964-165">Aufzeichnungen werden durch das **lokale Systemkonto** in den Ordner geschrieben, was Lese- und Schreibzugriff auf das Verzeichnis voraussetzt.</span><span class="sxs-lookup"><span data-stu-id="b7964-165">Transcripts are written to the folder by the **Local System** account, which requires read and write access to the directory.</span></span> <span data-ttu-id="b7964-166">Standardbenutzer sollten keinen Zugriff auf diesen Ordner besitzen.</span><span class="sxs-lookup"><span data-stu-id="b7964-166">Standard users should have no access to the folder.</span></span> <span data-ttu-id="b7964-167">Beschränken Sie die Anzahl der Sicherheitsadministratoren, die zur Überwachung auf die Aufzeichnungen zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="b7964-167">Limit the number of security administrators that have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="b7964-168">Benutzerlaufwerk</span><span class="sxs-lookup"><span data-stu-id="b7964-168">User drive</span></span>

<span data-ttu-id="b7964-169">Wenn Benutzer, die eine Verbindung herstellen, Dateien von einem oder auf einen JEA-Endpunkt kopieren müssen, können Sie das Benutzerlaufwerk in der Sitzungskonfigurationsdatei aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b7964-169">If your connecting users need to copy files to or from the JEA endpoint, you can enable the user drive in the session configuration file.</span></span> <span data-ttu-id="b7964-170">Das Benutzerlaufwerk ist ein **PSDrive**, das einem eindeutigen Ordner für jeden Benutzer zugeordnet ist, der eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="b7964-170">The user drive is a **PSDrive** that is mapped to a unique folder for each connecting user.</span></span> <span data-ttu-id="b7964-171">Benutzer können über diesen Ordner Dateien vom System oder auf das System kopieren, ohne dass sie Zugriff auf das gesamte Dateisystem benötigen bzw. ohne dass der FileSystem-Anbieter verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="b7964-171">This folder allows users to copy files to or from the system without giving them access to the full file system or exposing the FileSystem provider.</span></span> <span data-ttu-id="b7964-172">Der Inhalt der Benutzerlaufwerke steht durchgehend und sitzungsübergreifend zur Verfügung, um in Situationen Abhilfe zu schaffen, in denen die Netzwerkkonnektivität unterbrochen ist.</span><span class="sxs-lookup"><span data-stu-id="b7964-172">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="b7964-173">Auf dem Benutzerlaufwerk können standardmäßig maximal 50 MB Daten pro Benutzer gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b7964-173">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span> <span data-ttu-id="b7964-174">Sie können die Datenmenge, die ein Benutzer nutzen kann, mithilfe des Felds *UserDriveMaximumSize* einschränken.</span><span class="sxs-lookup"><span data-stu-id="b7964-174">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="b7964-175">Wenn die Daten auf dem Laufwerk nicht permanent zur Verfügung stehen sollen, können Sie eine geplante Aufgabe im System konfigurieren, damit der Ordner jede Nacht automatisch bereinigt wird.</span><span class="sxs-lookup"><span data-stu-id="b7964-175">If you don't want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="b7964-176">Das Benutzerlaufwerk ist nur in PowerShell 5.1 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b7964-176">The user drive is only available in PowerShell 5.1 or newer.</span></span>

<span data-ttu-id="b7964-177">Weitere Informationen zu PSDrives finden Sie unter [Verwalten von Windows PowerShell-Laufwerken](/powershell/scripting/samples/managing-windows-powershell-drives).</span><span class="sxs-lookup"><span data-stu-id="b7964-177">For more information about PSDrives, see [Managing PowerShell drives](/powershell/scripting/samples/managing-windows-powershell-drives).</span></span>

### <a name="role-definitions"></a><span data-ttu-id="b7964-178">Rollendefinitionen</span><span class="sxs-lookup"><span data-stu-id="b7964-178">Role definitions</span></span>

<span data-ttu-id="b7964-179">Über Rollendefinitionen in einer Sitzungskonfigurationsdatei legen Sie fest, welche **Benutzer** welchen **Rollen** zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="b7964-179">Role definitions in a session configuration file define the mapping of **users** to **roles**.</span></span> <span data-ttu-id="b7964-180">Jeder Benutzer bzw. jede Gruppe in diesem Feld erhält die Berechtigung für den JEA-Endpunkt, sobald er registriert ist.</span><span class="sxs-lookup"><span data-stu-id="b7964-180">Every user or group included in this field is granted permission to the JEA endpoint when it's registered.</span></span>
<span data-ttu-id="b7964-181">Jeder Benutzer und jede Gruppe kann jeweils nur einmal als Schlüssel in der Hashtabelle eingefügt werden, darf jedoch über mehrere Rollen verfügen.</span><span class="sxs-lookup"><span data-stu-id="b7964-181">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span> <span data-ttu-id="b7964-182">Der Name der Rollenfunktion sollte dem Namen der Rollenfunktionsdatei ohne die Erweiterung `.psrc` entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b7964-182">The name of the role capability should be the name of the role capability file, without the `.psrc` extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="b7964-183">Wenn ein Benutzer zu mehr als einer Gruppe in der Rollendefinition gehört, erhält er Zugriff auf die Rollen jeder einzelnen Gruppe.</span><span class="sxs-lookup"><span data-stu-id="b7964-183">If a user belongs to more than one group in the role definition, they get access to the roles of each.</span></span> <span data-ttu-id="b7964-184">Wenn zwei Rollen Zugriff auf die gleichen Cmdlets erteilen, erhält der Benutzer den Parametersatz mit den höchsten Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="b7964-184">When two roles grant access to the same cmdlets, the most permissive parameter set is granted to the user.</span></span>

<span data-ttu-id="b7964-185">Wenn Sie im Rollendefinitionsfeld lokale Benutzer bzw. Gruppen angeben, verwenden Sie den Computernamen, und nicht **localhost** oder Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="b7964-185">When specifying local users or groups in the role definitions field, be sure to use the computer name, not **localhost** or wildcards.</span></span> <span data-ttu-id="b7964-186">Überprüfen Sie den Computernamen durch Untersuchen der Variablen `$env:COMPUTERNAME`.</span><span class="sxs-lookup"><span data-stu-id="b7964-186">You can check the computer name by inspecting the `$env:COMPUTERNAME` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="b7964-187">Suchreihenfolge für Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="b7964-187">Role capability search order</span></span>

<span data-ttu-id="b7964-188">Auf die Rollenfunktionen wird, wie im vorherigen Beispiel gezeigt, durch den Basisnamen der Rollenfunktionsdatei verwiesen.</span><span class="sxs-lookup"><span data-stu-id="b7964-188">As shown in the example above, role capabilities are referenced by the base name of the role capability file.</span></span> <span data-ttu-id="b7964-189">Der Basisname einer Datei entspricht dem Dateinamen ohne Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="b7964-189">The base name of a file is the filename without the extension.</span></span> <span data-ttu-id="b7964-190">Sind im System mehrere Rollenfunktionen mit demselben Namen verfügbar, verwendet PowerShell die implizite Suchreihenfolge, um die gültige Rollenfunktionsdatei auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="b7964-190">If multiple role capabilities are available on the system with the same name, PowerShell uses its implicit search order to select the effective role capability file.</span></span> <span data-ttu-id="b7964-191">JEA erteilt **keinen** Zugriff auf alle Rollenfunktionsdateien mit demselben Namen.</span><span class="sxs-lookup"><span data-stu-id="b7964-191">JEA does **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="b7964-192">JEA verwendet die Umgebungsvariable `$env:PSModulePath`, um zu bestimmen, welche Pfaden nach Rollenfunktionsdateien gescannt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b7964-192">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span> <span data-ttu-id="b7964-193">JEA sucht innerhalb dieser Pfade nach gültigen PowerShell-Modulen, die einen Unterordner namens „RoleCapabilities“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="b7964-193">Within each of those paths, JEA looks for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span> <span data-ttu-id="b7964-194">Wie beim Importieren von Modulen zieht JEA Rollenfunktionen, die mit Windows ausgeliefert wurden, benutzerdefinierten Rollenfunktionen gleichen Namens vor.</span><span class="sxs-lookup"><span data-stu-id="b7964-194">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>

<span data-ttu-id="b7964-195">Bei allen anderen Namenskonflikten wird die Rangfolge durch die Reihenfolge bestimmt, in der Windows die Dateien im Verzeichnis aufzählt.</span><span class="sxs-lookup"><span data-stu-id="b7964-195">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory.</span></span> <span data-ttu-id="b7964-196">Diese Reihenfolge muss nicht unbedingt alphabetisch sein.</span><span class="sxs-lookup"><span data-stu-id="b7964-196">The order isn't guaranteed to be alphabetical.</span></span> <span data-ttu-id="b7964-197">Die erste gefundene Rollenfunktionsdatei, die mit dem angegebenen Namen übereinstimmt, wird für den Benutzer verwendet, der eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="b7964-197">The first role capability file found that matches the specified name is used for the connecting user.</span></span> <span data-ttu-id="b7964-198">Da die Suchreihenfolge für die Rollenfunktionen nicht deterministisch ist, wird **dringend empfohlen**, Rollenfunktionen eindeutige Dateinamen zu geben.</span><span class="sxs-lookup"><span data-stu-id="b7964-198">Since the role capability search order isn't deterministic, it's **strongly recommended** that role capabilities have unique filenames.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="b7964-199">Regeln für bedingten Zugriff</span><span class="sxs-lookup"><span data-stu-id="b7964-199">Conditional access rules</span></span>

<span data-ttu-id="b7964-200">Alle Benutzer und Gruppen im Feld **RoleDefinitions** erhalten automatisch Zugriff auf JEA-Endpunkte.</span><span class="sxs-lookup"><span data-stu-id="b7964-200">All users and groups included in the **RoleDefinitions** field are automatically granted access to JEA endpoints.</span></span> <span data-ttu-id="b7964-201">Sie können diesen Zugriff über Regeln für bedingten Zugriff optimieren und festlegen, dass Benutzer zusätzlichen Sicherheitsgruppen angehören müssen, die keinen Einfluss auf die ihnen zugewiesenen Rollen haben.</span><span class="sxs-lookup"><span data-stu-id="b7964-201">Conditional access rules allow you to refine this access and require users to belong to additional security groups that don't impact the roles to which they're assigned.</span></span> <span data-ttu-id="b7964-202">Dies ist hilfreich, wenn Sie eine Just-in-Time-Lösung für Privileged Access Management, eine Smartcard-Authentifizierung oder eine andere mehrstufige Authentifizierungslösung in JEA integrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="b7964-202">This is useful when you want to integrate a just-in-time privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="b7964-203">Bedingte Zugriffsregeln werden im Feld „RequiredGroups“ in einer Sitzungskonfigurationsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="b7964-203">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="b7964-204">Geben Sie dazu eine (optional geschachtelte) Hashtabelle an, die zum Erstellen Ihrer Regeln die Schlüssel „And“ und „Or“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="b7964-204">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="b7964-205">Nachfolgend finden Sie einige Beispiele für die Verwendung dieses Felds:</span><span class="sxs-lookup"><span data-stu-id="b7964-205">Here are some examples of how to use this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> <span data-ttu-id="b7964-206">Regeln für bedingten Zugriff sind nur in PowerShell 5.1 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b7964-206">Conditional access rules are only available in PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="b7964-207">Weitere Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="b7964-207">Other properties</span></span>

<span data-ttu-id="b7964-208">Sitzungskonfigurationsdateien verfügen über die gleichen Möglichkeiten wie eine Rollenfunktionsdatei, ohne jedoch Benutzern, die eine Verbindung herstellen, Zugriff auf unterschiedliche Befehle zu geben.</span><span class="sxs-lookup"><span data-stu-id="b7964-208">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span> <span data-ttu-id="b7964-209">Wenn Sie allen Benutzern den Zugriff auf bestimmte Cmdlets, Funktionen oder Anbieter ermöglichen möchten, können Sie dies direkt in der Sitzungskonfigurationsdatei tun.</span><span class="sxs-lookup"><span data-stu-id="b7964-209">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="b7964-210">Eine vollständige Liste der unterstützten Eigenschaften in der Sitzungskonfigurationsdatei erhalten Sie, wenn Sie `Get-Help New-PSSessionConfigurationFile -Full` ausführen.</span><span class="sxs-lookup"><span data-stu-id="b7964-210">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="b7964-211">Testen einer Sitzungskonfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="b7964-211">Testing a session configuration file</span></span>

<span data-ttu-id="b7964-212">Sie können eine Sitzungskonfigurationsdatei über das [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile)-Cmdlet testen.</span><span class="sxs-lookup"><span data-stu-id="b7964-212">You can test a session configuration using the [Test-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span> <span data-ttu-id="b7964-213">Es wird empfohlen, die Sitzungskonfigurationsdatei zu testen, wenn Sie die Datei `.pssc` manuell bearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="b7964-213">It's recommended that you test your session configuration file if you've manually edited the `.pssc` file.</span></span> <span data-ttu-id="b7964-214">Dadurch wird sichergestellt, dass die Syntax korrekt ist.</span><span class="sxs-lookup"><span data-stu-id="b7964-214">Testing ensures the syntax is correct.</span></span> <span data-ttu-id="b7964-215">Besteht eine Sitzungskonfigurationsdatei diesen Test nicht, kann sie im System auch nicht registriert werden.</span><span class="sxs-lookup"><span data-stu-id="b7964-215">If a session configuration file fails this test, it can't be registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="b7964-216">Beispiel für eine Sitzungskonfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="b7964-216">Sample session configuration file</span></span>

<span data-ttu-id="b7964-217">Im folgenden Beispiel wird eine Sitzungskonfiguration für JEA erstellt und überprüft.</span><span class="sxs-lookup"><span data-stu-id="b7964-217">The following example shows how to create and validate a session configuration for JEA.</span></span> <span data-ttu-id="b7964-218">Zur Vereinfachung und aus Gründen der Lesbarkeit werden die Rollendefinitionen in der `$roles`-Variable erstellt und gespeichert.</span><span class="sxs-lookup"><span data-stu-id="b7964-218">The role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span> <span data-ttu-id="b7964-219">Dies ist jedoch nicht unbedingt erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b7964-219">It isn't a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="b7964-220">Aktualisieren von Sitzungskonfigurationsdateien</span><span class="sxs-lookup"><span data-stu-id="b7964-220">Updating session configuration files</span></span>

<span data-ttu-id="b7964-221">Wenn Sie die Eigenschaften einer JEA-Sitzungskonfiguration einschließlich der Zuordnung von Benutzern zu Rollen ändern möchten, müssen Sie zunächst die [Registrierung aufheben](register-jea.md#unregistering-jea-configurations).</span><span class="sxs-lookup"><span data-stu-id="b7964-221">To change the properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations).</span></span> <span data-ttu-id="b7964-222">Führen Sie anschließend für die JEA-Sitzungskonfiguration mit einer aktualisierten Sitzungskonfigurationsdatei eine [erneute Registrierung](register-jea.md) durch.</span><span class="sxs-lookup"><span data-stu-id="b7964-222">Then, [re-register](register-jea.md) the JEA session configuration using an updated session configuration file.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b7964-223">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b7964-223">Next steps</span></span>

- [<span data-ttu-id="b7964-224">Registrieren einer JEA-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="b7964-224">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="b7964-225">Erstellen von JEA-Rollen</span><span class="sxs-lookup"><span data-stu-id="b7964-225">Author JEA roles</span></span>](role-capabilities.md)
