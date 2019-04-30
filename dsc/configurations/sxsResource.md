---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Importieren einer spezifischen Version einer installierten Ressource
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079998"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="8671f-103">Importieren einer spezifischen Version einer installierten Ressource</span><span class="sxs-lookup"><span data-stu-id="8671f-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="8671f-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8671f-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8671f-105">In PowerShell 5.0 können separate Versionen von DSC-Ressourcen auf einem Computer parallel installiert werden.</span><span class="sxs-lookup"><span data-stu-id="8671f-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="8671f-106">Ein Ressourcenmodul kann separate Versionen einer Ressource in nach der Version benannten Ordnern speichern.</span><span class="sxs-lookup"><span data-stu-id="8671f-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="8671f-107">Paralleles Installieren separater Ressourcenversionen</span><span class="sxs-lookup"><span data-stu-id="8671f-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="8671f-108">Sie können die Parameter **MinimumVersion**, **MaximumVersion** und **RequiredVersion** des Cmdlets [Install-Module](/powershell/module/PowershellGet/Install-Module) verwenden, um anzugeben, welche Version eines Moduls installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="8671f-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="8671f-109">Wenn Sie **Install-Module** ohne Angabe eine Version aufrufen, wird die neueste Version installiert.</span><span class="sxs-lookup"><span data-stu-id="8671f-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="8671f-110">So gibt es beispielsweise mehrere Versionen des **xFailOverCluster**-Moduls, von denen jede eine **xCluster**-Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="8671f-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="8671f-111">Wenn Sie **Install-Module** ohne Angabe der Versionsnummer aufrufen, wird die neueste Version des Moduls installiert.</span><span class="sxs-lookup"><span data-stu-id="8671f-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="8671f-112">Um eine bestimmte Version eines Moduls zu installieren, geben Sie eine **RequiredVersion** von 1.1.0.0 an.</span><span class="sxs-lookup"><span data-stu-id="8671f-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="8671f-113">Dadurch wird die angegebene Version parallel mit der installierten Version installiert.</span><span class="sxs-lookup"><span data-stu-id="8671f-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="8671f-114">Nun sehen Sie, dass beide Versionen des Moduls aufgelistet werden, wenn Sie `Get-DSCResource` verwenden.</span><span class="sxs-lookup"><span data-stu-id="8671f-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="8671f-115">Angeben einer Ressourcenversion in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="8671f-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="8671f-116">Wenn Sie separate Ressourcenversionen auf einem Computer installiert haben, müssen Sie die Version dieser Ressource angeben, wenn Sie sie in einer Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="8671f-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="8671f-117">Hierzu geben Sie den Parameter **ModuleVersion** des Schlüsselworts **Import-DscResource** an.</span><span class="sxs-lookup"><span data-stu-id="8671f-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="8671f-118">Wenn Sie bei einer Ressource, von der Sie mehr als eine Version installiert haben, keine Version des Ressourcenmoduls angeben, generiert die Konfiguration einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="8671f-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="8671f-119">Die folgende Konfiguration zeigt, wie Sie die Version der aufzurufenden Ressource angeben:</span><span class="sxs-lookup"><span data-stu-id="8671f-119">The following configuration shows how to specify the version of the resource to call:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

><span data-ttu-id="8671f-120">Hinweis: Der Parameter „ModuleVersion“ von „Import-DscResource“ ist in PowerShell 4.0 nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8671f-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="8671f-121">In PowerShell 4.0 können Sie eine Modulversion angeben, indem Sie ein Modulspezifikationsobjekt an den Parameter „ModuleName“ von „Import-DscResource“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="8671f-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="8671f-122">Ein Modulspezifikationsobjekt ist eine Hashtabelle, die die Schlüssel „ModuleName“ und „RequiredVersion“ enthält.</span><span class="sxs-lookup"><span data-stu-id="8671f-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="8671f-123">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="8671f-123">For example:</span></span>

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

<span data-ttu-id="8671f-124">Dies funktioniert auch in PowerShell 5.0, aber es wird empfohlen, dass Sie den Parameter **ModuleVersion** verwenden.</span><span class="sxs-lookup"><span data-stu-id="8671f-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="8671f-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8671f-125">See also</span></span>

- [<span data-ttu-id="8671f-126">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="8671f-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="8671f-127">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8671f-127">DSC Resources</span></span>](../resources/resources.md)
