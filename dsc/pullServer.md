---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Webpullservers
ms.openlocfilehash: ffe5b1ae058b9757def30ad53019a1b61605a42a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a><span data-ttu-id="55830-103">Einrichten eines DSC-Webpullservers</span><span class="sxs-lookup"><span data-stu-id="55830-103">Setting up a DSC web pull server</span></span>

> <span data-ttu-id="55830-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="55830-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="55830-105">Ein DSC-Webpullserver ist ein Webdienst in IIS, der eine OData-Schnittstelle verwendet, um DSC-Konfigurationsdateien für Zielknoten zur Verfügung zu stellen, wenn sie von diesen Knoten angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="55830-105">A DSC web pull server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="55830-106">Anforderungen für die Verwendung eines Pullservers:</span><span class="sxs-lookup"><span data-stu-id="55830-106">Requirements for using a pull server:</span></span>

* <span data-ttu-id="55830-107">Ein Server mit:</span><span class="sxs-lookup"><span data-stu-id="55830-107">A server running:</span></span>
  - <span data-ttu-id="55830-108">WMF/PowerShell 5.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="55830-108">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="55830-109">IIS-Serverrolle</span><span class="sxs-lookup"><span data-stu-id="55830-109">IIS server role</span></span>
  - <span data-ttu-id="55830-110">DSC-Dienst</span><span class="sxs-lookup"><span data-stu-id="55830-110">DSC Service</span></span>
* <span data-ttu-id="55830-111">Im Idealfall eine Möglichkeit zum Generieren eines Zertifikats, um die an den lokalen Konfigurations-Manager (LCM) auf Zielknoten übergebenen Anmeldeinformationen abzusichern</span><span class="sxs-lookup"><span data-stu-id="55830-111">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="55830-112">Sie können die IIS-Serverrolle und den DSC-Dienst mit dem Assistenten zum Hinzufügen von Rollen und Features in Server Manager oder unter Verwendung von PowerShell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="55830-112">You can add the IIS server role and DSC Service with the Add Roles and Features wizard in Server Manager, or by using PowerShell.</span></span> <span data-ttu-id="55830-113">Die in diesem Thema enthaltenen Beispielskripts führen beide Schritte aus.</span><span class="sxs-lookup"><span data-stu-id="55830-113">The sample scripts included in this topic will handle both of these steps for you as well.</span></span>

## <a name="using-the-xwebservice-resource"></a><span data-ttu-id="55830-114">Verwenden der xWebService-Ressource</span><span class="sxs-lookup"><span data-stu-id="55830-114">Using the xWebService resource</span></span>
<span data-ttu-id="55830-115">Die einfachste Möglichkeit einen Webpullserver einzurichten, ist die Verwendung der Ressource „xWebService“ im Modul „xPSDesiredStateConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="55830-115">The easiest way to set up a web pull server is to use the xWebService resource, included in the xPSDesiredStateConfiguration module.</span></span> <span data-ttu-id="55830-116">Die folgenden Schritte erläutern, wie Sie die Ressource in einer Konfiguration verwenden, die den Webdienst einrichtet.</span><span class="sxs-lookup"><span data-stu-id="55830-116">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="55830-117">Rufen Sie das Cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) auf, um das Modul **xPSDesiredStateConfiguration** zu installieren.</span><span class="sxs-lookup"><span data-stu-id="55830-117">Call the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="55830-118">**Hinweis**: **Install-Module** ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 ist.</span><span class="sxs-lookup"><span data-stu-id="55830-118">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="55830-119">Das Modul **PowerShellGet** für PowerShell 3.0 und 4.0 können Sie unter [PowerShell-Module „PackageManagement“ – Vorschau](https://www.microsoft.com/en-us/download/details.aspx?id=49186) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="55830-119">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> 
1. <span data-ttu-id="55830-120">Rufen Sie ein SSL-Zertifikat für den DSC-Pullserver von einer vertrauenswürdigen Zertifizierungsstelle innerhalb Ihrer Organisation oder von einer öffentlichen Zertifizierungsstelle ab.</span><span class="sxs-lookup"><span data-stu-id="55830-120">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your orgnaization or a public authority.</span></span> <span data-ttu-id="55830-121">Das von der Zertifizierungsstelle empfangene Zertifikat weist normalerweise das PFX-Format auf.</span><span class="sxs-lookup"><span data-stu-id="55830-121">The certificate recieved from the authority is usually in the PFX format.</span></span> <span data-ttu-id="55830-122">Installieren Sie auf dem Knoten, der als DSC-Pullserver fungieren soll, das Zertifikat am Standardspeicherort, also normalerweise unter „CERT:\LocalMachine\My“.</span><span class="sxs-lookup"><span data-stu-id="55830-122">Install the certificate on the node that will become the DSC Pull server in the default location which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="55830-123">Notieren Sie sich den Zertifikatfingerabdruck.</span><span class="sxs-lookup"><span data-stu-id="55830-123">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="55830-124">Wählen Sie eine GUID als der Registrierungsschlüssel aus.</span><span class="sxs-lookup"><span data-stu-id="55830-124">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="55830-125">Um einen mithilfe von PowerShell zu generieren, geben Sie ``` [guid]::newGuid()``` oder ```New-Guid``` an der PS-Eingabeaufforderung ein, und drücken Sie anschließend die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="55830-125">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="55830-126">Dieser Schlüssel wird von Clientknoten bei der Registrierung als gemeinsamer Schlüssel zum Authentifizieren verwendet.</span><span class="sxs-lookup"><span data-stu-id="55830-126">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="55830-127">Weitere Informationen finden Sie weiter unten im Abschnitt „Registrierungsschlüssel“.</span><span class="sxs-lookup"><span data-stu-id="55830-127">For more information see the Registration Key section below.</span></span>
1. <span data-ttu-id="55830-128">Starten Sie (F5) in PowerShell ISE das folgende Konfigurationsskript (enthalten im Beispielordner des Moduls **xPSDesiredStateConfiguration** als Sample_xDscWebService.ps1).</span><span class="sxs-lookup"><span data-stu-id="55830-128">In the PowerShell ISE, start (F5) the following configuration script (included in the Example folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebService.ps1).</span></span> <span data-ttu-id="55830-129">Dieses Skript richtet den Pullserver ein.</span><span class="sxs-lookup"><span data-stu-id="55830-129">This script sets up the pull server.</span></span>
  
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

1. <span data-ttu-id="55830-130">Führen Sie die Konfiguration aus, und übergeben Sie als Parameter **certificateThumbPrint** den Fingerabdruck des SSL-Zertifikats und als Parameter **RegistrationKey** einen GUID-Registrierungschlüssel:</span><span class="sxs-lookup"><span data-stu-id="55830-130">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certifcates in your local store 
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

## <a name="registration-key"></a><span data-ttu-id="55830-131">Registrierungsschlüssel</span><span class="sxs-lookup"><span data-stu-id="55830-131">Registration Key</span></span>
<span data-ttu-id="55830-132">Um zuzulassen, dass Clientknoten sich beim Server registrieren und Konfigurationsnamen anstelle einer Konfigurations-ID verwenden können, wird ein von der oben beschriebenen Konfiguration erstellter Registrierungsschlüssel in einer Datei namens `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="55830-132">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key which was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="55830-133">Der Registrierungsschlüssel fungiert als ein gemeinsamer geheimer Schlüssel, der vom Client während der anfänglichen Registrierung beim Pullserver verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="55830-133">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="55830-134">Der Client generiert ein selbstsigniertes Zertifikat, das nach der erfolgreich abgeschlossenen Registrierung zur eindeutigen Authentifizierung beim Pullserver verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="55830-134">The client will generate a self-signed certificate which is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="55830-135">Der Fingerabdruck des Zertifikats wird lokal gespeichert und der URL des Pullservers zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="55830-135">The thumbprint of the this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="55830-136">**Hinweis**: Registrierungsschlüssel werden in PowerShell 4.0 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55830-136">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span> 

<span data-ttu-id="55830-137">Zum Konfigurieren des Knotens zur Authentifizierung beim Pullserver muss der Registrierungsschlüssel in der Metakonfiguration für alle Zielknoten enthalten sein, die sich bei diesem Pullserver registrieren.</span><span class="sxs-lookup"><span data-stu-id="55830-137">In order to configure the a node to authenticate with the pull server the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="55830-138">Beachten Sie, dass **RegistrationKey** aus der unten stehenden Metakonfiguration entfernt wird, nachdem der Zielcomputer erfolgreich registriert wurde, und dass der Wert „140a952b-b9d6-406b-b416-e0f759c9c0e4“ dem in der Datei „RegistrationKeys.txt“ auf dem Pullserver gespeicherten Wert entsprechen muss.</span><span class="sxs-lookup"><span data-stu-id="55830-138">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="55830-139">Behandeln Sie den Registrierungsschlüsselwert immer vertraulich, da sich jeder beliebige Zielcomputer mit diesem Schlüssel beim Pullserver registrieren könnte.</span><span class="sxs-lookup"><span data-stu-id="55830-139">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="55830-140">**Hinweis**: Der Abschnitt **ReportServerWeb** ermöglicht das Senden von Berichtsdaten an den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="55830-140">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span> 

<span data-ttu-id="55830-141">Das Fehlen der Eigenschaft **ConfigurationID** in der Metakonfigurationsdatei bedeutet implizit, dass der Pullserver die V2-Version des Pullserverprotokolls unterstützt und somit eine Registrierung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="55830-141">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="55830-142">Umgekehrt bedeutet das Vorhandensein einer **ConfigurationID**, dass die V1-Version des Pullserverprotokolls verwendet wird und keine Registrierungsverarbeitung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="55830-142">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="55830-143">**Hinweis**: In einem PUSH-Szenario tritt in der aktuellen Version ein Fehler auf, aufgrund dessen es erforderlich ist, in der Metakonfigurationsdatei für Knoten, die noch nie bei einem Pullserver registriert wurden, die Eigenschaft „ConfigurationID“ zu definieren.</span><span class="sxs-lookup"><span data-stu-id="55830-143">**Note**: In a PUSH scenario, a bug exists in the current relase that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="55830-144">Dies erzwingt die Verwendung des V1-Pullserver-Protokolls verhindert Registrierungsfehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="55830-144">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="55830-145">Platzieren von Konfigurationen und Ressourcen</span><span class="sxs-lookup"><span data-stu-id="55830-145">Placing configurations and resources</span></span>

<span data-ttu-id="55830-146">Nach Abschluss des Pullserversetups befinden sich die von den Eigenschaften **ConfigurationPath** und **ModulePath** in der Pullserverkonfiguration definierten Ordner an dem Ort, an dem Module und Konfigurationen abgelegt werden, die für Zielknoten zum Abrufen verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="55830-146">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="55830-147">Diese Dateien müssen in einem bestimmten Format vorliegen, damit sie von den Pullservern ordnungsgemäß verarbeiten werden können.</span><span class="sxs-lookup"><span data-stu-id="55830-147">These files need to be in a specific format in order for the pull server to correctly process them.</span></span> 

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="55830-148">Format des DSC-Ressourcenmodulpakets</span><span class="sxs-lookup"><span data-stu-id="55830-148">DSC resource module package format</span></span>

<span data-ttu-id="55830-149">Jedes Ressourcenmodul muss komprimiert und entsprechend dem folgenden Muster benannt werden: `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="55830-149">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="55830-150">Ein Modul namens „xWebAdminstration“ mit einer Modulversion 3.1.2.0 würde beispielsweise „xWebAdministration_3.2.1.0.zip“ heißen.</span><span class="sxs-lookup"><span data-stu-id="55830-150">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="55830-151">Jede Version eines Moduls muss in einer eigenen ZIP-Datei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="55830-151">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="55830-152">Da jede ZIP-Datei nur jeweils eine Version einer Ressource enthält, wird das in WMF 5.0 eingeführte das Modulformat, das mehrere Versionen in einem einzigen Verzeichnis ermöglicht, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55830-152">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="55830-153">Das bedeutet, dass Sie vor dem Packen von DSC-Ressourcenmodulen für die Verwendung mit einem Pullserver eine kleine Änderung an der Verzeichnisstruktur vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="55830-153">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="55830-154">Das Standardformat für Module mit DSC-Ressourcen in WMF 5.0 ist: {Modulordner}\{Modulversion}\DscResources\{DSC-Ressourcenordner}\'.</span><span class="sxs-lookup"><span data-stu-id="55830-154">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="55830-155">Entfernen Sie vor dem Packen für den Pullserver einfach den Ordner **{Modulversion}**, damit der Pfad wie folgt geändert wird: {Modulordner}\DscResources\{DSC-Ressourcenordner}\'.</span><span class="sxs-lookup"><span data-stu-id="55830-155">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="55830-156">Komprimieren Sie den Odner nach dieser Änderung wie oben beschrieben, und speichern Sie die ZIP-Dateien im Ordner **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="55830-156">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="55830-157">Verwenden Sie `new-dscchecksum {module zip file}` zum Erstellen einer Prüfsummendatei für das neu hinzugefügte Modul.</span><span class="sxs-lookup"><span data-stu-id="55830-157">Use `new-dscchecksum {module zip file}` to create a checksum file for the newly-added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="55830-158">MOF-Konfigurationsformat</span><span class="sxs-lookup"><span data-stu-id="55830-158">Configuration MOF format</span></span> 
<span data-ttu-id="55830-159">Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="55830-159">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="55830-160">Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) auf.</span><span class="sxs-lookup"><span data-stu-id="55830-160">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="55830-161">Das Cmdlet verwendet einen **Path**-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet.</span><span class="sxs-lookup"><span data-stu-id="55830-161">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="55830-162">Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist.</span><span class="sxs-lookup"><span data-stu-id="55830-162">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="55830-163">Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.</span><span class="sxs-lookup"><span data-stu-id="55830-163">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="55830-164">Platzieren Sie die MOF-Dateien und die zugeordneten Prüfsummendateien im Ordner **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="55830-164">Place the MOF files and their associated checksum files in the the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="55830-165">**Hinweis**: Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="55830-165">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="tooling"></a><span data-ttu-id="55830-166">Tools</span><span class="sxs-lookup"><span data-stu-id="55830-166">Tooling</span></span>
<span data-ttu-id="55830-167">Um das Einrichten, Überprüfen und Verwalten des Pullservers zu vereinfachen, enthält die neueste Version des Moduls „xPSDesiredStateConfiguration“ folgende Tools als Beispiele:</span><span class="sxs-lookup"><span data-stu-id="55830-167">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>
1. <span data-ttu-id="55830-168">Ein Modul, das beim Packen von DSC-Ressourcenmodulen und Konfigurationsdateien zur Verwendung auf dem Pullserver hilft.</span><span class="sxs-lookup"><span data-stu-id="55830-168">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="55830-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="55830-169">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="55830-170">Beispiele unten:</span><span class="sxs-lookup"><span data-stu-id="55830-170">Examples below:</span></span>

```powershell
    # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
     $moduleList = @("xWebAdministration", "xPhp") 
     Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 
     
     # Example 2 - Package modules and mof documents from c:\LocalDepot
     Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
```

1. <span data-ttu-id="55830-171">Ein Skript, das den Pullserver überprüft, wurde ordnungsgemäß konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="55830-171">A script that validates the Pull Server is configured correctly.</span></span> <span data-ttu-id="55830-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="55830-172">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>


## <a name="pull-client-configuration"></a><span data-ttu-id="55830-173">Pullclientkonfiguration</span><span class="sxs-lookup"><span data-stu-id="55830-173">Pull client configuration</span></span> 
<span data-ttu-id="55830-174">In den folgenden Themen wird das Einrichten von Pullclients im Detail beschrieben:</span><span class="sxs-lookup"><span data-stu-id="55830-174">The following topics describe setting up pull clients in detail:</span></span>

* [<span data-ttu-id="55830-175">Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="55830-175">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
* [<span data-ttu-id="55830-176">Einrichten eines DSC-Pullclients mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="55830-176">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="55830-177">Teilkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="55830-177">Partial configurations</span></span>](partialConfigs.md)


## <a name="see-also"></a><span data-ttu-id="55830-178">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="55830-178">See also</span></span>
* [<span data-ttu-id="55830-179">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="55830-179">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="55830-180">Inkraftsetzung von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="55830-180">Enacting configurations</span></span>](enactingConfigurations.md)
* [<span data-ttu-id="55830-181">Verwenden eines DSC-Berichtsservers</span><span class="sxs-lookup"><span data-stu-id="55830-181">Using a DSC report server</span></span>](reportServer.md)

