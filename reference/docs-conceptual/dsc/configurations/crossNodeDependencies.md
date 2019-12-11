---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Angeben knotenübergreifender Abhängigkeiten
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954107"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="d7ce1-103">Angeben knotenübergreifender Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="d7ce1-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="d7ce1-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d7ce1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d7ce1-105">DSC bietet spezielle Ressourcen **WaitForAll**, **WaitForAny** und **WaitForSome**, die in Konfigurationen zum Angeben von Abhängigkeiten von Konfigurationen auf anderen Knoten verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="d7ce1-106">Die Ressourcen verhalten sich wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d7ce1-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="d7ce1-107">**WaitForAll**: Ist erfolgreich, wenn die angegebene Ressource auf allen Zielknoten, die in der **NodeName**-Eigenschaft definiert sind, den gewünschten Zustand aufweist.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="d7ce1-108">**WaitForAny**: Ist erfolgreich, wenn die angegebene Ressource auf mindestens einem der Zielknoten, die in der **NodeName**-Eigenschaft definiert sind, den gewünschten Zustand aufweist.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="d7ce1-109">**WaitForSome**: Gibt zusätzlich zu einer **NodeName**-Eigenschaft eine **NodeCount**-Eigenschaft an.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="d7ce1-110">Die Ressource ist erfolgreich, wenn sich die Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die von der **NodeName**-Eigenschaft definiert sind, im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7ce1-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7ce1-111">Syntax</span></span>

<span data-ttu-id="d7ce1-112">Die **WaitForAll**- und **WaitForAny**-Ressourcen verwenden die gleiche Syntax.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="d7ce1-113">Ersetzen Sie \<ResourceType\> im folgenden Beispiel durch **WaitForAny** oder durch **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="d7ce1-114">Wie beim Schlüsselwort **DependsOn** müssen Sie den Namen als „[RessourcenTyp]RessourcenName“ formatieren.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="d7ce1-115">Wenn die Ressource zu einer separaten [Konfiguration](configurations.md) gehört, fügen Sie den **KonfigurationsNamen** in die formatierte Zeichenfolge „[RessourcenTyp]RessourcenName::[KonfigurationsName]::[KonfigurationsName]“ ein.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="d7ce1-116">Der **NodeName** ist der Computer oder Knoten, auf den die aktuelle Ressource warten soll.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="d7ce1-117">Die Ressource **WaitForSome** hat eine ähnliche Syntax wie das Beispiel oben, fügt aber den Schlüssel **NodeCount** hinzu.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="d7ce1-118">Der **NodeCount** gibt an, auf wie viele Knoten die aktuelle Ressource warten soll.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="d7ce1-119">Alle **WaitForXXXX**-Ressourcen verwenden die folgenden Syntaxschlüssel gemeinsam.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="d7ce1-120">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="d7ce1-120">Property</span></span>|  <span data-ttu-id="d7ce1-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d7ce1-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="d7ce1-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="d7ce1-122">RetryIntervalSec</span></span>| <span data-ttu-id="d7ce1-123">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-123">The number of seconds before retrying.</span></span> <span data-ttu-id="d7ce1-124">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-124">Minimum is 1.</span></span>|
| <span data-ttu-id="d7ce1-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="d7ce1-125">RetryCount</span></span>| <span data-ttu-id="d7ce1-126">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="d7ce1-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="d7ce1-127">ThrottleLimit</span></span>| <span data-ttu-id="d7ce1-128">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="d7ce1-129">Die Standardeinstellung lautet `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="d7ce1-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d7ce1-130">DependsOn</span></span> | <span data-ttu-id="d7ce1-131">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d7ce1-132">Weitere Informationen finden Sie unter [DependsOn](resource-depends-on.md).</span><span class="sxs-lookup"><span data-stu-id="d7ce1-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="d7ce1-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d7ce1-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="d7ce1-134">Informationen finden Sie unter [Verwenden von DSC mit Benutzeranmeldeinformationen](./runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d7ce1-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="d7ce1-135">Verwenden von WaitForXXXX-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d7ce1-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="d7ce1-136">Jede **WaitForXXXX**-Ressource wartet darauf, dass die angegebenen Ressourcen auf dem angegebenen Knoten abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="d7ce1-137">Andere Ressourcen in derselben Konfiguration können dann von der **WaitForXXXX**-Ressource mit dem Schlüssel **DependsOn** als *abhängig* gekennzeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="d7ce1-138">Bei der folgenden Konfiguration wartet der Zielknoten beispielsweise, bis die Ressource **xADDomain** auf dem Knoten **MyDC** (bei einer maximalen Anzahl von 30 Wiederholungen in 15-Sekunden-Intervallen) abgeschlossen ist, ehe der Zielknoten der Domäne beitreten kann.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="d7ce1-139">Standardmäßig führen die **WaitForXXXX**-Ressourcen einen Versuch durch und verursachen dann einen Fehler.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="d7ce1-140">Auch wenn dies nicht erforderlich ist, sollten Sie in der Regel **RetryCount** sowie **RetryIntervalSec** angeben.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

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

<span data-ttu-id="d7ce1-141">Wenn Sie die Konfiguration kompilieren, werden zwei MOF-Dateien generiert.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="d7ce1-142">Wenden Sie beide MOF-Dateien mit dem Cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) auf die Zielknoten an.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="d7ce1-143">Die Ressource **WaitForXXX** verwendet die Windows-Remoteverwaltung, um den Status anderer Knoten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="d7ce1-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="d7ce1-144">Weitere Informationen zu Anforderungen zur Portierung und Sicherheit für WinRM finden Sie unter [Sicherheitsaspekte von PowerShell-Remoting](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="d7ce1-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7ce1-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d7ce1-145">See Also</span></span>

- [<span data-ttu-id="d7ce1-146">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="d7ce1-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="d7ce1-147">Verwenden von Ressourcenabhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="d7ce1-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="d7ce1-148">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d7ce1-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="d7ce1-149">Konfigurieren des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="d7ce1-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
