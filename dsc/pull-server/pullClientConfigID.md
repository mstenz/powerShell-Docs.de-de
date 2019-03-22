---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pullclients mit Konfigurations-IDs in PowerShell 5.0 und höher
ms.openlocfilehash: 14db98d240bc87aca3ee985db08c14b7c65d8bb8
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055715"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="b42b9-103">Einrichten eines Pullclients mit Konfigurations-IDs in PowerShell 5.0 und höher</span><span class="sxs-lookup"><span data-stu-id="b42b9-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="b42b9-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b42b9-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b42b9-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b42b9-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b42b9-107">Bevor Sie einen Pullclient einrichten, sollten Sie einen Pullserver einrichten.</span><span class="sxs-lookup"><span data-stu-id="b42b9-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="b42b9-108">Diese Reihenfolge ist zwar nicht erforderlich, jedoch hilft sie bei der Problembehandlung und unterstützt Sie dabei, sicherzustellen, dass die Registrierung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="b42b9-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="b42b9-109">Sie können eine der folgenden Führungslinien zum Einrichten eines Pullservers verwenden:</span><span class="sxs-lookup"><span data-stu-id="b42b9-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="b42b9-110">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="b42b9-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b42b9-111">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="b42b9-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b42b9-112">Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b42b9-113">In den folgenden Abschnitten wird veranschaulicht, wie Sie einen Pullclient mit einer SMB-Freigabe oder einem HTTP-DSC-Pullserver konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="b42b9-114">Wenn der lokale Konfigurations-Manager des Knotens aktualisiert wird, wendet dieser sich an den konfigurierten Speicherort, um zugewiesene Konfigurationen herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="b42b9-115">Wenn erforderliche Ressourcen nicht auf dem Knoten vorhanden sind, werden diese automatisch vom konfigurierten Speicherort heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="b42b9-116">Wenn der Knoten mit einem [Berichtsserver](reportServer.md) konfiguriert wurde, wird anschließend der Status des Vorgangs gemeldet.</span><span class="sxs-lookup"><span data-stu-id="b42b9-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="b42b9-117">Dieser Artikel gilt nur für PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b42b9-117">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="b42b9-118">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="b42b9-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="b42b9-119">Konfigurieren des lokalen Konfigurations-Managers für den Pullclient</span><span class="sxs-lookup"><span data-stu-id="b42b9-119">Configure the pull client LCM</span></span>

<span data-ttu-id="b42b9-120">Durch Ausführen der folgenden Beispiele wird ein neuer Ausgabeordner namens **PullClientConfigID** erstellt, und in diesem wird eine MOF-Datei mit der Metakonfiguration platziert.</span><span class="sxs-lookup"><span data-stu-id="b42b9-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="b42b9-121">In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="b42b9-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="b42b9-122">Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="b42b9-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="b42b9-123">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b42b9-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="b42b9-124">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="b42b9-124">Configuration ID</span></span>

<span data-ttu-id="b42b9-125">In den folgenden Beispielen wird die Eigenschaft **ConfigurationID** des lokalen Konfigurations-Managers auf eine **GUID** festgelegt, die zuvor zu diesem Zweck erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="b42b9-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="b42b9-126">Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver.</span><span class="sxs-lookup"><span data-stu-id="b42b9-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="b42b9-127">Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="b42b9-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="b42b9-128">Weitere Informationen finden Sie unter [Publish Configurations to a Pull Server (v4/v5) (Veröffentlichen von Konfigurationen für einen Pullserver (PowerShell 4.0 und 5.0))](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="b42b9-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="b42b9-129">Sie können eine zufällige **GUID** mithilfe des folgenden Beispiels oder des Cmdlets [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) erstellen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="b42b9-130">Weitere Informationen zur Verwendung von **GUIDs** in Ihrer Umgebung finden Sie unter [Plan for Guids (Planen von GUIDs)](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="b42b9-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="b42b9-131">Einrichten eines Pullclients zum Herunterladen von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="b42b9-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="b42b9-132">Jeder Client muss im Modus **Pull** konfiguriert werden und mit der Pullserver-URL zum Speicherort der Konfiguration versehen werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="b42b9-133">Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="b42b9-134">Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs.</span><span class="sxs-lookup"><span data-stu-id="b42b9-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="b42b9-135">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="b42b9-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="b42b9-136">HTTP-DSC-Pullserver</span><span class="sxs-lookup"><span data-stu-id="b42b9-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="b42b9-137">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“.</span><span class="sxs-lookup"><span data-stu-id="b42b9-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="b42b9-138">Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="b42b9-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="b42b9-139">**ServerUrl** gibt die URL für den DSC-Pull an.</span><span class="sxs-lookup"><span data-stu-id="b42b9-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="b42b9-140">SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="b42b9-140">SMB Share</span></span>

<span data-ttu-id="b42b9-141">Mit dem folgenden Skript wird der lokale Konfigurations-Manager zum Pullen von Konfigurationen aus der SMB-Freigabe `\\SMBPullServer\Pull` konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="b42b9-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="b42b9-142">Der **ConfigurationRepositoryShare**-Block im Skript definiert den Pullserver, bei dem es sich in diesem Fall lediglich um eine SMB-Freigabe handelt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="b42b9-143">Einrichten eines Pullclients zum Herunterladen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="b42b9-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="b42b9-144">Wenn Sie nur den **ConfigurationRepositoryWeb**- oder den **ConfigurationRepositoryShare**-Block in Ihrer Konfiguration für den lokalen Konfigurations-Manager angeben (wie in den vorherigen Beispielen), ruft der Pullclient die Ressourcen vom gleichen Speicherort wie die Konfigurationen per Pull ab.</span><span class="sxs-lookup"><span data-stu-id="b42b9-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="b42b9-145">Sie können auch einen separaten Speicherort für Ressourcen festlegen.</span><span class="sxs-lookup"><span data-stu-id="b42b9-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="b42b9-146">Verwenden Sie den **ResourceRepositoryWeb**-Block zum Festlegen eines Ressourcenspeicherorts als separater Server.</span><span class="sxs-lookup"><span data-stu-id="b42b9-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="b42b9-147">Verwenden Sie den **ResourceRepositoryShare**-Block zum Festlegen eines Ressourcenspeicherorts als SMB-Freigabe.</span><span class="sxs-lookup"><span data-stu-id="b42b9-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="b42b9-148">Sie können **ConfigurationRepositoryWeb** mit **ResourceRepositoryShare** oder **ConfigurationRepositoryShare** mit **ResourceRepositoryWeb** kombinieren.</span><span class="sxs-lookup"><span data-stu-id="b42b9-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="b42b9-149">Hierfür werden keine Beispiele gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b42b9-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="b42b9-150">HTTP-DSC-Pullserver</span><span class="sxs-lookup"><span data-stu-id="b42b9-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="b42b9-151">Mit der folgenden Metakonfiguration wird ein Pullclient zum Abrufen der Konfigurationen von **CONTOSO-PullSrv** und der Ressourcen von **CONTOSO-ResourceSrv** konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="b42b9-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="b42b9-152">SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="b42b9-152">SMB Share</span></span>

<span data-ttu-id="b42b9-153">Im folgenden Beispiel wird eine Metakonfiguration gezeigt, die einen Client zum Pullen von Konfigurationen aus der SMB-Freigabe `\\SMBPullServer\Configurations` und Ressourcen aus der SMB-Freigabe `\\SMBPullServer\Resources` einrichtet.</span><span class="sxs-lookup"><span data-stu-id="b42b9-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="b42b9-154">Automatisches Herunterladen von Ressourcen im Pushmodus</span><span class="sxs-lookup"><span data-stu-id="b42b9-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="b42b9-155">Ab PowerShell 5.0 können Ihre Pullclients Module aus einer SMB-Freigabe auch dann herunterladen, wenn sie für den **Pushmodus** konfiguriert sind.</span><span class="sxs-lookup"><span data-stu-id="b42b9-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="b42b9-156">Dies ist insbesondere in Szenarios hilfreich, in denen Sie keinen Pullserver einrichten möchten.</span><span class="sxs-lookup"><span data-stu-id="b42b9-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="b42b9-157">Der **ResourceRepositoryShare**-Block kann ohne Festlegen von **ConfigurationRepositoryShare** verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="b42b9-158">Im folgenden Beispiel wird eine Metakonfiguration gezeigt, die einen Client zum Pullen von Ressourcen aus der SMB-Freigabe `\\SMBPullServer\Resources` einrichtet.</span><span class="sxs-lookup"><span data-stu-id="b42b9-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="b42b9-159">Wenn der Knoten eine Konfiguration per **PUSH** übertragen hat, lädt er automatisch alle erforderlichen Ressourcen von der angegebenen Freigabe herunter.</span><span class="sxs-lookup"><span data-stu-id="b42b9-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="b42b9-160">Einrichten eines Pullclients zum Berichten des Status</span><span class="sxs-lookup"><span data-stu-id="b42b9-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="b42b9-161">Knoten senden standardmäßig keine Berichte an einen konfigurierten Pullserver.</span><span class="sxs-lookup"><span data-stu-id="b42b9-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="b42b9-162">Sie können für Konfigurationen, Ressourcen und Berichte einen einzigen Pullserver verwenden, allerdings müssen Sie einen **ReportRepositoryWeb**-Block erstellen, um die Berichterstattung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="b42b9-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="b42b9-163">HTTP-DSC-Pullserver</span><span class="sxs-lookup"><span data-stu-id="b42b9-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="b42b9-164">Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="b42b9-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="b42b9-165">Um einen Berichtsserver anzugeben, verwenden Sie einen **ReportRepositoryWeb**-Block.</span><span class="sxs-lookup"><span data-stu-id="b42b9-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="b42b9-166">Ein Berichtsserver kann kein SMB-Server sein.</span><span class="sxs-lookup"><span data-stu-id="b42b9-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="b42b9-167">Die folgende Metakonfiguration konfiguriert einen Pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von**CONTOSO-ResourceSrv** und Senden von Statusberichten an **CONTOSO-ReportSrv**.</span><span class="sxs-lookup"><span data-stu-id="b42b9-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="b42b9-168">SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="b42b9-168">SMB Share</span></span>

<span data-ttu-id="b42b9-169">Ein Berichtsserver kann keine SMB-Freigabe sein.</span><span class="sxs-lookup"><span data-stu-id="b42b9-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b42b9-170">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b42b9-170">Next Steps</span></span>

<span data-ttu-id="b42b9-171">Sobald der Pullclient konfiguriert wurde, können Sie die folgenden Leitfäden zum Durchführen der nächsten Schritte verwenden:</span><span class="sxs-lookup"><span data-stu-id="b42b9-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="b42b9-172">Veröffentlichen von Konfigurationen auf einem Pullserver (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="b42b9-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="b42b9-173">Verpacken und Hochladen von Ressourcen auf einen Pullserver (v4)</span><span class="sxs-lookup"><span data-stu-id="b42b9-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="b42b9-174">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b42b9-174">See Also</span></span>

* [<span data-ttu-id="b42b9-175">Einrichten eines Pullclients mit Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="b42b9-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
