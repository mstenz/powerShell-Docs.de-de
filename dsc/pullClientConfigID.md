---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID
ms.openlocfilehash: 5ab57ae908ada102b0d57971542eff09d102fb8f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="85bf4-103">Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="85bf4-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="85bf4-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="85bf4-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="85bf4-105">Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL angegeben werden, unter der der Pullserver zum Abrufen von Konfigurationen kontaktiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="85bf4-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="85bf4-106">Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="85bf4-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="85bf4-107">Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs.</span><span class="sxs-lookup"><span data-stu-id="85bf4-107">To configure the LCM, you create a special type of configuration, derated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="85bf4-108">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="85bf4-108">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="85bf4-109">**Hinweis**: Dieses Thema gilt für PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="85bf4-109">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="85bf4-110">Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="85bf4-110">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="85bf4-111">Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“.</span><span class="sxs-lookup"><span data-stu-id="85bf4-111">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="85bf4-112">Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver.</span><span class="sxs-lookup"><span data-stu-id="85bf4-112">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="85bf4-113">Die **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="85bf4-113">The **ServerURL**</span></span>

<span data-ttu-id="85bf4-114">Nachdem das Skript ausgeführt wurde, erstellt es einen neuen Ausgabeordner mit dem Namen **PullClientConfigID**, der eine MOF-Datei mit der Metakonfiguration enthält.</span><span class="sxs-lookup"><span data-stu-id="85bf4-114">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="85bf4-115">In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="85bf4-115">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="85bf4-116">Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="85bf4-116">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="85bf4-117">Beispiel: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="85bf4-117">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="85bf4-118">Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="85bf4-118">Configuration ID</span></span>

<span data-ttu-id="85bf4-119">Das Skript legt die **ConfigurationID**-Eigenschaft des LCM auf eine GUID fest, die zuvor für diesen Zweck erstellt wurde (Sie können eine GUID mit dem Cmdlet **New-Guid** erstellen).</span><span class="sxs-lookup"><span data-stu-id="85bf4-119">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="85bf4-120">Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver.</span><span class="sxs-lookup"><span data-stu-id="85bf4-120">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="85bf4-121">Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen _ConfigurationID.mof_ haben, wobei _ConfigurationID_ der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="85bf4-121">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="85bf4-122">SMB-Pullserver</span><span class="sxs-lookup"><span data-stu-id="85bf4-122">SMB pull server</span></span>

<span data-ttu-id="85bf4-123">Um einen Client zum Abrufen von Konfigurationen per Pull von einem SMB-Server einzurichten, verwenden Sie einen **ConfigurationRepositoryShare**-Block.</span><span class="sxs-lookup"><span data-stu-id="85bf4-123">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="85bf4-124">Im **ConfigurationRepositoryShare**-Block geben Sie den Pfad zum Server durch Festlegen der **SourcePath**-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="85bf4-124">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="85bf4-125">Die folgende Metakonfiguration konfiguriert den Zielknoten zum Abrufen von Daten von einem SMB-Pullserver mit dem Namen **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="85bf4-125">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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
            SourcePath = '\\SMBPullServer\PullSource'
            
        }     
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="85bf4-126">Ressourcen und Berichtsserver</span><span class="sxs-lookup"><span data-stu-id="85bf4-126">Resource and report servers</span></span>

<span data-ttu-id="85bf4-127">Wenn Sie in Ihrer LCM-Konfiguration nur einen **ConfigurationRepositoryWeb**- oder einen **ConfigurationRepositoryShare**-Block angeben (wie im vorherigen Beispiel), ruft der Pullclient Ressourcen per Pull vom angegebenen Server ab, sendet aber keine Berichte an den Server.</span><span class="sxs-lookup"><span data-stu-id="85bf4-127">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="85bf4-128">Sie können für Konfigurationen, Ressourcen und Berichte einen einzigen Pullserver verwenden, allerdings müssen Sie einen **ReportRepositoryWeb**-Block erstellen, um die Berichterstattung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="85bf4-128">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span> 

<span data-ttu-id="85bf4-129">Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="85bf4-129">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="85bf4-130">Sie können für den Abruf von Ressourcen und die Berichterstattung auch unterschiedliche Pullserver angeben.</span><span class="sxs-lookup"><span data-stu-id="85bf4-130">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="85bf4-131">Um einen Ressourcenserver anzugeben, verwenden Sie entweder einen **ResourceRepositoryWeb**-Block (für einen Webpullserver) oder einen **ResourceRepositoryShare**-Block (für einen SMB-Pullserver).</span><span class="sxs-lookup"><span data-stu-id="85bf4-131">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="85bf4-132">Um einen Berichtsserver anzugeben, verwenden Sie einen **ReportRepositoryWeb**-Block.</span><span class="sxs-lookup"><span data-stu-id="85bf4-132">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="85bf4-133">Ein Berichtsserver kann kein SMB-Server sein.</span><span class="sxs-lookup"><span data-stu-id="85bf4-133">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="85bf4-134">Die folgende Metakonfiguration konfiguriert einen Pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von**CONTOSO-ResourceSrv** und Senden von Statusberichten an **CONTOSO-ReportSrv**.</span><span class="sxs-lookup"><span data-stu-id="85bf4-134">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="85bf4-135">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="85bf4-135">See Also</span></span>

* [<span data-ttu-id="85bf4-136">Einrichten eines Pullclients mit Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="85bf4-136">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)

