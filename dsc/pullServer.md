---
ms.date: 2018-02-02
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC-Pulldienst
ms.openlocfilehash: d5e24dcc093c73d8ebbaa618517193dacc4f2aaf
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="82064-103">Desired State Configuration – Pulldienst</span><span class="sxs-lookup"><span data-stu-id="82064-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="82064-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="82064-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="82064-105">Der lokale Konfigurations-Manager kann zentral mithilfe einer Pulldienstlösung verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="82064-105">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="82064-106">Bei diesem Ansatz wird der verwaltete Knoten bei einem Dienst registriert und in den LCM-Einstellungen einer Konfiguration zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="82064-106">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="82064-107">Die Konfiguration und alle DSC-Ressourcen, die als Abhängigkeiten für die Konfiguration erforderlich sind, werden auf den Computer heruntergeladen und von LCM zum Verwalten der Konfiguration verwendet.</span><span class="sxs-lookup"><span data-stu-id="82064-107">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="82064-108">Informationen über den Status des verwalteten Computers werden zur Berichterstellung auf den Dienst hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="82064-108">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="82064-109">Dieses Konzept wird als "Pulldienst" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="82064-109">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="82064-110">Folgende Optionen sind zurzeit für den Pulldienst verfügbar:</span><span class="sxs-lookup"><span data-stu-id="82064-110">The current options for pull service include:</span></span>

- <span data-ttu-id="82064-111">Azure Automation DSC-Dienst (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="82064-111">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="82064-112">Ein Pulldienst bei der Ausführung unter Windows Server</span><span class="sxs-lookup"><span data-stu-id="82064-112">A pull service running on Windows Server</span></span>
- <span data-ttu-id="82064-113">Von der Community verwaltete Open-Source-Lösungen</span><span class="sxs-lookup"><span data-stu-id="82064-113">Community maintained open source solutions</span></span>
- <span data-ttu-id="82064-114">Eine SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="82064-114">An SMB share</span></span>

<span data-ttu-id="82064-115">**Die empfohlene Lösung** und die Option mit den meisten verfügbaren Features ist [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="82064-115">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="82064-116">Der Azure-Dienst kann Knoten lokal in privaten Rechenzentren oder in öffentlichen Clouds wie Azure und AWS verwalten.</span><span class="sxs-lookup"><span data-stu-id="82064-116">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="82064-117">Für private Umgebungen, in denen Server keine direkte Verbindung mit dem Internet herstellen können, sollten Sie die Begrenzung des ausgehenden Datenverkehrs auf den veröffentlichten Azure-IP-Adressbereich in Betracht ziehen. Informationen hierzu finden Sie unter [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653) (IP-Adressbereiche für Azure-Rechenzentren).</span><span class="sxs-lookup"><span data-stu-id="82064-117">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="82064-118">Features des Onlinediensts, die im Pulldienst unter Windows Server zurzeit nicht verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="82064-118">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="82064-119">Verschlüsselung aller Daten während der Übertragung und im Ruhezustand</span><span class="sxs-lookup"><span data-stu-id="82064-119">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="82064-120">Automatische Erstellung und Verwaltung von Clientzertifikaten</span><span class="sxs-lookup"><span data-stu-id="82064-120">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="82064-121">Speicherung von Geheimnissen zur zentralen Verwaltung von [Kennwörtern/Anmeldeinformationen](https://docs.microsoft.com/en-us/azure/automation/automation-credentials) oder [Variablen](https://docs.microsoft.com/en-us/azure/automation/automation-variables) wie z.B. Servernamen oder Verbindungszeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="82064-121">Secrets store for centrally managing [passwords/credentials](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), or [variables](https://docs.microsoft.com/en-us/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="82064-122">Zentrale Verwaltung der [LCM-Konfiguration](metaConfig.md#basic-settings) für Knoten</span><span class="sxs-lookup"><span data-stu-id="82064-122">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="82064-123">Zentrale Zuweisung von Konfigurationen zu Clientknoten</span><span class="sxs-lookup"><span data-stu-id="82064-123">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="82064-124">Freigabe von Konfigurationsänderungen für Canarygruppen zum Durchführen von Tests vor Einführung in die Produktion</span><span class="sxs-lookup"><span data-stu-id="82064-124">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="82064-125">Grafische Berichterstellung</span><span class="sxs-lookup"><span data-stu-id="82064-125">Graphical reporting</span></span>
  - <span data-ttu-id="82064-126">Statusdetails auf der Granularitätsstufe von DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="82064-126">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="82064-127">Ausführliche Fehlermeldungen von Clientcomputern für die Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="82064-127">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="82064-128">[Integration in Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) für Warnungen, automatisierte Tasks, Android-/iOS-App für Berichte und Warnungen</span><span class="sxs-lookup"><span data-stu-id="82064-128">[Integration with Azure Log Analytics](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="82064-129">DSC-Pulldienst in Windows Server</span><span class="sxs-lookup"><span data-stu-id="82064-129">DSC pull service in Windows Server</span></span>

<span data-ttu-id="82064-130">Es ist möglich, einen Pulldienst für die Ausführung unter Windows Server zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="82064-130">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="82064-131">Bitte beachten Sie, dass die in Windows Server enthaltene Pulldienstlösung nur die Funktionen zum Speichern von Konfigurationen/Modulen für den Download und das Erfassen von Berichtsdaten in einer Datenbank umfasst.</span><span class="sxs-lookup"><span data-stu-id="82064-131">Please be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="82064-132">Sie umfasst viele der Funktionen nicht, die vom Dienst in Azure bereitgestellt werden, und stellt daher kein gutes Tool dar, um den Einsatz des Diensts zu bewerten.</span><span class="sxs-lookup"><span data-stu-id="82064-132">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="82064-133">Der in Windows Server angebotene Pulldienst ist ein Webdienst in IIS, der DSC-Konfigurationsdateien mithilfe einer OData-Schnittstelle für Zielknoten verfügbar macht, wenn die Zielknoten diese anfordern.</span><span class="sxs-lookup"><span data-stu-id="82064-133">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="82064-134">Anforderungen für die Verwendung eines Pullservers:</span><span class="sxs-lookup"><span data-stu-id="82064-134">Requirements for using a pull server:</span></span>

- <span data-ttu-id="82064-135">Ein Server mit:</span><span class="sxs-lookup"><span data-stu-id="82064-135">A server running:</span></span>
  - <span data-ttu-id="82064-136">WMF/PowerShell 5.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="82064-136">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="82064-137">IIS-Serverrolle</span><span class="sxs-lookup"><span data-stu-id="82064-137">IIS server role</span></span>
  - <span data-ttu-id="82064-138">DSC-Dienst</span><span class="sxs-lookup"><span data-stu-id="82064-138">DSC Service</span></span>
- <span data-ttu-id="82064-139">Im Idealfall eine Möglichkeit zum Generieren eines Zertifikats, um die an den lokalen Konfigurations-Manager (LCM) auf Zielknoten übergebenen Anmeldeinformationen abzusichern</span><span class="sxs-lookup"><span data-stu-id="82064-139">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="82064-140">Die beste Möglichkeit, Windows Server zum Hosten eines Pulldiensts zu konfigurieren, ist die Verwendung einer DSC-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="82064-140">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="82064-141">Ein Beispielskript finden Sie unten.</span><span class="sxs-lookup"><span data-stu-id="82064-141">An example script is provided below.</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="82064-142">Verwenden der xDSCWebService-Ressource</span><span class="sxs-lookup"><span data-stu-id="82064-142">Using the xDSCWebService resource</span></span>

<span data-ttu-id="82064-143">Die einfachste Möglichkeit einen Webpullserver einzurichten, ist die Verwendung der Ressource „xWebService“ im Modul „xPSDesiredStateConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="82064-143">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="82064-144">Die folgenden Schritte erläutern, wie Sie die Ressource in einer Konfiguration verwenden, die den Webdienst einrichtet.</span><span class="sxs-lookup"><span data-stu-id="82064-144">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="82064-145">Rufen Sie das Cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) auf, um das Modul **xPSDesiredStateConfiguration** zu installieren.</span><span class="sxs-lookup"><span data-stu-id="82064-145">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="82064-146">**Hinweis**: **Install-Module** ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 ist.</span><span class="sxs-lookup"><span data-stu-id="82064-146">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="82064-147">Das Modul **PowerShellGet** für PowerShell 3.0 und 4.0 können Sie unter [PowerShell-Module „PackageManagement“ – Vorschau](https://www.microsoft.com/en-us/download/details.aspx?id=49186) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="82064-147">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="82064-148">Rufen Sie ein SSL-Zertifikat für den DSC-Pullserver von einer vertrauenswürdigen Zertifizierungsstelle innerhalb Ihrer Organisation oder von einer öffentlichen Zertifizierungsstelle ab.</span><span class="sxs-lookup"><span data-stu-id="82064-148">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="82064-149">Das von der Zertifizierungsstelle empfangene Zertifikat weist normalerweise das PFX-Format auf.</span><span class="sxs-lookup"><span data-stu-id="82064-149">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="82064-150">Installieren Sie auf dem Knoten, der als DSC-Pullserver fungieren soll, das Zertifikat am Standardspeicherort, also normalerweise unter „CERT:\LocalMachine\My“.</span><span class="sxs-lookup"><span data-stu-id="82064-150">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="82064-151">Notieren Sie sich den Zertifikatfingerabdruck.</span><span class="sxs-lookup"><span data-stu-id="82064-151">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="82064-152">Wählen Sie eine GUID als der Registrierungsschlüssel aus.</span><span class="sxs-lookup"><span data-stu-id="82064-152">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="82064-153">Um einen mithilfe von PowerShell zu generieren, geben Sie ``` [guid]::newGuid()``` oder ```New-Guid``` an der PS-Eingabeaufforderung ein, und drücken Sie anschließend die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="82064-153">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="82064-154">Dieser Schlüssel wird von Clientknoten bei der Registrierung als gemeinsamer Schlüssel zum Authentifizieren verwendet.</span><span class="sxs-lookup"><span data-stu-id="82064-154">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="82064-155">Weitere Informationen finden Sie weiter unten im Abschnitt „Registrierungsschlüssel“.</span><span class="sxs-lookup"><span data-stu-id="82064-155">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="82064-156">Starten Sie (F5) in PowerShell ISE das folgende Konfigurationsskript (enthalten im Beispielordner des Moduls **xPSDesiredStateConfiguration** als Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="82064-156">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="82064-157">Dieses Skript richtet den Pullserver ein.</span><span class="sxs-lookup"><span data-stu-id="82064-157">This script sets up the pull server.</span></span>

```powershell
    configuration Sample_xDscPullServer
    {
        param
        (
                [string[]]$NodeName = 'localhost',

                [ValidateNotNullOrEmpty()]
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey
         )

         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName
         {
             WindowsFeature DSCServiceFeature
             {
                 Ensure = 'Present'
                 Name   = 'DSC-Service'
             }

             xDscWebService PSDSCPullServer
             {
                 Ensure                   = 'Present'
                 EndpointName             = 'PSDSCPullServer'
                 Port                     = 8080
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer"
                 CertificateThumbPrint    = $certificateThumbPrint
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'
                 UseSecurityBestPractices = $false
             }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }

```

1. <span data-ttu-id="82064-158">Führen Sie die Konfiguration aus, und übergeben Sie als Parameter **certificateThumbPrint** den Fingerabdruck des SSL-Zertifikats und als Parameter **RegistrationKey** einen GUID-Registrierungschlüssel:</span><span class="sxs-lookup"><span data-stu-id="82064-158">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store 
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose

```

#### <a name="registration-key"></a><span data-ttu-id="82064-159">Registrierungsschlüssel</span><span class="sxs-lookup"><span data-stu-id="82064-159">Registration Key</span></span>

<span data-ttu-id="82064-160">Um zuzulassen, dass Clientknoten sich beim Server registrieren und Konfigurationsnamen anstelle einer Konfigurations-ID verwenden können, wird ein von der oben beschriebenen Konfiguration erstellter Registrierungsschlüssel in einer Datei namens `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="82064-160">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="82064-161">Der Registrierungsschlüssel fungiert als ein gemeinsamer geheimer Schlüssel, der vom Client während der anfänglichen Registrierung beim Pullserver verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="82064-161">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="82064-162">Der Client generiert ein selbstsigniertes Zertifikat, das nach der erfolgreich abgeschlossenen Registrierung zur eindeutigen Authentifizierung beim Pullserver verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="82064-162">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="82064-163">Der Fingerabdruck dieses Zertifikats wird lokal gespeichert und der URL des Pullservers zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="82064-163">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="82064-164">**Hinweis**: Registrierungsschlüssel werden in PowerShell 4.0 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="82064-164">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="82064-165">Zum Konfigurieren eines Knotens zur Authentifizierung beim Pullserver muss der Registrierungsschlüssel in der Metakonfiguration für alle Zielknoten enthalten sein, die sich bei diesem Pullserver registrieren.</span><span class="sxs-lookup"><span data-stu-id="82064-165">In order to configure a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="82064-166">Beachten Sie, dass **RegistrationKey** aus der unten stehenden Metakonfiguration entfernt wird, nachdem der Zielcomputer erfolgreich registriert wurde, und dass der Wert „140a952b-b9d6-406b-b416-e0f759c9c0e4“ dem in der Datei „RegistrationKeys.txt“ auf dem Pullserver gespeicherten Wert entsprechen muss.</span><span class="sxs-lookup"><span data-stu-id="82064-166">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="82064-167">Behandeln Sie den Registrierungsschlüsselwert immer vertraulich, da sich jeder beliebige Zielcomputer mit diesem Schlüssel beim Pullserver registrieren könnte.</span><span class="sxs-lookup"><span data-stu-id="82064-167">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes


```

> <span data-ttu-id="82064-168">**Hinweis**: Der Abschnitt **ReportServerWeb** ermöglicht das Senden von Berichtsdaten an den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="82064-168">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="82064-169">Das Fehlen der Eigenschaft **ConfigurationID** in der Metakonfigurationsdatei bedeutet implizit, dass der Pullserver die V2-Version des Pullserverprotokolls unterstützt und somit eine Registrierung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="82064-169">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="82064-170">Umgekehrt bedeutet das Vorhandensein einer **ConfigurationID**, dass die V1-Version des Pullserverprotokolls verwendet wird und keine Registrierungsverarbeitung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="82064-170">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="82064-171">**Hinweis**: In einem PUSH-Szenario tritt in der aktuellen Version ein Fehler auf, aufgrund dessen es erforderlich ist, in der Metakonfigurationsdatei für Knoten, die noch nie bei einem Pullserver registriert wurden, die Eigenschaft „ConfigurationID“ zu definieren.</span><span class="sxs-lookup"><span data-stu-id="82064-171">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="82064-172">Dies erzwingt die Verwendung des V1-Pullserver-Protokolls verhindert Registrierungsfehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="82064-172">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="82064-173">Platzieren von Konfigurationen und Ressourcen</span><span class="sxs-lookup"><span data-stu-id="82064-173">Placing configurations and resources</span></span>

<span data-ttu-id="82064-174">Nach Abschluss des Pullserversetups befinden sich die von den Eigenschaften **ConfigurationPath** und **ModulePath** in der Pullserverkonfiguration definierten Ordner an dem Ort, an dem Module und Konfigurationen abgelegt werden, die für Zielknoten zum Abrufen verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="82064-174">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="82064-175">Diese Dateien müssen in einem bestimmten Format vorliegen, damit sie von den Pullservern ordnungsgemäß verarbeiten werden können.</span><span class="sxs-lookup"><span data-stu-id="82064-175">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="82064-176">Format des DSC-Ressourcenmodulpakets</span><span class="sxs-lookup"><span data-stu-id="82064-176">DSC resource module package format</span></span>

<span data-ttu-id="82064-177">Jedes Ressourcenmodul muss komprimiert und entsprechend dem folgenden Muster benannt werden: `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="82064-177">Each resource module needs to be zipped and named according the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="82064-178">Ein Modul namens „xWebAdminstration“ mit einer Modulversion 3.1.2.0 würde beispielsweise „xWebAdministration_3.2.1.0.zip“ heißen.</span><span class="sxs-lookup"><span data-stu-id="82064-178">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="82064-179">Jede Version eines Moduls muss in einer eigenen ZIP-Datei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="82064-179">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="82064-180">Da jede ZIP-Datei nur jeweils eine Version einer Ressource enthält, wird das in WMF 5.0 eingeführte das Modulformat, das mehrere Versionen in einem einzigen Verzeichnis ermöglicht, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="82064-180">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="82064-181">Das bedeutet, dass Sie vor dem Packen von DSC-Ressourcenmodulen für die Verwendung mit einem Pullserver eine kleine Änderung an der Verzeichnisstruktur vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="82064-181">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="82064-182">Das Standardformat für Module mit DSC-Ressourcen in WMF 5.0 ist: {Modulordner}\{Modulversion}\DscResources\{DSC-Ressourcenordner}\'.</span><span class="sxs-lookup"><span data-stu-id="82064-182">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="82064-183">Entfernen Sie vor dem Packen für den Pullserver einfach den Ordner **{Modulversion}**, damit der Pfad wie folgt geändert wird: {Modulordner}\DscResources\{DSC-Ressourcenordner}\'.</span><span class="sxs-lookup"><span data-stu-id="82064-183">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="82064-184">Komprimieren Sie den Odner nach dieser Änderung wie oben beschrieben, und speichern Sie die ZIP-Dateien im Ordner **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="82064-184">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="82064-185">Verwenden Sie `new-dscchecksum {module zip file}` zum Erstellen einer Prüfsummendatei für das neu hinzugefügte Modul.</span><span class="sxs-lookup"><span data-stu-id="82064-185">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="82064-186">MOF-Konfigurationsformat</span><span class="sxs-lookup"><span data-stu-id="82064-186">Configuration MOF format</span></span>

<span data-ttu-id="82064-187">Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="82064-187">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="82064-188">Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) auf.</span><span class="sxs-lookup"><span data-stu-id="82064-188">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span>
<span data-ttu-id="82064-189">Das Cmdlet verwendet einen **Path**-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet.</span><span class="sxs-lookup"><span data-stu-id="82064-189">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="82064-190">Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist.</span><span class="sxs-lookup"><span data-stu-id="82064-190">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="82064-191">Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.</span><span class="sxs-lookup"><span data-stu-id="82064-191">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="82064-192">Platzieren Sie die MOF-Dateien und die zugeordneten Prüfsummendateien im Ordner **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="82064-192">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="82064-193">**Hinweis**: Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82064-193">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="82064-194">Tools</span><span class="sxs-lookup"><span data-stu-id="82064-194">Tooling</span></span>

<span data-ttu-id="82064-195">Um das Einrichten, Überprüfen und Verwalten des Pullservers zu vereinfachen, enthält die neueste Version des Moduls „xPSDesiredStateConfiguration“ folgende Tools als Beispiele:</span><span class="sxs-lookup"><span data-stu-id="82064-195">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="82064-196">Ein Modul, das beim Packen von DSC-Ressourcenmodulen und Konfigurationsdateien zur Verwendung auf dem Pullserver hilft.</span><span class="sxs-lookup"><span data-stu-id="82064-196">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="82064-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="82064-197">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="82064-198">Beispiele unten:</span><span class="sxs-lookup"><span data-stu-id="82064-198">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="82064-199">Ein Skript, das den Pullserver überprüft, wurde ordnungsgemäß konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="82064-199">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="82064-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="82064-200">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="82064-201">Community-Lösungen für Pulldienste</span><span class="sxs-lookup"><span data-stu-id="82064-201">Community Solutions for Pull Service</span></span>

<span data-ttu-id="82064-202">Die DSC-Community hat mehrere Lösungen zum Implementieren des Pulldienstprotokolls erstellt.</span><span class="sxs-lookup"><span data-stu-id="82064-202">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="82064-203">Für lokale Umgebungen bieten diese Pulldienstfunktionen und die Möglichkeit, der Community mit inkrementellen Verbesserungen etwas zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="82064-203">For on-premises environments these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="82064-204">Tug</span><span class="sxs-lookup"><span data-stu-id="82064-204">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="82064-205">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="82064-205">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="82064-206">Pullclientkonfiguration</span><span class="sxs-lookup"><span data-stu-id="82064-206">Pull client configuration</span></span>

<span data-ttu-id="82064-207">In den folgenden Themen wird das Einrichten von Pullclients im Detail beschrieben:</span><span class="sxs-lookup"><span data-stu-id="82064-207">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="82064-208">Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="82064-208">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="82064-209">Einrichten eines DSC-Pullclients mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="82064-209">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="82064-210">Teilkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="82064-210">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="82064-211">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="82064-211">See also</span></span>

- [<span data-ttu-id="82064-212">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="82064-212">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="82064-213">Inkraftsetzung von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="82064-213">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="82064-214">Verwenden eines DSC-Berichtsservers</span><span class="sxs-lookup"><span data-stu-id="82064-214">Using a DSC report server</span></span>](reportServer.md)
