---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Angeben knotenübergreifender Abhängigkeiten
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401163"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="4c00e-103">Angeben knotenübergreifender Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="4c00e-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="4c00e-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4c00e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4c00e-105">DSC bietet spezielle Ressourcen **WaitForAll**, **WaitForAny** und **WaitForSome**, die in Konfigurationen zum Angeben von Abhängigkeiten von Konfigurationen auf anderen Knoten verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="4c00e-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="4c00e-106">Die Ressourcen verhalten sich wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4c00e-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="4c00e-107">**WaitForAll**: Ist erfolgreich, wenn die angegebene Ressource auf allen Zielknoten, die definiert, die den gewünschten Zustand der **NodeName** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4c00e-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="4c00e-108">**WaitForAny**: Ist erfolgreich, wenn die angegebene Ressource auf mindestens einem der Zielknoten im gewünschten Zustand wird die **NodeName** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4c00e-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="4c00e-109">**WaitForSome**: Gibt an, eine **NodeCount** Eigenschaft zusätzlich zu einem **NodeName** Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="4c00e-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="4c00e-110">Die Ressource ist erfolgreich, wenn sich die Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die von der **NodeName**-Eigenschaft definiert sind, im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="4c00e-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c00e-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c00e-111">Syntax</span></span>

<span data-ttu-id="4c00e-112">Die **WaitForAll** und **WaitForAny** Ressourcen freigeben, die gleiche Syntax.</span><span class="sxs-lookup"><span data-stu-id="4c00e-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="4c00e-113">Ersetzen Sie dies \<ResourceType\> im folgenden Beispiel mit einem **WaitForAny** oder **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="4c00e-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="4c00e-114">Wie die **"DependsOn"** -Schlüsselwort, Sie müssen den Namen wie "[ResourceType] ResourceName" zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="4c00e-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="4c00e-115">Wenn die Ressource, zu einem eigenen gehört [Konfiguration](configurations.md), enthalten die **ConfigurationName** in der formatierten Zeichenfolge "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="4c00e-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="4c00e-116">Die **NodeName** wird vom Computer bzw. der Knoten, auf dem die aktuelle Ressource warten muss.</span><span class="sxs-lookup"><span data-stu-id="4c00e-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="4c00e-117">Die **WaitForSome** Ressource verfügt über eine ähnliche Syntax im obigen Beispiel, jedoch fügt die **NodeCount** Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="4c00e-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="4c00e-118">Die **NodeCount** gibt an, wie viele Knoten, die die aktuelle Ressource sollte auf warten.</span><span class="sxs-lookup"><span data-stu-id="4c00e-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="4c00e-119">Alle **WaitForXXXX** Teilen Sie die folgende Syntax-Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="4c00e-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="4c00e-120">|  Eigenschaft |  Beschreibung || RetryIntervalSec | Die Anzahl der Sekunden, bevor der Vorgang wird wiederholt.</span><span class="sxs-lookup"><span data-stu-id="4c00e-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="4c00e-121">Der Mindestwert lautet 1. | | RetryCount | Die maximale Anzahl der Wiederholungsversuche. | | ThrottleLimit | Anzahl von Computern gleichzeitig eine Verbindung herstellen.</span><span class="sxs-lookup"><span data-stu-id="4c00e-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="4c00e-122">Der Standardwert ist `New-CimSession` Standard. | | "DependsOn" | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="4c00e-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4c00e-123">Weitere Informationen finden Sie unter ["DependsOn"](resource-depends-on.md)|| "Psdscrunascredential" | Finden Sie unter [unter Verwendung von DSC mit Benutzeranmeldeinformationen](./runAsUser.md) |</span><span class="sxs-lookup"><span data-stu-id="4c00e-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="4c00e-124">Verwenden von WaitForXXXX-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4c00e-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="4c00e-125">Jede **WaitForXXXX** ressourcenwartevorgänge für die angegebenen Ressourcen auf dem angegebenen Knoten ausführen.</span><span class="sxs-lookup"><span data-stu-id="4c00e-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="4c00e-126">Andere Ressourcen in der gleichen Konfiguration können Sie *hängen* der **WaitForXXXX** Ressource mit der **"DependsOn"** Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="4c00e-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="4c00e-127">Bei der folgenden Konfiguration wartet der Zielknoten beispielsweise, bis die Ressource **xADDomain** auf dem Knoten **MyDC** (bei einer maximalen Anzahl von 30 Wiederholungen in 15-Sekunden-Intervallen) abgeschlossen ist, ehe der Zielknoten der Domäne beitreten kann.</span><span class="sxs-lookup"><span data-stu-id="4c00e-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="4c00e-128">Wenn Sie die Konfiguration kompilieren, werden zwei "MOF"-Dateien generiert.</span><span class="sxs-lookup"><span data-stu-id="4c00e-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="4c00e-129">Sowohl "MOF"-Dateien anwenden, an die Zielknoten, die mit der [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4c00e-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="4c00e-130">**Hinweis:** Standardmäßig ist die Waitforxxxx Ressourcen einen Versuch und schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="4c00e-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="4c00e-131">Obwohl es nicht erforderlich ist, wird in der Regel angeben möchten einer **RetryCount** und **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="4c00e-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c00e-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4c00e-132">See Also</span></span>

- [<span data-ttu-id="4c00e-133">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4c00e-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="4c00e-134">Verwenden Sie die Ressourcenabhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="4c00e-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="4c00e-135">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4c00e-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="4c00e-136">Konfigurieren des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="4c00e-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
