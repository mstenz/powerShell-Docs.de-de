---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: JEA-Sitzungskonfigurationen
ms.openlocfilehash: 0a8931ae15caf04a3639ab46f130e5f5b0498d8c
ms.sourcegitcommit: 0733db9a05e89e6a23f6b52b9edd784fcbe8beec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2017
---
# <a name="jea-session-configurations"></a><span data-ttu-id="9341c-103">JEA-Sitzungskonfigurationen</span><span class="sxs-lookup"><span data-stu-id="9341c-103">JEA Session Configurations</span></span>

> <span data-ttu-id="9341c-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9341c-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9341c-105">Ein JEA-Endpunkt wird auf einem System durch Erstellen und Registrieren einer PowerShell-Konfigurationsdatei auf eine bestimmte Art und Weise registriert.</span><span class="sxs-lookup"><span data-stu-id="9341c-105">A JEA endpoint is registered on a system by creating and registering a PowerShell session configuration file in a specific way.</span></span>
<span data-ttu-id="9341c-106">Sitzungskonfigurationen bestimmen, *welche Benutzer* den JEA-Endpunkt verwenden können und auf welche Rollen sie Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="9341c-106">Session configurations determine *who* can use the JEA endpoint, and which role(s) they will have access to.</span></span>
<span data-ttu-id="9341c-107">Sie legen außerdem globale Einstellungen fest, die für alle Benutzer einer Rolle in der JEA-Sitzung gelten.</span><span class="sxs-lookup"><span data-stu-id="9341c-107">They also define global settings that apply to users of any role in the JEA session.</span></span>

<span data-ttu-id="9341c-108">In diesem Thema wird beschrieben, wie Sie eine PowerShell-Konfigurationsdatei erstellen und einen JEA-Endpunkt registrieren.</span><span class="sxs-lookup"><span data-stu-id="9341c-108">This topic describes how to create a PowerShell session configuration file and register a JEA endpoint.</span></span>

## <a name="create-a-session-configuration-file"></a><span data-ttu-id="9341c-109">Erstellen einer Sitzungskonfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="9341c-109">Create a session configuration file</span></span>

<span data-ttu-id="9341c-110">Sie müssen zunächst angeben, wie ein JEA-Endpunkt konfiguriert werden soll, bevor Sie ihn registrieren können.</span><span class="sxs-lookup"><span data-stu-id="9341c-110">In order to register a JEA endpoint, you need to specify how that endpoint should be configured.</span></span>
<span data-ttu-id="9341c-111">Dabei stehen mehrere Optionen zur Auswahl. Am wichtigsten sind die folgenden: Wer sollte Zugriff auf den JEA-Endpunkt haben? Welche Rollen sollten den Benutzern zugewiesen werden? Welche Identität verwendet JEA unter der Oberfläche und welchen Namen soll der JEA-Endpunkt erhalten?</span><span class="sxs-lookup"><span data-stu-id="9341c-111">There are many options to consider here, the most important of which being who should have access to the JEA endpoint, which roles will they be assigned, which identity will JEA use under the covers, and what will be the name of the JEA endpoint.</span></span>
<span data-ttu-id="9341c-112">Alle diese Einstellungen sind in einer PowerShell-Sitzungskonfigurationsdatei definiert. Dabei handelt es sich um eine PowerShell-Datendatei mit der Erweiterung PSSC.</span><span class="sxs-lookup"><span data-stu-id="9341c-112">These are all defined in a PowerShell session configuration file, which is a PowerShell data file ending with a .pssc extension.</span></span>

<span data-ttu-id="9341c-113">Führen Sie den folgenden Befehl aus, um eine Gerüstdatei der Sitzungskonfigurationsdatei für JEA-Endpunkte zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="9341c-113">To create a skeleton session configuration file for JEA endpoints, run the following command.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> <span data-ttu-id="9341c-114">Standardmäßig sind nur die häufigsten Konfigurationsoptionen in der Gerüstdatei vorhanden.</span><span class="sxs-lookup"><span data-stu-id="9341c-114">Only the most common configuration options are included in the skeleton file by default.</span></span>
> <span data-ttu-id="9341c-115">Verwenden Sie den `-Full`-Switch, um alle anwendbaren Einstellungen in die generierte PSSC-Datei einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="9341c-115">Use the `-Full` switch to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="9341c-116">Sie können die Sitzungskonfigurationsdatei in einem beliebigen Texteditor öffnen.</span><span class="sxs-lookup"><span data-stu-id="9341c-116">You can open the session configuration file in any text editor.</span></span>
<span data-ttu-id="9341c-117">Das `-SessionType RestrictedRemoteServer`-Feld gibt an, dass die Sitzungskonfiguration von JEA für eine sichere Verwaltung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9341c-117">The `-SessionType RestrictedRemoteServer` field indicates that the session configuration will be used by JEA for secure management.</span></span>
<span data-ttu-id="9341c-118">Auf diese Weise konfigurierte Sitzungen arbeiten im [NoLanguage-Modus](https://technet.microsoft.com/en-us/library/dn433292.aspx) und verfügen nur über die folgenden acht Standardbefehle (und Aliase):</span><span class="sxs-lookup"><span data-stu-id="9341c-118">Sessions configured this way will operate in [NoLanguage mode](https://technet.microsoft.com/en-us/library/dn433292.aspx) and only have the following 8 default commands (and aliases) available:</span></span>

- <span data-ttu-id="9341c-119">Clear-Host (cls, löschen)</span><span class="sxs-lookup"><span data-stu-id="9341c-119">Clear-Host (cls, clear)</span></span>
- <span data-ttu-id="9341c-120">Exit-PSSession (exsn, beenden)</span><span class="sxs-lookup"><span data-stu-id="9341c-120">Exit-PSSession (exsn, exit)</span></span>
- <span data-ttu-id="9341c-121">Get-Command (gcm)</span><span class="sxs-lookup"><span data-stu-id="9341c-121">Get-Command (gcm)</span></span>
- <span data-ttu-id="9341c-122">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="9341c-122">Get-FormatData</span></span>
- <span data-ttu-id="9341c-123">"Get-Help "</span><span class="sxs-lookup"><span data-stu-id="9341c-123">Get-Help</span></span>
- <span data-ttu-id="9341c-124">Measure-Object (messen)</span><span class="sxs-lookup"><span data-stu-id="9341c-124">Measure-Object (measure)</span></span>
- <span data-ttu-id="9341c-125">Out-Default</span><span class="sxs-lookup"><span data-stu-id="9341c-125">Out-Default</span></span>
- <span data-ttu-id="9341c-126">Select-Object (auswählen)</span><span class="sxs-lookup"><span data-stu-id="9341c-126">Select-Object (select)</span></span>

<span data-ttu-id="9341c-127">Weder PowerShell-Anbieter noch externe Programme (ausführbare Dateien, Skripts usw.) stehen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="9341c-127">No PowerShell providers are available, nor are any external programs (executables, scripts, etc.).</span></span>

<span data-ttu-id="9341c-128">Es gibt mehrere andere Felder, die Sie für die JEA-Sitzung konfigurieren sollten.</span><span class="sxs-lookup"><span data-stu-id="9341c-128">There are several other fields you will want to configure for the JEA session.</span></span>
<span data-ttu-id="9341c-129">Sie werden in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9341c-129">They are covered in the following sections.</span></span>

### <a name="choose-the-jea-identity"></a><span data-ttu-id="9341c-130">Wählen der JEA-Identität</span><span class="sxs-lookup"><span data-stu-id="9341c-130">Choose the JEA identity</span></span>

<span data-ttu-id="9341c-131">JEA benötigt ein Identitätskonto im Hintergrund, wenn die Befehle eines Benutzers ausgeführt werden, der die Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="9341c-131">Behind the scenes, JEA needs an identity (account) to use when running a connected user's commands.</span></span>
<span data-ttu-id="9341c-132">Sie entscheiden, welche Identität JEA in der Sitzungskonfigurationsdatei verwendet.</span><span class="sxs-lookup"><span data-stu-id="9341c-132">You decide which identity JEA will use in the session configuration file.</span></span>

#### <a name="local-virtual-account"></a><span data-ttu-id="9341c-133">Lokales virtuelles Konto</span><span class="sxs-lookup"><span data-stu-id="9341c-133">Local Virtual Account</span></span>

<span data-ttu-id="9341c-134">Wenn alle von diesem JEA-Endpunkt unterstützten Rollen für die Verwaltung des lokalen Computers eingesetzt werden und ein lokales Administratorkonto ausreicht, um die Befehle erfolgreich auszuführen, sollten Sie JEA für die Verwendung eines lokalen virtuellen Kontos konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="9341c-134">If the roles supported by this JEA endpoint are all used to manage the local machine, and a local administrator account is sufficient to run the commands succesfully, you should configure JEA to use a local virtual account.</span></span>
<span data-ttu-id="9341c-135">Virtuelle Konten sind temporäre Konten, die für einen bestimmten Benutzer eindeutig sind und nur für die Dauer seiner PowerShell-Sitzung gültig sind.</span><span class="sxs-lookup"><span data-stu-id="9341c-135">Virtual accounts are temporary accounts that are unique to a specific user and only last for the duration of their PowerShell session.</span></span>
<span data-ttu-id="9341c-136">Virtuelle Konten auf einem Mitgliedsserver oder einer Arbeitsstation gehören zur Gruppe der **Administratoren** des lokalen Computers und haben Zugriff auf die meisten Systemressourcen.</span><span class="sxs-lookup"><span data-stu-id="9341c-136">On a member server or workstation, virtual accounts belong to the local computer's **Administrators** group, and have access to most system resources.</span></span>
<span data-ttu-id="9341c-137">Auf einem Active Directory-Domänencontroller gehören virtuelle Konten zur Gruppe der **Domänen-Admins** der Domäne.</span><span class="sxs-lookup"><span data-stu-id="9341c-137">On an Active Directory Domain Controller, virtual accounts belong to the domain's **Domain Admins** group.</span></span>

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

<span data-ttu-id="9341c-138">Wenn die Rollen, die von der Sitzungskonfiguration unterstützt werden, keine derart umfassenden Berechtigungen benötigen, können Sie optional die Sicherheitsgruppen angeben, zu denen das virtuelle Konto gehören wird.</span><span class="sxs-lookup"><span data-stu-id="9341c-138">If the roles supported by the session configuration do not require such broad privileges, you can optionally specify the security groups to which the virtual account will belong.</span></span>
<span data-ttu-id="9341c-139">Auf einem Mitgliedsserver oder einer Arbeitsstation müssen die angegebenen Sicherheitsgruppen lokale Gruppen sein. Es darf sich nicht um Gruppen aus einer Domäne handeln.</span><span class="sxs-lookup"><span data-stu-id="9341c-139">On a member server or workstation, the specified security groups must be local groups, not groups from a domain.</span></span>

<span data-ttu-id="9341c-140">Wenn eine oder mehrere Sicherheitsgruppen angegeben wurden, gehört das virtuelle Konto nicht mehr zur lokalen Gruppe oder der Administratorengruppe der Domäne.</span><span class="sxs-lookup"><span data-stu-id="9341c-140">When one or more security groups is specified, the virtual account will no longer belong to the local or domain administrators group.</span></span>

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```

#### <a name="group-managed-service-account"></a><span data-ttu-id="9341c-141">Gruppenverwaltetes Dienstkonto</span><span class="sxs-lookup"><span data-stu-id="9341c-141">Group Managed Service Account</span></span>


<span data-ttu-id="9341c-142">Für Szenarios, in denen der JEA-Benutzer Zugriff auf Netzwerkressourcen wie einen anderen Computer oder andere Webdienste benötigt, empfiehlt sich ein gruppenverwaltetes Dienstkonto (Group Managed Service Account, gMSA) als bessere Identität.</span><span class="sxs-lookup"><span data-stu-id="9341c-142">For scenarios requiring the JEA user to access network resources such as other machines or web services, a group managed service account (gMSA) is a more appropriate identity to use.</span></span>
<span data-ttu-id="9341c-143">gMSA-Konten bieten Ihnen eine Domänenidentität, die eine Authentifizierung von Ressourcen auf einem beliebigen Computer innerhalb der Domäne ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="9341c-143">gMSA accounts give you a domain identity which can be used to authenticate against resources on any machine within the domain.</span></span>
<span data-ttu-id="9341c-144">Die Rechte eines gMSA-Kontos werden durch die Ressourcen bestimmt, auf die Sie zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9341c-144">The rights the gMSA account gives you is determined by the resources you are accessing.</span></span>
<span data-ttu-id="9341c-145">Administratorrechte auf einem beliebigen Computer oder auf Dienste werden automatisch zugewiesen, wenn Ihnen der Computer-/Dienstadministrator explizit Administratorberechtigungen für das gMSA-Konto erteilt hat.</span><span class="sxs-lookup"><span data-stu-id="9341c-145">You will not automatically have admin rights on any machines or services unless the machine/service administrator has explicitly granted the gMSA account admin privileges.</span></span>

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

<span data-ttu-id="9341c-146">gMSA-Konten sollten nur dann verwendet werden, wenn ein Zugriff auf Netzwerkressourcen erforderlich ist, und das aus folgenden Gründen:</span><span class="sxs-lookup"><span data-stu-id="9341c-146">gMSA accounts should only be used when access to network resources are required for a few reasons:</span></span>

- <span data-ttu-id="9341c-147">Es ist schwieriger, Aktionen zu einem Benutzer zurückzuverfolgen, wenn ein gMSA-Konto verwendet wird, da jeder Benutzer die gleiche ausführende Identität aufweist.</span><span class="sxs-lookup"><span data-stu-id="9341c-147">It is harder to trace back actions to a user when using a gMSA account since every user shares the same run-as identity.</span></span> <span data-ttu-id="9341c-148">Sie müssen PowerShell-Sitzungsaufzeichnungen und -protokolle überprüfen, um Benutzer mit ihren Aktionen zu korrelieren.</span><span class="sxs-lookup"><span data-stu-id="9341c-148">You will need to consult PowerShell session transcripts and logs to correlate users with their actions.</span></span>

- <span data-ttu-id="9341c-149">Das gMSA-Konto hat möglicherweise Zugriff auf zahlreiche Netzwerkressourcen, auf die der Benutzer, der eine Verbindung herstellt, keinen Zugriff benötigt.</span><span class="sxs-lookup"><span data-stu-id="9341c-149">The gMSA account may have access to many network resources which the connecting user does not need access to.</span></span> <span data-ttu-id="9341c-150">Versuchen Sie immer, effektive Berechtigungen in einer JEA-Sitzung zu beschränken und damit das Prinzip der geringsten Rechte anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="9341c-150">Always try to limit effective permissions in a JEA session to follow the principle of least privilege.</span></span>

> [!NOTE]
> <span data-ttu-id="9341c-151">Gruppenverwaltete Dienstkonten sind nur unter Windows PowerShell 5.1 oder höher verfügbar sowie auf den einer Domäne angehörigen Computern.</span><span class="sxs-lookup"><span data-stu-id="9341c-151">Group managed service accounts are only available in Windows PowerShell 5.1 or newer and on domain-joined machines.</span></span>


#### <a name="more-information-about-run-as-users"></a><span data-ttu-id="9341c-152">Weitere Informationen zum Ausführen als Benutzer</span><span class="sxs-lookup"><span data-stu-id="9341c-152">More information about run as users</span></span>

<span data-ttu-id="9341c-153">Weitere Informationen zum Ausführen als Identitäten und wie sie zur Sicherheit einer JEA-Sitzung beitragen finden Sie im Artikel zum Thema [Security Considerations (Sicherheitsaspekte)](security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="9341c-153">Additional information about run as identities and how they factor into the security of a JEA session can be found in the [security considerations](security-considerations.md) article.</span></span>

### <a name="session-transcripts"></a><span data-ttu-id="9341c-154">Sitzungsaufzeichnungen</span><span class="sxs-lookup"><span data-stu-id="9341c-154">Session transcripts</span></span>

<span data-ttu-id="9341c-155">Es wird empfohlen, dass Sie eine JEA-Sitzungskonfigurationsdatei konfigurieren, um Protokolle von Benutzersitzungen automatisch aufzuzeichnen.</span><span class="sxs-lookup"><span data-stu-id="9341c-155">It is recommended that you configure a JEA session configuration file to automatically record transcripts of users' sessions.</span></span>
<span data-ttu-id="9341c-156">PowerShell-Sitzungsaufzeichnungen enthalten Informationen zu Benutzern, die eine Verbindung herstellen, die ihnen zugewiesene ausführende Identität und die vom Benutzer ausgeführten Befehle.</span><span class="sxs-lookup"><span data-stu-id="9341c-156">PowerShell session transcripts contain information about the connecting user, the run as identity assigned to them, and the commands run by the user.</span></span>
<span data-ttu-id="9341c-157">Diese Informationen können für ein Überwachungsteam nützlich sein, das wissen muss, wer an einem System eine Änderung vorgenommen hat.</span><span class="sxs-lookup"><span data-stu-id="9341c-157">They can be useful to an auditing team who needs to understand who performed a specific change to a system.</span></span>

<span data-ttu-id="9341c-158">Geben Sie einen Pfad zu einem Ordner an, in dem die Aufzeichnungen gespeichert werden sollen, um eine automatische Protokollierung in der Sitzungskonfigurationsdatei festzulegen.</span><span class="sxs-lookup"><span data-stu-id="9341c-158">To configure automatic transcription in the session configuration file, provide a path to a folder where the transcripts should be stored.</span></span>

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

<span data-ttu-id="9341c-159">Der angegebene Ordner sollte so konfiguriert sein, dass Benutzer ihn weder ändern noch darin enthaltene Daten löschen können.</span><span class="sxs-lookup"><span data-stu-id="9341c-159">The specified folder should be configured to prevent users from modifying or deleting any data in it.</span></span>
<span data-ttu-id="9341c-160">Aufzeichnungen werden durch das lokale Systemkonto in den Ordner geschrieben, was Lese- und Schreibzugriff auf das Verzeichnis voraussetzt.</span><span class="sxs-lookup"><span data-stu-id="9341c-160">Transcripts are written to the folder by the Local System account, which requires read and write access to the directory.</span></span>
<span data-ttu-id="9341c-161">Standardbenutzer sollten keinen Zugriff auf den Ordner haben. Außerdem sollte nur eine begrenzte Anzahl von Sicherheitsadministratoren über Rechte für die Überwachung der Aufzeichnungen verfügen.</span><span class="sxs-lookup"><span data-stu-id="9341c-161">Standard users should have no access to the folder, and a limited set of security administrators should have access to audit the transcripts.</span></span>

### <a name="user-drive"></a><span data-ttu-id="9341c-162">Benutzerlaufwerk</span><span class="sxs-lookup"><span data-stu-id="9341c-162">User drive</span></span>

<span data-ttu-id="9341c-163">Wenn Benutzer, die eine Verbindung herstellen, Dateien von einem bzw. auf einen JEA-Endpunkt kopieren müssen, um einen Befehl auszuführen, können Sie das Benutzerlaufwerk in der Sitzungskonfigurationsdatei aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9341c-163">If your connecting users will need to copy files to/from the JEA endpoint in order to run a command, you can enable the user drive in the session configuration file.</span></span>
<span data-ttu-id="9341c-164">Das Benutzerlaufwerk ist ein [PSDrive](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives), das einem eindeutigen Ordner für jeden Benutzer zugeordnet ist, der eine Verbindung herstellt.</span><span class="sxs-lookup"><span data-stu-id="9341c-164">The user drive is a [PSDrive](https://msdn.microsoft.com/en-us/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) that is mapped to a unique folder for each connecting user.</span></span>
<span data-ttu-id="9341c-165">Dieser Ordner dient als Speicherplatz, um Dateien vom und auf das System zu kopieren, ohne dass die Benutzer Zugriff auf das gesamte Dateisystem benötigen bzw. ohne den FileSystem-Anbieter verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="9341c-165">This folder serves as a space for them to copy files to/from the system, without giving them access to the full file system or exposing the FileSystem provider.</span></span>
<span data-ttu-id="9341c-166">Der Inhalt der Benutzerlaufwerke steht durchgehend und sitzungsübergreifend zur Verfügung, um in Situationen Abhilfe zu schaffen, in denen die Netzwerkkonnektivität unterbrochen ist.</span><span class="sxs-lookup"><span data-stu-id="9341c-166">The user drive contents are persistent across sessions to accommodate situations where network connectivity may be interrupted.</span></span>

```powershell
MountUserDrive = $true
```

<span data-ttu-id="9341c-167">Auf dem Benutzerlaufwerk können standardmäßig maximal 50 MB Daten pro Benutzer gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="9341c-167">By default, the user drive allows you to store a maximum of 50MB of data per user.</span></span>
<span data-ttu-id="9341c-168">Sie können die Datenmenge, die ein Benutzer nutzen kann, mithilfe des Felds *UserDriveMaximumSize* einschränken.</span><span class="sxs-lookup"><span data-stu-id="9341c-168">You can limit the amount of data a user can consume with the *UserDriveMaximumSize* field.</span></span>

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

<span data-ttu-id="9341c-169">Wenn die Daten auf dem Laufwerk nicht permanent zur Verfügung stehen sollen, können Sie eine geplante Aufgabe auf dem System konfigurieren, damit der Ordner jede Nacht automatisch bereinigt wird.</span><span class="sxs-lookup"><span data-stu-id="9341c-169">If you do not want data in the user drive to be persistent, you can configure a scheduled task on the system to automatically clean up the folder every night.</span></span>

> [!NOTE]
> <span data-ttu-id="9341c-170">Das Benutzerlaufwerk ist nur in Windows PowerShell 5.1 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9341c-170">The user drive is only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="role-definitions"></a><span data-ttu-id="9341c-171">Rollendefinitionen</span><span class="sxs-lookup"><span data-stu-id="9341c-171">Role definitions</span></span>

<span data-ttu-id="9341c-172">Über Rollendefinitionen in einer Sitzungskonfigurationsdatei legen Sie fest, welche *Benutzer* welchen *Rollen* zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="9341c-172">Role definitions in a session configuration file define the mapping of *users* to *roles*.</span></span>
<span data-ttu-id="9341c-173">Jeder Benutzer bzw. jede Gruppe in diesem Feld erhält automatisch Berechtigungen für den JEA-Endpunkt, sobald er registriert ist.</span><span class="sxs-lookup"><span data-stu-id="9341c-173">Every user or group included in this field will automatically be granted permission to the JEA endpoint when it is registered.</span></span>
<span data-ttu-id="9341c-174">Jeder Benutzer und jede Gruppe kann jeweils nur einmal als Schlüssel in der Hashtabelle eingefügt werden, darf jedoch über mehrere Rollen verfügen.</span><span class="sxs-lookup"><span data-stu-id="9341c-174">Each user or group can be included as a key in the hashtable only once, but can be assigned multiple roles.</span></span>
<span data-ttu-id="9341c-175">Der Name der Rollenfunktion sollte dem Namen der Rollenfunktionsdatei ohne die Erweiterung PSRC entsprechen.</span><span class="sxs-lookup"><span data-stu-id="9341c-175">The name of the role capability should be the name of the role capability file, without the .psrc extension.</span></span>

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

<span data-ttu-id="9341c-176">Wenn ein Benutzer zu mehr als einer Gruppe in der Rollendefinition gehört, erhält er Zugriff auf die Rollen jeder einzelnen Gruppe.</span><span class="sxs-lookup"><span data-stu-id="9341c-176">If a user belongs to more than one group in the role definition, they will get access to the roles of each.</span></span>
<span data-ttu-id="9341c-177">Wenn zwei Rollen Zugriff auf die gleichen Cmdlets vergeben, erhält der Benutzer den Parameter mit den höchsten Berechtigungen.</span><span class="sxs-lookup"><span data-stu-id="9341c-177">If two roles grant access to the same cmdlets, the most permissive parameter set will be granted to the user.</span></span>

<span data-ttu-id="9341c-178">Wenn Sie im Rollendefinitionsfeld lokale Benutzer oder Gruppen angeben, geben Sie vor dem umgekehrten Schrägstrich den Computernamen (nicht *localhost* oder *.*) an.</span><span class="sxs-lookup"><span data-stu-id="9341c-178">When specifying local users or groups in the role definitions field, be sure to use the computer name (not *localhost* or *.*) before the backslash.</span></span>
<span data-ttu-id="9341c-179">Überprüfen Sie den Computernamen durch Untersuchen der Variablen `$env:computername`.</span><span class="sxs-lookup"><span data-stu-id="9341c-179">You can check the computer name by inspecting the `$env:computername` variable.</span></span>

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a><span data-ttu-id="9341c-180">Suchreihenfolge für Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="9341c-180">Role capability search order</span></span>
<span data-ttu-id="9341c-181">Wie im obigen Beispiel gezeigt, wird auf die Rollenfunktionen durch den flachen Namen (Dateiname ohne Erweiterung) verwiesen.</span><span class="sxs-lookup"><span data-stu-id="9341c-181">As shown in the example above, role capabilities are referenced by the flat name (filename without the extension) of the role capability file.</span></span>
<span data-ttu-id="9341c-182">Wenn mehrere Rollenfunktionen mit dem gleichen flachen Namen im System verfügbar sind, verwendet PowerShell die implizite Suchreihenfolge, um die zutreffende Rollenfunktionsdatei auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="9341c-182">If multiple role capabilities are available on the system with the same flat name, PowerShell will use its implicit search order to select the effective role capability file.</span></span>
<span data-ttu-id="9341c-183">Sie erhalten **keinen** Zugriff auf alle Rollenfunktionsdateien mit dem gleichen Namen.</span><span class="sxs-lookup"><span data-stu-id="9341c-183">It will **not** give access to all role capability files with the same name.</span></span>

<span data-ttu-id="9341c-184">JEA verwendet die Umgebungsvariable `$env:PSModulePath`, um zu bestimmen, welche Pfaden nach Rollenfunktionsdateien gescannt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="9341c-184">JEA uses the `$env:PSModulePath` environment variable to determine which paths to scan for role capability files.</span></span>
<span data-ttu-id="9341c-185">JEA sucht innerhalb dieser Pfade nach gültigen PowerShell-Modulen, die einen Unterordner namens „RoleCapabilities“ enthalten.</span><span class="sxs-lookup"><span data-stu-id="9341c-185">Within each of those paths, JEA will look for valid PowerShell modules that contain a "RoleCapabilities" subfolder.</span></span>
<span data-ttu-id="9341c-186">Wie beim Importieren von Modulen zieht JEA Rollenfunktionen, die mit Windows ausgeliefert wurden, benutzerdefinierten Rollenfunktionen gleichen Namens vor.</span><span class="sxs-lookup"><span data-stu-id="9341c-186">As with importing modules, JEA prefers role capabilities that are shipped with Windows to custom role capabilities with the same name.</span></span>
<span data-ttu-id="9341c-187">Bei allen anderen Namenskonflikten wird die Rangfolge durch die Reihenfolge bestimmt, in der Windows die Dateien im Verzeichnis aufzählt (nicht unbedingt alphabetisch).</span><span class="sxs-lookup"><span data-stu-id="9341c-187">For all other naming conflicts, precedence is determined by the order in which Windows enumerates the files in the directory (not guaranteed to be alphabetically).</span></span>
<span data-ttu-id="9341c-188">Die erste gefundene Rollenfunktionsdatei, die den gewünschten Namen hat, wird für den verbindenden Benutzer verwendet.</span><span class="sxs-lookup"><span data-stu-id="9341c-188">The first role capability file found that matches the desired name will be used for the connecting user.</span></span>

<span data-ttu-id="9341c-189">Da die Suchreihenfolge der Rollenfunktion nicht deterministisch ist, wenn zwei oder mehr Funktionen der Rolle den gleichen Namen aufweisen, wird **dringend empfohlen**, sicherzustellen, dass Rollenfunktionen auf Ihrem Computer über eindeutige Namen verfügen.</span><span class="sxs-lookup"><span data-stu-id="9341c-189">Since the role capability search order is not deterministic when two or more role capabilities share the same name, it is **strongly recommended** that you ensure role capabilities have unique names on your machine.</span></span>

### <a name="conditional-access-rules"></a><span data-ttu-id="9341c-190">Regeln für bedingten Zugriff</span><span class="sxs-lookup"><span data-stu-id="9341c-190">Conditional access rules</span></span>

<span data-ttu-id="9341c-191">Alle Benutzer und Gruppen im Feld „RoleDefinitions“ haben automatisch Zugriff auf JEA-Endpunkte.</span><span class="sxs-lookup"><span data-stu-id="9341c-191">All users and groups included in the RoleDefinitions field are automatically granted access to JEA endpoints.</span></span>
<span data-ttu-id="9341c-192">Anhand von bedingten Zugriffsregeln können Sie diesen Zugriff optimieren und zur Bedingung machen, dass Benutzer zusätzlichen Sicherheitsgruppen angehören, die keinen Einfluss auf die ihnen zugewiesenen Rollen haben.</span><span class="sxs-lookup"><span data-stu-id="9341c-192">Conditional access rules allow you to refine this access and require users to belong to additional security groups which do not impact the roles which they are assigned.</span></span>
<span data-ttu-id="9341c-193">Dies kann hilfreich sein, wenn Sie eine Just-in-Time-Privileged Access Management-Lösung, eine Smartcard-Authentifizierung oder eine andere Multifaktor-Authentifizierungslösung mit JEA integrieren möchten.</span><span class="sxs-lookup"><span data-stu-id="9341c-193">This can be useful if you want to integrate a "just in time" privileged access management solution, smartcard authentication, or other multifactor authentication solution with JEA.</span></span>

<span data-ttu-id="9341c-194">Bedingte Zugriffsregeln werden im Feld „RequiredGroups“ in einer Sitzungskonfigurationsdatei definiert.</span><span class="sxs-lookup"><span data-stu-id="9341c-194">Conditional access rules are defined in the RequiredGroups field in a session configuration file.</span></span>
<span data-ttu-id="9341c-195">Geben Sie dazu eine (optional geschachtelte) Hashtabelle an, die zum Erstellen Ihrer Regeln die Schlüssel „And“ und „Or“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="9341c-195">There, you can provide a hashtable (optionally nested) that uses 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="9341c-196">Nachfolgend finden Sie einige Beispiele für die Verwendung dieses Felds:</span><span class="sxs-lookup"><span data-stu-id="9341c-196">Here are some examples of how to leverage this field:</span></span>

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
> <span data-ttu-id="9341c-197">Bedingte Zugriffsregeln sind nur in Windows PowerShell 5.1 oder höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9341c-197">Conditional access rules are only available in Windows PowerShell 5.1 or newer.</span></span>

### <a name="other-properties"></a><span data-ttu-id="9341c-198">Weitere Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="9341c-198">Other properties</span></span>
<span data-ttu-id="9341c-199">Sitzungskonfigurationsdateien verfügen über die gleichen Möglichkeiten wie eine Rollenfunktionsdatei, ohne jedoch Benutzern, die eine Verbindung herstellen, Zugriff auf unterschiedliche Befehle zu geben.</span><span class="sxs-lookup"><span data-stu-id="9341c-199">Session configuration files can also do everything a role capability file can do, just without the ability to give connecting users access to different commands.</span></span>
<span data-ttu-id="9341c-200">Wenn Sie allen Benutzern den Zugriff auf bestimmte Cmdlets, Funktionen oder Anbieter ermöglichen möchten, können Sie dies direkt in der Sitzungskonfigurationsdatei tun.</span><span class="sxs-lookup"><span data-stu-id="9341c-200">If you want to allow all users access to specific cmdlets, functions, or providers, you can do so right in the session configuration file.</span></span>
<span data-ttu-id="9341c-201">Eine vollständige Liste der unterstützten Eigenschaften in der Sitzungskonfigurationsdatei erhalten Sie, wenn Sie `Get-Help New-PSSessionConfigurationFile -Full` ausführen.</span><span class="sxs-lookup"><span data-stu-id="9341c-201">For a full list of supported properties in the session configuration file, run `Get-Help New-PSSessionConfigurationFile -Full`.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="9341c-202">Testen einer Sitzungskonfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="9341c-202">Testing a session configuration file</span></span>

<span data-ttu-id="9341c-203">Sie können eine Sitzungskonfigurationsdatei über das [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile)-Cmdlet testen.</span><span class="sxs-lookup"><span data-stu-id="9341c-203">You can test a session configuration using the [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile) cmdlet.</span></span>
<span data-ttu-id="9341c-204">Es wird dringend empfohlen, die Sitzungskonfigurationsdatei zu testen, wenn Sie die PSSC-Datei manuell mithilfe eines Text-Editors bearbeitet haben, um eine korrekte Syntax zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="9341c-204">It is strongly recommended that you test your session configuration file if you have edited the pssc file manually using a text editor to ensure the syntax is correct.</span></span>
<span data-ttu-id="9341c-205">Wenn eine Sitzungskonfigurationsdatei den Test nicht bestanden hat, kann sie nicht erfolgreich auf dem System registriert werden.</span><span class="sxs-lookup"><span data-stu-id="9341c-205">If a session configuration file does not pass this test, it will not be able to be successfully registered on the system.</span></span>

## <a name="sample-session-configuration-file"></a><span data-ttu-id="9341c-206">Beispiel für eine Sitzungskonfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="9341c-206">Sample session configuration file</span></span>

<span data-ttu-id="9341c-207">Nachstehend finden Sie ein vollständiges Beispiel zum Erstellen und Überprüfen einer Sitzungskonfiguration für JEA.</span><span class="sxs-lookup"><span data-stu-id="9341c-207">Below is a complete example showing how to create and validate a session configuration for JEA.</span></span>
<span data-ttu-id="9341c-208">Beachten Sie, dass die Rollendefinitionen zur Vereinfachung und aus Gründen der Lesbarkeit in der `$roles`-Variablen erstellt und gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="9341c-208">Note that the role definitions are created and stored in the `$roles` variable for convenience and readability.</span></span>
<span data-ttu-id="9341c-209">Dies ist jedoch nicht Voraussetzung.</span><span class="sxs-lookup"><span data-stu-id="9341c-209">It is not a requirement to do so.</span></span>

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a><span data-ttu-id="9341c-210">Aktualisieren von Sitzungskonfigurationsdateien</span><span class="sxs-lookup"><span data-stu-id="9341c-210">Updating session configuration files</span></span>

<span data-ttu-id="9341c-211">Wenn Sie die Eigenschaften einer JEA-Sitzungskonfiguration einschließlich der Zuordnung von Benutzern zu Rollen ändern möchten, müssen Sie für diese JEA-Sitzungskonfiguration zunächst die [Registrierung aufheben](register-jea.md#unregistering-jea-configurations) und sie dann [erneut registrieren](register-jea.md).</span><span class="sxs-lookup"><span data-stu-id="9341c-211">If you need to change properties of a JEA session configuration, including the mapping of users to roles, you must [unregister](register-jea.md#unregistering-jea-configurations) and [re-register](register-jea.md) the JEA session configuration.</span></span>
<span data-ttu-id="9341c-212">Wenn Sie die JEA-Sitzungskonfiguration erneut registrieren, verwenden Sie eine aktualisierte PowerShell-Sitzungskonfigurationsdatei, die die gewünschten Änderungen enthält.</span><span class="sxs-lookup"><span data-stu-id="9341c-212">When you re-register the JEA session configuration, use an updated PowerShell session configuration file that includes your desired changes.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9341c-213">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="9341c-213">Next steps</span></span>

- [<span data-ttu-id="9341c-214">Registrieren einer JEA-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="9341c-214">Register a JEA configuration</span></span>](register-jea.md)
- [<span data-ttu-id="9341c-215">Erstellen von JEA-Rollen</span><span class="sxs-lookup"><span data-stu-id="9341c-215">Author JEA roles</span></span>](role-capabilities.md)

