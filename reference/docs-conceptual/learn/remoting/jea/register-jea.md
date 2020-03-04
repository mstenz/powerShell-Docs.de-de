---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Registrieren von JEA-Konfigurationen
ms.openlocfilehash: 7cc67e891bc14dd667c97e9a8b550b33b4c2b874
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706205"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="1a83d-103">Registrieren von JEA-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="1a83d-103">Registering JEA Configurations</span></span>

<span data-ttu-id="1a83d-104">Nachdem Sie Ihre [Rollenfunktionen](role-capabilities.md) und die [Sitzungskonfigurationsdatei](session-configurations.md) erstellt haben, müssen Sie nur noch den JEA-Endpunkt registrieren.</span><span class="sxs-lookup"><span data-stu-id="1a83d-104">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step is to register the JEA endpoint.</span></span> <span data-ttu-id="1a83d-105">Das Registrieren des JEA-Endpunkts beim System stellt den Endpunkt für Benutzer und Automatisierungs-Engines zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1a83d-105">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="1a83d-106">Einzelcomputerkonfiguration</span><span class="sxs-lookup"><span data-stu-id="1a83d-106">Single machine configuration</span></span>

<span data-ttu-id="1a83d-107">Sie können JEA für kleine Umgebungen bereitstellen, indem Sie die Konfigurationsdatei mithilfe des [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration)-Cmdlets registrieren.</span><span class="sxs-lookup"><span data-stu-id="1a83d-107">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="1a83d-108">Vergewissern Sie sich vor Beginn, dass die folgenden Voraussetzungen erfüllt sind:</span><span class="sxs-lookup"><span data-stu-id="1a83d-108">Before you begin, ensure that the following prerequisites have been met:</span></span>

- <span data-ttu-id="1a83d-109">Eine oder mehrere Rollen wurden erstellt und im Ordner **RoleCapabilities** eines PowerShell-Moduls abgelegt.</span><span class="sxs-lookup"><span data-stu-id="1a83d-109">One or more roles has been created and placed in the **RoleCapabilities** folder of a PowerShell module.</span></span>
- <span data-ttu-id="1a83d-110">Eine Sitzungskonfigurationsdatei wurde erstellt und getestet.</span><span class="sxs-lookup"><span data-stu-id="1a83d-110">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="1a83d-111">Der Benutzer, der die JEA-Konfiguration registriert, verfügt über Administratorrechte auf dem System.</span><span class="sxs-lookup"><span data-stu-id="1a83d-111">The user registering the JEA configuration has administrator rights on the system.</span></span>
- <span data-ttu-id="1a83d-112">Sie haben einen Namen für Ihren JEA-Endpunkt ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="1a83d-112">You've selected a name for your JEA endpoint.</span></span>

<span data-ttu-id="1a83d-113">Der Name des JEA-Endpunkts wird benötigt, wenn Benutzer mit JEA eine Verbindung mit dem System herstellen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-113">The name of the JEA endpoint is required when users connect to the system using JEA.</span></span> <span data-ttu-id="1a83d-114">Das [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet listet die Namen der Endpunkte auf einem System auf.</span><span class="sxs-lookup"><span data-stu-id="1a83d-114">The [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet lists the names of the endpoints on a system.</span></span> <span data-ttu-id="1a83d-115">Endpunkte, deren Name mit `microsoft` beginnen, gehören normalerweise zum Funktionsumfang von Windows.</span><span class="sxs-lookup"><span data-stu-id="1a83d-115">Endpoints that start with `microsoft` are typically shipped with Windows.</span></span> <span data-ttu-id="1a83d-116">Der Endpunkt `microsoft.powershell` ist der Standardendpunkt, der verwendet wird, wenn eine Verbindung mit einem PowerShell-Remoteendpunkt hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1a83d-116">The `microsoft.powershell` endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="1a83d-117">Führen Sie den folgenden Befehl aus, um den Endpunkt zu registrieren:</span><span class="sxs-lookup"><span data-stu-id="1a83d-117">Run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1a83d-118">Der oben angegebene Befehl startet den WinRM-Dienst im System neu.</span><span class="sxs-lookup"><span data-stu-id="1a83d-118">The previous command restarts the WinRM service on the system.</span></span> <span data-ttu-id="1a83d-119">Dadurch werden alle PowerShell-Remotingsitzungen und alle laufenden DSC-Konfigurationen beendet.</span><span class="sxs-lookup"><span data-stu-id="1a83d-119">This terminates all PowerShell remoting sessions and any ongoing DSC configurations.</span></span> <span data-ttu-id="1a83d-120">Schalten Sie nach Möglichkeit vor dem Ausführen des Befehls alle Produktionscomputer offline, um Unterbrechung des Geschäftsbetriebs zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="1a83d-120">We recommended you take production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="1a83d-121">Nach der Registrierung können Sie [JEA verwenden](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="1a83d-121">After registration, you're ready to [use JEA](using-jea.md).</span></span> <span data-ttu-id="1a83d-122">Sie können die Sitzungskonfigurationsdatei jederzeit löschen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-122">You may delete the session configuration file at any time.</span></span> <span data-ttu-id="1a83d-123">Die Konfigurationsdatei wird nach der Registrierung des Endpunkts nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="1a83d-123">The configuration file isn't used after registration of the endpoint.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="1a83d-124">Konfigurieren mehrerer Computer mit DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="1a83d-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="1a83d-125">Wenn Sie JEA auf mehreren Computern bereitstellen, bietet sich als einfachstes Bereitstellungsmodell die Verwendung der JEA-[DSC-](../../../dsc/overview/overview.md)-Ressource (Desired State Configuration) an, um JEA schnell und konsistent auf jedem Computer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-125">When deploying JEA on multiple machines, the simplest deployment model uses the JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="1a83d-126">Um JEA mit DSC bereitzustellen, müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="1a83d-126">To deploy JEA with DSC, ensure the following prerequisites are met:</span></span>

- <span data-ttu-id="1a83d-127">Eine oder mehrere Rollenfunktionen wurden erstellt und einem PowerShell-Modul hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1a83d-127">One or more role capabilities have been authored and added to a PowerShell module.</span></span>
- <span data-ttu-id="1a83d-128">Das PowerShell-Modul, das die Rollen enthält, ist auf einer (schreibgeschützten) Freigabe gespeichert, auf die von jedem Computer aus zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="1a83d-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="1a83d-129">Die Einstellungen für die Sitzungskonfiguration wurden festgelegt.</span><span class="sxs-lookup"><span data-stu-id="1a83d-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="1a83d-130">Sie müssen keine Sitzungskonfigurationsdatei erstellen, um die JEA-DSC-Ressource zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="1a83d-130">You don't need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="1a83d-131">Sie verfügen über Anmeldeinformationen, die Verwaltungsaktionen auf allen Computern ermöglichen, oder Sie haben Zugriff auf einen DSC-Pullserver, um die Computer zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="1a83d-131">You have credentials that allow administrative actions on each machine or access to the DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="1a83d-132">Sie haben die [JEA-DSC-Ressourcen](https://github.com/powershell/JEA/tree/master/DSC%20Resource) heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-132">You've downloaded the [JEA DSC resource](https://github.com/powershell/JEA/tree/master/DSC%20Resource).</span></span>

<span data-ttu-id="1a83d-133">Erstellen Sie auf einem Zielcomputer (oder gegebenenfalls einem Pullserver) eine DSC-Konfiguration für Ihren JEA-Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="1a83d-133">Create a DSC configuration for your JEA endpoint on a target machine or pull server.</span></span> <span data-ttu-id="1a83d-134">In dieser Konfiguration definiert die **JustEnoughAdministration**-DSC-Ressource die Sitzungskonfigurationsdatei, und die **Dateiressource** kopiert die Rollenfunktionen aus der Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="1a83d-134">In this configuration, the **JustEnoughAdministration** DSC resource defines the session configuration file and the **File** resource copies the role capabilities from the file share.</span></span>

<span data-ttu-id="1a83d-135">Die folgenden Eigenschaften können mithilfe der DSC-Ressource konfiguriert werden:</span><span class="sxs-lookup"><span data-stu-id="1a83d-135">The following properties are configurable using the DSC resource:</span></span>

- <span data-ttu-id="1a83d-136">Rollendefinitionen</span><span class="sxs-lookup"><span data-stu-id="1a83d-136">Role Definitions</span></span>
- <span data-ttu-id="1a83d-137">Virtuelle Kontogruppen</span><span class="sxs-lookup"><span data-stu-id="1a83d-137">Virtual account groups</span></span>
- <span data-ttu-id="1a83d-138">Gruppenverwalteter Dienstkontoname</span><span class="sxs-lookup"><span data-stu-id="1a83d-138">Group-managed service account name</span></span>
- <span data-ttu-id="1a83d-139">Aufzeichnungsverzeichnis</span><span class="sxs-lookup"><span data-stu-id="1a83d-139">Transcript directory</span></span>
- <span data-ttu-id="1a83d-140">Benutzerlaufwerk</span><span class="sxs-lookup"><span data-stu-id="1a83d-140">User drive</span></span>
- <span data-ttu-id="1a83d-141">Regeln für bedingten Zugriff</span><span class="sxs-lookup"><span data-stu-id="1a83d-141">Conditional access rules</span></span>
- <span data-ttu-id="1a83d-142">Skripts zum Starten der JEA-Sitzung</span><span class="sxs-lookup"><span data-stu-id="1a83d-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="1a83d-143">Die Syntax für jede dieser Eigenschaften in einer DSC-Konfiguration stimmt mit Konfigurationsdatei der PowerShell-Sitzung überein.</span><span class="sxs-lookup"><span data-stu-id="1a83d-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="1a83d-144">Es folgt ein Beispiel einer DSC-Konfiguration für ein allgemeines Serverwartungsmodul.</span><span class="sxs-lookup"><span data-stu-id="1a83d-144">Below is a sample DSC configuration for a general server maintenance module.</span></span> <span data-ttu-id="1a83d-145">Dabei wird von einem gültigen PowerShell-Modul mit Rollenfunktionen ausgegangen, das sich auf der Dateifreigabe `\\myfileshare\JEA` befindet.</span><span class="sxs-lookup"><span data-stu-id="1a83d-145">It assumes that a valid PowerShell module containing role capabilities is located on the `\\myfileshare\JEA` file share.</span></span>

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

<span data-ttu-id="1a83d-146">Diese Konfiguration wird danach auf einem System angewendet. Dazu müssen Sie den [lokalen Konfigurations-Manager aufrufen ](/powershell/scripting/dsc/managing-nodes/metaConfig) oder die [Pullserverkonfiguration](/powershell/scripting/dsc/pull-server/pullServer) aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="1a83d-146">Next, the configuration is applied on a system by directly invoking the [Local Configuration Manager](/powershell/scripting/dsc/managing-nodes/metaConfig) or updating the [pull server configuration](/powershell/scripting/dsc/pull-server/pullServer).</span></span>

<span data-ttu-id="1a83d-147">Mithilfe der DSC-Ressource können Sie außerdem den **Microsoft.PowerShell**-Standardendpunkt ersetzen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-147">The DSC resource also allows you to replace the default **Microsoft.PowerShell** endpoint.</span></span> <span data-ttu-id="1a83d-148">Wenn dieser ersetzt wird, registriert die Ressource automatisch einen Sicherungsendpunkt namens **Microsoft.PowerShell.Restricted**.</span><span class="sxs-lookup"><span data-stu-id="1a83d-148">When replaced, the resource automatically registers a backup endpoint named **Microsoft.PowerShell.Restricted**.</span></span> <span data-ttu-id="1a83d-149">Der Sicherungsendpunkt verfügt über die Standard-WinRM-ACL, die Remotemanagementbenutzern und Mitgliedern der lokalen Administratorengruppe erlaubt, auf diesen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-149">The backup endpoint has the default WinRM ACL that allows Remote Management Users and local Administrators group members to access it.</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="1a83d-150">Aufheben der Registrierung von JEA-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="1a83d-150">Unregistering JEA configurations</span></span>

<span data-ttu-id="1a83d-151">Verwenden Sie das [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration)-Cmdlet, um einen JEA-Endpunkt von einem System zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-151">The [Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet removes a JEA endpoint.</span></span> <span data-ttu-id="1a83d-152">Das Aufheben der Registrierung eines JEA-Endpunkts verhindert, dass neue Benutzer neue JEA-Sitzungen auf dem System erstellen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-152">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span> <span data-ttu-id="1a83d-153">Sie können auch eine JEA-Konfiguration aktualisieren, indem Sie eine aktualisierte Sitzungskonfigurationsdatei erneut registrieren und den gleichen Endpunktnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="1a83d-153">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="1a83d-154">Wenn Sie die Registrierung eines JEA-Endpunkts aufheben, wird der WinRM-Dienst neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="1a83d-154">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span> <span data-ttu-id="1a83d-155">Dadurch werden die meisten aktuell ausgeführten Remoteverwaltungsvorgänge unterbrochen, z.B. andere PowerShell-Sitzungen, WMI-Aufrufe und einige Verwaltungstools.</span><span class="sxs-lookup"><span data-stu-id="1a83d-155">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span> <span data-ttu-id="1a83d-156">Heben Sie daher die Registrierung von PowerShell-Endpunkte nur während geplanter Wartungsfenster auf.</span><span class="sxs-lookup"><span data-stu-id="1a83d-156">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1a83d-157">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="1a83d-157">Next steps</span></span>

[<span data-ttu-id="1a83d-158">Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="1a83d-158">Test the JEA endpoint</span></span>](using-jea.md)
