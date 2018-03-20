---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Registrieren von JEA-Konfigurationen
ms.openlocfilehash: d6b007fed97be6470bfe4cf4d42f72cb4edc3a45
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="registering-jea-configurations"></a><span data-ttu-id="9f8d5-103">Registrieren von JEA-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="9f8d5-103">Registering JEA Configurations</span></span>

> <span data-ttu-id="9f8d5-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9f8d5-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9f8d5-105">Sobald Sie Ihre [Rollenfunktionen](role-capabilities.md) und die [Sitzungskonfigurationsdatei](session-configurations.md) erstellt haben, ist JEA einsatzbereit. Der letzte Schritt besteht darin, den JEA-Endpunkt zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-105">The last step before you can use JEA once you have your [role capabilities](role-capabilities.md) and [session configuration file](session-configurations.md) created is to register the JEA endpoint.</span></span>
<span data-ttu-id="9f8d5-106">Bei diesem Vorgang werden die Informationen der Sitzungskonfiguration auf das System angewendet, und der Endpunkt kann von Benutzern und Automatisierungsmodulen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-106">This process applies the session configuration information to the system and makes the endpoint available for use by users and automation engines.</span></span>

## <a name="single-machine-configuration"></a><span data-ttu-id="9f8d5-107">Einzelcomputerkonfiguration</span><span class="sxs-lookup"><span data-stu-id="9f8d5-107">Single machine configuration</span></span>

<span data-ttu-id="9f8d5-108">Sie können JEA für kleine Umgebungen bereitstellen, indem Sie die Konfigurationsdatei mithilfe des [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration)-Cmdlets registrieren.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-108">For small environments, you can deploy JEA by registering the session configuration file using the [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) cmdlet.</span></span>

<span data-ttu-id="9f8d5-109">Vergewissern Sie sich vor Beginn, dass die folgenden Voraussetzungen erfüllt sind:</span><span class="sxs-lookup"><span data-stu-id="9f8d5-109">Before you begin, ensure that the following prerequisites have been met:</span></span>
- <span data-ttu-id="9f8d5-110">Eine oder mehrere Rollen wurden erstellt und im Ordner „RoleCapabilities“ eines gültigen PowerShell-Moduls abgelegt.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-110">One or more roles has been created and placed in the 'RoleCapabilities' folder of a valid PowerShell module.</span></span>
- <span data-ttu-id="9f8d5-111">Eine Sitzungskonfigurationsdatei wurde erstellt und getestet.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-111">A session configuration file has been created and tested.</span></span>
- <span data-ttu-id="9f8d5-112">Der Benutzer, der die JEA-Konfiguration registriert, verfügt über Administratorrechte auf den Systemen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-112">The user registering the JEA configuration has administrator rights on the system(s).</span></span>

<span data-ttu-id="9f8d5-113">Sie müssen auch einen Namen für den JEA-Endpunkt auswählen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-113">You will also need to select a name for your JEA endpoint.</span></span>
<span data-ttu-id="9f8d5-114">Der Name des JEA-Endpunkts wird benötigt, wenn Benutzer mithilfe von JEA eine Verbindung mit dem System herstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-114">The name of the JEA endpoint will be required when users want to connect to the system using JEA.</span></span>
<span data-ttu-id="9f8d5-115">Sie können das [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration)-Cmdlet zum Überprüfen der Namen der vorhandenen Endpunkte auf dem System verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-115">You can use the [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet to check the names of existing endpoints on the system.</span></span>
<span data-ttu-id="9f8d5-116">Endpunkte, deren Name mit „microsoft“ beginnt, gehören normalerweise zum Funktionsumfang von Windows.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-116">Endpoints that start with 'microsoft' are typically shipped with Windows.</span></span>
<span data-ttu-id="9f8d5-117">Der Endpunkt „microsoft.powershell“ ist der Standardendpunkt, der verwendet wird, wenn eine Verbindung mit einem PowerShell-Remoteendpunkt hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-117">The 'microsoft.powershell' endpoint is the default endpoint used when connecting to a remote PowerShell endpoint.</span></span>

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

<span data-ttu-id="9f8d5-118">Wenn Sie einen entsprechenden Namen für den JEA-Endpunkt festgelegt haben, führen Sie den folgenden Befehl zum Registrieren des Endpunkts aus:</span><span class="sxs-lookup"><span data-stu-id="9f8d5-118">When you have determined an appropriate name for your JEA endpoint, run the following command to register the endpoint.</span></span>

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="9f8d5-119">Durch den oben angegebenen Befehl wird der WinRM-Dienst auf dem System neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-119">The above command will restart the WinRM service on the system.</span></span>
> <span data-ttu-id="9f8d5-120">Dadurch werden alle PowerShell-Remoting-Sitzungen sowie alle laufenden DSC-Konfigurationen beendet.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-120">This will terminate all PowerShell remoting sessions as well as any ongoing DSC configurations.</span></span>
> <span data-ttu-id="9f8d5-121">Schalten Sie nach Möglichkeit vor dem Ausführen des Befehls alle Produktionscomputern offline, um Unterbrechung des Geschäftsbetriebs zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-121">It is recommended that you take any production machines offline before running the command to avoid disrupting business operations.</span></span>

<span data-ttu-id="9f8d5-122">Wenn die Registrierung erfolgreich war, können Sie mit dem [Verwenden von JEA](using-jea.md) beginnen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-122">If registration was successful, you are ready to [use JEA](using-jea.md).</span></span>
<span data-ttu-id="9f8d5-123">Sie können die Sitzungskonfigurationsdatei jederzeit löschen. Sie wird nach der Registrierung nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-123">You may delete the session configuration file at any time; it is not used after registration.</span></span>

## <a name="multi-machine-configuration-with-dsc"></a><span data-ttu-id="9f8d5-124">Konfigurieren mehrerer Computer mit DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="9f8d5-124">Multi-machine configuration with DSC</span></span>

<span data-ttu-id="9f8d5-125">Wenn Sie JEA auf mehreren Computern bereitstellen, bietet sich als einfachstes Bereitstellungsmodell die Verwendung der JEA-[DSC-](https://msdn.microsoft.com/en-us/powershell/dsc/overview)-Ressource an, um JEA schnell und konsistent auf jedem Computer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-125">If you are deploying JEA on multiple machines, the simplest deployment model is to use the JEA [Desired State Configuration](https://msdn.microsoft.com/en-us/powershell/dsc/overview) resource to quickly and consistently deploy JEA on each machine.</span></span>

<span data-ttu-id="9f8d5-126">Wenn Sie JEA mit DSC bereitstellen möchten, müssen Sie sicherstellen, dass die folgenden erforderlichen Anforderungen erfüllt sind:</span><span class="sxs-lookup"><span data-stu-id="9f8d5-126">To deploy JEA with DSC, you will need to ensure the following prerequisites are met:</span></span>
- <span data-ttu-id="9f8d5-127">Eine oder mehrere Rollenfunktionen wurden erstellt und einem gültigen PowerShell-Modul hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-127">One or more role capabilities have been authored and added to a valid PowerShell module.</span></span>
- <span data-ttu-id="9f8d5-128">Das PowerShell-Modul, das die Rollen enthält, ist auf einer (schreibgeschützten) Freigabe gespeichert, auf die von jedem Computer aus zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-128">The PowerShell module containing the roles is stored on a (read-only) file share accessible by each machine.</span></span>
- <span data-ttu-id="9f8d5-129">Die Einstellungen für die Sitzungskonfiguration wurden festgelegt.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-129">Settings for the session configuration have been determined.</span></span> <span data-ttu-id="9f8d5-130">Sie müssen keine Sitzungskonfigurationsdatei erstellen, um die JEA-DSC-Ressource zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-130">You do not need to create a session configuration file when using the JEA DSC resource.</span></span>
- <span data-ttu-id="9f8d5-131">Sie verfügen über Anmeldeinformationen, mit denen Sie administrative Aktionen auf allen Computern ausführen können, oder Sie haben Zugriff auf einen DSC-Pullserver, um die Computer zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-131">You have credentials that will allow you to perform administrative actions on each machine, or have access to a DSC pull server used to manage the machines.</span></span>
- <span data-ttu-id="9f8d5-132">Sie haben die [JEA-DSC-Ressourcen](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource) heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-132">You have downloaded the [JEA DSC resource](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)</span></span>

<span data-ttu-id="9f8d5-133">Erstellen Sie auf einem Zielcomputer (oder gegebenenfalls einem Pullserver) eine DSC-Konfiguration für Ihren JEA-Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-133">On a target machine (or pull server, if you are using one), create a DSC configuration for your JEA endpoint.</span></span>
<span data-ttu-id="9f8d5-134">In dieser Konfiguration verwenden Sie die JustEnoughAdministration-DSC-Ressource, um die Sitzungskonfigurationsdatei einzurichten, und die Dateiressource, um die Rollenfunktionen von der Dateifreigabe zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-134">In this configuration, you will use the JustEnoughAdministration DSC resource to set up the session configuration file and the File resource to copy over the role capabilities from the file share.</span></span>

<span data-ttu-id="9f8d5-135">Die folgenden Eigenschaften können mithilfe der DSC-Ressource konfiguriert werden:</span><span class="sxs-lookup"><span data-stu-id="9f8d5-135">The following properties are configurable using the DSC resource:</span></span>
- <span data-ttu-id="9f8d5-136">Rollendefinitionen</span><span class="sxs-lookup"><span data-stu-id="9f8d5-136">Role Definitions</span></span>
- <span data-ttu-id="9f8d5-137">Virtuelle Kontogruppen</span><span class="sxs-lookup"><span data-stu-id="9f8d5-137">Virtual Account groups</span></span>
- <span data-ttu-id="9f8d5-138">Gruppenverwalteter Dienstkontoname</span><span class="sxs-lookup"><span data-stu-id="9f8d5-138">Group Managed Service Account name</span></span>
- <span data-ttu-id="9f8d5-139">Aufzeichnungsverzeichnis</span><span class="sxs-lookup"><span data-stu-id="9f8d5-139">Transcript directory</span></span>
- <span data-ttu-id="9f8d5-140">Benutzerlaufwerk</span><span class="sxs-lookup"><span data-stu-id="9f8d5-140">User drive</span></span>
- <span data-ttu-id="9f8d5-141">Regeln für bedingten Zugriff</span><span class="sxs-lookup"><span data-stu-id="9f8d5-141">Conditional access rules</span></span>
- <span data-ttu-id="9f8d5-142">Skripts zum Starten der JEA-Sitzung</span><span class="sxs-lookup"><span data-stu-id="9f8d5-142">Startup scripts for the JEA session</span></span>

<span data-ttu-id="9f8d5-143">Die Syntax für jede dieser Eigenschaften in einer DSC-Konfiguration stimmt mit Konfigurationsdatei der PowerShell-Sitzung überein.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-143">The syntax for each of these properties in a DSC configuration is consistent with the PowerShell session configuration file.</span></span>

<span data-ttu-id="9f8d5-144">Es folgt ein Beispiel einer DSC-Konfiguration für ein allgemeines Serverwartungsmodul.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-144">Below is a sample DSC configuration for a general server maintenance module.</span></span>

<span data-ttu-id="9f8d5-145">Dabei wird von einem gültigen PowerShell-Modul mit Rollenfunktionen in einem Unterordner „RoleCapabilities“ ausgegangen, das sich auf der Dateifreigabe „\\\\Myfileshare\\JEA“ befindet.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-145">It assumes that a valid PowerShell module containing role capabilities in a 'RoleCapabilities' subfolder is located on the '\\\\myfileshare\\JEA' file share.</span></span>


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

<span data-ttu-id="9f8d5-146">Diese Konfiguration kann direkt auf einem System angewendet werden. Dazu müssen Sie den [lokalen Konfigurations-Managers aufrufen ](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) oder die [Pullserverkonfiguration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-146">This configuration can then be applied on a system by [directly invoking the Local Configuration Manager](https://msdn.microsoft.com/en-us/powershell/dsc/metaconfig) or updating the [pull server configuration](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver).</span></span>

<span data-ttu-id="9f8d5-147">Mithilfe der DSC-Ressource können Sie außerdem den standardmäßigen Microsoft.PowerShell-Remoting-Endpunkt ersetzen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-147">The DSC resource also allows you to replace the default Microsoft.PowerShell remoting endpoint.</span></span>
<span data-ttu-id="9f8d5-148">In diesem Fall registriert die Ressource automatisch einen nicht eingeschränkten Sicherungsendpunkt mit dem Namen „Microsoft.PowerShell.Restricted“, der über die Standard-WinRM-ACL verfügt. (Remotemanagementbenutzer und Mitglieder lokaler Administratorengruppen erhalten auf diese Weise Zugriff.)</span><span class="sxs-lookup"><span data-stu-id="9f8d5-148">If you do this, the resource will automatically register a backup unconstrainted endpoint named "Microsoft.PowerShell.Restricted" which has the default WinRM ACL (allowing Remote Management Users and local Administrators group members to access it).</span></span>

## <a name="unregistering-jea-configurations"></a><span data-ttu-id="9f8d5-149">Aufheben der Registrierung von JEA-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="9f8d5-149">Unregistering JEA configurations</span></span>

<span data-ttu-id="9f8d5-150">Verwenden Sie das [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration)-Cmdlet, um einen JEA-Endpunkt von einem System zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-150">To remove a JEA endpoint on a system, use the [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) cmdlet.</span></span>
<span data-ttu-id="9f8d5-151">Durch das Aufheben der Registrierung eines JEA-Endpunkts wird verhindert, dass neue Benutzer neue JEA-Sitzungen auf dem System erstellen.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-151">Unregistering a JEA endpoint will prevent new users from creating new JEA sessions on the system.</span></span>
<span data-ttu-id="9f8d5-152">Sie können auch eine JEA-Konfiguration aktualisieren, indem Sie eine aktualisierte Sitzungskonfigurationsdatei erneut registrieren und den gleichen Endpunktnamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-152">It also allows you to update a JEA configuration by re-registering an updated session configuration file using the same endpoint name.</span></span>

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> <span data-ttu-id="9f8d5-153">Wenn Sie die Registrierung eines JEA-Endpunkts aufheben, wird der WinRM-Dienst neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-153">Unregistering a JEA endpoint will cause the WinRM service to restart.</span></span>
> <span data-ttu-id="9f8d5-154">Dadurch werden die meisten aktuell ausgeführten Remoteverwaltungsvorgänge unterbrochen, darunter andere PowerShell-Sitzungen, WMI-Aufrufe und einige Verwaltungstools.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-154">This will interrupt most remote management operations in progress, including other PowerShell sessions, WMI invocations, and some management tools.</span></span>
> <span data-ttu-id="9f8d5-155">Heben Sie daher die Registrierung von PowerShell-Endpunkte nur während geplanter Wartungsfenster auf.</span><span class="sxs-lookup"><span data-stu-id="9f8d5-155">Only unregister PowerShell endpoints during planned maintenance windows.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9f8d5-156">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="9f8d5-156">Next steps</span></span>

- [<span data-ttu-id="9f8d5-157">Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="9f8d5-157">Test the JEA endpoint</span></span>](using-jea.md)

