---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pullclients mit Konfigurationsnamen in PowerShell 5.0 und höher
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953627"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="f126c-103">Einrichten eines Pullclients mit Konfigurationsnamen in PowerShell 5.0 und höher</span><span class="sxs-lookup"><span data-stu-id="f126c-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="f126c-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f126c-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f126c-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="f126c-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="f126c-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="f126c-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="f126c-107">Bevor Sie einen Pullclient einrichten, sollten Sie einen Pullserver einrichten.</span><span class="sxs-lookup"><span data-stu-id="f126c-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="f126c-108">Diese Reihenfolge ist zwar nicht erforderlich, jedoch hilft sie bei der Problembehandlung und unterstützt Sie dabei, sicherzustellen, dass die Registrierung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="f126c-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="f126c-109">Sie können eine der folgenden Führungslinien zum Einrichten eines Pullservers verwenden:</span><span class="sxs-lookup"><span data-stu-id="f126c-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="f126c-110">Einrichten eines DSC-SMB-Pullservers</span><span class="sxs-lookup"><span data-stu-id="f126c-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="f126c-111">Einrichten eines DSC-HTTP-Pullservers</span><span class="sxs-lookup"><span data-stu-id="f126c-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="f126c-112">Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="f126c-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="f126c-113">In den folgenden Abschnitten wird veranschaulicht, wie Sie einen Pullclient mit einer SMB-Freigabe oder einem HTTP-DSC-Pullserver konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="f126c-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="f126c-114">Wenn der lokale Konfigurations-Manager des Knotens aktualisiert wird, wendet dieser sich an den konfigurierten Speicherort, um zugewiesene Konfigurationen herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="f126c-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="f126c-115">Wenn erforderliche Ressourcen nicht auf dem Knoten vorhanden sind, werden diese automatisch vom konfigurierten Speicherort heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="f126c-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="f126c-116">Wenn der Knoten mit einem [Berichtsserver](reportServer.md) konfiguriert wurde, wird anschließend der Status des Vorgangs gemeldet.</span><span class="sxs-lookup"><span data-stu-id="f126c-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="f126c-117">Dieser Artikel gilt nur für PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="f126c-117">This topic applies to PowerShell 5.0.</span></span>
> <span data-ttu-id="f126c-118">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Set up a pull client using configuration ID in PowerShell 4.0 (Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0)](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="f126c-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="f126c-119">Konfigurieren des lokalen Konfigurations-Managers für den Pullclient</span><span class="sxs-lookup"><span data-stu-id="f126c-119">Configure the pull client LCM</span></span>

<span data-ttu-id="f126c-120">Durch Ausführen der folgenden Beispiele wird ein neuer Ausgabeordner namens **PullClientConfigName** erstellt, und in diesem wird eine MOF-Datei mit der Metakonfiguration platziert.</span><span class="sxs-lookup"><span data-stu-id="f126c-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="f126c-121">In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="f126c-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="f126c-122">Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="f126c-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="f126c-123">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f126c-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="f126c-124">Konfigurationsname</span><span class="sxs-lookup"><span data-stu-id="f126c-124">Configuration Name</span></span>

<span data-ttu-id="f126c-125">In den folgenden Beispielen wird die Eigenschaft **ConfigurationName** des lokalen Konfigurations-Managers auf den Namen einer zuvor kompilierten Konfiguration festgelegt, die zu diesem Zweck erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="f126c-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="f126c-126">Der lokale Konfigurations-Manager verwenden die Eigenschaft **ConfigurationName**, um die entsprechende Konfiguration auf dem Pullserver zu finden.</span><span class="sxs-lookup"><span data-stu-id="f126c-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="f126c-127">Die MOF-Datei für die Konfiguration auf dem Pullserver muss den Namen `<ConfigurationName>.mof` haben, in diesem Fall lautet er „ClientConfig.mof“.</span><span class="sxs-lookup"><span data-stu-id="f126c-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="f126c-128">Weitere Informationen finden Sie unter [Publish Configurations to a Pull Server (v4/v5) (Veröffentlichen von Konfigurationen für einen Pullserver (PowerShell 4.0 und 5.0))](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="f126c-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="f126c-129">Einrichten eines Pullclients zum Herunterladen von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="f126c-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="f126c-130">Jeder Client muss im Modus **Pull** konfiguriert werden und mit der Pullserver-URL zum Speicherort der Konfiguration versehen werden.</span><span class="sxs-lookup"><span data-stu-id="f126c-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="f126c-131">Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="f126c-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="f126c-132">Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs.</span><span class="sxs-lookup"><span data-stu-id="f126c-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="f126c-133">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="f126c-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="f126c-134">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“.</span><span class="sxs-lookup"><span data-stu-id="f126c-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="f126c-135">Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="f126c-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="f126c-136">Die **ServerURL**-Eigenschaft gibt den Endpunkt für den Pullserver an.</span><span class="sxs-lookup"><span data-stu-id="f126c-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="f126c-137">Die **RegistrationKey**-Eigenschaft ist ein freigegebener Schlüssel zwischen allen Clientknoten für einen Pullserver und dem jeweiligen Pullserver.</span><span class="sxs-lookup"><span data-stu-id="f126c-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="f126c-138">Der gleiche Wert wird in einer Datei auf dem Pullserver gespeichert.</span><span class="sxs-lookup"><span data-stu-id="f126c-138">The same value is stored in a file on the pull server.</span></span>
  > [!NOTE]
  > <span data-ttu-id="f126c-139">Registrierungsschlüssel funktionieren nur mit **Webpullservern**.</span><span class="sxs-lookup"><span data-stu-id="f126c-139">Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="f126c-140">Bei einem **SMB**-Pullserver müssen Sie **ConfigurationID** weiterhin verwenden.</span><span class="sxs-lookup"><span data-stu-id="f126c-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="f126c-141">Informationen zum Konfigurieren eines Pullservers unter Verwendung von **ConfigurationID** finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID](pullClientConfigId.md).</span><span class="sxs-lookup"><span data-stu-id="f126c-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="f126c-142">Die **ConfigurationNames**-Eigenschaft ist ein Array, das die Namen der Konfigurationen angibt, die für den Clientknoten vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="f126c-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="f126c-143">**Hinweis:** Bei Angabe mehrerer Werte unter **ConfigurationNames** müssen Sie auch **PartialConfiguration**-Blöcke in Ihrer Konfiguration angeben.</span><span class="sxs-lookup"><span data-stu-id="f126c-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="f126c-144">Informationen zu partiellen Konfigurationen finden Sie unter [PowerShell DSC – Teilkonfigurationen](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="f126c-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="f126c-145">Einrichten eines Pullclients zum Herunterladen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="f126c-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="f126c-146">Wenn Sie nur den **ConfigurationRepositoryWeb**- oder den **ConfigurationRepositoryShare**-Block in Ihrer Konfiguration für den lokalen Konfigurations-Manager angeben (wie im vorherigen Beispiel), ruft der Pullclient die Ressourcen vom gleichen Speicherort per Pull ab, an dem Ihre MOF-Dateien gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="f126c-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="f126c-147">Sie können auch andere Speicherorte angeben, von denen Clients Ressourcen herunterladen können.</span><span class="sxs-lookup"><span data-stu-id="f126c-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="f126c-148">Um einen Ressourcenserver anzugeben, verwenden Sie entweder einen **ResourceRepositoryWeb**-Block (für einen Webpullserver) oder einen **ResourceRepositoryShare**-Block (für einen SMB-Pullserver).</span><span class="sxs-lookup"><span data-stu-id="f126c-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="f126c-149">Im folgenden Beispiel wird eine Metakonfiguration gezeigt, die einen Client zum Herunterladen von Konfigurationen von einem Pullserver und Ressourcen aus einer SMB-Freigabe einrichtet.</span><span class="sxs-lookup"><span data-stu-id="f126c-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="f126c-150">Einrichten eines Pullclients zum Berichten des Status</span><span class="sxs-lookup"><span data-stu-id="f126c-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="f126c-151">Sie können einen einzelnen Pullserver für Konfigurationen, Ressourcen und Berichte verwenden.</span><span class="sxs-lookup"><span data-stu-id="f126c-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="f126c-152">Die Berichterstellung ist standardmäßig nicht für Clients konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="f126c-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="f126c-153">Sie müssen einen **ReportRepositoryWeb**-Block erstellen, um einen Client zum Berichten des Status zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="f126c-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="f126c-154">Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="f126c-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="f126c-155">Ein Berichtsserver kann keine SMB-Freigabe sein.</span><span class="sxs-lookup"><span data-stu-id="f126c-155">A report server cannot be an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="f126c-156">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f126c-156">See Also</span></span>

* [<span data-ttu-id="f126c-157">Einrichten eines Pullclients mit Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="f126c-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="f126c-158">Einrichten eines DSC-Webpullservers</span><span class="sxs-lookup"><span data-stu-id="f126c-158">Setting up a DSC web pull server</span></span>](pullServer.md)
