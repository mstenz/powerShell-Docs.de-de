---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: DSC-Verbesserungen in WMF 5.1
ms.openlocfilehash: a5efa38ce791a893580316bad7b61a6689153a86
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416676"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="12f97-103">Verbesserungen an DSC (Desired State Configuration) in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="12f97-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="12f97-104">Verbesserungen an DSC-Klassenressourcen</span><span class="sxs-lookup"><span data-stu-id="12f97-104">DSC class resource improvements</span></span>

<span data-ttu-id="12f97-105">In WMF 5.1 haben wir die folgenden bekannten Probleme behoben:</span><span class="sxs-lookup"><span data-stu-id="12f97-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="12f97-106">„Get-DscConfiguration“ gibt möglicherweise leere Werte (NULL) oder Fehler zurück, wenn von der „Get()“-Funktion einer klassenbasierten DSC-Ressource ein komplexer Typ bzw. ein Hashtabellentyp zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="12f97-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="12f97-107">„Get-DscConfiguration“ gibt einen Fehler zurück, wenn die RunAs-Anmeldeinformationen bei der DSC-Konfiguration verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="12f97-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="12f97-108">Eine klassenbasierte Ressource kann nicht in einer zusammengesetzten Konfiguration verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="12f97-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="12f97-109">„Start-DscConfiguration“ reagiert nicht mehr, wenn die klassenbasierte Ressource eine Eigenschaft des eigenen Typs aufweist.</span><span class="sxs-lookup"><span data-stu-id="12f97-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="12f97-110">Eine klassenbasierte Ressource kann nicht als exklusive Ressource verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="12f97-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="12f97-111">Verbesserungen beim Debuggen von DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="12f97-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="12f97-112">In WMF 5.0 hat der PowerShell-Debugger nicht direkt an der klassenbasierten Ressourcenmethode (Get/Set/Test) angehalten.</span><span class="sxs-lookup"><span data-stu-id="12f97-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="12f97-113">In WMF 5.1 wird der Debugger bei der klassenbasierten Ressourcenmethode auf die gleiche Weise wie bei MOF-basierten Ressourcenmethoden anhalten.</span><span class="sxs-lookup"><span data-stu-id="12f97-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="12f97-114">Der DSC-Pull-Client unterstützt TLS 1.1 und TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="12f97-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="12f97-115">Zuvor unterstützte der DSC-Pull-Client nur SSL 3.0 und TLS 1.0 über HTTPS-Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="12f97-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="12f97-116">Wenn er gezwungen wurde, sicherere Protokolle zu verwenden, funktionierte der Pull-Client nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="12f97-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="12f97-117">In WMF 5.1 unterstützt der DSC-Pull-Client SSL 3.0 nicht mehr. Stattdessen werden die sichereren TLS 1.1- und TLS 1.2-Protokolle unterstützt.</span><span class="sxs-lookup"><span data-stu-id="12f97-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="12f97-118">Verbesserte Pull-Serverregistrierung</span><span class="sxs-lookup"><span data-stu-id="12f97-118">Improved pull server registration</span></span>

<span data-ttu-id="12f97-119">In früheren Versionen von WMF führten gleichzeitige Registrierungen/Berichterstellungsanforderungen an einen DSC-Pullserver während der Verwendung der ESENT-Datenbank zu einem LCM-Registrierungs- und/oder Berichterstellungsfehler.</span><span class="sxs-lookup"><span data-stu-id="12f97-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="12f97-120">In solchen Fällen enthalten die Ereignisprotokolle auf dem Pull-Server den Fehler „Der Instanzname wird bereits verwendet“.</span><span class="sxs-lookup"><span data-stu-id="12f97-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="12f97-121">Die Ursache hierfür ist die Verwendung eines falschen Musters für den Zugriff auf die ESENT-Datenbank in einem Multithread-Szenario.</span><span class="sxs-lookup"><span data-stu-id="12f97-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="12f97-122">In WMF 5.1 wurde dieses Problem behoben.</span><span class="sxs-lookup"><span data-stu-id="12f97-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="12f97-123">Gleichzeitige Registrierungen oder Berichterstellung (mit ESENT-Datenbank) funktionieren in WMF 5.1 einwandfrei.</span><span class="sxs-lookup"><span data-stu-id="12f97-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="12f97-124">Dieses Problem gilt nur für die ESENT-Datenbank und nicht für die OLE DB-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="12f97-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="12f97-125">Aktivieren des Umlaufprotokolls in der ESENT-Datenbankinstanz</span><span class="sxs-lookup"><span data-stu-id="12f97-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="12f97-126">In früheren Version von DSC-PullServer füllten die ESENT-Datenbankprotokolldateien den Speicherplatz des Pullservers, weil die Datenbankinstanz ohne Umlaufprotokoll erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="12f97-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="12f97-127">In dieser Version können Sie das Umlaufprotokollverhalten der Instanz mit „web.config“ des Pull-Servers steuern.</span><span class="sxs-lookup"><span data-stu-id="12f97-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="12f97-128">Standardmäßig ist „CircularLogging“ auf TRUE festgelegt.</span><span class="sxs-lookup"><span data-stu-id="12f97-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="12f97-129">Wow64-Unterstützung für das Schlüsselwort „Configuration“</span><span class="sxs-lookup"><span data-stu-id="12f97-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="12f97-130">Das Schlüsselwort `Configuration` wird nun in WOW64 auf 64-Bit-Computern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="12f97-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="12f97-131">Dies bedeutet, dass eine DSC-Konfiguration in einem 32-Bit-Prozess, wie z. B. Windows PowerShell ISE (x86) auf einem 64-Bit-Computer, definiert und kompiliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="12f97-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="12f97-132">Übertragen einer Namenskonvention für eine partielle Konfiguration mithilfe von Pull</span><span class="sxs-lookup"><span data-stu-id="12f97-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="12f97-133">Im vorherigen Release besagte die Namenskonvention für eine partielle Konfiguration, dass der MOF-Dateiname im Pull-Server/-Dienst mit dem Namen der partiellen Konfiguration übereinstimmen soll, der in den Einstellungen des lokalen Konfigurations-Managers (Local Configuration Manager; LCM) angegeben wurde. Dieser Name sollte wiederum mit dem in der MOF-Datei eingebetteten Konfigurationsnamen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="12f97-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="12f97-134">Weitere Informationen finden Sie in den nachfolgenden Abbildungen:</span><span class="sxs-lookup"><span data-stu-id="12f97-134">See the snapshots below:</span></span>

- <span data-ttu-id="12f97-135">Lokale Konfigurationseinstellungen, die eine Teilkonfiguration definieren, die von einem Knoten empfangen werden darf.</span><span class="sxs-lookup"><span data-stu-id="12f97-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![Beispiel einer Metakonfiguration](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="12f97-137">Beispieldefinition einer partiellen Konfiguration</span><span class="sxs-lookup"><span data-stu-id="12f97-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="12f97-138">ConfigurationName, eingebettet in der generierten MOF-Datei</span><span class="sxs-lookup"><span data-stu-id="12f97-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![Beispiel einer generierten MOF-Datei](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="12f97-140">FileName im Repository der Pull-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="12f97-140">FileName in the pull configuration repository</span></span>

  ![FileName im Repository der Konfiguration](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="12f97-142">Basierend auf dem Namen des Azure Automation-Diensts generierte MOF-Dateien nach dem Schema „`<ConfigurationName>.<NodeName>.mof`“.</span><span class="sxs-lookup"><span data-stu-id="12f97-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="12f97-143">Die nachstehende Konfiguration wird also in „PartialOne.localhost.mof“ kompiliert.</span><span class="sxs-lookup"><span data-stu-id="12f97-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="12f97-144">Aus diesem Grund war es nicht möglich, eine Ihrer Teilkonfigurationen aus dem Azure Automation-Dienst mithilfe von Pull zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="12f97-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="12f97-145">In WMF 5.1 kann die Teilkonfiguration im Pull-Server/Dienst nach dem Schema „`<ConfigurationName>.<NodeName>.mof`“ benannt werden.</span><span class="sxs-lookup"><span data-stu-id="12f97-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="12f97-146">Darüber hinaus kann die Konfigurationsdatei auf dem Konfigurationsrepository des Pull-Servers einen beliebigen Dateinamen haben, wenn ein Computer eine einzelne Konfiguration von einem Pull-Server/-Dienst mithilfe von Pull überträgt.</span><span class="sxs-lookup"><span data-stu-id="12f97-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="12f97-147">Diese Benennungsflexibilität erlaubt Ihnen, Ihre Knoten teilweise über den Azure Automation-Dienst zu verwalten, wobei ein Teil der Konfiguration Ihres Knotens von Azure Automation DSC stammt und die andere Teilkonfiguration von Ihnen lokal verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="12f97-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="12f97-148">Mit der nachstehenden Metakonfiguration wird ein Knoten so eingerichtet, dass er sowohl lokal als auch vom Azure Automation-Dienst verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="12f97-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="12f97-149">Verwenden von PsDscRunAsCredential mit zusammengesetzten DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="12f97-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="12f97-150">Ab jetzt können Sie auch[PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) mit [zusammengesetzten](/powershell/scripting/dsc/authoringresourcecomposite) DSC-Ressourcen verwenden.</span><span class="sxs-lookup"><span data-stu-id="12f97-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="12f97-151">Sie können jetzt für **PsDscRunAsCredential** einen Wert angeben, wenn sie zusammengesetzte Ressourcen innerhalb von Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="12f97-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="12f97-152">Wenn angegeben, werden alle Ressourcen in einer zusammengesetzten Ressource als RunAs-Benutzer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="12f97-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="12f97-153">Wenn eine zusammengesetzte Ressource eine andere zusammengesetzte Ressource aufruft, werden deren gesamte Ressourcen ebenfalls als RunAs-Benutzer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="12f97-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="12f97-154">RunAs-Anmeldeinformationen werden auf alle Hierarchieebenen der zusammengesetzten Ressource verteilt.</span><span class="sxs-lookup"><span data-stu-id="12f97-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="12f97-155">Wenn eine Ressource in einer zusammengesetzten Ressource einen eigenen Wert für **PsDscRunAsCredential** angibt, wird während der Kompilierung der Konfiguration ein Fehler beim Zusammenführen zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="12f97-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="12f97-156">Dieses Beispiel zeigt die Verwendung in Kombination mit der zusammengesetzten [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource)-Ressource, die im PSDesiredStateConfiguration-Modul enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="12f97-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="12f97-157">Zulassen identischer doppelter Ressourcen in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="12f97-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="12f97-158">DSC lässt keine in Konflikt stehenden Ressourcendefinitionen in einer Konfiguration zu bzw. behandeln diese nicht.</span><span class="sxs-lookup"><span data-stu-id="12f97-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="12f97-159">Anstatt zu versuchen, den Konflikt zu lösen, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="12f97-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="12f97-160">Sobald die Wiederverwendung von Konfigurationen mittels zusammengesetzter Ressourcen häufiger vorkommt, werden Konflikte häufiger auftreten.</span><span class="sxs-lookup"><span data-stu-id="12f97-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="12f97-161">Wenn in Konflikt stehende Ressourcendefinitionen identisch sind, sollte DSC diese intelligent zulassen.</span><span class="sxs-lookup"><span data-stu-id="12f97-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="12f97-162">In dieser Version unterstützen wir mehrere Ressourceninstanzen, die identische Definitionen aufweisen:</span><span class="sxs-lookup"><span data-stu-id="12f97-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="12f97-163">In früheren Versionen wäre das Ergebnis eine fehlerhafte Kompilierung aufgrund eines Konflikts zwischen der „WindowsFeature FE_IIS“-Instanz und der „WindowsFeature Worker_IIS“-Instanz beim Versuch sicherzustellen, dass die Roll „Web-Server“ installiert ist.</span><span class="sxs-lookup"><span data-stu-id="12f97-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="12f97-164">Beachten Sie, dass *alle* Eigenschaften, die konfiguriert werden, in diesen beiden Konfigurationen identisch sind.</span><span class="sxs-lookup"><span data-stu-id="12f97-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="12f97-165">Da *alle* Eigenschaften in diesen beiden Ressourcen identisch sind, führt dies jetzt zu einer erfolgreichen Kompilierung.</span><span class="sxs-lookup"><span data-stu-id="12f97-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="12f97-166">Wenn Eigenschaften in beiden Ressourcen unterschiedlich sind, werden sie nicht als identisch eingestuft, weshalb die Kompilierung misslingt.</span><span class="sxs-lookup"><span data-stu-id="12f97-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="12f97-167">Überprüfen der Signatur von DSC-Modulen und -Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="12f97-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="12f97-168">In DSC werden Konfigurationen und Module über den Pull-Server auf die verwalteten Computer verteilt.</span><span class="sxs-lookup"><span data-stu-id="12f97-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="12f97-169">Wenn ein Pull-Server kompromittiert ist, kann ein Angreifer möglicherweise die Konfigurationen und Module auf dem Pull-Server ändern und sie anschließend an alle verwalteten Knoten verteilen lassen.</span><span class="sxs-lookup"><span data-stu-id="12f97-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="12f97-170">In WMF 5.1 unterstützt DSC die Überprüfung der digitalen Signaturen in Katalog- und Konfigurationsdateien (MOF-Dateien).</span><span class="sxs-lookup"><span data-stu-id="12f97-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="12f97-171">Diese Funktion verhindert, dass Knoten Konfigurationen oder Moduldateien ausführen, die nicht von einem vertrauenswürdigen Signaturgeber signiert oder die manipuliert wurden, nachdem der vertrauenswürdige Signaturgeber sie signiert hat.</span><span class="sxs-lookup"><span data-stu-id="12f97-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="12f97-172">So signieren Sie Konfigurationen und Module</span><span class="sxs-lookup"><span data-stu-id="12f97-172">How to sign configuration and module</span></span>

- <span data-ttu-id="12f97-173">Konfigurationsdateien (MOF-Dateien): Das vorhandene PowerShell-Cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) wurde erweitert und unterstützt nun das Signieren von MOF-Dateien.</span><span class="sxs-lookup"><span data-stu-id="12f97-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="12f97-174">Module: Module werden signiert, indem der entsprechende Modulkatalog wie in den nachfolgenden Schritten erläutert signiert wird:</span><span class="sxs-lookup"><span data-stu-id="12f97-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="12f97-175">Erstellen einer Katalogdatei: Eine Katalogdatei enthält eine Sammlung kryptografischer Hashes oder Fingerabdrücke.</span><span class="sxs-lookup"><span data-stu-id="12f97-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="12f97-176">Jeder Fingerabdruck entspricht einer Datei, die im Modul enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="12f97-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="12f97-177">Mit dem neu hinzugefügten Cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) können Benutzer eine Katalogdatei für ihr Modul erstellen.</span><span class="sxs-lookup"><span data-stu-id="12f97-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="12f97-178">Signieren der Katalogdatei: Mit [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) wird die Katalogdatei signiert.</span><span class="sxs-lookup"><span data-stu-id="12f97-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="12f97-179">Fügen Sie die Katalogdatei in den Modulordner ein.</span><span class="sxs-lookup"><span data-stu-id="12f97-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="12f97-180">Gemäß der Konvention sollte die Modulkatalogdatei mit dem gleichen Namen wie das Modul im Modulordner abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="12f97-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="12f97-181">Einstellungen des lokalen Konfigurations-Managers zur Aktivierung von Signaturüberprüfungen</span><span class="sxs-lookup"><span data-stu-id="12f97-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="12f97-182">Pull</span><span class="sxs-lookup"><span data-stu-id="12f97-182">Pull</span></span>

<span data-ttu-id="12f97-183">Der lokale Konfigurations-Manager eines Knotens überprüft die Signatur von Modulen und Konfigurationen auf Grundlage der aktuellen Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="12f97-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="12f97-184">Die Überprüfung der Signatur ist standardmäßig deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="12f97-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="12f97-185">Die Signaturüberprüfung kann aktiviert werden, indem Sie wie nachfolgend gezeigt den Block „SignatureValidation“ der Metakonfigurationsdefinition des Knotens hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="12f97-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="12f97-186">Die Festlegung der oben genannten Metakonfiguration auf einem Knoten aktiviert die Überprüfung der Signatur für heruntergeladene Konfigurationen und Module.</span><span class="sxs-lookup"><span data-stu-id="12f97-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="12f97-187">Der lokale Konfigurations-Manager führt die folgenden Schritte aus, um die digitalen Signaturen zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="12f97-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="12f97-188">Überprüfen, ob die Signatur einer Konfigurationsdatei (MOF) gültig ist, mithilfe des Cmdlets `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="12f97-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="12f97-189">Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat.</span><span class="sxs-lookup"><span data-stu-id="12f97-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="12f97-190">Herunterladen der Modul-/Ressourcenabhängigkeiten der Konfiguration in einen temporären Speicherort.</span><span class="sxs-lookup"><span data-stu-id="12f97-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="12f97-191">Überprüfen der Signatur des Katalogs, der im Modul enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="12f97-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="12f97-192">Suchen einer `<moduleName>.cat`-Datei und Überprüfen ihrer Signatur mithilfe von `Get-AuthenticodeSignature`.</span><span class="sxs-lookup"><span data-stu-id="12f97-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="12f97-193">Überprüfen der Zertifizierungsstelle, die den Signaturgeber als vertrauenswürdig eingestuft hat</span><span class="sxs-lookup"><span data-stu-id="12f97-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="12f97-194">Sicherstellen, dass der Inhalt der Module nicht manipuliert wurde, mithilfe des neuen Cmdlets `Test-FileCatalog`.</span><span class="sxs-lookup"><span data-stu-id="12f97-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="12f97-195">`Install-Module` in `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="12f97-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="12f97-196">Prozesskonfiguration</span><span class="sxs-lookup"><span data-stu-id="12f97-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="12f97-197">Signaturen von Modulkatalogen und -konfigurationen werden nur bei der ersten Anwendung der Konfiguration auf das System überprüft, oder wenn das Modul heruntergeladen und installiert wird.</span><span class="sxs-lookup"><span data-stu-id="12f97-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="12f97-198">Konsistenzläufe überprüfen nicht die Signatur von „current.mof“-Dateien oder deren Modulabhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="12f97-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="12f97-199">Wenn bei der Überprüfung zu irgendeinem Zeitpunkt ein Fehler auftritt, z. B. wenn die vom Pull-Server mithilfe von Pull übertragene Konfiguration nicht signiert ist, wird bei der Verarbeitung der Konfiguration der nachstehende Fehler ausgegeben, und alle temporären Dateien werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="12f97-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![Beispielkonfiguration einer Fehlerausgabe](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="12f97-201">Entsprechend wird beim Übertragen eines Moduls mithilfe von Pull, dessen Katalog nicht signiert ist, der folgende Fehler ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="12f97-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![Beispielmodul einer Fehlerausgabe](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="12f97-203">Push</span><span class="sxs-lookup"><span data-stu-id="12f97-203">Push</span></span>

<span data-ttu-id="12f97-204">Eine Konfiguration, die über Push bereitgestellt wurde, könnte an ihrer Quelle manipuliert worden sein, bevor sie an den Knoten übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="12f97-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="12f97-205">Der lokale Konfigurations-Manager führt für mithilfe von Push übertragene oder veröffentlichte Konfigurationen ähnliche Schritte zur Überprüfung der Signatur durch.</span><span class="sxs-lookup"><span data-stu-id="12f97-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="12f97-206">Nachstehend finden Sie ein vollständiges Beispiel für die Signaturüberprüfung bei einer mithilfe von Push übertragenen Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="12f97-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="12f97-207">Aktivieren Sie die Überprüfung der Signatur auf dem Knoten.</span><span class="sxs-lookup"><span data-stu-id="12f97-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="12f97-208">Erstellen Sie eine Beispielkonfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="12f97-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="12f97-209">Versuchen Sie, die nicht signierte Konfigurationsdatei mithilfe von Push auf den Knoten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="12f97-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="12f97-211">Signieren Sie die Konfigurationsdatei mithilfe eines Codesignaturzertifikats.</span><span class="sxs-lookup"><span data-stu-id="12f97-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="12f97-213">Versuchen Sie, die signierte MOF-Datei mithilfe von Push zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="12f97-213">Try pushing the signed MOF file.</span></span>

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
