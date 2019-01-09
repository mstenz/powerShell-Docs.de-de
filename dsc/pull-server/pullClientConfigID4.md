---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401757"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="d4eb8-103">Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="d4eb8-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="d4eb8-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d4eb8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4eb8-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="d4eb8-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="d4eb8-107">Vor dem Einrichten eines pullclients festlegen, sollten Sie eine Pull-Server einrichten.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="d4eb8-108">Obwohl diese Reihenfolge nicht erforderlich ist, hilft bei der Problembehandlung, und hilft Ihnen, stellen Sie sicher, dass die Registrierung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="d4eb8-109">Informationen zum Einrichten eines pullservers, können Sie die folgenden Handbüchern:</span><span class="sxs-lookup"><span data-stu-id="d4eb8-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="d4eb8-110">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="d4eb8-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="d4eb8-111">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="d4eb8-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="d4eb8-112">Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="d4eb8-113">In den folgenden Abschnitten gezeigt, wie einen pullclient mit einem SMB-Freigabe oder ein HTTP-DSC-Pull-Server zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="d4eb8-114">Wenn des Knotens LCM aktualisiert, wird es an den konfigurierten Speicherort zugewiesene Konfigurationen herunterladen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="d4eb8-115">Wenn alle erforderlichen Ressourcen nicht auf dem Knoten vorhanden sind, werden sie automatisch aus dem konfigurierten Speicherort heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="d4eb8-116">Wenn der Knoten mit konfiguriert ist ein [Berichtsserver](reportServer.md), er meldet klicken Sie dann den Status des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="d4eb8-117">Konfigurieren Sie den LCM-Pull-client</span><span class="sxs-lookup"><span data-stu-id="d4eb8-117">Configure the pull client LCM</span></span>

<span data-ttu-id="d4eb8-118">Ausführen von den folgenden Beispielen erstellt einen neuen Ausgabeordner mit dem Namen **PullClientConfigID** und fügt Sie einer MOF-metakonfigurationsdatei vorhanden.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="d4eb8-119">In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="d4eb8-120">Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="d4eb8-121">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d4eb8-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="d4eb8-122">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="d4eb8-122">Configuration ID</span></span>

<span data-ttu-id="d4eb8-123">In den Beispielen unten Satz der **ConfigurationID** -Eigenschaft des LCM auf eine **Guid** , wurde zuvor für diesen Zweck erstellt.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="d4eb8-124">Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="d4eb8-125">Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="d4eb8-126">Weitere Informationen finden Sie unter [Konfigurationen veröffentlichen, um einen Pull-Server (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="d4eb8-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="d4eb8-127">Sie können einen zufälligen erstellen **Guid** verwenden das folgende Beispiel.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="d4eb8-128">Ein Pull-Client zum Herunterladen von Konfigurationen einrichten</span><span class="sxs-lookup"><span data-stu-id="d4eb8-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="d4eb8-129">Jeder Client muss konfiguriert werden, **Pull** Modus und die Pull-Server-Url angegeben werden, in die Konfiguration gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="d4eb8-130">Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="d4eb8-131">Zum Konfigurieren des LCM müssen Sie eine besondere Art von Konfiguration erstellen, mit einem **"localconfigurationmanager"** Block.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="d4eb8-132">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="d4eb8-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="d4eb8-133">HTTP-DSC-Pullserver</span><span class="sxs-lookup"><span data-stu-id="d4eb8-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="d4eb8-134">Wenn der Pull-Server als Webdienst eingerichtet ist, legen Sie die **DownloadManagerName** zu **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="d4eb8-135">Die **WebDownloadManager** erfordert die Angabe ein **ServerUrl** auf die **DownloadManagerCustomData** Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="d4eb8-136">Sie können auch angeben, einen Wert für **AllowUnsecureConnection**, wie im folgenden Beispiel.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="d4eb8-137">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „PullServer“.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="d4eb8-138">SMB-Freigabe</span><span class="sxs-lookup"><span data-stu-id="d4eb8-138">SMB Share</span></span>

<span data-ttu-id="d4eb8-139">Wenn der Pull-Server als SMB-Dateifreigabe, anstatt eines Webdiensts eingerichtet ist, legen Sie die **DownloadManagerName** zu **DscFileDownloadManager** anstelle der **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="d4eb8-140">Die **DscFileDownloadManager** erfordert die Angabe einer **SourcePath** -Eigenschaft in der **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="d4eb8-141">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einer SMB-Freigabe namens „SmbDscShare“ auf einem Server namens „CONTOSO-SERVER“.</span><span class="sxs-lookup"><span data-stu-id="d4eb8-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="d4eb8-142">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="d4eb8-142">Next Steps</span></span>

<span data-ttu-id="d4eb8-143">Nachdem der Pull-Client konfiguriert wurde, können Sie die folgenden Anleitungen, die nächsten Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d4eb8-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="d4eb8-144">Veröffentlichen von Konfigurationen auf einem Pullserver (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="d4eb8-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="d4eb8-145">Verpacken und Hochladen von Ressourcen auf einen Pullserver (v4)</span><span class="sxs-lookup"><span data-stu-id="d4eb8-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="d4eb8-146">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d4eb8-146">See Also</span></span>

- [<span data-ttu-id="d4eb8-147">Einrichten eines DSC-webpullservers</span><span class="sxs-lookup"><span data-stu-id="d4eb8-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="d4eb8-148">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="d4eb8-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
