---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Bereitstellung und Wartung mehrerer Computer
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="07af5-103">Bereitstellung und Wartung mehrerer Computer</span><span class="sxs-lookup"><span data-stu-id="07af5-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="07af5-104">Bisher haben Sie JEA mehrmals auf lokalen Systemen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="07af5-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="07af5-105">Da Ihre Produktionsumgebung aller Wahrscheinlichkeit nach aus mehr als einen Computer besteht, müssen Sie die wichtigen Schritte im Bereitstellungsprozesses kennen, die auf jedem Computer ausgeführt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="07af5-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="07af5-106">Allgemeine Schritte:</span><span class="sxs-lookup"><span data-stu-id="07af5-106">High Level Steps:</span></span>
1.  <span data-ttu-id="07af5-107">Kopieren Sie Ihre Module (mit Rollenfunktionen) auf jeden Knoten.</span><span class="sxs-lookup"><span data-stu-id="07af5-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="07af5-108">Kopieren Sie Ihre Sitzungskonfigurationsdateien auf jeden Knoten.</span><span class="sxs-lookup"><span data-stu-id="07af5-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="07af5-109">Führen Sie `Register-PSSessionConfiguration` mit Ihrer Sitzungskonfiguration aus.</span><span class="sxs-lookup"><span data-stu-id="07af5-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="07af5-110">Speichern Sie eine Kopie Ihrer Sitzungskonfiguration und Toolkits an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="07af5-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="07af5-111">Wenn Sie Änderungen vornehmen, ist es gut, über eine „sichere Informationsquelle“ zu verfügen.</span><span class="sxs-lookup"><span data-stu-id="07af5-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="07af5-112">Beispielskript</span><span class="sxs-lookup"><span data-stu-id="07af5-112">Example Script</span></span>
<span data-ttu-id="07af5-113">Hier sehen Sie ein Beispielskript für die Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="07af5-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="07af5-114">Um dieses Skript in Ihrer Umgebung zu verwenden, müssen Sie die Namen/Pfade echter Dateifreigaben und Module angeben.</span><span class="sxs-lookup"><span data-stu-id="07af5-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## <a name="modifying-capabilities"></a><span data-ttu-id="07af5-115">Ändern von Funktionen</span><span class="sxs-lookup"><span data-stu-id="07af5-115">Modifying Capabilities</span></span>
<span data-ttu-id="07af5-116">Beim Arbeiten mit vielen Computern ist es wichtig, dass Änderungen auf konsistente Weise eingeführt werden.</span><span class="sxs-lookup"><span data-stu-id="07af5-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="07af5-117">Sobald JEA über eine DSC-Ressource verfügt, wird sichergestellt, dass Ihre Umgebung synchronisiert ist.</span><span class="sxs-lookup"><span data-stu-id="07af5-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="07af5-118">Bis dahin empfiehlt es sich dringend, eine Masterkopie Ihrer Sitzungskonfigurationen zu speichern und diese nach jeder Änderung erneut bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="07af5-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="07af5-119">Entfernen von Funktionen:</span><span class="sxs-lookup"><span data-stu-id="07af5-119">Removing Capabilities</span></span>
<span data-ttu-id="07af5-120">Um Ihre JEA-Konfiguration von Ihren Systemen zu entfernen, verwenden Sie den folgenden Befehl auf jedem Computer:</span><span class="sxs-lookup"><span data-stu-id="07af5-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

