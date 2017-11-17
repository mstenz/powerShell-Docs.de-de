---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Angeben knotenübergreifender Abhängigkeiten"
ms.openlocfilehash: 885c130fb050629aac4c072e18a147d77b9deb8f
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="3c1f0-103">Angeben knotenübergreifender Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="3c1f0-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="3c1f0-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3c1f0-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3c1f0-105">DSC bietet spezielle Ressourcen **WaitForAll**, **WaitForAny** und **WaitForSome**, die in Konfigurationen zum Angeben von Abhängigkeiten von Konfigurationen auf anderen Knoten verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="3c1f0-106">Die Ressourcen verhalten sich wie folgt:</span><span class="sxs-lookup"><span data-stu-id="3c1f0-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="3c1f0-107">**WaitForAll**: Ist erfolgreich, wenn die angegebene Ressource auf allen Zielknoten, die in der **NodeName**-Eigenschaft definiert sind, den gewünschten Zustand hat.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="3c1f0-108">**WaitForAny**: Ist erfolgreich, wenn die angegebene Ressource auf mindestens einem der Zielknoten, die in der **NodeName**-Eigenschaft definiert sind, den gewünschten Zustand hat.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="3c1f0-109">**WaitForSome**: Gibt zusätzlich zu einer **NodeName**-Eigenschaft eine **NodeCount**-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="3c1f0-110">Die Ressource ist erfolgreich, wenn sich die Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die von der **NodeName**-Eigenschaft definiert sind, im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="3c1f0-111">Verwenden von WaitForXXXX-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="3c1f0-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="3c1f0-112">Um die **WaitForXXXX**-Ressourcen zu verwenden, erstellen Sie einen Ressourcenblock des Ressourcentyps, der die DSC-Ressource und Knoten angibt, auf die gewartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="3c1f0-113">Dann verwenden Sie die **DependsOn**-Eigenschaft in allen anderen Ressourcenblöcken Ihrer Konfiguration und warten darauf, dass die im **WaitForXXXX**-Knoten angegebenen Bedingungen erfolgreich erfüllt werden.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="3c1f0-114">Bei der folgenden Konfiguration wartet der Zielknoten beispielsweise, bis die Ressource **xADDomain** auf dem Knoten **MyDC** (bei einer maximalen Anzahl von 30 Wiederholungen in 15-Sekunden-Intervallen) abgeschlossen ist, ehe der Zielknoten der Domäne beitreten kann.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

```powershell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present' 
            Name = 'AD-Domain-Services' 
        }

        xADDomain NewDomain 
        { 
            DomainName = 'Contoso.com'            
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }

    }

    Node myDomainJoinedServer
    {

        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

><span data-ttu-id="3c1f0-115">**Hinweis:** Standardmäßig führen die „WaitForXXXX“-Ressourcen einen Versuch durch und verursachen dann einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="3c1f0-116">Auch wenn dies nicht erforderlich ist, sollten Sie doch in der Regel ein Wiederholungsintervall sowie eine Anzahl von Wiederholungen angeben.</span><span class="sxs-lookup"><span data-stu-id="3c1f0-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c1f0-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3c1f0-117">See Also</span></span>
* [<span data-ttu-id="3c1f0-118">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="3c1f0-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="3c1f0-119">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="3c1f0-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="3c1f0-120">Konfigurieren des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="3c1f0-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

