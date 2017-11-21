---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Erstellen einer Pipeline für Continuous Integration und Continuous Deplyoment mit DSC"
ms.openlocfilehash: baa56088d83fba56d3a19cff7954d3081f341f9a
ms.sourcegitcommit: 60c6f9d8cf316e6d5b285854e6e5641ac7648f3f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="947bb-103">Erstellen einer Pipeline für Continuous Integration und Continuous Deplyoment mit DSC</span><span class="sxs-lookup"><span data-stu-id="947bb-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="947bb-104">Dieses Beispiel zeigt, wie Sie unter Verwendung von PowerShell, DSC, Pester und Visual Studio Team Foundation Server (TFS) eine CI/CD-Pipeline (Continuous Integration/Continuous Deployment) erstellen.</span><span class="sxs-lookup"><span data-stu-id="947bb-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="947bb-105">Nachdem die Pipeline erstellt und konfiguriert wurde, können Sie sie für das vollständige Bereitstellen, Konfigurieren und Testen eines DNS-Servers sowie der zugeordneten Hosteinträge verwenden.</span><span class="sxs-lookup"><span data-stu-id="947bb-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span> <span data-ttu-id="947bb-106">Dieser Prozess simuliert den ersten Teil einer Pipeline, die in einer Entwicklungsumgebung verwendet werden würde.</span><span class="sxs-lookup"><span data-stu-id="947bb-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="947bb-107">Eine automatisierte CI/CD-Pipeline unterstützt Sie bei einer schnelleren und zuverlässigeren Aktualisierung Ihrer Software. Außerdem wird sichergestellt, dass der gesamte Code getestet wird und dass immer ein aktueller Build Ihres Codes verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="947bb-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="947bb-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="947bb-108">Prerequisites</span></span>

<span data-ttu-id="947bb-109">Um dieses Beispiel zu verwenden, sollten Sie mit folgenden Konzepten und Modellen vertraut sein:</span><span class="sxs-lookup"><span data-stu-id="947bb-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="947bb-110">CI-CD-Konzepte,</span><span class="sxs-lookup"><span data-stu-id="947bb-110">CI-CD concepts.</span></span> <span data-ttu-id="947bb-111">eine gute Referenz bietet [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf) (Das Releasepipeline-Modell)</span><span class="sxs-lookup"><span data-stu-id="947bb-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="947bb-112">[Git](https://git-scm.com/)-Quellcodeverwaltung</span><span class="sxs-lookup"><span data-stu-id="947bb-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="947bb-113">Das [Pester](https://github.com/pester/Pester)-Testframework</span><span class="sxs-lookup"><span data-stu-id="947bb-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="947bb-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="947bb-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="947bb-115">Benötigte Komponenten</span><span class="sxs-lookup"><span data-stu-id="947bb-115">What you will need</span></span>

<span data-ttu-id="947bb-116">Um dieses Beispiel zu erstellen und auszuführen, benötigen Sie eine Umgebung mit verschiedenen physischen und/oder virtuellen Computern.</span><span class="sxs-lookup"><span data-stu-id="947bb-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="947bb-117">Client</span><span class="sxs-lookup"><span data-stu-id="947bb-117">Client</span></span>

<span data-ttu-id="947bb-118">Dies ist der Computer, auf dem Sie die gesamte Arbeitseinrichtung vornehmen und das Beispiel ausführen.</span><span class="sxs-lookup"><span data-stu-id="947bb-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="947bb-119">Der Clientcomputer muss ein Windows-Computer sein, auf dem folgende Komponenten installiert sind:</span><span class="sxs-lookup"><span data-stu-id="947bb-119">The client computer must be a Windows computer with the following installed:</span></span>
- [<span data-ttu-id="947bb-120">Git</span><span class="sxs-lookup"><span data-stu-id="947bb-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="947bb-121">Ein lokales Git-Repository, geklont aus https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="947bb-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="947bb-122">Ein Text-Editor, z.B. [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="947bb-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="947bb-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="947bb-123">TFSSrv1</span></span>

<span data-ttu-id="947bb-124">Der Computer, der den TFS-Server hostet, auf dem Sie Build und Release definieren.</span><span class="sxs-lookup"><span data-stu-id="947bb-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="947bb-125">Auf diesem Computer muss [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installiert sein.</span><span class="sxs-lookup"><span data-stu-id="947bb-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="947bb-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="947bb-126">BuildAgent</span></span>

<span data-ttu-id="947bb-127">Der Computer, auf dem der Windows-Build-Agent ausgeführt wird, mit dem das Projekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="947bb-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="947bb-128">Auf diesem Computer muss ein Windows-Build-Agent installiert sein und ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="947bb-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="947bb-129">Anweisungen zum Installieren und Ausführen eines Windows-Build-Agents finden Sie unter [Bereitstellen eines Agents unter Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows).</span><span class="sxs-lookup"><span data-stu-id="947bb-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="947bb-130">Sie müssen außerdem die DSC-Module `xDnsServer` und `xNetworking` auf diesem Computer installieren.</span><span class="sxs-lookup"><span data-stu-id="947bb-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="947bb-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="947bb-131">TestAgent1</span></span>

<span data-ttu-id="947bb-132">Dies ist der Computer, der anhand der DSC-Konfiguration in diesem Beispiel als DNS-Server konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="947bb-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="947bb-133">Auf dem Computer muss [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="947bb-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="947bb-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="947bb-134">TestAgent2</span></span>

<span data-ttu-id="947bb-135">Dies ist der Computer, der die in diesem Beispiel konfigurierte Website hostet.</span><span class="sxs-lookup"><span data-stu-id="947bb-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="947bb-136">Auf dem Computer muss [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016) ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="947bb-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> 

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="947bb-137">Hinzufügen des Codes zu TFS</span><span class="sxs-lookup"><span data-stu-id="947bb-137">Add the code to TFS</span></span>

<span data-ttu-id="947bb-138">Im ersten Schritt erstellen wir ein Git-Repository in TFS und importieren den Code aus Ihrem lokalen Repository auf den Clientcomputer.</span><span class="sxs-lookup"><span data-stu-id="947bb-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="947bb-139">Wenn Sie das Demo_CI-Repository noch nicht auf Ihren Clientcomputer geklont haben, holen Sie dies jetzt nach, indem Sie den folgenden Git-Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="947bb-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="947bb-140">Navigieren Sie auf Ihrem Clientcomputer in einem Webbrowser zu Ihrem TFS-Server.</span><span class="sxs-lookup"><span data-stu-id="947bb-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="947bb-141">[Erstellen Sie in TFS ein neues Teamprojekt](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) mit dem Namen „Demo_CI“.</span><span class="sxs-lookup"><span data-stu-id="947bb-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

    <span data-ttu-id="947bb-142">Stellen Sie sicher, dass **Versionskontrolle** auf **Git** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="947bb-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="947bb-143">Fügen Sie dem soeben auf Ihrem Clientcomputer in TFS erstellten Repository mit dem folgenden Befehl ein Remoterepository hinzu:</span><span class="sxs-lookup"><span data-stu-id="947bb-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

    `git remote add tfs <YourTFSRepoURL>`

    <span data-ttu-id="947bb-144">Hierbei steht `<YourTFSRepoURL>` für die URL zum Klonen des TFS-Repositorys, das Sie im vorherigen Schritt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="947bb-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

    <span data-ttu-id="947bb-145">Wenn Sie nicht wissen, wo Sie diese URL finden, lesen Sie den Artikel [Klonen eines vorhandenen Git-Repositorys](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span><span class="sxs-lookup"><span data-stu-id="947bb-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="947bb-146">Pushen Sie mit dem folgenden Befehl den Code aus Ihrem lokalen Repository in Ihr TFS-Repository:</span><span class="sxs-lookup"><span data-stu-id="947bb-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

    `git push tfs --all`
1. <span data-ttu-id="947bb-147">Das TFS-Repository wird mit dem Demo_CI-Code aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="947bb-147">The TFS repository will be populated with the Demo_CI code.</span></span>

><span data-ttu-id="947bb-148">**Hinweis**: Dieses Beispiel verwendet den Code im `ci-cd-example`-Branch des Git-Repositorys.</span><span class="sxs-lookup"><span data-stu-id="947bb-148">**Note:** This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
><span data-ttu-id="947bb-149">Achten Sie darauf, diesen Branch in Ihrem TFS-Projekt sowie für die erstellten CI/CD-Trigger als Standardbranch anzugeben.</span><span class="sxs-lookup"><span data-stu-id="947bb-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="947bb-150">Grundlegendes zum Code</span><span class="sxs-lookup"><span data-stu-id="947bb-150">Understanding the code</span></span>

<span data-ttu-id="947bb-151">Sehen wir uns vor dem Erstellen der Build- und Bereitstellungspipelines einige Codeabschnitt an, um deren Bedeutung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="947bb-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="947bb-152">Öffnen Sie auf dem Clientcomputer Ihren bevorzugten Text-Editor, und navigieren Sie zum Stamm Ihres Git-Repositorys „Demo_CI“.</span><span class="sxs-lookup"><span data-stu-id="947bb-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="947bb-153">Die DSC-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="947bb-153">The DSC configuration</span></span>

<span data-ttu-id="947bb-154">Öffnen Sie die Datei `DNSServer.ps1` (ausgehend vom Stamm des lokalen Demo_CI-Repositorys, `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="947bb-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="947bb-155">Diese Datei enthält die DSC-Konfiguration zum Einrichten des DNS-Servers.</span><span class="sxs-lookup"><span data-stu-id="947bb-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="947bb-156">Dies ist der vollständige Code:</span><span class="sxs-lookup"><span data-stu-id="947bb-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="947bb-157">Beachten Sie die `Node`-Anweisung:</span><span class="sxs-lookup"><span data-stu-id="947bb-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="947bb-158">Hiermit werden alle Knoten gesucht, die in den vom `DevEnv.ps1`-Skript erstellten [Konfigurationsdaten](configData.md) mit der Rolle `DNSServer` definiert wurden.</span><span class="sxs-lookup"><span data-stu-id="947bb-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="947bb-159">Die Verwendung von Konfigurationsdaten zum Definieren von Knoten ist im Rahmen der Continuous Integration wichtig, weil sich Knoteninformationen je nach Umgebung wahrscheinlich ändern. Mithilfe von Konfigurationsdaten können Sie problemlos Änderungen an Knoteninformationen durchführen, ohne den Konfigurationscode ändern zu müssen.</span><span class="sxs-lookup"><span data-stu-id="947bb-159">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="947bb-160">Im ersten Ressourcenblock ruft die Konfiguration [WindowsFeature](windowsFeatureResource.md) auf, um sicherzustellen, dass das DNS-Feature aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="947bb-160">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span> <span data-ttu-id="947bb-161">Die folgenden Ressourcenblöcke rufen Ressourcen aus dem [xDnsServer](https://github.com/PowerShell/xDnsServer)-Modul auf, um die primäre Zone und DNS-Einträge zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="947bb-161">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="947bb-162">Beachten Sie, dass die zwei `xDnsRecord`-Blöcke von `foreach`-Schleifen umschlossen sind, mit denen die Arrays in den Konfigurationsdaten durchlaufen werden.</span><span class="sxs-lookup"><span data-stu-id="947bb-162">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="947bb-163">Auch hier werden die Konfigurationsdaten durch das `DevEnv.ps1`-Skript erstellt, das wir nachfolgend betrachten.</span><span class="sxs-lookup"><span data-stu-id="947bb-163">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="947bb-164">Konfigurationsdaten</span><span class="sxs-lookup"><span data-stu-id="947bb-164">Configuration data</span></span>

<span data-ttu-id="947bb-165">Die `DevEnv.ps1`-Datei (ausgehend vom Stamm des lokalen Demo_CI-Repositorys, `./InfraDNS/DevEnv.ps1`), gibt die umgebungsspezifischen Konfigurationsdaten in einer Hashtabelle an und übergibt diese Hashtabelle an einen Aufruf der `New-DscConfigurationDataDocument`-Funktion, die in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`) definiert ist.</span><span class="sxs-lookup"><span data-stu-id="947bb-165">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="947bb-166">Die Datei `DevEnv.ps1` enthält Folgendes:</span><span class="sxs-lookup"><span data-stu-id="947bb-166">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="947bb-167">Die `New-DscConfigurationDataDocument`-Funktion (definiert in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) erstellt programmgesteuert ein Dokument mit Konfigurationsdaten aus der Hashtabelle (Knotendaten) und dem Array (Nicht-Knotendaten), die als Parameter `RawEnvData` und `OtherEnvData` übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="947bb-167">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="947bb-168">Im vorliegenden Fall wird nur der Parameter `RawEnvData` verwendet.</span><span class="sxs-lookup"><span data-stu-id="947bb-168">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="947bb-169">Das psake-Buildskript</span><span class="sxs-lookup"><span data-stu-id="947bb-169">The psake build script</span></span>

<span data-ttu-id="947bb-170">Das in `Build.ps1` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Build.ps1`) definierte [psake](https://github.com/psake/psake)-Buildskript definiert Tasks, die Bestandteil des Builds sind.</span><span class="sxs-lookup"><span data-stu-id="947bb-170">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="947bb-171">Darüber hinaus wird definiert, von welchen weiteren Tasks jeder Task abhängt.</span><span class="sxs-lookup"><span data-stu-id="947bb-171">It also defines which other tasks each task depends on.</span></span> <span data-ttu-id="947bb-172">Beim Aufruf des psake-Skripts wird sichergestellt, dass der angegebene Task (oder der Task `Default`, sofern kein Task angegeben wird) ausgeführt wird, ebenso wie alle abhängigen Komponenten (dieser Vorgang ist rekursiv, d.h. abhängige Komponenten von abhängigen Komponenten werden ausgeführt usw.).</span><span class="sxs-lookup"><span data-stu-id="947bb-172">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="947bb-173">In diesem Beispiel ist der `Default`-Task so definiert:</span><span class="sxs-lookup"><span data-stu-id="947bb-173">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="947bb-174">Der `Default`-Task weist selbst keine Implementierung auf, sondern hängt vom `CompileConfigs`-Task ab.</span><span class="sxs-lookup"><span data-stu-id="947bb-174">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="947bb-175">Die Ergebniskette aus Taskabhängigkeiten stellt sicher, dass alle Tasks im Buildskript ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="947bb-175">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="947bb-176">In diesem Beispiel wird das psake-Skript durch einen Aufruf von `Invoke-PSake` in der `Initiate.ps1`-Datei aufgerufen (diese befindet sich im Stamm des Demo_CI-Repositorys):</span><span class="sxs-lookup"><span data-stu-id="947bb-176">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="947bb-177">Wenn wir die Builddefinition für unser Beispiel in TFS erstellen, geben wir unsere pskake-Skriptdatei als `fileName`-Parameter für dieses Skript an.</span><span class="sxs-lookup"><span data-stu-id="947bb-177">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="947bb-178">Das Buildskript definiert die folgenden Tasks:</span><span class="sxs-lookup"><span data-stu-id="947bb-178">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="947bb-179">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="947bb-179">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="947bb-180">Führt `DevEnv.ps1` aus, mit der die Konfigurationsdatendatei generiert wird.</span><span class="sxs-lookup"><span data-stu-id="947bb-180">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="947bb-181">InstallModules</span><span class="sxs-lookup"><span data-stu-id="947bb-181">InstallModules</span></span>

<span data-ttu-id="947bb-182">Installiert die von der Konfiguration `DNSServer.ps1` benötigten Module.</span><span class="sxs-lookup"><span data-stu-id="947bb-182">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="947bb-183">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="947bb-183">ScriptAnalysis</span></span>

<span data-ttu-id="947bb-184">Ruft [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) auf.</span><span class="sxs-lookup"><span data-stu-id="947bb-184">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="947bb-185">UnitTests</span><span class="sxs-lookup"><span data-stu-id="947bb-185">UnitTests</span></span>

<span data-ttu-id="947bb-186">Führt die [Pester](https://github.com/pester/Pester/wiki)-Komponententests aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-186">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="947bb-187">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="947bb-187">CompileConfigs</span></span>

<span data-ttu-id="947bb-188">Kompiliert die Konfiguration (`DNSServer.ps1`) unter Verwendung der über den `GenerateEnvironmentFiles`-Task generierten Konfigurationsdaten in eine MOF-Datei.</span><span class="sxs-lookup"><span data-stu-id="947bb-188">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="947bb-189">Clean</span><span class="sxs-lookup"><span data-stu-id="947bb-189">Clean</span></span>

<span data-ttu-id="947bb-190">Erstellt die für das Beispiel verwendeten Ordner und entfernt alle Testergebnisse, Konfigurationsdatendateien und Module aus vorherigen Ausführungen.</span><span class="sxs-lookup"><span data-stu-id="947bb-190">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="947bb-191">Das psake-Bereitstellungsskript</span><span class="sxs-lookup"><span data-stu-id="947bb-191">The psake deploy script</span></span>

<span data-ttu-id="947bb-192">Das in `Deploy.ps1` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Deploy.ps1`) definierte [psake](https://github.com/psake/psake)-Bereitstellungsskript definiert Tasks zum Bereitstellen und Ausführen der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="947bb-192">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="947bb-193">`Deploy.ps1` definiert die folgenden Tasks:</span><span class="sxs-lookup"><span data-stu-id="947bb-193">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="947bb-194">DeployModules</span><span class="sxs-lookup"><span data-stu-id="947bb-194">DeployModules</span></span>

<span data-ttu-id="947bb-195">Startet eine PowerShell-Sitzung auf `TestAgent1` und installiert die Module mit den DSC-Ressourcen, die für die Konfiguration erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="947bb-195">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="947bb-196">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="947bb-196">DeployConfigs</span></span>

<span data-ttu-id="947bb-197">Ruft das Cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) auf, um die Konfiguration auf `TestAgent1` auszuführen.</span><span class="sxs-lookup"><span data-stu-id="947bb-197">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="947bb-198">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="947bb-198">IntegrationTests</span></span>

<span data-ttu-id="947bb-199">Führt die [Pester](https://github.com/pester/Pester/wiki)-Integrationstests aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-199">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="947bb-200">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="947bb-200">AcceptanceTests</span></span>

<span data-ttu-id="947bb-201">Führt die [Pester](https://github.com/pester/Pester/wiki)-Akzeptanztests aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-201">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="947bb-202">Clean</span><span class="sxs-lookup"><span data-stu-id="947bb-202">Clean</span></span>

<span data-ttu-id="947bb-203">Entfernt alle in vorherigen Ausführungen installierten Module und stellt sicher, dass die Testergebnisordner vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="947bb-203">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="947bb-204">Testskripts</span><span class="sxs-lookup"><span data-stu-id="947bb-204">Test scripts</span></span>

<span data-ttu-id="947bb-205">Die Akzeptanz-, Integrations- und Komponententests werden in Skripts im Ordner `Tests` (ausgehend vom Stamm des Demo_CI-Repositorys, `./InfraDNS/Tests`) definiert, in Dateien namens `DNSServer.tests.ps1` in den jeweiligen Ordnern.</span><span class="sxs-lookup"><span data-stu-id="947bb-205">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="947bb-206">Die Testskripts verwenden die [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.</span><span class="sxs-lookup"><span data-stu-id="947bb-206">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="947bb-207">Komponententests</span><span class="sxs-lookup"><span data-stu-id="947bb-207">Unit tests</span></span>

<span data-ttu-id="947bb-208">Mit den Komponententests werden die DSC-Konfigurationen selbst getestet. So wird sichergestellt, dass die Konfigurationen bei ihrer Ausführung wie erwartet funktionieren.</span><span class="sxs-lookup"><span data-stu-id="947bb-208">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="947bb-209">Das Skript für den Komponententest verwendet [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="947bb-209">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="947bb-210">Integrationstests</span><span class="sxs-lookup"><span data-stu-id="947bb-210">Integration tests</span></span>

<span data-ttu-id="947bb-211">Mit den Integrationstests wird die Konfiguration des Systems getestet. So wird gewährleistet, dass das System bei der Integration in andere Komponenten wie erwartet konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="947bb-211">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="947bb-212">Diese Tests werden nach der Konfiguration mit DSC auf dem Zielknoten ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="947bb-212">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="947bb-213">Das Skript für die Integrationstests verwendet eine Kombination aus der [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.</span><span class="sxs-lookup"><span data-stu-id="947bb-213">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="947bb-214">Akzeptanztests</span><span class="sxs-lookup"><span data-stu-id="947bb-214">Acceptance tests</span></span>

<span data-ttu-id="947bb-215">Über die Akzeptanztests wird getestet, ob sich das System wie erwartet verhält.</span><span class="sxs-lookup"><span data-stu-id="947bb-215">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="947bb-216">Beispielsweise wird getestet, ob eine Webseite bei der Abfrage die richtigen Informationen zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="947bb-216">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="947bb-217">Diese Tests werden remote vom Zielknoten aus ausgeführt, um ein realistisches Szenario für den Test zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="947bb-217">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="947bb-218">Das Skript für die Integrationstests verwendet eine Kombination aus der [Pester](https://github.com/pester/Pester/wiki)- und [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction)-Syntax.</span><span class="sxs-lookup"><span data-stu-id="947bb-218">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="947bb-219">Definieren des Builds</span><span class="sxs-lookup"><span data-stu-id="947bb-219">Define the build</span></span>

<span data-ttu-id="947bb-220">Fahren wir jetzt, nachdem wir unseren Code in TFS hochgeladen und uns seine Funktionsweise angesehen haben, mit dem Definieren unseres Builds fort.</span><span class="sxs-lookup"><span data-stu-id="947bb-220">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="947bb-221">Nachfolgend werden nur die Buildschritte abgedeckt, die Sie dem Build hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="947bb-221">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="947bb-222">Anweisungen zum Erstellen einer Builddefinition in TFS finden Sie unter [Erstellen einer Builddefinition und Einreihen in die Warteschlange](https://www.visualstudio.com/en-us/docs/build/define/create).</span><span class="sxs-lookup"><span data-stu-id="947bb-222">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="947bb-223">Erstellen Sie eine neue Builddefinition namens „InfraDNS“ (wählen Sie die Vorlage **Leer** aus).</span><span class="sxs-lookup"><span data-stu-id="947bb-223">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="947bb-224">Fügen Sie Ihrer Builddefinition die folgenden Schritte hinzu:</span><span class="sxs-lookup"><span data-stu-id="947bb-224">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="947bb-225">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="947bb-225">PowerShell Script</span></span>
- <span data-ttu-id="947bb-226">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="947bb-226">Publish Test Results</span></span>
- <span data-ttu-id="947bb-227">Dateien kopieren</span><span class="sxs-lookup"><span data-stu-id="947bb-227">Copy Files</span></span>
- <span data-ttu-id="947bb-228">Artefakt veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="947bb-228">Publish Artifact</span></span>

<span data-ttu-id="947bb-229">Nachdem Sie diese Buildschritte hinzugefügt haben, bearbeiten Sie die Eigenschaften jedes Schritts folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="947bb-229">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="947bb-230">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="947bb-230">PowerShell Script</span></span>

1. <span data-ttu-id="947bb-231">Legen Sie die Eigenschaft **Typ** auf `File Path` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-231">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="947bb-232">Legen Sie die Eigenschaft **Skriptpfad** auf `initiate.ps1` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-232">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="947bb-233">Fügen Sie `-fileName build` zur Eigenschaft **Argumente** hinzu.</span><span class="sxs-lookup"><span data-stu-id="947bb-233">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="947bb-234">Mit diesem Buildschritt wird die Datei `initiate.ps1` ausgeführt, mit der das psake-Buildskript aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="947bb-234">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="947bb-235">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="947bb-235">Publish Test Results</span></span>

1. <span data-ttu-id="947bb-236">Legen Sie **Testergebnisformat** auf `NUnit` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-236">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="947bb-237">Legen Sie **Testergebnisdateien** auf `InfraDNS/Tests/Results/*.xml` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-237">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="947bb-238">Legen Sie **Testlauftitel** auf `Unit` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-238">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="947bb-239">Stellen Sie sicher, dass sowohl **Steuerungsoptionen** **Aktiviert** als auch **Immer ausführen** ausgewählt sind.</span><span class="sxs-lookup"><span data-stu-id="947bb-239">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="947bb-240">Mit diesem Buildschritt werden die Komponententests im Pester-Skript ausgeführt, das wir uns weiter oben angesehen haben. Die Ergebnisse werden im Ordner `InfraDNS/Tests/Results/*.xml` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="947bb-240">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="947bb-241">Dateien kopieren</span><span class="sxs-lookup"><span data-stu-id="947bb-241">Copy Files</span></span>

1. <span data-ttu-id="947bb-242">Fügen Sie **Inhalte** jede der folgenden Zeilen hinzu:</span><span class="sxs-lookup"><span data-stu-id="947bb-242">Add each of the following lines to **Contents**:</span></span>

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. <span data-ttu-id="947bb-243">Legen Sie **TargetFolder** auf `$(Build.ArtifactStagingDirectory)\` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-243">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="947bb-244">Mit diesem Schritt werden der Build und die Testskripts in das Stagingverzeichnis kopiert, sodass im nächsten Schritt eine Veröffentlichung als Buildartefakte erfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="947bb-244">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="947bb-245">Artefakt veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="947bb-245">Publish Artifact</span></span>

1. <span data-ttu-id="947bb-246">Legen Sie **Zu veröffentlichender Pfad** auf `$(Build.ArtifactStagingDirectory)\` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-246">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="947bb-247">Legen Sie **Artefaktname** auf `Deploy` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-247">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="947bb-248">Legen Sie **Artefaktyp** auf `Server` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-248">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="947bb-249">Wählen Sie in den **Steuerungsoptionen** die Einstellung `Enabled` aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-249">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="947bb-250">Aktivieren der Continuous Integration</span><span class="sxs-lookup"><span data-stu-id="947bb-250">Enable continuous integration</span></span>

<span data-ttu-id="947bb-251">Jetzt richten wir einen Trigger ein, mit dem das Projekt immer dann erstellt wird, wenn eine Änderung in den `ci-cd-example`-Branch des Git-Repositorys eingecheckt wird.</span><span class="sxs-lookup"><span data-stu-id="947bb-251">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="947bb-252">Klicken Sie in TFS auf die Registerkarte **Build und Release**.</span><span class="sxs-lookup"><span data-stu-id="947bb-252">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="947bb-253">Wählen Sie die Builddefinition `DNS Infra` aus, und klicken Sie auf **Bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="947bb-253">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="947bb-254">Klicken Sie auf die Registerkarte **Trigger**.</span><span class="sxs-lookup"><span data-stu-id="947bb-254">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="947bb-255">Wählen Sie **Continuous Integration (CI)** aus, und wählen Sie in der Dropdownliste für den Branch `refs/heads/ci-cd-example` aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-255">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="947bb-256">Klicken Sie auf **Speichern** und anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="947bb-256">Click **Save** and then **OK**</span></span>

<span data-ttu-id="947bb-257">Jetzt löst jede Änderung im TFS-Git-Repository eine automatisierte Builderstellung aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-257">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="947bb-258">Erstellen der Releasedefinition</span><span class="sxs-lookup"><span data-stu-id="947bb-258">Create the release definition</span></span>

<span data-ttu-id="947bb-259">Erstellen wir jetzt eine Releasedefinition, damit das Projekt immer dann in der Entwicklungsumgebung bereitgestellt wird, wenn der Code eingecheckt wird.</span><span class="sxs-lookup"><span data-stu-id="947bb-259">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="947bb-260">Fügen Sie hierzu eine neue Releasedefinition hinzu, die der zuvor erstellten Builddefinition `InfraDNS` zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="947bb-260">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="947bb-261">Stellen Sie sicher, dass **Continuous Deployment** ausgewählt ist, damit immer dann eine neue Release ausgelöst wird, wenn ein neuer Build erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="947bb-261">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="947bb-262">([Gewusst wie: Arbeiten mit Releasedefinitionen](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) und anschließende Konfiguration:</span><span class="sxs-lookup"><span data-stu-id="947bb-262">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="947bb-263">Fügen Sie der Releasedefinition die folgenden Schritte hinzu:</span><span class="sxs-lookup"><span data-stu-id="947bb-263">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="947bb-264">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="947bb-264">PowerShell Script</span></span>
- <span data-ttu-id="947bb-265">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="947bb-265">Publish Test Results</span></span>
- <span data-ttu-id="947bb-266">Testergebnisse veröffentlichen</span><span class="sxs-lookup"><span data-stu-id="947bb-266">Publish Test Results</span></span>

<span data-ttu-id="947bb-267">Bearbeiten Sie die Schritte wie folgt:</span><span class="sxs-lookup"><span data-stu-id="947bb-267">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="947bb-268">PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="947bb-268">PowerShell Script</span></span>

1. <span data-ttu-id="947bb-269">Legen Sie das Feld **Skriptpfad** auf `$(Build.DefinitionName)\Deploy\initiate.ps1"` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-269">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="947bb-270">Legen Sie das Feld **Argumente** auf `-fileName Deploy` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-270">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="947bb-271">Erstes Veröffentlichen der Testergebnisse</span><span class="sxs-lookup"><span data-stu-id="947bb-271">First Publish Test Results</span></span>

1. <span data-ttu-id="947bb-272">Wählen Sie für das Feld **Testergebnisformat** die Einstellung `NUnit` aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-272">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="947bb-273">Legen Sie das Feld **Testergebnisdateien** auf `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-273">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="947bb-274">Legen Sie **Testlauftitel** auf `Integration` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-274">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="947bb-275">Aktivieren Sie unter **Steuerungsoptionen** die Option **Immer ausführen**.</span><span class="sxs-lookup"><span data-stu-id="947bb-275">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="947bb-276">Zweites Veröffentlichen der Testergebnisse</span><span class="sxs-lookup"><span data-stu-id="947bb-276">Second Publish Test Results</span></span>

1. <span data-ttu-id="947bb-277">Wählen Sie für das Feld **Testergebnisformat** die Einstellung `NUnit` aus.</span><span class="sxs-lookup"><span data-stu-id="947bb-277">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="947bb-278">Legen Sie das Feld **Testergebnisdateien** auf `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-278">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="947bb-279">Legen Sie **Testlauftitel** auf `Acceptance` fest.</span><span class="sxs-lookup"><span data-stu-id="947bb-279">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="947bb-280">Aktivieren Sie unter **Steuerungsoptionen** die Option **Immer ausführen**.</span><span class="sxs-lookup"><span data-stu-id="947bb-280">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="947bb-281">Überprüfen Ihrer Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="947bb-281">Verify your results</span></span>

<span data-ttu-id="947bb-282">Jetzt wird jedes Mal, wenn Sie Änderungen in den `ci-cd-example`-Branch in TFS pushen, ein neuer Build gestartet.</span><span class="sxs-lookup"><span data-stu-id="947bb-282">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="947bb-283">Bei einem erfolgreichen Abschluss des Builds wird eine neue Bereitstellung ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="947bb-283">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="947bb-284">Sie können die Ergebnisse der Bereitstellung überprüfen, indem Sie einen Browser auf dem Clientcomputer öffnen und zu `www.contoso.com` navigieren.</span><span class="sxs-lookup"><span data-stu-id="947bb-284">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="947bb-285">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="947bb-285">Next steps</span></span>

<span data-ttu-id="947bb-286">In diesem Beispiel wird der DNS-Server `TestAgent1` konfiguriert, damit die URL `www.contoso.com` in `TestAgent2` aufgelöst wird. Es erfolgt jedoch keine tatsächliche Bereitstellung einer Website.</span><span class="sxs-lookup"><span data-stu-id="947bb-286">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="947bb-287">Das Skeleton hierfür wird im Repository unterhalb des Ordners `WebApp` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="947bb-287">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="947bb-288">Sie können die bereitgestellten Stubs zum Erstellen von psake-Skripts, Pester-Tests und DSC-Konfigurationen verwenden, um Ihre eigene Website bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="947bb-288">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>







