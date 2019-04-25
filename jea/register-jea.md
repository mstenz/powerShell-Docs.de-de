---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Registrieren von JEA-Konfigurationen
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084826"
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="19593-103">Registrieren von JEA-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="19593-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="19593-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="19593-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="19593-105">Nachdem Sie Ihre [Rollenfunktionen](role-capabilities.md) und die [Sitzungskonfigurationsdatei](session-configurations.md) erstellt haben, müssen Sie nur noch den JEA-Endpunkt registrieren, bevor Sie JEA verwenden können.</span><span class="sxs-lookup"><span data-stu-id="19593-105">Once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created, the last step before you can use JEA is to register the JEA endpoint.</span></span>
<span data-ttu-id="19593-106">Das Registrieren des JEA-Endpunkts beim System stellt den Endpunkt für Benutzer und Automatisierungs-Engines zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="19593-106">Registering the JEA endpoint with the system makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="19593-107">Einzelcomputerkonfiguration</span><span class="sxs-lookup"><span data-stu-id="19593-107">Single machine configuration</span></span>

<span data-ttu-id="19593-108">Sie können JEA für kleine Umgebungen bereitstellen, indem Sie die Konfigurationsdatei mithilfe des [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration)-Cmdlets registrieren.</span><span class="sxs-lookup"><span data-stu-id="19593-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="19593-109">Vergewissern Sie sich vor Beginn, dass die folgenden Voraussetzungen erfüllt sind:</span><span class="sxs-lookup"><span data-stu-id="19593-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="19593-110">Eine oder mehrere Rollen wurden erstellt und im Ordner „RoleCapabilities“ eines gültigen PowerShell-Moduls abgelegt.</span><span class="sxs-lookup"><span data-stu-id="19593-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="19593-111">Eine Sitzungskonfigurationsdatei wurde erstellt und getestet.</span><span class="sxs-lookup"><span data-stu-id="19593-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="19593-112">Der Benutzer, der die JEA-Konfiguration registriert, verfügt über Administratorrechte auf den Systemen.</span><span class="sxs-lookup"><span data-stu-id="19593-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="19593-113">Sie müssen auch einen Namen für den JEA-Endpunkt auswählen.</span><span class="sxs-lookup"><span data-stu-id="19593-113">You also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="19593-114">Der Name des JEA-Endpunkts wird benötigt, wenn Benutzer mit JEA eine Verbindung mit dem System herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="19593-114">The name of the JEA endpoint is required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="19593-115">Sie können das [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet zum Überprüfen der Namen der vorhandenen Endpunkte auf dem System verwenden.</span><span class="sxs-lookup"><span data-stu-id="19593-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="19593-116">Endpunkte, deren Name mit „microsoft“ beginnt, gehören normalerweise zum Funktionsumfang von Windows.</span><span class="sxs-lookup"><span data-stu-id="19593-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="19593-117">Der Endpunkt „microsoft.powershell“ ist der Standardendpunkt, der verwendet wird, wenn eine Verbindung mit einem PowerShell-Remoteendpunkt hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="19593-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="19593-118">Wenn Sie einen entsprechenden Namen für den JEA-Endpunkt festgelegt haben, führen Sie den folgenden Befehl zum Registrieren des Endpunkts aus:</span><span class="sxs-lookup"><span data-stu-id="19593-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="19593-119">Der oben angegebene Befehl startet den WinRM-Dienst im System neu.</span><span class="sxs-lookup"><span data-stu-id="19593-119">The above command restarts the WinRM service on the system.</span></span>
> <span data-ttu-id="19593-120">Dadurch werden alle PowerShell-Remotingsitzungen und alle laufenden DSC-Konfigurationen beendet.</span><span class="sxs-lookup"><span data-stu-id="19593-120">This terminates all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="19593-121">Schalten Sie nach Möglichkeit vor dem Ausführen des Befehls alle Produktionscomputern offline, um Unterbrechung des Geschäftsbetriebs zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="19593-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="19593-122">Wenn die Registrierung erfolgreich war, können Sie [JEA direkt verwenden](using-jea.md).</span><span class="sxs-lookup"><span data-stu-id="19593-122">If registration is successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="19593-123">Sie können die Sitzungskonfigurationsdatei jederzeit löschen. Sie wird nach der Registrierung des Endpunkts nicht mehr benötigt.</span><span class="sxs-lookup"><span data-stu-id="19593-123">You may delete the session configuration file at any time; it is not used after registration of the end point.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="19593-124">Konfigurieren mehrerer Computer mit DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="19593-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="19593-125">Wenn Sie JEA auf mehreren Computern bereitstellen, bietet sich als einfachstes Bereitstellungsmodell die Verwendung der JEA-[DSC-](https://msdn.microsoft.com/powershell/dsc/overview)-Ressource an, um JEA schnell und konsistent auf jedem Computer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="19593-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="19593-126">Um JEA mit DSC bereitzustellen, müssen die folgenden Voraussetzungen erfüllt sein:</span><span class="sxs-lookup"><span data-stu-id="19593-126">To deploy JEA with DSC, you need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="19593-127">Eine oder mehrere Rollenfunktionen wurden erstellt und einem gültigen PowerShell-Modul hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="19593-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="19593-128">Das PowerShell-Modul, das die Rollen enthält, ist auf einer (schreibgeschützten) Freigabe gespeichert, auf die von jedem Computer aus zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="19593-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="19593-129">Die Einstellungen für die Sitzungskonfiguration wurden festgelegt.</span><span class="sxs-lookup"><span data-stu-id="19593-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="19593-130">Sie müssen keine Sitzungskonfigurationsdatei erstellen, um die JEA-DSC-Ressource zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="19593-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="19593-131">Sie verfügen über Anmeldeinformationen, mit denen Sie Verwaltungsaktionen auf allen Computern ausführen können, oder Sie haben Zugriff auf einen DSC-Pullserver, um die Computer zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="19593-131">You have credentials that allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="19593-132">Sie haben die [JEA-DSC-Ressourcen](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource) heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="19593-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="19593-133">Erstellen Sie auf einem Zielcomputer (oder gegebenenfalls einem Pullserver) eine DSC-Konfiguration für Ihren JEA-Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="19593-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="19593-134">In dieser Konfiguration verwenden Sie die JustEnoughAdministration-DSC-Ressource zum Einrichten der Sitzungskonfigurationsdatei und die Dateiressource zum Kopieren der Rollenfunktionen aus der Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="19593-134">In this configuration, you use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="19593-135">Die folgenden Eigenschaften können mithilfe der DSC-Ressource konfiguriert werden:</span><span class="sxs-lookup"><span data-stu-id="19593-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="19593-136">Rollendefinitionen</span><span class="sxs-lookup"><span data-stu-id="19593-136">Role Definitions</span></span>
- <span data-ttu-id="19593-137">Virtuelle Kontogruppen</span><span class="sxs-lookup"><span data-stu-id="19593-137">Virtual Account groups</span></span>
- <span data-ttu-id="19593-138">Gruppenverwalteter Dienstkontoname</span><span class="sxs-lookup"><span data-stu-id="19593-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="19593-139">Aufzeichnungsverzeichnis</span><span class="sxs-lookup"><span data-stu-id="19593-139">Transcript directory</span></span>
- <span data-ttu-id="19593-140">Benutzerlaufwerk</span><span class="sxs-lookup"><span data-stu-id="19593-140">User drive</span></span>
- <span data-ttu-id="19593-141">Regeln für bedingten Zugriff</span><span class="sxs-lookup"><span data-stu-id="19593-141">Conditional access rules</span></span>
- <span data-ttu-id="19593-142">Skripts zum Starten der JEA-Sitzung</span><span class="sxs-lookup"><span data-stu-id="19593-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="19593-143">Die Syntax für jede dieser Eigenschaften in einer DSC-Konfiguration stimmt mit Konfigurationsdatei der PowerShell-Sitzung überein.</span><span class="sxs-lookup"><span data-stu-id="19593-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="19593-144">Es folgt ein Beispiel einer DSC-Konfiguration für ein allgemeines Serverwartungsmodul.</span><span class="sxs-lookup"><span data-stu-id="19593-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="19593-145">Dabei wird von einem gültigen PowerShell-Modul mit Rollenfunktionen in einem Unterordner „RoleCapabilities“ ausgegangen, das sich auf der Dateifreigabe „\\\\Myfileshare\\JEA“ befindet.</span><span class="sxs-lookup"><span data-stu-id="19593-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="19593-146">Diese Konfiguration kann direkt auf einem System angewendet werden. Dazu müssen Sie den [lokalen Konfigurations-Managers aufrufen ](https://msdn.microsoft.com/powershell/dsc/metaconfig) oder die [Pullserverkonfiguration](https://msdn.microsoft.com/powershell/dsc/pullserver) aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="19593-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="19593-147">Mithilfe der DSC-Ressource können Sie außerdem den standardmäßigen Microsoft.PowerShell-Remoting-Endpunkt ersetzen.</span><span class="sxs-lookup"><span data-stu-id="19593-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="19593-148">In diesem Fall registriert die Ressource automatisch einen nicht eingeschränkten Sicherungsendpunkt mit dem Namen „Microsoft.PowerShell.Restricted“, der über die Standard-WinRM-ACL verfügt. Benutzer der Remoteverwaltung und Mitglieder lokaler Administratorengruppen erhalten so Zugriff.</span><span class="sxs-lookup"><span data-stu-id="19593-148">If you do this, the resource automatically registers a backup unconstrained endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="19593-149">Aufheben der Registrierung von JEA-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="19593-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="19593-150">Verwenden Sie das [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration)-Cmdlet, um einen JEA-Endpunkt von einem System zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="19593-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="19593-151">Das Aufheben der Registrierung eines JEA-Endpunkts verhindert, dass neue Benutzer neue JEA-Sitzungen auf dem System erstellen.</span><span class="sxs-lookup"><span data-stu-id="19593-151">Unregistering a JEA endpoint prevents new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="19593-152">Sie können auch eine JEA-Konfiguration aktualisieren, indem Sie eine aktualisierte Sitzungskonfigurationsdatei erneut registrieren und den gleichen Endpunktnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="19593-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="19593-153">Wenn Sie die Registrierung eines JEA-Endpunkts aufheben, wird der WinRM-Dienst neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="19593-153">Unregistering a JEA endpoint causes the WinRM service to restart.</span></span>
> <span data-ttu-id="19593-154">Dadurch werden die meisten aktuell ausgeführten Remoteverwaltungsvorgänge unterbrochen, z.B. andere PowerShell-Sitzungen, WMI-Aufrufe und einige Verwaltungstools.</span><span class="sxs-lookup"><span data-stu-id="19593-154">This interrupts most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="19593-155">Heben Sie daher die Registrierung von PowerShell-Endpunkte nur während geplanter Wartungsfenster auf.</span><span class="sxs-lookup"><span data-stu-id="19593-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="19593-156">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="19593-156">Next steps</span></span>

- [<span data-ttu-id="19593-157">Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="19593-157">Test the JEA endpoint</span></span>](using-jea.md)
