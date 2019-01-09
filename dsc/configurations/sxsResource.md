---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Importieren einer spezifischen Version einer installierten Ressource
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401169"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="b94c2-103">Importieren einer spezifischen Version einer installierten Ressource</span><span class="sxs-lookup"><span data-stu-id="b94c2-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="b94c2-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b94c2-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b94c2-105">In PowerShell 5.0 können jeweils eine Version der DSC-Ressourcen auf einem Computer parallel installiert werden.</span><span class="sxs-lookup"><span data-stu-id="b94c2-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="b94c2-106">Ein Ressourcenmodul kann separate Versionen einer Ressource in Version, die mit dem Namen Ordner speichern.</span><span class="sxs-lookup"><span data-stu-id="b94c2-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="b94c2-107">Separate Ressource Versionen parallel installieren</span><span class="sxs-lookup"><span data-stu-id="b94c2-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="b94c2-108">Sie können die Parameter **MinimumVersion**, **MaximumVersion** und **RequiredVersion** des Cmdlets [Install-Module](/powershell/module/PowershellGet/Install-Module) verwenden, um anzugeben, welche Version eines Moduls installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="b94c2-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="b94c2-109">Wenn Sie **Install-Module** ohne Angabe eine Version aufrufen, wird die neueste Version installiert.</span><span class="sxs-lookup"><span data-stu-id="b94c2-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="b94c2-110">So gibt es beispielsweise mehrere Versionen des **xFailOverCluster**-Moduls, von denen jede eine **xCluster**-Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="b94c2-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="b94c2-111">Aufrufen von **Install-Module** ohne Angabe der Versionsnummer Anzahl die neueste Version des Moduls wird installiert.</span><span class="sxs-lookup"><span data-stu-id="b94c2-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="b94c2-112">Um eine bestimmte Version eines Moduls zu installieren, geben Sie einen **"requiredversion"** von 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="b94c2-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="b94c2-113">Dadurch wird die angegebene Version parallel mit der installierten Version installiert.</span><span class="sxs-lookup"><span data-stu-id="b94c2-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="b94c2-114">Sie sehen Sie sich sowohl Version des Moduls aufgeführt, bei der Verwendung `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="b94c2-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="b94c2-115">Angeben einer Ressourcenversion in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="b94c2-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="b94c2-116">Wenn Sie eine separate Ressource-Versionen, die auf einem Computer installiert haben, müssen Sie die Version der Ressource, die bei Verwendung in einer Konfiguration angeben.</span><span class="sxs-lookup"><span data-stu-id="b94c2-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="b94c2-117">Hierzu geben Sie den Parameter **ModuleVersion** des Schlüsselworts **Import-DscResource** an.</span><span class="sxs-lookup"><span data-stu-id="b94c2-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="b94c2-118">Wenn Sie bei einer Ressource, von der Sie mehr als eine Version installiert haben, keine Version des Ressourcenmoduls angeben, generiert die Konfiguration einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="b94c2-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="b94c2-119">Die folgende Konfiguration zeigt, wie Sie die Version der aufzurufenden Ressource angeben:</span><span class="sxs-lookup"><span data-stu-id="b94c2-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="b94c2-120">Hinweis: Der Parameter "ModuleVersion" des Import-DscResource ist nicht in PowerShell 4.0 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b94c2-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="b94c2-121">In PowerShell 4.0 können Sie eine Modulversion angeben, indem Sie ein Modulspezifikationsobjekt an den Parameter „ModuleName“ von „Import-DscResource“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="b94c2-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="b94c2-122">Ein Modulspezifikationsobjekt ist eine Hashtabelle, die die Schlüssel „ModuleName“ und „RequiredVersion“ enthält.</span><span class="sxs-lookup"><span data-stu-id="b94c2-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="b94c2-123">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b94c2-123">For example:</span></span>

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

<span data-ttu-id="b94c2-124">Dies funktioniert auch in PowerShell 5.0, aber es wird empfohlen, dass Sie den Parameter **ModuleVersion** verwenden.</span><span class="sxs-lookup"><span data-stu-id="b94c2-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b94c2-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b94c2-125">See also</span></span>

- [<span data-ttu-id="b94c2-126">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="b94c2-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="b94c2-127">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="b94c2-127">DSC Resources</span></span>](../resources/resources.md)
