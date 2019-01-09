---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 5.0 und höher
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401601"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="dfa10-103">Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 5.0 und höher</span><span class="sxs-lookup"><span data-stu-id="dfa10-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="dfa10-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dfa10-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfa10-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="dfa10-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="dfa10-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="dfa10-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="dfa10-107">Vor dem Einrichten eines pullclients festlegen, sollten Sie eine Pull-Server einrichten.</span><span class="sxs-lookup"><span data-stu-id="dfa10-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="dfa10-108">Obwohl diese Reihenfolge nicht erforderlich ist, hilft bei der Problembehandlung, und hilft Ihnen, stellen Sie sicher, dass die Registrierung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="dfa10-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="dfa10-109">Informationen zum Einrichten eines pullservers, können Sie die folgenden Handbüchern:</span><span class="sxs-lookup"><span data-stu-id="dfa10-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="dfa10-110">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="dfa10-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="dfa10-111">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="dfa10-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="dfa10-112">Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="dfa10-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="dfa10-113">In den folgenden Abschnitten gezeigt, wie einen pullclient mit einem SMB-Freigabe oder ein HTTP-DSC-Pull-Server zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="dfa10-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="dfa10-114">Wenn des Knotens LCM aktualisiert, wird es an den konfigurierten Speicherort zugewiesene Konfigurationen herunterladen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="dfa10-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="dfa10-115">Wenn alle erforderlichen Ressourcen nicht auf dem Knoten vorhanden sind, werden sie automatisch aus dem konfigurierten Speicherort heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="dfa10-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="dfa10-116">Wenn der Knoten mit konfiguriert ist ein [Berichtsserver](reportServer.md), er meldet klicken Sie dann den Status des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="dfa10-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="dfa10-117">**Hinweis**: Dieses Thema gilt für PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="dfa10-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="dfa10-118">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="dfa10-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="dfa10-119">Konfigurieren Sie den LCM-Pull-client</span><span class="sxs-lookup"><span data-stu-id="dfa10-119">Configure the pull client LCM</span></span>

<span data-ttu-id="dfa10-120">Ausführen von den folgenden Beispielen erstellt einen neuen Ausgabeordner mit dem Namen **PullClientConfigID** und fügt Sie einer MOF-metakonfigurationsdatei vorhanden.</span><span class="sxs-lookup"><span data-stu-id="dfa10-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="dfa10-121">In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="dfa10-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="dfa10-122">Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="dfa10-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="dfa10-123">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="dfa10-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="dfa10-124">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="dfa10-124">Configuration ID</span></span>

<span data-ttu-id="dfa10-125">In den Beispielen unten legt der **ConfigurationID** -Eigenschaft des LCM auf eine **Guid** , wurde zuvor für diesen Zweck erstellt.</span><span class="sxs-lookup"><span data-stu-id="dfa10-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="dfa10-126">Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver.</span><span class="sxs-lookup"><span data-stu-id="dfa10-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="dfa10-127">Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="dfa10-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="dfa10-128">Weitere Informationen finden Sie unter [Konfigurationen veröffentlichen, um einen Pull-Server (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="dfa10-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="dfa10-129">Sie können einen zufälligen erstellen **Guid** verwenden Sie das Beispiel unten oder mithilfe der [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dfa10-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="dfa10-130">Weitere Informationen zur Verwendung von **Guids** in Ihrer Umgebung finden Sie unter [Guids planen](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="dfa10-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="dfa10-131">Ein Pull-Client zum Herunterladen von Konfigurationen einrichten</span><span class="sxs-lookup"><span data-stu-id="dfa10-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="dfa10-132">Jeder Client muss konfiguriert werden, **Pull** Modus und die Pull-Server-Url angegeben werden, in die Konfiguration gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="dfa10-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="dfa10-133">Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="dfa10-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="dfa10-134">Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs.</span><span class="sxs-lookup"><span data-stu-id="dfa10-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="dfa10-135">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="dfa10-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="dfa10-136">HTTP-DSC-Pullserver</span><span class="sxs-lookup"><span data-stu-id="dfa10-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="dfa10-137">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“.</span><span class="sxs-lookup"><span data-stu-id="dfa10-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="dfa10-138">Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="dfa10-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="dfa10-139">Die **ServerUrl** gibt die Url der DSC-Pull</span><span class="sxs-lookup"><span data-stu-id="dfa10-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="dfa10-140">SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="dfa10-140">SMB Share</span></span>

<span data-ttu-id="dfa10-141">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen aus der SMB-Freigabe `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="dfa10-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="dfa10-142">Im Skript die **ConfigurationRepositoryShare** -Block definiert die Pull-Server, die in diesem Fall nur eine SMB-Freigabe ist.</span><span class="sxs-lookup"><span data-stu-id="dfa10-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="dfa10-143">Richten Sie einen Pull-Client Ressourcen herunterladen</span><span class="sxs-lookup"><span data-stu-id="dfa10-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="dfa10-144">Wenn Sie nur angeben, die **ConfigurationRepositoryWeb** oder **ConfigurationRepositoryShare** -block in Ihrer LCM-Konfiguration (wie im vorherigen Beispiel), der pullclient Ressourcen aus der gleichen der Speicherort abgerufen, die Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="dfa10-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="dfa10-145">Sie können auch separate Standorte für Ressourcen angeben.</span><span class="sxs-lookup"><span data-stu-id="dfa10-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="dfa10-146">Um einen Ressourcenspeicherort als separater Server anzugeben, verwenden die **ResourceRepositoryWeb** Block.</span><span class="sxs-lookup"><span data-stu-id="dfa10-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="dfa10-147">Verwenden Sie zum Angeben eines Speicherorts für die Ressource als eine SMB-Freigabe der **ResourceRepositoryShare** Block.</span><span class="sxs-lookup"><span data-stu-id="dfa10-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="dfa10-148">Sie können kombinieren **ConfigurationRepositoryWeb** mit **ResourceRepositoryShare** oder **ConfigurationRepositoryShare** mit **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="dfa10-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="dfa10-149">Beispiele hierfür sind unten nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="dfa10-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="dfa10-150">HTTP-DSC-Pullserver</span><span class="sxs-lookup"><span data-stu-id="dfa10-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="dfa10-151">Die folgende metakonfiguration konfiguriert einen pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="dfa10-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="dfa10-152">SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="dfa10-152">SMB Share</span></span>

<span data-ttu-id="dfa10-153">Das folgende Beispiel zeigt eine metakonfiguration, mit dem ein Client zum Abrufen von Konfigurationen aus der SMB-Freigabe eingerichtet `\\SMBPullServer\Configurations`, und Ressourcen aus der SMB-Freigabe `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="dfa10-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="dfa10-154">Herunterladen Sie automatisch, Ressourcen im Modus mithilfe von Push übertragen</span><span class="sxs-lookup"><span data-stu-id="dfa10-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="dfa10-155">Ab PowerShell 5.0 können Ihre pullclients können-Module herunterladen von einer SMB-Freigabe, selbst wenn sie für konfiguriert sind **Push** Modus.</span><span class="sxs-lookup"><span data-stu-id="dfa10-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="dfa10-156">Dies ist besonders nützlich in Szenarien, in denen Sie nicht, um eine Pull-Server einzurichten möchten.</span><span class="sxs-lookup"><span data-stu-id="dfa10-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="dfa10-157">Die **ResourceRepositoryShare** Block kann verwendet werden, ohne Angabe einer **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="dfa10-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="dfa10-158">Das folgende Beispiel zeigt eine metakonfiguration, mit dem ein Client zum Abrufen von Ressourcen aus einer SMB-Dateifreigabe eingerichtet `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="dfa10-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="dfa10-159">Wenn der Knoten ist **PUSHED** eine Konfiguration, es werden automatisch herunterladen, alle erforderlichen Ressourcen, aus der angegebenen Freigabe.</span><span class="sxs-lookup"><span data-stu-id="dfa10-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="dfa10-160">Richten Sie einen Pull-Client zum Melden von status</span><span class="sxs-lookup"><span data-stu-id="dfa10-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="dfa10-161">Standardmäßig werden der Knoten Berichte nicht mit einem konfigurierten Pull-Server senden.</span><span class="sxs-lookup"><span data-stu-id="dfa10-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="dfa10-162">Sie können für Konfigurationen, Ressourcen und Berichte einen einzigen Pullserver verwenden, allerdings müssen Sie einen **ReportRepositoryWeb**-Block erstellen, um die Berichterstattung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="dfa10-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="dfa10-163">HTTP-DSC-Pullserver</span><span class="sxs-lookup"><span data-stu-id="dfa10-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="dfa10-164">Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="dfa10-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="dfa10-165">Um einen Berichtsserver anzugeben, verwenden Sie einen **ReportRepositoryWeb**-Block.</span><span class="sxs-lookup"><span data-stu-id="dfa10-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="dfa10-166">Ein Berichtsserver kann kein SMB-Server sein.</span><span class="sxs-lookup"><span data-stu-id="dfa10-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="dfa10-167">Die folgende Metakonfiguration konfiguriert einen Pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von**CONTOSO-ResourceSrv** und Senden von Statusberichten an **CONTOSO-ReportSrv**.</span><span class="sxs-lookup"><span data-stu-id="dfa10-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="dfa10-168">SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="dfa10-168">SMB Share</span></span>

<span data-ttu-id="dfa10-169">Ein Berichtsserver eine SMB-Freigabe nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="dfa10-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dfa10-170">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="dfa10-170">Next Steps</span></span>

<span data-ttu-id="dfa10-171">Nachdem der Pull-Client konfiguriert wurde, können Sie die folgenden Anleitungen, die nächsten Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="dfa10-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="dfa10-172">Veröffentlichen von Konfigurationen auf einem Pullserver (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="dfa10-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="dfa10-173">Verpacken und Hochladen von Ressourcen auf einen Pullserver (v4)</span><span class="sxs-lookup"><span data-stu-id="dfa10-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="dfa10-174">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="dfa10-174">See Also</span></span>

* [<span data-ttu-id="dfa10-175">Einrichten eines Pullclients mit Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="dfa10-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
