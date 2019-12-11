---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PowerShell DSC – Teilkonfigurationen
ms.openlocfilehash: 379ecf804329f318e9604c1af43a60a0e24551f1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417745"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="20f0e-103">PowerShell DSC – Teilkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="20f0e-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="20f0e-104">_Gilt für: Windows PowerShell 5.0 und höher_</span><span class="sxs-lookup"><span data-stu-id="20f0e-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="20f0e-105">In PowerShell 5.0 ermöglicht DSC (Desired State Configuration, Konfiguration des gewünschten Zustands), dass Konfigurationen in Fragmenten und aus mehreren Quellen übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="20f0e-106">Der LCM (Local Configuration Manager, lokale Konfigurations-Manager) auf dem Zielknoten setzt die Fragmente zusammen, ehe sie als einzelne Konfiguration angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="20f0e-107">Dies ermöglicht die gemeinsame Steuerung der Konfiguration durch Teams oder Einzelpersonen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="20f0e-108">Wenn z. B. zwei oder mehr Teams an der Entwicklung eines Diensts zusammenarbeiten, möchte ggf. jedes Team Konfigurationen für die Verwaltung seines Teils des Diensts erstellen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="20f0e-109">Jede dieser Konfigurationen kann von verschiedenen Pullservern abgerufen und in verschiedenen Phasen der Entwicklung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="20f0e-110">Teilkonfigurationen ermöglichen außerdem verschiedenen Personen oder Teams das Steuern verschiedener Aspekte der Konfiguration von Knoten, ohne dass die Bearbeitung eines einzelnen Konfigurationsdokuments koordiniert werden muss.</span><span class="sxs-lookup"><span data-stu-id="20f0e-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="20f0e-111">Ein Team kann z. B. für die Bereitstellung einer VM und eines Betriebssystems verantwortlich sein, während ein anderes Team andere Anwendungen und Dienste auf dieser VM bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="20f0e-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="20f0e-112">Bei Teilkonfigurationen kann jedes Team seine eigene Konfiguration erstellen, die dann nicht unnötig kompliziert sein muss.</span><span class="sxs-lookup"><span data-stu-id="20f0e-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="20f0e-113">Sie können Teilkonfigurationen im Pushmodus, Pullmodus oder einer Kombination aus beidem verwenden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="20f0e-114">Teilkonfigurationen im Pushmodus</span><span class="sxs-lookup"><span data-stu-id="20f0e-114">Partial configurations in push mode</span></span>

<span data-ttu-id="20f0e-115">Um Teilkonfigurationen im Pushmodus zu verwenden, konfigurieren Sie den LCM auf dem Zielknoten für das Empfangen von Teilkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="20f0e-116">Jede Teilkonfiguration muss mithilfe von Push auf den Zielknoten übertragen werden, wozu das Cmdlet `Publish-DSCConfiguration` verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="20f0e-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="20f0e-117">Der Zielknoten kombiniert dann die Teilkonfigurationen zu einer einzelnen Konfiguration, und Sie können die Konfiguration durch Aufrufen des Cmdlets [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="20f0e-118">Konfigurieren des LCM für Teilkonfigurationen im Pushmodus</span><span class="sxs-lookup"><span data-stu-id="20f0e-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="20f0e-119">Zum Konfigurieren des LCM für Teilkonfigurationen im Pushmodus erstellen Sie eine **DSCLocalConfigurationManager**-Konfiguration mit einem **PartialConfiguration**-Block für jede Teilkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="20f0e-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="20f0e-120">Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](/powershell/scripting/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="20f0e-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/scripting/dsc/metaConfig).</span></span> <span data-ttu-id="20f0e-121">Das folgende Beispiel zeigt eine LCM-Konfiguration, die zwei Teilkonfigurationen erwartet: eine, die das Betriebssystem bereitgestellt, und eine, die SharePoint bereitstellt und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="20f0e-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="20f0e-122">**RefreshMode** für jede Teilkonfiguration ist auf „Push“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="20f0e-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="20f0e-123">Die Namen der **PartialConfiguration**-Blöcke (in diesem Fall „ServiceAccountConfig“ und „SharePointConfig“) müssen genau mit den Namen der Konfigurationen übereinstimmen, die per Push an die Zielknoten übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="20f0e-124">Die benannten einzelnen **PartialConfiguration**-Blocks müssen mit dem tatsächlichen Namen der Konfiguration übereinstimmen, der im Konfigurationsskript angegeben ist, und nicht mit dem Namen der MOF-Datei, der der Name des Zielknotens oder `localhost` sein sollte.</span><span class="sxs-lookup"><span data-stu-id="20f0e-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="20f0e-125">Veröffentlichen und Starten von Teilkonfigurationen im Pushmodus</span><span class="sxs-lookup"><span data-stu-id="20f0e-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="20f0e-126">Rufen Sie dann [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) für jede Konfiguration auf, und übergeben Sie die Ordner mit den Konfigurationsdokumenten als **Path**-Parameter.</span><span class="sxs-lookup"><span data-stu-id="20f0e-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="20f0e-127">`Publish-DSCConfiguration` positioniert die Konfigurations-MOF-Dateien auf die Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="20f0e-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="20f0e-128">Nach Veröffentlichen beider Konfigurationen können Sie `Start-DSCConfiguration –UseExisting` auf dem Zielknoten aufrufen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="20f0e-129">Wenn Sie z.B. die folgenden Konfigurations-MOF-Dokumente auf dem Erstellungsknoten kompiliert haben:</span><span class="sxs-lookup"><span data-stu-id="20f0e-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="20f0e-130">Sie würden die Konfigurationen wie folgt veröffentlichen und ausführen:</span><span class="sxs-lookup"><span data-stu-id="20f0e-130">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="20f0e-131">Der Benutzer, der das Cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) ausführt, muss über Administratorrechte auf dem Zielknoten verfügen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="20f0e-132">Teilkonfigurationen im Pullmodus</span><span class="sxs-lookup"><span data-stu-id="20f0e-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="20f0e-133">Teilkonfigurationen können von einem oder mehreren Pullservern abgerufen werden (weitere Informationen zu Pullservern finden Sie unter [Windows PowerShell DSC – Pullserver](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="20f0e-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="20f0e-134">Konfigurieren Sie hierzu den LCM so, dass die Teilkonfigurationen per Pull auf den Zielknoten abgerufen werden, und sorgen Sie dafür, dass die Konfigurationsdokumente auf den Pullservern ordnungsgemäß benannt und abgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="20f0e-135">Konfigurieren des LCM für Teilkonfigurationen im Pullmodus</span><span class="sxs-lookup"><span data-stu-id="20f0e-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="20f0e-136">Zum Konfigurieren des LCM zum Abrufen von Teilkonfigurationen per Pull von einem Pullserver müssen Sie den Pullserver entweder in einem **ConfigurationRepositoryWeb**-Block (für einen HTTP-Pullserver) oder einem **ConfigurationRepositoryShare**-Block (für einen SMB-Pullserver) definieren.</span><span class="sxs-lookup"><span data-stu-id="20f0e-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="20f0e-137">Dann erstellen Sie **PartialConfiguration**-Blöcke, die unter Verwendung der **ConfigurationSource**-Eigenschaft auf den Pullserver verweisen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="20f0e-138">Sie müssen außerdem einen **Settings**-Block erstellen, um anzugeben, dass der LCM den Pullmodus verwendet, und um die **ConfigurationNames**- oder **ConfigurationID**-Werte anzugeben, die der Pullserver und Zielknoten zum Identifizieren der Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="20f0e-139">Die folgende Metakonfiguration definiert einen HTTP-Pullserver mit dem Namen „CONTOSO-PullSrv“ und zwei Teilkonfigurationen, die diesen Pullserver verwenden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="20f0e-140">Weitere Informationen zum Konfigurieren des LCM unter Verwendung von **ConfigurationNames** finden Sie unter [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="20f0e-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="20f0e-141">Weitere Informationen zum Konfigurieren des LCM unter Verwendung von **ConfigurationID** finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="20f0e-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="20f0e-142">Konfigurieren des LCM für Pullmoduskonfigurationen mithilfe von Konfigurationsnamen</span><span class="sxs-lookup"><span data-stu-id="20f0e-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="20f0e-143">Konfigurieren des LCM für Pullmoduskonfigurationen mithilfe der Konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="20f0e-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="20f0e-144">Sie können Teilkonfigurationen per Pull von mehreren Pullservern abrufen. Sie müssen dazu die einzelnen Pullserver definieren und dann im jeweiligen **PartialConfiguration**-Block auf den entsprechenden Pullserver verweisen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="20f0e-145">Nach dem Erstellen der Metakonfiguration müssen Sie diese ausführen, um ein Konfigurationsdokument (eine MOF-Datei) zu erstellen. Rufen Sie anschließend [Set- DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) auf, um den LCM zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="20f0e-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="20f0e-146">Benennen und Ablegen der Konfigurationsdokumente auf dem Pullserver (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="20f0e-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="20f0e-147">Die Teilkonfigurationsdokumente müssen in dem Ordner abgelegt werden, der als **ConfigurationPath** in der Datei `web.config` für den Pullserver angegeben ist (meist `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="20f0e-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="20f0e-148">Benennen der Konfigurationsdokumente auf dem Pullserver in PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="20f0e-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="20f0e-149">Wenn Sie nur eine partielle Konfiguration von einem einzelnen Pullserver abrufen, kann das Konfigurationsdokument beliebig benannt werden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="20f0e-150">Wenn Sie mehrere partielle Konfigurationen von einem Pullserver abrufen, kann das Konfigurationsdokument entweder `<ConfigurationName>.mof` genannt werden, wobei *ConfigurationName* der Name der partiellen Konfiguration ist, oder `<ConfigurationName>.<NodeName>.mof`, wobei *ConfigurationName* der Name der partiellen Konfiguration und *NodeName* der Name des Zielknotens ist.</span><span class="sxs-lookup"><span data-stu-id="20f0e-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="20f0e-151">Dadurch können Sie Konfigurationen vom DSC-Pullserver für Azure Automation abrufen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="20f0e-152">Benennen der Konfigurationsdokumente auf dem Pullserver in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="20f0e-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="20f0e-153">Konfigurationsdokumente müssen wie folgt benannt werden: `ConfigurationName.mof`, wobei *ConfigurationName* der Name der partiellen Konfiguration ist.</span><span class="sxs-lookup"><span data-stu-id="20f0e-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="20f0e-154">In unserem Beispiel sollten die Konfigurationsdokumente wie folgt heißen:</span><span class="sxs-lookup"><span data-stu-id="20f0e-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="20f0e-155">Benennen und Ablegen der Konfigurationsdokumente auf dem Pullserver (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="20f0e-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="20f0e-156">Die Teilkonfigurationsdokumente müssen in dem Ordner abgelegt werden, der als **ConfigurationPath** in der Datei `web.config` für den Pullserver angegeben ist (meist `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="20f0e-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="20f0e-157">Die Konfigurationsdokumente müssen wie folgt genannt werden: `<ConfigurationName>.<ConfigurationID>.mof`, wobei _ConfigurationName_ der Name der partiellen Konfiguration und _ConfigurationID_ die Konfigurations-ID ist, die im LCM auf dem Zielknoten definiert ist.</span><span class="sxs-lookup"><span data-stu-id="20f0e-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="20f0e-158">In unserem Beispiel sollten die Konfigurationsdokumente wie folgt heißen:</span><span class="sxs-lookup"><span data-stu-id="20f0e-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="20f0e-159">Ausführen von Teilkonfigurationen von einem Pullserver</span><span class="sxs-lookup"><span data-stu-id="20f0e-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="20f0e-160">Nachdem der LCM auf dem Zielknoten konfiguriert wurde und die Konfigurationsdokumente auf dem Pullserver erstellt und ordnungsgemäß benannt wurden, ruft der Zielknoten die Teilkonfigurationen ab, kombiniert sie und wendet die resultierende Konfiguration in regelmäßigen Abständen entsprechend der Angabe der **RefreshFrequencyMins**-Eigenschaft des LCM an.</span><span class="sxs-lookup"><span data-stu-id="20f0e-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="20f0e-161">Wenn Sie eine Aktualisierung erzwingen möchten, können Sie das Cmdlet [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) aufrufen, um die Konfigurationen per Pull abzurufen, und dann `Start-DSCConfiguration –UseExisting` aufrufen, um sie anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="20f0e-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="20f0e-162">Teilkonfigurationen im gemischten Push- und Pullmodus</span><span class="sxs-lookup"><span data-stu-id="20f0e-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="20f0e-163">Sie können Push- und Pullmodus für Teilkonfigurationen auch mischen.</span><span class="sxs-lookup"><span data-stu-id="20f0e-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="20f0e-164">Es ist also möglich, dass eine Teilkonfiguration per Pull von einem Pullserver abgerufen wird, während eine andere per Push übertragen wird.</span><span class="sxs-lookup"><span data-stu-id="20f0e-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="20f0e-165">Geben Sie den Aktualisierungsmodus für jede partielle Konfiguration an, wie in den vorherigen Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="20f0e-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="20f0e-166">In der folgenden Metakonfiguration wird z. B. dasselbe Beispiel beschrieben – mit der partiellen Konfiguration für `ServiceAccountConfig` im Pullmodus und der partiellen Konfiguration für `SharePointConfig` im Pushmodus.</span><span class="sxs-lookup"><span data-stu-id="20f0e-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="20f0e-167">Gemischte Push- und Pullmodi unter Verwendung von „ConfigurationNames“</span><span class="sxs-lookup"><span data-stu-id="20f0e-167">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="20f0e-168">Gemischte Push- und Pullmodi unter Verwendung von „ConfigurationID“</span><span class="sxs-lookup"><span data-stu-id="20f0e-168">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="20f0e-169">Beachten Sie, dass der im „Settings“-Block angegebene **RefreshMode** auf „Pull“, aber der **RefreshMode** für die partielle Konfiguration `SharePointConfig` auf „Push“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="20f0e-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="20f0e-170">Benennen Sie die MOF-Konfigurationsdateien und legen Sie sie ab, wie oben für die entsprechenden Aktualisierungsmodi beschrieben.</span><span class="sxs-lookup"><span data-stu-id="20f0e-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="20f0e-171">Rufen Sie `Publish-DSCConfiguration` zum Veröffentlichen der `SharePointConfig`-Teilkonfiguration auf. Warten Sie dann entweder, bis die `ServiceAccountConfig`-Konfiguration vom Pullserver abgerufen wird, oder erzwingen Sie eine Aktualisierung durch das Aufrufen von [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="20f0e-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="20f0e-172">Beispiel für eine ServiceAccountConfig-Teilkonfiguration</span><span class="sxs-lookup"><span data-stu-id="20f0e-172">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="20f0e-173">Beispiel für eine SharePointConfig-Teilkonfiguration</span><span class="sxs-lookup"><span data-stu-id="20f0e-173">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="20f0e-174">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="20f0e-174">See Also</span></span>

[<span data-ttu-id="20f0e-175">Windows PowerShell DSC (Desired State Configuration): Pullserver</span><span class="sxs-lookup"><span data-stu-id="20f0e-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="20f0e-176">Konfigurieren des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="20f0e-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
