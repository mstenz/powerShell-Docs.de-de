---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Verwenden von Ressourcen mit mehreren Versionen
ms.openlocfilehash: 8bd8b1dab9418c6d8cf64cd682c527a7f039cdb4
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="88f09-103">Verwenden von Ressourcen mit mehreren Versionen</span><span class="sxs-lookup"><span data-stu-id="88f09-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="88f09-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="88f09-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="88f09-105">In PowerShell 5.0 können DSC-Ressourcen mehrere Versionen haben, und verschiedene Versionen können parallel auf einem Computer installiert sein.</span><span class="sxs-lookup"><span data-stu-id="88f09-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="88f09-106">Dies wird dadurch implementiert, dass mehrere Versionen eines Ressourcenmoduls vorhanden sind, die sich im selben Modulordner befinden.</span><span class="sxs-lookup"><span data-stu-id="88f09-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="88f09-107">Paralleles Installieren mehrerer Ressourcenversionen</span><span class="sxs-lookup"><span data-stu-id="88f09-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="88f09-108">Sie können die Parameter **MinimumVersion**, **MaximumVersion** und **RequiredVersion** des Cmdlets [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) verwenden, um anzugeben, welche Version eines Moduls installiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="88f09-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="88f09-109">Wenn Sie **Install-Module** ohne Angabe eine Version aufrufen, wird die neueste Version installiert.</span><span class="sxs-lookup"><span data-stu-id="88f09-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="88f09-110">So gibt es beispielsweise mehrere Versionen des **xFailOverCluster**-Moduls, von denen jede eine **xCluster**-Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="88f09-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="88f09-111">Das Ergebnis des Aufrufs von **Install-Module** ohne Angabe der Versionsnummer sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="88f09-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="88f09-112">Wenn Sie nun **Install-Module** erneut aufrufen, dabei aber eine **RequiredVersion** von „1.1.0.0“ angeben, erhalten Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="88f09-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="88f09-113">Angeben einer Ressourcenversion in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="88f09-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="88f09-114">Wenn Sie mehrere Ressourcen auf einem Computer installiert haben, müssen Sie die Version dieser Ressource angeben, wenn Sie sie in einer Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="88f09-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="88f09-115">Hierzu geben Sie den Parameter **ModuleVersion** des Schlüsselworts **Import-DscResource** an.</span><span class="sxs-lookup"><span data-stu-id="88f09-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="88f09-116">Wenn Sie bei einer Ressource, von der Sie mehr als eine Version installiert haben, keine Version des Ressourcenmoduls angeben, generiert die Konfiguration einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="88f09-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="88f09-117">Die folgende Konfiguration zeigt, wie Sie die Version der aufzurufenden Ressource angeben:</span><span class="sxs-lookup"><span data-stu-id="88f09-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="88f09-118">Hinweis: Der Parameter „ModuleVersion“ von „Import-DscResource“ ist in PowerShell 4.0 nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="88f09-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="88f09-119">In PowerShell 4.0 können Sie eine Modulversion angeben, indem Sie ein Modulspezifikationsobjekt an den Parameter „ModuleName“ von „Import-DscResource“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="88f09-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="88f09-120">Ein Modulspezifikationsobjekt ist eine Hashtabelle, die die Schlüssel „ModuleName“ und „RequiredVersion“ enthält.</span><span class="sxs-lookup"><span data-stu-id="88f09-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="88f09-121">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="88f09-121">For example:</span></span>

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

<span data-ttu-id="88f09-122">Dies funktioniert auch in PowerShell 5.0, aber es wird empfohlen, dass Sie den Parameter **ModuleVersion** verwenden.</span><span class="sxs-lookup"><span data-stu-id="88f09-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="88f09-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="88f09-123">See also</span></span>
* [<span data-ttu-id="88f09-124">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="88f09-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="88f09-125">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="88f09-125">DSC Resources</span></span>](resources.md)

