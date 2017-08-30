---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: DSC-Verbesserungen in WMF 5.1
ms.openlocfilehash: ce897dab2344455453e9bf2d0b5a897f9abb4392
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="4d481-103">Verbesserungen an DSC (Desired State Configuration) in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="4d481-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="4d481-104">Verbesserungen an DSC-Klassenressourcen</span><span class="sxs-lookup"><span data-stu-id="4d481-104">DSC class resource improvements</span></span>

<span data-ttu-id="4d481-105">In WMF 5.1 haben wir die folgenden bekannten Probleme behoben:</span><span class="sxs-lookup"><span data-stu-id="4d481-105">In WMF 5.1, we have fixed the following known issues:</span></span>
* <span data-ttu-id="4d481-106">„Get-DscConfiguration“ gibt möglicherweise leere Werte (NULL) oder Fehler zurück, wenn von der „Get()“-Funktion einer klassenbasierten DSC-Ressource ein komplexer Typ bzw. ein Hashtabellentyp zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="4d481-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
* <span data-ttu-id="4d481-107">„Get-DscConfiguration“ gibt einen Fehler zurück, wenn die RunAs-Anmeldeinformationen bei der DSC-Konfiguration verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4d481-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
* <span data-ttu-id="4d481-108">Eine klassenbasierte Ressource kann nicht in einer zusammengesetzten Konfiguration verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4d481-108">Class-based resource cannot be used in a composite configuration.</span></span>
* <span data-ttu-id="4d481-109">„Start-DscConfiguration“ reagiert nicht mehr, wenn die klassenbasierte Ressource eine Eigenschaft des eigenen Typs aufweist.</span><span class="sxs-lookup"><span data-stu-id="4d481-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
* <span data-ttu-id="4d481-110">Eine klassenbasierte Ressource kann nicht als exklusive Ressource verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4d481-110">Class-based resource cannot be used as an exclusive resource.</span></span>


## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="4d481-111">Verbesserungen beim Debuggen von DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4d481-111">DSC resource debugging improvements</span></span>
<span data-ttu-id="4d481-112">In WMF 5.0 hat der PowerShell-Debugger nicht direkt an der klassenbasierten Ressourcenmethode (Get/Set/Test) angehalten.</span><span class="sxs-lookup"><span data-stu-id="4d481-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="4d481-113">In WMF 5.1 wird der Debugger bei der klassenbasierten Ressourcenmethode auf die gleiche Weise wie bei MOF-basierten Ressourcenmethoden anhalten.</span><span class="sxs-lookup"><span data-stu-id="4d481-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="4d481-114">Der DSC-Pull-Client unterstützt TLS 1.1 und TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="4d481-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span> 
<span data-ttu-id="4d481-115">Zuvor unterstützte der DSC-Pull-Client nur SSL 3.0 und TLS 1.0 über HTTPS-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="4d481-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="4d481-116">Wenn er gezwungen wurde, sicherere Protokolle zu verwenden, funktionierte der Pull-Client nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="4d481-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="4d481-117">In WMF 5.1 unterstützt der DSC-Pull-Client SSL 3.0 nicht mehr. Stattdessen werden die sichereren TLS 1.1- und TLS 1.2-Protokolle unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4d481-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>  

## <a name="improved-pull-server-registration"></a><span data-ttu-id="4d481-118">Verbesserte Pull-Serverregistrierung</span><span class="sxs-lookup"><span data-stu-id="4d481-118">Improved pull server registration</span></span> ##

<span data-ttu-id="4d481-119">In früheren Versionen von WMF führten gleichzeitige Registrierungen/Berichterstellungsanforderungen an einen DSC-Pullserver während der Verwendung der ESENT-Datenbank zu einem LCM-Registrierungs- und/oder Berichterstellungsfehler.</span><span class="sxs-lookup"><span data-stu-id="4d481-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="4d481-120">In solchen Fällen enthalten die Ereignisprotokolle auf dem Pull-Server den Fehler „Der Instanzname wird bereits verwendet“.</span><span class="sxs-lookup"><span data-stu-id="4d481-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="4d481-121">Die Ursache hierfür ist die Verwendung eines falschen Musters für den Zugriff auf die ESENT-Datenbank in einem Multithread-Szenario.</span><span class="sxs-lookup"><span data-stu-id="4d481-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="4d481-122">In WMF 5.1 wurde dieses Problem behoben.</span><span class="sxs-lookup"><span data-stu-id="4d481-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="4d481-123">Gleichzeitige Registrierungen oder Berichterstellung (mit ESENT-Datenbank) funktionieren in WMF 5.1 einwandfrei.</span><span class="sxs-lookup"><span data-stu-id="4d481-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="4d481-124">Dieses Problem gilt nur für die ESENT-Datenbank und nicht für die OLE DB-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="4d481-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span> 

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="4d481-125">Aktivieren des Umlaufprotokolls in der ESENT-Datenbankinstanz</span><span class="sxs-lookup"><span data-stu-id="4d481-125">Enable Circular log on ESENT database instance</span></span>
<span data-ttu-id="4d481-126">In früheren Version von DSC-PullServer füllten die ESENT-Datenbankprotokolldateien den Speicherplatz des Pullservers, weil die Datenbankinstanz ohne Umlaufprotokoll erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="4d481-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="4d481-127">In dieser Version können Sie das Umlaufprotokollverhalten der Instanz mit „web.config“ des Pull-Servers steuern.</span><span class="sxs-lookup"><span data-stu-id="4d481-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="4d481-128">Standardmäßig ist „CircularLogging“ auf TRUE festgelegt.</span><span class="sxs-lookup"><span data-stu-id="4d481-128">By default CircularLogging is set to TRUE.</span></span>
```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```
## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="4d481-129">Übertragen einer Namenskonvention für eine partielle Konfiguration mithilfe von Pull</span><span class="sxs-lookup"><span data-stu-id="4d481-129">Pull partial configuration naming convention</span></span>
<span data-ttu-id="4d481-130">Im vorherigen Release besagte die Namenskonvention für eine partielle Konfiguration, dass der MOF-Dateiname im Pull-Server/-Dienst mit dem Namen der partiellen Konfiguration übereinstimmen soll, der in den Einstellungen des lokalen Konfigurations-Managers (Local Configuration Manager; LCM) angegeben wurde. Dieser Name sollte wiederum mit dem in der MOF-Datei eingebetteten Konfigurationsnamen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4d481-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span> 

<span data-ttu-id="4d481-131">Weitere Informationen finden Sie in den nachfolgenden Abbildungen:</span><span class="sxs-lookup"><span data-stu-id="4d481-131">See the snapshots below:</span></span>

<span data-ttu-id="4d481-132">•   lokale Konfigurationseinstellungen, die eine Teilkonfiguration definieren, die von einem Knoten empfangen werden darf.</span><span class="sxs-lookup"><span data-stu-id="4d481-132">•   Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![Beispiel einer Metakonfiguration](../images/MetaConfigPartialOne.png)

<span data-ttu-id="4d481-134">•   Beispieldefinition einer partiellen Konfiguration</span><span class="sxs-lookup"><span data-stu-id="4d481-134">•   Sample partial configuration definition</span></span> 

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="4d481-135">•   ConfigurationName, eingebettet in der generierten MOF-Datei.</span><span class="sxs-lookup"><span data-stu-id="4d481-135">•   'ConfigurationName' embedded in the generated MOF file.</span></span>

![Beispiel einer generierten MOF-Datei](../images/PartialGeneratedMof.png)

<span data-ttu-id="4d481-137">•   FileName im Repository der Pull-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="4d481-137">•   FileName in the pull configuration repository</span></span> 

![FileName im Repository der Konfiguration](../images/PartialInConfigRepository.png)

<span data-ttu-id="4d481-139">Basierend auf dem Namen des Azure Automation-Diensts generierte MOF-Dateien nach dem Schema „`<ConfigurationName>.<NodeName>.mof`“.</span><span class="sxs-lookup"><span data-stu-id="4d481-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="4d481-140">Die nachstehende Konfiguration wird also in „PartialOne.localhost.mof“ kompiliert.</span><span class="sxs-lookup"><span data-stu-id="4d481-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="4d481-141">Aus diesem Grund war es nicht möglich, eine Ihrer Teilkonfigurationen aus dem Azure Automation-Dienst mithilfe von Pull zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="4d481-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test 
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="4d481-142">In WMF 5.1 kann die Teilkonfiguration im Pull-Server/Dienst nach dem Schema „`<ConfigurationName>.<NodeName>.mof`“ benannt werden.</span><span class="sxs-lookup"><span data-stu-id="4d481-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="4d481-143">Darüber hinaus kann die Konfigurationsdatei auf dem Konfigurationsrepository des Pull-Servers einen beliebigen Dateinamen haben, wenn ein Computer eine einzelne Konfiguration von einem Pull-Server/-Dienst mithilfe von Pull überträgt.</span><span class="sxs-lookup"><span data-stu-id="4d481-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="4d481-144">Diese Benennungsflexibilität erlaubt Ihnen, Ihre Knoten teilweise über den Azure Automation-Dienst zu verwalten, wobei ein Teil der Konfiguration Ihres Knotens von Azure Automation DSC stammt und die andere Teilkonfiguration von Ihnen lokal verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="4d481-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="4d481-145">Mit der nachstehenden Metakonfiguration wird ein Knoten so eingerichtet, dass er sowohl lokal als auch vom Azure Automation-Dienst verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="4d481-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
  [DscLocalConfigurationManager()]
   Configuration RegistrationMetaConfig
   {
        Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PULL"            
        }

        ConfigurationRepositoryWeb web
        {
            ServerURL =  $endPoint
            RegistrationKey = $registrationKey
            ConfigurationNames = $configurationName
        }

        # Partial configuration managed by Azure Automation service.
        PartialConfiguration PartialConfigurationManagedByAzureAutomation
        {
            ConfigurationSource = "[ConfigurationRepositoryWeb]Web"   
        }
    
        # This partial configuration is managed locally.
        PartialConfiguration OnPremisesConfig
        {
            RefreshMode = "PUSH"
            ExclusiveResources = @("Script")
        }

   }

   RegistrationMetaConfig
   Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
 ```

# <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="4d481-146">Verwenden von PsDscRunAsCredential mit zusammengesetzten DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4d481-146">Using PsDscRunAsCredential with DSC composite resources</span></span>   

<span data-ttu-id="4d481-147">Ab jetzt können Sie auch[*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) mit [zusammengesetzten](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) DSC-Ressourcen verwenden.</span><span class="sxs-lookup"><span data-stu-id="4d481-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) resources.</span></span>    

<span data-ttu-id="4d481-148">Sie können jetzt für „PsDscRunAsCredential“ einen Wert angeben, wenn sie zusammengesetzte Ressourcen innerhalb von Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="4d481-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span> <span data-ttu-id="4d481-149">Wenn angegeben, werden alle Ressourcen in einer zusammengesetzten Ressource als RunAs-Benutzer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4d481-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="4d481-150">Wenn eine zusammengesetzte Ressource eine andere zusammengesetzte Ressource aufruft, werden deren gesamte Ressourcen ebenfalls als RunAs-Benutzer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4d481-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span> <span data-ttu-id="4d481-151">RunAs-Anmeldeinformationen werden auf alle Hierarchieebenen der zusammengesetzten Ressource verteilt.</span><span class="sxs-lookup"><span data-stu-id="4d481-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="4d481-152">Wenn eine Ressource in einer zusammengesetzten Ressource einen eigenen Wert für „PsDscRunAsCredential“ angibt, wird während der Kompilierung der Konfiguration ein Fehler beim Zusammenführen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="4d481-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="4d481-153">Dieses Beispiel zeigt die Verwendung in Kombination mit der zusammengesetzten [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources)-Ressource, die im PSDesiredStateConfiguration-Modul enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="4d481-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span> 



```powershell

Configuration InstallWindowsFeature     
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features 
        {  
            Name = @("Telnet-Client","SNMP-Service")  
            Ensure = "Present"  
            IncludeAllSubFeature = $true  
            PsDscRunAsCredential = Get-Credential   
        }  
    }

}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}


InstallWindowsFeature -ConfigurationData $configData 

```

##<a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="4d481-154">Überprüfen der Signatur von DSC-Modulen und -Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4d481-154">DSC module and configuration signing validations</span></span>
<span data-ttu-id="4d481-155">In DSC werden Konfigurationen und Module über den Pull-Server auf die verwalteten Computer verteilt.</span><span class="sxs-lookup"><span data-stu-id="4d481-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="4d481-156">Wenn der Pull-Server kompromittiert ist, kann ein Angreifer möglicherweise die Konfigurationen und Module auf dem Pull-Server ändern und sie anschließend an alle verwalteten Knoten verteilen lassen, wodurch all diese gefährdet werden.</span><span class="sxs-lookup"><span data-stu-id="4d481-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span> 

 <span data-ttu-id="4d481-157">In WMF 5.1 unterstützt DSC die Überprüfung der digitalen Signaturen in Katalog- und Konfigurationsdateien (MOF-Dateien).</span><span class="sxs-lookup"><span data-stu-id="4d481-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="4d481-158">Diese Funktion verhindert, dass Knoten Konfigurationen oder Moduldateien ausführen, die nicht von einem vertrauenswürdigen Signaturgeber signiert oder die manipuliert wurden, nachdem der vertrauenswürdige Signaturgeber sie signiert hat.</span><span class="sxs-lookup"><span data-stu-id="4d481-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span> 



###<a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="4d481-159">So signieren Sie Konfigurationen und Module</span><span class="sxs-lookup"><span data-stu-id="4d481-159">How to sign configuration and module</span></span> 
***
* <span data-ttu-id="4d481-160">Konfigurationsdateien (MOF-Dateien): Das vorhandene PowerShell-Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) wurde erweitert und unterstützt nun das Signieren von MOF-Dateien.</span><span class="sxs-lookup"><span data-stu-id="4d481-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>  
* <span data-ttu-id="4d481-161">Module: Module werden signiert, indem der entsprechende Modulkatalog wie in den nachfolgenden Schritten erläutert signiert wird:</span><span class="sxs-lookup"><span data-stu-id="4d481-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span> 
    1. <span data-ttu-id="4d481-162">Erstellen einer Katalogdatei: Eine Katalogdatei enthält eine Sammlung kryptografischer Hashes oder Fingerabdrücke.</span><span class="sxs-lookup"><span data-stu-id="4d481-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> 
       <span data-ttu-id="4d481-163">Jeder Fingerabdruck entspricht einer Datei, die im Modul enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="4d481-163">Each thumbprint corresponds to a file that is included in the module.</span></span> 
       <span data-ttu-id="4d481-164">Mit dem neu hinzugefügten Cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) können Benutzer eine Katalogdatei für ihr Modul erstellen.</span><span class="sxs-lookup"><span data-stu-id="4d481-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="4d481-165">Signieren der Katalogdatei: Mit [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) wird die Katalogdatei signiert.</span><span class="sxs-lookup"><span data-stu-id="4d481-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="4d481-166">Fügen Sie die Katalogdatei in den Modulordner ein.</span><span class="sxs-lookup"><span data-stu-id="4d481-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="4d481-167">Gemäß der Konvention sollte die Modulkatalogdatei mit dem gleichen Namen wie das Modul im Modulordner abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="4d481-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

###<a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="4d481-168">Einstellungen des lokalen Konfigurations-Managers zur Aktivierung von Signaturüberprüfungen</span><span class="sxs-lookup"><span data-stu-id="4d481-168">LocalConfigurationManager settings to enable signing validations</span></span>

####<a name="pull"></a><span data-ttu-id="4d481-169">Pull</span><span class="sxs-lookup"><span data-stu-id="4d481-169">Pull</span></span>
<span data-ttu-id="4d481-170">Der lokale Konfigurations-Manager eines Knotens überprüft die Signatur von Modulen und Konfigurationen auf Grundlage der aktuellen Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="4d481-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="4d481-171">Die Überprüfung der Signatur ist standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="4d481-171">By default, signature validation is disabled.</span></span> <span data-ttu-id="4d481-172">Die Signaturüberprüfung kann aktiviert werden, indem Sie wie nachfolgend gezeigt den Block „SignatureValidation“ der Metakonfigurationsdefinition des Knotens hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4d481-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'        
    } 
    
    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # By default, LCM uses the default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM uses this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

<span data-ttu-id="4d481-173">Die Festlegung der oben genannten Metakonfiguration auf einem Knoten aktiviert die Überprüfung der Signatur für heruntergeladene Konfigurationen und Module.</span><span class="sxs-lookup"><span data-stu-id="4d481-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="4d481-174">Der lokale Konfigurations-Manager führt die folgenden Schritte aus, um die digitalen Signaturen zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="4d481-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="4d481-175">Überprüfen, ob die Signatur einer Konfigurationsdatei (MOF) gültig ist.</span><span class="sxs-lookup"><span data-stu-id="4d481-175">Verify the signature on a configuration file (.MOF) is valid.</span></span> 
   <span data-ttu-id="4d481-176">Der lokale Konfigurations-Manager verwendet das PowerShell-Cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), das in 5.1 zur Unterstützung der Überprüfung von MOF-Signaturen erweitert wurde.</span><span class="sxs-lookup"><span data-stu-id="4d481-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="4d481-177">Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat.</span><span class="sxs-lookup"><span data-stu-id="4d481-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="4d481-178">Herunterladen der Modul-/Ressourcenabhängigkeiten der Konfiguration in einen temporären Speicherort.</span><span class="sxs-lookup"><span data-stu-id="4d481-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="4d481-179">Überprüfen der Signatur des Katalogs, der im Modul enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="4d481-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="4d481-180">Suchen einer `<moduleName>.cat`-Datei und Überprüfen der Signatur mithilfe des Cmdlets [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span><span class="sxs-lookup"><span data-stu-id="4d481-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="4d481-181">Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat</span><span class="sxs-lookup"><span data-stu-id="4d481-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="4d481-182">Sicherstellen, dass der Inhalt der Module nicht mit dem neuen Cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) manipuliert wurde.</span><span class="sxs-lookup"><span data-stu-id="4d481-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="4d481-183">Installieren des Moduls mithilfe des Cmdlets „Install-Module“ im Verzeichnis „$env:ProgramFiles\WindowsPowerShell\Modules\“</span><span class="sxs-lookup"><span data-stu-id="4d481-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="4d481-184">Prozesskonfiguration</span><span class="sxs-lookup"><span data-stu-id="4d481-184">Process configuration</span></span>

> <span data-ttu-id="4d481-185">Hinweis: Signaturen von Modulkatalogen und -konfigurationen werden nur bei der ersten Anwendung der Konfiguration auf das System überprüft, oder wenn das Modul heruntergeladen und installiert wird.</span><span class="sxs-lookup"><span data-stu-id="4d481-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span> <span data-ttu-id="4d481-186">Konsistenzläufe überprüfen nicht die Signatur von „current.mof“-Dateien oder deren Modulabhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="4d481-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="4d481-187">Wenn bei der Überprüfung zu irgendeinem Zeitpunkt ein Fehler auftritt, z. B. wenn die vom Pull-Server mithilfe von Pull übertragene Konfiguration nicht signiert ist, wird bei der Verarbeitung der Konfiguration der nachstehende Fehler ausgegeben, und alle temporären Dateien werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="4d481-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Beispielkonfiguration einer Fehlerausgabe](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="4d481-189">Entsprechend wird beim Übertragen eines Moduls mithilfe von Pull, dessen Katalog nicht signiert ist, der folgende Fehler ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="4d481-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Beispielmodul einer Fehlerausgabe](../images/PullUnisgnedCatalog.png)

####<a name="push"></a><span data-ttu-id="4d481-191">Push</span><span class="sxs-lookup"><span data-stu-id="4d481-191">Push</span></span>
<span data-ttu-id="4d481-192">Eine Konfiguration, die über Push bereitgestellt wurde, könnte an ihrer Quelle manipuliert worden sein, bevor sie an den Knoten übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="4d481-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="4d481-193">Der lokale Konfigurations-Manager führt für mithilfe von Push übertragene oder veröffentlichte Konfigurationen ähnliche Schritte zur Überprüfung der Signatur durch.</span><span class="sxs-lookup"><span data-stu-id="4d481-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="4d481-194">Nachstehend finden Sie ein vollständiges Beispiel für die Signaturüberprüfung bei einer mithilfe von Push übertragenen Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4d481-194">Below is a complete example of signature validation for push.</span></span>

* <span data-ttu-id="4d481-195">Aktivieren Sie die Überprüfung der Signatur auf dem Knoten.</span><span class="sxs-lookup"><span data-stu-id="4d481-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'        
    } 
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'   
        SignedItemType =  'Configuration','Module'             
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
``` 
* <span data-ttu-id="4d481-196">Erstellen Sie eine Beispielkonfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="4d481-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* <span data-ttu-id="4d481-197">Versuchen Sie, die nicht signierte Konfigurationsdatei mithilfe von Push auf den Knoten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="4d481-197">Try pushing the unsigned configuration file in to the node.</span></span> 

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

* <span data-ttu-id="4d481-199">Signieren Sie die Konfigurationsdatei mithilfe eines Codesignaturzertifikats.</span><span class="sxs-lookup"><span data-stu-id="4d481-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

* <span data-ttu-id="4d481-201">Versuchen Sie, die signierte MOF-Datei mithilfe von Push zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="4d481-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)

