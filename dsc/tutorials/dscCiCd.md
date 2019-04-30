---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Erstellen einer Pipeline für Continuous Integration und Continuous Deplyoment mit DSC
ms.openlocfilehash: 012057a32ccf85b0d15e76a332cadda4b226180a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076472"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="63818-103">Erstellen einer Pipeline für Continuous Integration und Continuous Deplyoment mit DSC</span><span class="sxs-lookup"><span data-stu-id="63818-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="63818-104">Dieses Beispiel zeigt, wie Sie unter Verwendung von PowerShell, DSC, Pester und Visual Studio Team Foundation Server (TFS) eine CI/CD-Pipeline (Continuous Integration/Continuous Deployment) erstellen.</span><span class="sxs-lookup"><span data-stu-id="63818-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="63818-105">Nachdem die Pipeline erstellt und konfiguriert wurde, können Sie sie für das vollständige Bereitstellen, Konfigurieren und Testen eines DNS-Servers sowie der zugeordneten Hosteinträge verwenden.</span><span class="sxs-lookup"><span data-stu-id="63818-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="63818-106">Dieser Prozess simuliert den ersten Teil einer Pipeline, die in einer Entwicklungsumgebung verwendet werden würde.</span><span class="sxs-lookup"><span data-stu-id="63818-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="63818-107">Eine automatisierte CI/CD-Pipeline unterstützt Sie bei einer schnelleren und zuverlässigeren Aktualisierung Ihrer Software. Außerdem wird sichergestellt, dass der gesamte Code getestet wird und dass immer ein aktueller Build Ihres Codes verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="63818-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63818-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="63818-108">Prerequisites</span></span>

<span data-ttu-id="63818-109">Um dieses Beispiel zu verwenden, sollten Sie mit folgenden Konzepten und Modellen vertraut sein:</span><span class="sxs-lookup"><span data-stu-id="63818-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="63818-110">CI-CD-Konzepte,</span><span class="sxs-lookup"><span data-stu-id="63818-110">CI-CD concepts.</span></span> <span data-ttu-id="63818-111">eine gute Referenz bietet [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf) (Das Releasepipeline-Modell)</span><span class="sxs-lookup"><span data-stu-id="63818-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="63818-112">[Git](https://git-scm.com/)-Quellcodeverwaltung</span><span class="sxs-lookup"><span data-stu-id="63818-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="63818-113">Das [Pester](https://github.com/pester/Pester)-Testframework</span><span class="sxs-lookup"><span data-stu-id="63818-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="63818-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="63818-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="63818-115">Benötigte Komponenten</span><span class="sxs-lookup"><span data-stu-id="63818-115">What you will need</span></span>

<span data-ttu-id="63818-116">Um dieses Beispiel zu erstellen und auszuführen, benötigen Sie eine Umgebung mit verschiedenen physischen und/oder virtuellen Computern.</span><span class="sxs-lookup"><span data-stu-id="63818-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="63818-117">Client</span><span class="sxs-lookup"><span data-stu-id="63818-117">Client</span></span>

<span data-ttu-id="63818-118">Dies ist der Computer, auf dem Sie die gesamte Arbeitseinrichtung vornehmen und das Beispiel ausführen.</span><span class="sxs-lookup"><span data-stu-id="63818-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="63818-119">Der Clientcomputer muss ein Windows-Computer sein, auf dem folgende Komponenten installiert sind:</span><span class="sxs-lookup"><span data-stu-id="63818-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="63818-120">Git</span><span class="sxs-lookup"><span data-stu-id="63818-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="63818-121">Ein aus https://github.com/PowerShell/Demo_CI geklontes lokales Git-Repository</span><span class="sxs-lookup"><span data-stu-id="63818-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="63818-122">Ein Text-Editor, z.B. [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="63818-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="63818-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="63818-123">TFSSrv1</span></span>

<span data-ttu-id="63818-124">Der Computer, der den TFS-Server hostet, auf dem Sie Build und Release definieren.</span><span class="sxs-lookup"><span data-stu-id="63818-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="63818-125">Auf diesem Computer muss [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installiert sein.</span><span class="sxs-lookup"><span data-stu-id="63818-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="63818-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="63818-126">BuildAgent</span></span>

<span data-ttu-id="63818-127">Der Computer, auf dem der Windows-Build-Agent ausgeführt wird, mit dem das Projekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="63818-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="63818-128">Auf diesem Computer muss ein Windows-Build-Agent installiert sein und ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="63818-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="63818-129">Anweisungen zum Installieren und Ausführen eines Windows-Build-Agents finden Sie unter [Bereitstellen eines Agents unter Windows](/azure/devops/pipelines/agents/v2-windows).</span><span class="sxs-lookup"><span data-stu-id="63818-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="63818-130">Sie müssen außerdem die DSC-Module `xDnsServer` und `xNetworking` auf diesem Computer installieren.</span><span class="sxs-lookup"><span data-stu-id="63818-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="63818-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="63818-131">TestAgent1</span></span>

<span data-ttu-id="63818-132">Dies ist der Computer, der anhand der DSC-Konfiguration in diesem Beispiel als DNS-Server konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="63818-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="63818-133">Auf dem Computer muss [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="63818-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="63818-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="63818-134">TestAgent2</span></span>

<span data-ttu-id="63818-135">Dies ist der Computer, der die in diesem Beispiel konfigurierte Website hostet.</span><span class="sxs-lookup"><span data-stu-id="63818-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="63818-136">Auf dem Computer muss [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="63818-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="63818-137">Hinzufügen des Codes zu TFS</span><span class="sxs-lookup"><span data-stu-id="63818-137">Add the code to TFS</span></span>

<span data-ttu-id="63818-138">Im ersten Schritt erstellen wir ein Git-Repository in TFS und importieren den Code aus Ihrem lokalen Repository auf den Clientcomputer.</span><span class="sxs-lookup"><span data-stu-id="63818-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="63818-139">Wenn Sie das Demo_CI-Repository noch nicht auf Ihren Clientcomputer geklont haben, holen Sie dies jetzt nach, indem Sie den folgenden Git-Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="63818-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="63818-140">Navigieren Sie auf Ihrem Clientcomputer in einem Webbrowser zu Ihrem TFS-Server.</span><span class="sxs-lookup"><span data-stu-id="63818-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="63818-141">[Erstellen Sie in TFS ein neues Teamprojekt](/azure/devops/organizations/projects/create-project) mit dem Namen „Demo_CI“.</span><span class="sxs-lookup"><span data-stu-id="63818-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="63818-142">Stellen Sie sicher, dass **Versionskontrolle** auf **Git** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="63818-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="63818-143">Fügen Sie dem soeben auf Ihrem Clientcomputer in TFS erstellten Repository mit dem folgenden Befehl ein Remoterepository hinzu:</span><span class="sxs-lookup"><span data-stu-id="63818-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="63818-144">Hierbei steht `<YourTFSRepoURL>` für die URL zum Klonen des TFS-Repositorys, das Sie im vorherigen Schritt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="63818-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="63818-145">Wenn Sie nicht wissen, wo Sie diese URL finden, lesen Sie den Artikel [Klonen eines vorhandenen Git-Repositorys](/azure/devops/repos/git/clone).</span><span class="sxs-lookup"><span data-stu-id="63818-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="63818-146">Pushen Sie mit dem folgenden Befehl den Code aus Ihrem lokalen Repository in Ihr TFS-Repository:</span><span class="sxs-lookup"><span data-stu-id="63818-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="63818-147">Das TFS-Repository wird mit dem Demo_CI-Code aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="63818-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="63818-148">Dieses Beispiel verwendet den Code im `ci-cd-example`-Branch des Git-Repositorys.</span><span class="sxs-lookup"><span data-stu-id="63818-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="63818-149">Achten Sie darauf, diesen Branch in Ihrem TFS-Projekt sowie für die erstellten CI/CD-Trigger als Standardbranch anzugeben.</span><span class="sxs-lookup"><span data-stu-id="63818-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="63818-150">Grundlegendes zum Code</span><span class="sxs-lookup"><span data-stu-id="63818-150">Understanding the code</span></span>

<span data-ttu-id="63818-151">Sehen wir uns vor dem Erstellen der Build- und Bereitstellungspipelines einige Codeabschnitt an, um deren Bedeutung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="63818-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="63818-152">Öffnen Sie auf dem Clientcomputer Ihren bevorzugten Text-Editor, und navigieren Sie zum Stamm Ihres Git-Repositorys „Demo_CI“.</span><span class="sxs-lookup"><span data-stu-id="63818-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="63818-153">Die DSC-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="63818-153">The DSC configuration</span></span>

<span data-ttu-id="63818-154">Öffnen Sie die Datei `DNSServer.ps1` (ausgehend vom Stamm des lokalen Demo_CI-Repositorys, `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="63818-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="63818-155">Diese Datei enthält die DSC-Konfiguration zum Einrichten des DNS-Servers.</span><span class="sxs-lookup"><span data-stu-id="63818-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="63818-156">Dies ist der vollständige Code:</span><span class="sxs-lookup"><span data-stu-id="63818-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="63818-157">Beachten Sie die `Node`-Anweisung:</span><span class="sxs-lookup"><span data-stu-id="63818-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="63818-158">Hiermit werden alle Knoten gesucht, die in den vom `DevEnv.ps1`-Skript erstellten [Konfigurationsdaten](../configurations/configData.md) mit der Rolle `DNSServer` definiert wurden.</span><span class="sxs-lookup"><span data-stu-id="63818-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="63818-159">Weitere Informationen zur Methode `Where` finden Sie unter [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md).</span><span class="sxs-lookup"><span data-stu-id="63818-159">You can read more about the `Where` method in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

<span data-ttu-id="63818-160">Die Verwendung von Konfigurationsdaten zum Definieren von Knoten ist im Rahmen der Continuous Integration wichtig, weil sich Knoteninformationen je nach Umgebung wahrscheinlich ändern. Mithilfe von Konfigurationsdaten können Sie problemlos Änderungen an Knoteninformationen durchführen, ohne den Konfigurationscode ändern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="63818-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="63818-161">Im ersten Ressourcenblock ruft die Konfiguration **WindowsFeature** auf, um sicherzustellen, dass das DNS-Feature aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="63818-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="63818-162">Die folgenden Ressourcenblöcke rufen Ressourcen aus dem [xDnsServer](https://github.com/PowerShell/xDnsServer)-Modul auf, um die primäre Zone und DNS-Einträge zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="63818-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="63818-163">Beachten Sie, dass die zwei `xDnsRecord`-Blöcke von `foreach`-Schleifen umschlossen sind, mit denen die Arrays in den Konfigurationsdaten durchlaufen werden.</span><span class="sxs-lookup"><span data-stu-id="63818-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="63818-164">Auch hier werden die Konfigurationsdaten durch das `DevEnv.ps1`-Skript erstellt, das wir nachfolgend betrachten.</span><span class="sxs-lookup"><span data-stu-id="63818-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="63818-165">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="63818-165">Configuration data</span></span>

<span data-ttu-id="63818-166">Die `DevEnv.ps1`-Datei (ausgehend vom Stamm des lokalen Demo_CI-Repositorys, `./InfraDNS/DevEnv.ps1`), gibt die umgebungsspezifischen Konfigurationsdaten in einer Hashtabelle an und übergibt diese Hashtabelle an einen Aufruf der `New-DscConfigurationDataDocument`-Funktion, die in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) definiert ist.</span><span class="sxs-lookup"><span data-stu-id="63818-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="63818-167">Die Datei `DevEnv.ps1` enthält Folgendes:</span><span class="sxs-lookup"><span data-stu-id="63818-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="63818-168">Die `New-DscConfigurationDataDocument`-Funktion (definiert in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) erstellt programmgesteuert ein Dokument mit Konfigurationsdaten aus der Hashtabelle (Knotendaten) und dem Array (Nicht-Knotendaten), die als Parameter `RawEnvData` und `OtherEnvData` übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="63818-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="63818-169">Im vorliegenden Fall wird nur der Parameter `RawEnvData` verwendet.</span><span class="sxs-lookup"><span data-stu-id="63818-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="63818-170">Das psake-Buildskript</span><span class="sxs-lookup"><span data-stu-id="63818-170">The psake build script</span></span>

<span data-ttu-id="63818-171">Das in `Build.ps1` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Build.ps1`) definierte [psake](https://github.com/psake/psake)-Buildskript definiert Tasks, die Bestandteil des Builds sind.</span><span class="sxs-lookup"><span data-stu-id="63818-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="63818-172">Darüber hinaus wird definiert, von welchen weiteren Tasks jeder Task abhängt.</span><span class="sxs-lookup"><span data-stu-id="63818-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="63818-173">Beim Aufruf des psake-Skripts wird sichergestellt, dass der angegebene Task (oder der Task `Default`, sofern kein Task angegeben wird) ausgeführt wird, ebenso wie alle abhängigen Komponenten (dieser Vorgang ist rekursiv, d.h. abhängige Komponenten von abhängigen Komponenten werden ausgeführt usw.).</span><span class="sxs-lookup"><span data-stu-id="63818-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="63818-174">In diesem Beispiel ist der `Default`-Task so definiert:</span><span class="sxs-lookup"><span data-stu-id="63818-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="63818-175">Der `Default`-Task weist selbst keine Implementierung auf, sondern hängt vom `CompileConfigs`-Task ab.</span><span class="sxs-lookup"><span data-stu-id="63818-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="63818-176">Die Ergebniskette aus Taskabhängigkeiten stellt sicher, dass alle Tasks im Buildskript ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="63818-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="63818-177">In diesem Beispiel wird das psake-Skript durch einen Aufruf von `Invoke-PSake` in der `Initiate.ps1`-Datei aufgerufen (diese befindet sich im Stamm des Demo_CI-Repositorys):</span><span class="sxs-lookup"><span data-stu-id="63818-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="63818-178">Wenn wir die Builddefinition für unser Beispiel in TFS erstellen, geben wir unsere pskake-Skriptdatei als `fileName`-Parameter für dieses Skript an.</span><span class="sxs-lookup"><span data-stu-id="63818-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="63818-179">Das Buildskript definiert die folgenden Tasks:</span><span class="sxs-lookup"><span data-stu-id="63818-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="63818-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="63818-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="63818-181">Führt `DevEnv.ps1` aus, mit der die Konfigurationsdatendatei generiert wird.</span><span class="sxs-lookup"><span data-stu-id="63818-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="63818-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="63818-182">InstallModules</span></span>

<span data-ttu-id="63818-183">Installiert die von der Konfiguration `DNSServer.ps1` benötigten Module.</span><span class="sxs-lookup"><span data-stu-id="63818-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="63818-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="63818-184">ScriptAnalysis</span></span>

<span data-ttu-id="63818-185">Ruft [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) auf.</span><span class="sxs-lookup"><span data-stu-id="63818-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="63818-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="63818-186">UnitTests</span></span>

<span data-ttu-id="63818-187">Führt die [Pester](https://github.com/pester/Pester/wiki)-Komponententests aus.</span><span class="sxs-lookup"><span data-stu-id="63818-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="63818-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="63818-188">CompileConfigs</span></span>

<span data-ttu-id="63818-189">Kompiliert die Konfiguration (`DNSServer.ps1`) unter Verwendung der über den `GenerateEnvironmentFiles`-Task generierten Konfigurationsdaten in eine MOF-Datei.</span><span class="sxs-lookup"><span data-stu-id="63818-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="63818-190">Clean</span><span class="sxs-lookup"><span data-stu-id="63818-190">Clean</span></span>

<span data-ttu-id="63818-191">Erstellt die für das Beispiel verwendeten Ordner und entfernt alle Testergebnisse, Konfigurationsdatendateien und Module aus vorherigen Ausführungen.</span><span class="sxs-lookup"><span data-stu-id="63818-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="63818-192">Das psake-Bereitstellungsskript</span><span class="sxs-lookup"><span data-stu-id="63818-192">The psake deploy script</span></span>

<span data-ttu-id="63818-193">Das in `Deploy.ps1` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Deploy.ps1`) definierte [psake](https://github.com/psake/psake)-Bereitstellungsskript definiert Tasks zum Bereitstellen und Ausführen der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="63818-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="63818-194">`Deploy.ps1` definiert die folgenden Tasks:</span><span class="sxs-lookup"><span data-stu-id="63818-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="63818-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="63818-195">DeployModules</span></span>

<span data-ttu-id="63818-196">Startet eine PowerShell-Sitzung auf `TestAgent1` und installiert die Module mit den DSC-Ressourcen, die für die Konfiguration erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="63818-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="63818-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="63818-197">DeployConfigs</span></span>

<span data-ttu-id="63818-198">Ruft das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) auf, um die Konfiguration auf `TestAgent1` auszuführen.</span><span class="sxs-lookup"><span data-stu-id="63818-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="63818-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="63818-199">IntegrationTests</span></span>

<span data-ttu-id="63818-200">Führt die [Pester](https://github.com/pester/Pester/wiki)-Integrationstests aus.</span><span class="sxs-lookup"><span data-stu-id="63818-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="63818-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="63818-201">AcceptanceTests</span></span>

<span data-ttu-id="63818-202">Führt die [Pester](https://github.com/pester/Pester/wiki)-Akzeptanztests aus.</span><span class="sxs-lookup"><span data-stu-id="63818-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="63818-203">Clean</span><span class="sxs-lookup"><span data-stu-id="63818-203">Clean</span></span>

<span data-ttu-id="63818-204">Entfernt alle in vorherigen Ausführungen installierten Module und stellt sicher, dass die Testergebnisordner vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="63818-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="63818-205">Testskripts</span><span class="sxs-lookup"><span data-stu-id="63818-205">Test scripts</span></span>

<span data-ttu-id="63818-206">Die Akzeptanz-, Integrations- und Komponententests werden in Skripts im Ordner `Tests` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Tests`) definiert, in Dateien namens `DNSServer.tests.ps1` in den jeweiligen Ordnern.</span><span class="sxs-lookup"><span data-stu-id="63818-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="63818-207">Die Testskripts verwenden die [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.</span><span class="sxs-lookup"><span data-stu-id="63818-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="63818-208">Komponententests</span><span class="sxs-lookup"><span data-stu-id="63818-208">Unit tests</span></span>

<span data-ttu-id="63818-209">Mit den Komponententests werden die DSC-Konfigurationen selbst getestet. So wird sichergestellt, dass die Konfigurationen bei ihrer Ausführung wie erwartet funktionieren.</span><span class="sxs-lookup"><span data-stu-id="63818-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="63818-210">Das Skript für den Komponententest verwendet [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="63818-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="63818-211">Integrationstests</span><span class="sxs-lookup"><span data-stu-id="63818-211">Integration tests</span></span>

<span data-ttu-id="63818-212">Mit den Integrationstests wird die Konfiguration des Systems getestet. So wird gewährleistet, dass das System bei der Integration in andere Komponenten wie erwartet konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="63818-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="63818-213">Diese Tests werden nach der Konfiguration mit DSC auf dem Zielknoten ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="63818-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="63818-214">Das Skript für die Integrationstests verwendet eine Kombination aus der [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.</span><span class="sxs-lookup"><span data-stu-id="63818-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="63818-215">Akzeptanztests</span><span class="sxs-lookup"><span data-stu-id="63818-215">Acceptance tests</span></span>

<span data-ttu-id="63818-216">Über die Akzeptanztests wird getestet, ob sich das System wie erwartet verhält.</span><span class="sxs-lookup"><span data-stu-id="63818-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="63818-217">Beispielsweise wird getestet, ob eine Webseite bei der Abfrage die richtigen Informationen zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="63818-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="63818-218">Diese Tests werden remote vom Zielknoten aus ausgeführt, um ein realistisches Szenario für den Test zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="63818-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="63818-219">Das Skript für die Integrationstests verwendet eine Kombination aus der [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.</span><span class="sxs-lookup"><span data-stu-id="63818-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="63818-220">Definieren des Builds</span><span class="sxs-lookup"><span data-stu-id="63818-220">Define the build</span></span>

<span data-ttu-id="63818-221">Fahren wir jetzt, nachdem wir unseren Code in TFS hochgeladen und uns seine Funktionsweise angesehen haben, mit dem Definieren unseres Builds fort.</span><span class="sxs-lookup"><span data-stu-id="63818-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="63818-222">Nachfolgend werden nur die Buildschritte abgedeckt, die Sie dem Build hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="63818-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="63818-223">Anweisungen zum Erstellen einer Builddefinition in TFS finden Sie unter [Erstellen einer Builddefinition und Einreihen in die Warteschlange](/azure/devops/pipelines/get-started-designer).</span><span class="sxs-lookup"><span data-stu-id="63818-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/get-started-designer).</span></span>

<span data-ttu-id="63818-224">Erstellen Sie eine neue Builddefinition namens „InfraDNS“ (wählen Sie die Vorlage **Leer** aus).</span><span class="sxs-lookup"><span data-stu-id="63818-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="63818-225">Fügen Sie Ihrer Builddefinition die folgenden Schritte hinzu:</span><span class="sxs-lookup"><span data-stu-id="63818-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="63818-226">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="63818-226">PowerShell Script</span></span>
- <span data-ttu-id="63818-227">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="63818-227">Publish Test Results</span></span>
- <span data-ttu-id="63818-228">Dateien kopieren</span><span class="sxs-lookup"><span data-stu-id="63818-228">Copy Files</span></span>
- <span data-ttu-id="63818-229">Artefakt veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="63818-229">Publish Artifact</span></span>

<span data-ttu-id="63818-230">Nachdem Sie diese Buildschritte hinzugefügt haben, bearbeiten Sie die Eigenschaften jedes Schritts folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="63818-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="63818-231">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="63818-231">PowerShell Script</span></span>

1. <span data-ttu-id="63818-232">Legen Sie die Eigenschaft **Typ** auf `File Path` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="63818-233">Legen Sie die Eigenschaft **Skriptpfad** auf `initiate.ps1` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="63818-234">Fügen Sie `-fileName build` zur Eigenschaft **Argumente** hinzu.</span><span class="sxs-lookup"><span data-stu-id="63818-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="63818-235">Mit diesem Buildschritt wird die Datei `initiate.ps1` ausgeführt, mit der das psake-Buildskript aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="63818-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="63818-236">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="63818-236">Publish Test Results</span></span>

1. <span data-ttu-id="63818-237">Legen Sie **Testergebnisformat** auf `NUnit` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="63818-238">Legen Sie **Testergebnisdateien** auf `InfraDNS/Tests/Results/*.xml` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="63818-239">Legen Sie **Testlauftitel** auf `Unit` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="63818-240">Stellen Sie sicher, dass sowohl **Steuerungsoptionen** **Aktiviert** als auch **Immer ausführen** ausgewählt sind.</span><span class="sxs-lookup"><span data-stu-id="63818-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="63818-241">Mit diesem Buildschritt werden die Komponententests im Pester-Skript ausgeführt, das wir uns weiter oben angesehen haben. Die Ergebnisse werden im Ordner `InfraDNS/Tests/Results/*.xml` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="63818-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="63818-242">Dateien kopieren</span><span class="sxs-lookup"><span data-stu-id="63818-242">Copy Files</span></span>

1. <span data-ttu-id="63818-243">Fügen Sie **Inhalte** jede der folgenden Zeilen hinzu:</span><span class="sxs-lookup"><span data-stu-id="63818-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="63818-244">Legen Sie **TargetFolder** auf `$(Build.ArtifactStagingDirectory)\` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="63818-245">Mit diesem Schritt werden der Build und die Testskripts in das Stagingverzeichnis kopiert, sodass im nächsten Schritt eine Veröffentlichung als Buildartefakte erfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="63818-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="63818-246">Artefakt veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="63818-246">Publish Artifact</span></span>

1. <span data-ttu-id="63818-247">Legen Sie **Zu veröffentlichender Pfad** auf `$(Build.ArtifactStagingDirectory)\` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="63818-248">Legen Sie **Artefaktname** auf `Deploy` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="63818-249">Legen Sie **Artefaktyp** auf `Server` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="63818-250">Wählen Sie in den **Steuerungsoptionen** die Einstellung `Enabled` aus.</span><span class="sxs-lookup"><span data-stu-id="63818-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="63818-251">Aktivieren der Continuous Integration</span><span class="sxs-lookup"><span data-stu-id="63818-251">Enable continuous integration</span></span>

<span data-ttu-id="63818-252">Jetzt richten wir einen Trigger ein, mit dem das Projekt immer dann erstellt wird, wenn eine Änderung in den `ci-cd-example`-Branch des Git-Repositorys eingecheckt wird.</span><span class="sxs-lookup"><span data-stu-id="63818-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="63818-253">Klicken Sie in TFS auf die Registerkarte **Build und Release**.</span><span class="sxs-lookup"><span data-stu-id="63818-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="63818-254">Wählen Sie die Builddefinition `DNS Infra` aus, und klicken Sie auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="63818-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="63818-255">Klicken Sie auf die Registerkarte **Trigger**.</span><span class="sxs-lookup"><span data-stu-id="63818-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="63818-256">Wählen Sie **Continuous Integration (CI)** aus, und wählen Sie in der Dropdownliste für den Branch `refs/heads/ci-cd-example` aus.</span><span class="sxs-lookup"><span data-stu-id="63818-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="63818-257">Klicken Sie auf **Speichern** und anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="63818-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="63818-258">Jetzt löst jede Änderung im TFS-Git-Repository eine automatisierte Builderstellung aus.</span><span class="sxs-lookup"><span data-stu-id="63818-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="63818-259">Erstellen der Releasedefinition</span><span class="sxs-lookup"><span data-stu-id="63818-259">Create the release definition</span></span>

<span data-ttu-id="63818-260">Erstellen wir jetzt eine Releasedefinition, damit das Projekt immer dann in der Entwicklungsumgebung bereitgestellt wird, wenn der Code eingecheckt wird.</span><span class="sxs-lookup"><span data-stu-id="63818-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="63818-261">Fügen Sie hierzu eine neue Releasedefinition hinzu, die der zuvor erstellten Builddefinition `InfraDNS` zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="63818-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="63818-262">Stellen Sie sicher, dass **Continuous Deployment** ausgewählt ist, damit immer dann eine neue Release ausgelöst wird, wenn ein neuer Build erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="63818-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="63818-263">([Was sind Releasepipelines?](/azure/devops/pipelines/release/what-is-release-management)), und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="63818-263">([What are release pipelines?](/azure/devops/pipelines/release/what-is-release-management)) and configure it as follows:</span></span>

<span data-ttu-id="63818-264">Fügen Sie der Releasedefinition die folgenden Schritte hinzu:</span><span class="sxs-lookup"><span data-stu-id="63818-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="63818-265">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="63818-265">PowerShell Script</span></span>
- <span data-ttu-id="63818-266">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="63818-266">Publish Test Results</span></span>
- <span data-ttu-id="63818-267">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="63818-267">Publish Test Results</span></span>

<span data-ttu-id="63818-268">Bearbeiten Sie die Schritte wie folgt:</span><span class="sxs-lookup"><span data-stu-id="63818-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="63818-269">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="63818-269">PowerShell Script</span></span>

1. <span data-ttu-id="63818-270">Legen Sie das Feld **Skriptpfad** auf `$(Build.DefinitionName)\Deploy\initiate.ps1"` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="63818-271">Legen Sie das Feld **Argumente** auf `-fileName Deploy` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="63818-272">Erstes Veröffentlichen der Testergebnisse</span><span class="sxs-lookup"><span data-stu-id="63818-272">First Publish Test Results</span></span>

1. <span data-ttu-id="63818-273">Wählen Sie für das Feld **Testergebnisformat** die Einstellung `NUnit` aus.</span><span class="sxs-lookup"><span data-stu-id="63818-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="63818-274">Legen Sie das Feld **Testergebnisdateien** auf `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="63818-275">Legen Sie **Testlauftitel** auf `Integration` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="63818-276">Aktivieren Sie unter **Steuerungsoptionen** die Option **Immer ausführen**.</span><span class="sxs-lookup"><span data-stu-id="63818-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="63818-277">Zweites Veröffentlichen der Testergebnisse</span><span class="sxs-lookup"><span data-stu-id="63818-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="63818-278">Wählen Sie für das Feld **Testergebnisformat** die Einstellung `NUnit` aus.</span><span class="sxs-lookup"><span data-stu-id="63818-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="63818-279">Legen Sie das Feld **Testergebnisdateien** auf `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="63818-280">Legen Sie **Testlauftitel** auf `Acceptance` fest.</span><span class="sxs-lookup"><span data-stu-id="63818-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="63818-281">Aktivieren Sie unter **Steuerungsoptionen** die Option **Immer ausführen**.</span><span class="sxs-lookup"><span data-stu-id="63818-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="63818-282">Überprüfen Ihrer Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="63818-282">Verify your results</span></span>

<span data-ttu-id="63818-283">Jetzt wird jedes Mal, wenn Sie Änderungen in den `ci-cd-example`-Branch in TFS pushen, ein neuer Build gestartet.</span><span class="sxs-lookup"><span data-stu-id="63818-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="63818-284">Bei einem erfolgreichen Abschluss des Builds wird eine neue Bereitstellung ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="63818-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="63818-285">Sie können die Ergebnisse der Bereitstellung überprüfen, indem Sie einen Browser auf dem Clientcomputer öffnen und zu `www.contoso.com` navigieren.</span><span class="sxs-lookup"><span data-stu-id="63818-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="63818-286">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="63818-286">Next steps</span></span>

<span data-ttu-id="63818-287">In diesem Beispiel wird der DNS-Server `TestAgent1` konfiguriert, damit die URL `www.contoso.com` in `TestAgent2` aufgelöst wird. Es erfolgt jedoch keine tatsächliche Bereitstellung einer Website.</span><span class="sxs-lookup"><span data-stu-id="63818-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="63818-288">Das Skeleton hierfür wird im Repository unterhalb des Ordners `WebApp` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="63818-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="63818-289">Sie können die bereitgestellten Stubs zum Erstellen von psake-Skripts, Pester-Tests und DSC-Konfigurationen verwenden, um Ihre eigene Website bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="63818-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
