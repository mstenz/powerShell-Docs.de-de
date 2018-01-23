---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pullclients mithilfe von Konfigurationsnamen
ms.openlocfilehash: 11de53fc349ce0ebacf0d4855d82fa8a22d55c99
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-pull-client-using-configuration-names"></a><span data-ttu-id="9b310-103">Einrichten eines Pullclients mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="9b310-103">Setting up a pull client using configuration names</span></span>

> <span data-ttu-id="9b310-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9b310-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9b310-105">Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL angegeben werden, unter der der Pullserver zum Abrufen von Konfigurationen kontaktiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="9b310-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span>
<span data-ttu-id="9b310-106">Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="9b310-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span>
<span data-ttu-id="9b310-107">Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs.</span><span class="sxs-lookup"><span data-stu-id="9b310-107">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span>
<span data-ttu-id="9b310-108">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="9b310-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="9b310-109">**Hinweis**: Dieses Thema gilt für PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="9b310-109">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="9b310-110">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="9b310-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="9b310-111">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“:</span><span class="sxs-lookup"><span data-stu-id="9b310-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv":</span></span>

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

<span data-ttu-id="9b310-112">Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="9b310-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span>
<span data-ttu-id="9b310-113">Die **ServerURL**-Eigenschaft gibt den Endpunkt für den Pullserver an.</span><span class="sxs-lookup"><span data-stu-id="9b310-113">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

<span data-ttu-id="9b310-114">Die **RegistrationKey**-Eigenschaft ist ein freigegebener Schlüssel zwischen allen Clientknoten für einen Pullserver und dem jeweiligen Pullserver.</span><span class="sxs-lookup"><span data-stu-id="9b310-114">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span>
<span data-ttu-id="9b310-115">Der gleiche Wert wird in einer Datei auf dem Pullserver gespeichert.</span><span class="sxs-lookup"><span data-stu-id="9b310-115">The same value is stored in a file on the pull server.</span></span>

<span data-ttu-id="9b310-116">Die **ConfigurationNames**-Eigenschaft ist ein Array, das die Namen der Konfigurationen angibt, die für den Clientknoten vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="9b310-116">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
<span data-ttu-id="9b310-117">Auf dem Pullserver muss die MOF-Konfigurationsdatei für diesen Clientknoten „*ConfigurationNames*.mof“ heißen, wobei *ConfigurationNames* dem Wert der **ConfigurationNames**-Eigenschaft entspricht, die Sie in dieser Metakonfiguration festlegen.</span><span class="sxs-lookup"><span data-stu-id="9b310-117">On the pull server, the configuration MOF file for this client node must be named *ConfigurationNames*.mof, where *ConfigurationNames* matches the value of the **ConfigurationNames** property you set in this metaconfiguration.</span></span>

><span data-ttu-id="9b310-118">**Hinweis:** Bei Angabe mehrerer Werte unter **ConfigurationNames** müssen Sie auch **PartialConfiguration**-Blöcke in Ihrer Konfiguration angeben.</span><span class="sxs-lookup"><span data-stu-id="9b310-118">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
<span data-ttu-id="9b310-119">Informationen zu partiellen Konfigurationen finden Sie unter [PowerShell DSC – Teilkonfigurationen](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="9b310-119">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

<span data-ttu-id="9b310-120">Nachdem das Skript ausgeführt wurde, erstellt es einen neuen Ausgabeordner mit dem Namen **PullClientConfigNames**, der eine MOF-Datei mit der Metakonfiguration enthält.</span><span class="sxs-lookup"><span data-stu-id="9b310-120">After this script runs, it creates a new output folder named **PullClientConfigNames** and puts a metaconfiguration MOF file there.</span></span>
<span data-ttu-id="9b310-121">In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="9b310-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="9b310-122">Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="9b310-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span>

```powershell
Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigNames –Verbose.
```

> <span data-ttu-id="9b310-123">**Hinweis**: Registrierungsschlüssel funktionieren nur mit dem Webpullserver.</span><span class="sxs-lookup"><span data-stu-id="9b310-123">**Note**: Registration keys work only with web pull servers.</span></span>
<span data-ttu-id="9b310-124">Bei einem SMB-Pullserver müssen Sie **ConfigurationID** weiterhin verwenden.</span><span class="sxs-lookup"><span data-stu-id="9b310-124">You must still use **ConfigurationID** with an SMB pull server.</span></span>
<span data-ttu-id="9b310-125">Informationen zum Konfigurieren eines Pullservers unter Verwendung von **ConfigurationID** finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID](PullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="9b310-125">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](PullClientConfigNames.md)</span></span>

## <a name="resource-and-report-servers"></a><span data-ttu-id="9b310-126">Ressourcen und Berichtsserver</span><span class="sxs-lookup"><span data-stu-id="9b310-126">Resource and report servers</span></span>

<span data-ttu-id="9b310-127">Wenn Sie in Ihrer LCM-Konfiguration nur einen **ConfigurationRepositoryWeb**- oder einen **ConfigurationRepositoryShare**-Block angeben (wie im vorherigen Beispiel), ruft der Pullclient Ressourcen per Pull vom angegebenen Server ab, sendet aber keine Berichte an den Server.</span><span class="sxs-lookup"><span data-stu-id="9b310-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span>
<span data-ttu-id="9b310-128">Sie können für Konfigurationen, Ressourcen und Berichte einen einzigen Pullserver verwenden, allerdings müssen Sie einen **ReportRepositoryWeb**-Block erstellen, um die Berichterstattung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="9b310-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>
<span data-ttu-id="9b310-129">Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9b310-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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
        }
    }
}
PullClientConfigNames
```

<span data-ttu-id="9b310-130">Sie können für den Abruf von Ressourcen und die Berichterstattung auch unterschiedliche Pullserver angeben.</span><span class="sxs-lookup"><span data-stu-id="9b310-130">You can also specify different pull servers for resources and reporting.</span></span>
<span data-ttu-id="9b310-131">Um einen Ressourcenserver anzugeben, verwenden Sie entweder einen **ResourceRepositoryWeb**-Block (für einen Webpullserver) oder einen **ResourceRepositoryShare**-Block (für einen SMB-Pullserver).</span><span class="sxs-lookup"><span data-stu-id="9b310-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="9b310-132">Um einen Berichtsserver anzugeben, verwenden Sie einen **ReportRepositoryWeb**-Block.</span><span class="sxs-lookup"><span data-stu-id="9b310-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span>
<span data-ttu-id="9b310-133">Ein Berichtsserver kann kein SMB-Server sein.</span><span class="sxs-lookup"><span data-stu-id="9b310-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="9b310-134">Die folgende Metakonfiguration konfiguriert einen Pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von**CONTOSO-ResourceSrv** und Senden von Statusberichten an **CONTOSO-ReportSrv**.</span><span class="sxs-lookup"><span data-stu-id="9b310-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-ResourceSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '30ef9bd8-9acf-4e01-8374-4dc35710fc90'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-ReportSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '6b392c6a-818c-4b24-bf38-47124f1e2f14'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="9b310-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9b310-135">See Also</span></span>

* [<span data-ttu-id="9b310-136">Einrichten eines Pullclients mit Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="9b310-136">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="9b310-137">Einrichten eines DSC-Webpullservers</span><span class="sxs-lookup"><span data-stu-id="9b310-137">Setting up a DSC web pull server</span></span>](pullServer.md)

