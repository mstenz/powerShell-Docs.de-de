---
ms.date: 01/08/2020
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Pulldienst
ms.openlocfilehash: 821f183c91e805154323f9f6a42f7f5006499182
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500723"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="a2fad-103">Desired State Configuration – Pulldienst</span><span class="sxs-lookup"><span data-stu-id="a2fad-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2fad-104">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="a2fad-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a2fad-105">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="a2fad-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a2fad-106">Local Configuration Manager (LCM) kann zentral über eine Pulldienstlösung verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="a2fad-106">Local Configuration Manager (LCM) can be centrally managed by a Pull Service solution.</span></span> <span data-ttu-id="a2fad-107">Bei diesem Ansatz wird der verwaltete Knoten bei einem Dienst registriert und in den LCM-Einstellungen einer Konfiguration zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="a2fad-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span> <span data-ttu-id="a2fad-108">Die Konfiguration und alle DSC-Ressourcen, die als Abhängigkeiten für die Konfiguration erforderlich sind, werden auf den Computer heruntergeladen und von LCM zum Verwalten der Konfiguration verwendet.</span><span class="sxs-lookup"><span data-stu-id="a2fad-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span> <span data-ttu-id="a2fad-109">Informationen über den Status des verwalteten Computers werden zur Berichterstellung auf den Dienst hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="a2fad-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span> <span data-ttu-id="a2fad-110">Dieses Konzept wird als "Pulldienst" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="a2fad-110">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="a2fad-111">Folgende Optionen sind zurzeit für den Pulldienst verfügbar:</span><span class="sxs-lookup"><span data-stu-id="a2fad-111">The current options for pull service include:</span></span>

- <span data-ttu-id="a2fad-112">Azure Automation DSC-Dienst (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="a2fad-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="a2fad-113">Ein Pulldienst bei der Ausführung unter Windows Server</span><span class="sxs-lookup"><span data-stu-id="a2fad-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="a2fad-114">Von der Community verwaltete Open-Source-Lösungen</span><span class="sxs-lookup"><span data-stu-id="a2fad-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="a2fad-115">Eine SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="a2fad-115">An SMB share</span></span>

<span data-ttu-id="a2fad-116">Die empfohlene Skalierung für jede Lösung lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a2fad-116">The recommended scale for each solution is as follows:</span></span>

|                   <span data-ttu-id="a2fad-117">Lösung</span><span class="sxs-lookup"><span data-stu-id="a2fad-117">Solution</span></span>                   |              <span data-ttu-id="a2fad-118">Clientknoten</span><span class="sxs-lookup"><span data-stu-id="a2fad-118">Client nodes</span></span>              |
| -------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="a2fad-119">Windows-Pullserver mit MDB-/ESENT-Datenbank</span><span class="sxs-lookup"><span data-stu-id="a2fad-119">Windows Pull Server using MDB/ESENT database</span></span> | <span data-ttu-id="a2fad-120">Bis zu 500 Knoten</span><span class="sxs-lookup"><span data-stu-id="a2fad-120">Up to 500 nodes</span></span>                        |
| <span data-ttu-id="a2fad-121">Windows-Pullserver mit SQL-Datenbank</span><span class="sxs-lookup"><span data-stu-id="a2fad-121">Windows Pull Server using SQL database</span></span>       | <span data-ttu-id="a2fad-122">Bis zu 3500 Knoten</span><span class="sxs-lookup"><span data-stu-id="a2fad-122">Up to 3500 nodes</span></span>                       |
| <span data-ttu-id="a2fad-123">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="a2fad-123">Azure Automation DSC</span></span>                         | <span data-ttu-id="a2fad-124">Sowohl kleine als auch große Umgebungen</span><span class="sxs-lookup"><span data-stu-id="a2fad-124">Both small and large environments</span></span>      |

<span data-ttu-id="a2fad-125">**Die empfohlene Lösung** und die Option mit den meisten verfügbaren Features ist [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="a2fad-125">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span> <span data-ttu-id="a2fad-126">Eine Obergrenze für die Anzahl von Knoten pro Automation-Konto wurde nicht bestimmt.</span><span class="sxs-lookup"><span data-stu-id="a2fad-126">An upper limit for number of nodes per Automation Account has not been identified.</span></span>

<span data-ttu-id="a2fad-127">Der Azure-Dienst kann Knoten lokal in privaten Rechenzentren oder in öffentlichen Clouds wie Azure und AWS verwalten.</span><span class="sxs-lookup"><span data-stu-id="a2fad-127">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span> <span data-ttu-id="a2fad-128">Für private Umgebungen, in denen Server keine direkte Verbindung mit dem Internet herstellen können, sollten Sie die Begrenzung des ausgehenden Datenverkehrs auf den veröffentlichten Azure-IP-Adressbereich in Betracht ziehen. Informationen hierzu finden Sie unter [Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653) (IP-Adressbereiche für Azure-Rechenzentren).</span><span class="sxs-lookup"><span data-stu-id="a2fad-128">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="a2fad-129">Features des Onlinediensts, die im Pulldienst unter Windows Server zurzeit nicht verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="a2fad-129">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="a2fad-130">Verschlüsselung aller Daten während der Übertragung und im Ruhezustand</span><span class="sxs-lookup"><span data-stu-id="a2fad-130">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="a2fad-131">Automatische Erstellung und Verwaltung von Clientzertifikaten</span><span class="sxs-lookup"><span data-stu-id="a2fad-131">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="a2fad-132">Speicherung von Geheimnissen zur zentralen Verwaltung von [Kennwörtern/Anmeldeinformationen](/azure/automation/automation-credentials) oder [Variablen](/azure/automation/automation-variables) wie z.B. Servernamen oder Verbindungszeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="a2fad-132">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="a2fad-133">Zentrale Verwaltung der [LCM-Konfiguration](../managing-nodes/metaConfig.md#basic-settings) für Knoten</span><span class="sxs-lookup"><span data-stu-id="a2fad-133">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="a2fad-134">Zentrale Zuweisung von Konfigurationen zu Clientknoten</span><span class="sxs-lookup"><span data-stu-id="a2fad-134">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="a2fad-135">Freigabe von Konfigurationsänderungen für Canarygruppen zum Durchführen von Tests vor Einführung in die Produktion</span><span class="sxs-lookup"><span data-stu-id="a2fad-135">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="a2fad-136">Grafische Berichterstellung</span><span class="sxs-lookup"><span data-stu-id="a2fad-136">Graphical reporting</span></span>
  - <span data-ttu-id="a2fad-137">Statusdetails auf der Granularitätsstufe von DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="a2fad-137">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="a2fad-138">Ausführliche Fehlermeldungen von Clientcomputern für die Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="a2fad-138">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="a2fad-139">[Integration in Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) für Warnungen, automatisierte Tasks, Android-/iOS-App für Berichte und Warnungen</span><span class="sxs-lookup"><span data-stu-id="a2fad-139">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="a2fad-140">DSC-Pulldienst in Windows Server</span><span class="sxs-lookup"><span data-stu-id="a2fad-140">DSC pull service in Windows Server</span></span>

<span data-ttu-id="a2fad-141">Es ist möglich, einen Pulldienst für die Ausführung unter Windows Server zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="a2fad-141">It is possible to configure a pull service to run on Windows Server.</span></span> <span data-ttu-id="a2fad-142">Beachten Sie, dass die in Windows Server enthaltene Pulldienstlösung nur die Funktionen zum Speichern von Konfigurationen/Modulen für den Download und das Erfassen von Berichtsdaten in einer Datenbank umfasst.</span><span class="sxs-lookup"><span data-stu-id="a2fad-142">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data into a database.</span></span> <span data-ttu-id="a2fad-143">Sie enthält viele der Funktionen nicht, die vom Dienst in Azure bereitgestellt werden, und eignet sich daher nicht gut, um den Einsatz des Diensts zu bewerten.</span><span class="sxs-lookup"><span data-stu-id="a2fad-143">It does not include many of the capabilities offered by the service in Azure and so, is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="a2fad-144">Der in Windows Server angebotene Pulldienst ist ein Webdienst in IIS, der DSC-Konfigurationsdateien mithilfe einer OData-Schnittstelle für Zielknoten verfügbar macht, wenn die Zielknoten diese anfordern.</span><span class="sxs-lookup"><span data-stu-id="a2fad-144">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="a2fad-145">Anforderungen für die Verwendung eines Pullservers:</span><span class="sxs-lookup"><span data-stu-id="a2fad-145">Requirements for using a pull server:</span></span>

- <span data-ttu-id="a2fad-146">Ein Server mit:</span><span class="sxs-lookup"><span data-stu-id="a2fad-146">A server running:</span></span>
  - <span data-ttu-id="a2fad-147">WMF/PowerShell 4.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="a2fad-147">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="a2fad-148">IIS-Serverrolle</span><span class="sxs-lookup"><span data-stu-id="a2fad-148">IIS server role</span></span>
  - <span data-ttu-id="a2fad-149">DSC-Dienst</span><span class="sxs-lookup"><span data-stu-id="a2fad-149">DSC Service</span></span>
- <span data-ttu-id="a2fad-150">Im Idealfall eine Möglichkeit zum Generieren eines Zertifikats, um die an den lokalen Konfigurations-Manager (LCM) auf Zielknoten übergebenen Anmeldeinformationen abzusichern</span><span class="sxs-lookup"><span data-stu-id="a2fad-150">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="a2fad-151">Die beste Möglichkeit, Windows Server zum Hosten eines Pulldiensts zu konfigurieren, ist die Verwendung einer DSC-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a2fad-151">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span> <span data-ttu-id="a2fad-152">Ein Beispielskript finden Sie unten.</span><span class="sxs-lookup"><span data-stu-id="a2fad-152">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="a2fad-153">Unterstützte Datenbanksysteme</span><span class="sxs-lookup"><span data-stu-id="a2fad-153">Supported database systems</span></span>

| <span data-ttu-id="a2fad-154">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="a2fad-154">WMF 4.0</span></span> |       <span data-ttu-id="a2fad-155">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="a2fad-155">WMF 5.0</span></span>        |       <span data-ttu-id="a2fad-156">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a2fad-156">WMF 5.1</span></span>        | <span data-ttu-id="a2fad-157">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="a2fad-157">WMF 5.1 (Windows Server Insider Preview 17090)</span></span> |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| <span data-ttu-id="a2fad-158">MDB</span><span class="sxs-lookup"><span data-stu-id="a2fad-158">MDB</span></span>     | <span data-ttu-id="a2fad-159">ESENT (Standard), MDB</span><span class="sxs-lookup"><span data-stu-id="a2fad-159">ESENT (Default), MDB</span></span> | <span data-ttu-id="a2fad-160">ESENT (Standard), MDB</span><span class="sxs-lookup"><span data-stu-id="a2fad-160">ESENT (Default), MDB</span></span> | <span data-ttu-id="a2fad-161">ESENT (Standard), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="a2fad-161">ESENT (Default), SQL Server, MDB</span></span>               |

<span data-ttu-id="a2fad-162">Ab Release 17090 von Windows Server ist SQL Server eine unterstützte Option für den Pulldienst (Windows-Feature *DSC-Service*).</span><span class="sxs-lookup"><span data-stu-id="a2fad-162">Starting in release 17090 of Windows Server, SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="a2fad-163">Dadurch wird eine neue Option für die Skalierung großer DSC-Umgebungen bereitgestellt, die nicht zu [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) migriert wurden.</span><span class="sxs-lookup"><span data-stu-id="a2fad-163">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="a2fad-164">Die Unterstützung für SQL Server wird vorherigen Versionen von WMF 5.1 (oder früher) nicht hinzugefügt und ist nur für Windows Server-Versionen ab 17090 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a2fad-164">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="a2fad-165">Um den Pull-Server so zu konfigurieren, dass er SQL Server verwendet, legen Sie **SqlProvider** auf `$true` und **SqlConnectionString** auf eine gültige SQL Server-Verbindungszeichenfolge fest.</span><span class="sxs-lookup"><span data-stu-id="a2fad-165">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="a2fad-166">Weitere Informationen finden Sie unter [SqlClient-Verbindungszeichenfolgen](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="a2fad-166">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="a2fad-167">Ein Beispiel einer SQL Server-Konfiguration mit **xDscWebService** finden Sie zunächst unter [Verwenden der xDSCWebService-Ressource](#using-the-xdscwebservice-resource), lesen Sie anschließend die GitHub-Seite zu [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="a2fad-167">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="a2fad-168">Verwenden der xDscWebService-Ressource</span><span class="sxs-lookup"><span data-stu-id="a2fad-168">Using the xDscWebService resource</span></span>

<span data-ttu-id="a2fad-169">Die einfachste Möglichkeit einen Web-Pull-Server einzurichten, ist die Verwendung der Ressource **xDscWebService** im Modul **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="a2fad-169">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="a2fad-170">Die folgenden Schritte erläutern, wie Sie die Ressource in einer `Configuration` verwenden, die den Webdienst einrichtet.</span><span class="sxs-lookup"><span data-stu-id="a2fad-170">The following steps explain how to use the resource in a `Configuration` that sets up the web service.</span></span>

1. <span data-ttu-id="a2fad-171">Rufen Sie das Cmdlet [Install-Module](/powershell/module/PowerShellGet/Install-Module) auf, um das Modul **xPSDesiredStateConfiguration** zu installieren.</span><span class="sxs-lookup"><span data-stu-id="a2fad-171">Call the [Install-Module](/powershell/module/PowerShellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a2fad-172">`Install-Module` ist im Modul **PowerShellGet** enthalten, das Bestandteil von PowerShell 5.0 und höher ist.</span><span class="sxs-lookup"><span data-stu-id="a2fad-172">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0 and higher.</span></span>

1. <span data-ttu-id="a2fad-173">Rufen Sie ein SSL-Zertifikat für den DSC-Pullserver von einer vertrauenswürdigen Zertifizierungsstelle innerhalb Ihrer Organisation oder von einer öffentlichen Zertifizierungsstelle ab.</span><span class="sxs-lookup"><span data-stu-id="a2fad-173">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="a2fad-174">Das von der Zertifizierungsstelle empfangene Zertifikat weist normalerweise das PFX-Format auf.</span><span class="sxs-lookup"><span data-stu-id="a2fad-174">The certificate received from the authority is usually in the PFX format.</span></span>
1. <span data-ttu-id="a2fad-175">Installieren Sie auf dem Knoten, der als DSC-Pull-Server fungieren soll, das Zertifikat am Standardspeicherort, also normalerweise unter `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="a2fad-175">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="a2fad-176">Notieren Sie sich den Zertifikatfingerabdruck.</span><span class="sxs-lookup"><span data-stu-id="a2fad-176">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="a2fad-177">Wählen Sie eine GUID als der Registrierungsschlüssel aus.</span><span class="sxs-lookup"><span data-stu-id="a2fad-177">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="a2fad-178">Um einen mithilfe von PowerShell zu generieren, geben Sie `[guid]::newGuid()` oder `New-Guid` an der PS-Eingabeaufforderung ein, und drücken Sie anschließend die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="a2fad-178">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="a2fad-179">Dieser Schlüssel wird von Clientknoten bei der Registrierung als gemeinsamer Schlüssel zum Authentifizieren verwendet.</span><span class="sxs-lookup"><span data-stu-id="a2fad-179">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="a2fad-180">Weitere Informationen finden Sie weiter unten im Abschnitt „Registrierungsschlüssel“.</span><span class="sxs-lookup"><span data-stu-id="a2fad-180">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="a2fad-181">Starten Sie in der PowerShell ISE (mit <kbd>F5</kbd>) das folgende Konfigurationsskript (im Beispielordner des Moduls **xPSDesiredStateConfiguration** als `Sample_xDscWebServiceRegistration.ps1` enthalten).</span><span class="sxs-lookup"><span data-stu-id="a2fad-181">In the PowerShell ISE, start (<kbd>F5</kbd>) the following configuration script (included in the folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`) .</span></span> <span data-ttu-id="a2fad-182">Dieses Skript richtet den Pullserver ein.</span><span class="sxs-lookup"><span data-stu-id="a2fad-182">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
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

1. <span data-ttu-id="a2fad-183">Führen Sie die Konfiguration aus, und übergeben Sie als Parameter **certificateThumbPrint** den Fingerabdruck des SSL-Zertifikats und als Parameter **RegistrationKey** einen GUID-Registrierungschlüssel:</span><span class="sxs-lookup"><span data-stu-id="a2fad-183">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="a2fad-184">Registrierungsschlüssel</span><span class="sxs-lookup"><span data-stu-id="a2fad-184">Registration Key</span></span>

<span data-ttu-id="a2fad-185">Um zuzulassen, dass Clientknoten sich beim Server registrieren und Konfigurationsnamen anstelle einer Konfigurations-ID verwenden können, wird ein von der oben beschriebenen Konfiguration erstellter Registrierungsschlüssel in einer Datei namens `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="a2fad-185">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="a2fad-186">Der Registrierungsschlüssel fungiert als ein gemeinsamer geheimer Schlüssel, der vom Client während der anfänglichen Registrierung beim Pullserver verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a2fad-186">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="a2fad-187">Der Client generiert ein selbstsigniertes Zertifikat, das nach der erfolgreich abgeschlossenen Registrierung zur eindeutigen Authentifizierung beim Pull-Server verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a2fad-187">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="a2fad-188">Der Fingerabdruck dieses Zertifikats wird lokal gespeichert und der URL des Pullservers zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="a2fad-188">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="a2fad-189">Registrierungsschlüssel werden in PowerShell 4.0 nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a2fad-189">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="a2fad-190">Zum Konfigurieren eines Knotens zur Authentifizierung beim Pull-Server muss der Registrierungsschlüssel in der Metakonfiguration für alle Zielknoten enthalten sein, die sich bei diesem Pull-Server registrieren.</span><span class="sxs-lookup"><span data-stu-id="a2fad-190">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="a2fad-191">Beachten Sie, dass **RegistrationKey** aus der unten stehenden Metakonfiguration entfernt wird, nachdem der Zielcomputer erfolgreich registriert wurde, und dass der Wert dem in der Datei `RegistrationKeys.txt` auf dem Pullserver gespeicherten Wert entsprechen muss. In diesem Beispiel ist dieser Wert „140a952b-b9d6-406b-b416-e0f759c9c0e4“.</span><span class="sxs-lookup"><span data-stu-id="a2fad-191">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="a2fad-192">Behandeln Sie den Registrierungsschlüsselwert immer vertraulich, da sich jeder beliebige Zielcomputer mit diesem Schlüssel beim Pullserver registrieren könnte.</span><span class="sxs-lookup"><span data-stu-id="a2fad-192">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="a2fad-193">Der Abschnitt **ReportServerWeb** ermöglicht das Senden von Berichtsdaten an den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="a2fad-193">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="a2fad-194">Das Fehlen der Eigenschaft **ConfigurationID** in der Metakonfigurationsdatei bedeutet implizit, dass der Pullserver die V2-Version des Pullserverprotokolls unterstützt und somit eine Registrierung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="a2fad-194">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="a2fad-195">Umgekehrt bedeutet das Vorhandensein einer **ConfigurationID**, dass die V1-Version des Pullserverprotokolls verwendet wird und keine Registrierungsverarbeitung erfolgt.</span><span class="sxs-lookup"><span data-stu-id="a2fad-195">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="a2fad-196">In einem PUSH-Szenario tritt im aktuellen Release ein Fehler auf, aufgrund dessen es erforderlich ist, in der Metakonfigurationsdatei für Knoten, die noch nie bei einem Pullserver registriert wurden, die Eigenschaft „ConfigurationID“ zu definieren.</span><span class="sxs-lookup"><span data-stu-id="a2fad-196">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="a2fad-197">Dies erzwingt die Verwendung des V1-Pullserver-Protokolls verhindert Registrierungsfehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="a2fad-197">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="a2fad-198">Platzieren von Konfigurationen und Ressourcen</span><span class="sxs-lookup"><span data-stu-id="a2fad-198">Placing configurations and resources</span></span>

<span data-ttu-id="a2fad-199">Nach Abschluss des Pullserversetups befinden sich die von den Eigenschaften **ConfigurationPath** und **ModulePath** in der Pullserverkonfiguration definierten Ordner an dem Ort, an dem Module und Konfigurationen abgelegt werden, die für Zielknoten zum Abrufen verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="a2fad-199">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="a2fad-200">Diese Dateien müssen in einem bestimmten Format vorliegen, damit sie von den Pullservern ordnungsgemäß verarbeiten werden können.</span><span class="sxs-lookup"><span data-stu-id="a2fad-200">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="a2fad-201">Format des DSC-Ressourcenmodulpakets</span><span class="sxs-lookup"><span data-stu-id="a2fad-201">DSC resource module package format</span></span>

<span data-ttu-id="a2fad-202">Jedes Ressourcenmodul muss komprimiert und entsprechend dem folgenden Muster benannt werden: `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="a2fad-202">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="a2fad-203">Ein Modul namens **xWebAdminstration** mit einer Modulversion 3.1.2.0 würde beispielsweise `xWebAdministration_3.1.2.0.zip` heißen.</span><span class="sxs-lookup"><span data-stu-id="a2fad-203">For example, a module named **xWebAdminstration** with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span> <span data-ttu-id="a2fad-204">Jede Version eines Moduls muss in einer eigenen ZIP-Datei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="a2fad-204">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="a2fad-205">Da jede ZIP-Datei nur jeweils eine Version einer Ressource enthält, wird das in WMF 5.0 eingeführte das Modulformat, das mehrere Versionen in einem einzigen Verzeichnis ermöglicht, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a2fad-205">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="a2fad-206">Das bedeutet, dass Sie vor dem Packen von DSC-Ressourcenmodulen für die Verwendung mit einem Pullserver eine kleine Änderung an der Verzeichnisstruktur vornehmen müssen.</span><span class="sxs-lookup"><span data-stu-id="a2fad-206">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="a2fad-207">Das Standardformat für Module mit DSC-Ressourcen in WMF 5.0 ist `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="a2fad-207">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="a2fad-208">Entfernen Sie vor dem Packvorgang für den Pullserver einfach den Ordner **{Module version}** , damit der Pfad zu `{Module Folder}\DscResources\{DSC Resource Folder}\` wird.</span><span class="sxs-lookup"><span data-stu-id="a2fad-208">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="a2fad-209">Komprimieren Sie den Odner nach dieser Änderung wie oben beschrieben, und speichern Sie die ZIP-Dateien im Ordner **ModulePath**.</span><span class="sxs-lookup"><span data-stu-id="a2fad-209">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="a2fad-210">Verwenden Sie `New-DscChecksum {module zip file}` zum Erstellen einer Prüfsummendatei für das neu hinzugefügte Modul.</span><span class="sxs-lookup"><span data-stu-id="a2fad-210">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="a2fad-211">MOF-Konfigurationsformat</span><span class="sxs-lookup"><span data-stu-id="a2fad-211">Configuration MOF format</span></span>

<span data-ttu-id="a2fad-212">Eine MOF-Konfigurationsdatei muss einer Prüfsummendatei zugeordnet werden, damit ein LCM auf einem Zielknoten die Konfiguration überprüfen kann.</span><span class="sxs-lookup"><span data-stu-id="a2fad-212">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="a2fad-213">Um eine Prüfsumme zu erstellen, rufen Sie das Cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) auf.</span><span class="sxs-lookup"><span data-stu-id="a2fad-213">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="a2fad-214">Das Cmdlet verwendet einen **Path**-Parameter, der den Ordner angibt, in dem sich die MOF-Konfigurationsdatei befindet.</span><span class="sxs-lookup"><span data-stu-id="a2fad-214">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="a2fad-215">Das Cmdlet erstellt eine Prüfsummendatei mit dem Namen `ConfigurationMOFName.mof.checksum`, wobei `ConfigurationMOFName` der Name der MOF-Konfigurationsdatei ist.</span><span class="sxs-lookup"><span data-stu-id="a2fad-215">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="a2fad-216">Wenn in dem angegebenen Ordner mehrere MOF-Konfigurationsdateien vorhanden sind, wird für jede Konfiguration im Ordner eine Prüfsumme erstellt.</span><span class="sxs-lookup"><span data-stu-id="a2fad-216">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="a2fad-217">Platzieren Sie die MOF-Dateien und die zugeordneten Prüfsummendateien im Ordner **ConfigurationPath**.</span><span class="sxs-lookup"><span data-stu-id="a2fad-217">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="a2fad-218">Wenn Sie die MOF-Konfigurationsdatei in irgendeiner Weise ändern, müssen Sie auch die Prüfsummendatei neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a2fad-218">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="a2fad-219">Tools</span><span class="sxs-lookup"><span data-stu-id="a2fad-219">Tooling</span></span>

<span data-ttu-id="a2fad-220">Um das Einrichten, Überprüfen und Verwalten des Pullservers zu vereinfachen, enthält die neueste Version des Moduls „xPSDesiredStateConfiguration“ folgende Tools als Beispiele:</span><span class="sxs-lookup"><span data-stu-id="a2fad-220">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="a2fad-221">Ein Modul, das beim Packen von DSC-Ressourcenmodulen und Konfigurationsdateien zur Verwendung auf dem Pullserver hilft.</span><span class="sxs-lookup"><span data-stu-id="a2fad-221">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="a2fad-222">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span><span class="sxs-lookup"><span data-stu-id="a2fad-222">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span></span>
   <span data-ttu-id="a2fad-223">Beispiele unten:</span><span class="sxs-lookup"><span data-stu-id="a2fad-223">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="a2fad-224">Ein Skript, das den Pullserver überprüft, wurde ordnungsgemäß konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="a2fad-224">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="a2fad-225">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span><span class="sxs-lookup"><span data-stu-id="a2fad-225">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="a2fad-226">Community-Lösungen für Pulldienste</span><span class="sxs-lookup"><span data-stu-id="a2fad-226">Community Solutions for Pull Service</span></span>

<span data-ttu-id="a2fad-227">Die DSC-Community hat mehrere Lösungen zum Implementieren des Pulldienstprotokolls erstellt.</span><span class="sxs-lookup"><span data-stu-id="a2fad-227">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span> <span data-ttu-id="a2fad-228">Für lokale Umgebungen bieten diese Pulldienstfunktionen und die Möglichkeit, der Community mit inkrementellen Verbesserungen etwas zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="a2fad-228">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="a2fad-229">Tug</span><span class="sxs-lookup"><span data-stu-id="a2fad-229">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="a2fad-230">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="a2fad-230">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="a2fad-231">Pullclientkonfiguration</span><span class="sxs-lookup"><span data-stu-id="a2fad-231">Pull client configuration</span></span>

<span data-ttu-id="a2fad-232">In den folgenden Themen wird das Einrichten von Pullclients im Detail beschrieben:</span><span class="sxs-lookup"><span data-stu-id="a2fad-232">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="a2fad-233">Set up a DSC pull client using a configuration ID (Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID)</span><span class="sxs-lookup"><span data-stu-id="a2fad-233">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="a2fad-234">Set up a DSC pull client using configuration names (Einrichten eines DSC-Pullclients mithilfe von Konfigurationsnamen)</span><span class="sxs-lookup"><span data-stu-id="a2fad-234">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="a2fad-235">Teilkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="a2fad-235">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="a2fad-236">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a2fad-236">See also</span></span>

- [<span data-ttu-id="a2fad-237">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="a2fad-237">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="a2fad-238">Inkraftsetzung von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="a2fad-238">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="a2fad-239">Verwenden eines DSC-Berichtsservers</span><span class="sxs-lookup"><span data-stu-id="a2fad-239">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="a2fad-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol ([MS-DSCPM]: DSC-Pullmodell-Protokoll)](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span><span class="sxs-lookup"><span data-stu-id="a2fad-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span></span>
- <span data-ttu-id="a2fad-241">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol ([MS-DSCPM]: DSC-Pullmodell-Protokoll Errata)](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span><span class="sxs-lookup"><span data-stu-id="a2fad-241">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span></span>
