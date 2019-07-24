---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: WaitForSome-Ressource in DSC
ms.openlocfilehash: 2260f37002171154a6f2c3996b2af1bd9120039d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726770"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="53d0a-103">WaitForSome-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="53d0a-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="53d0a-104">Gilt für: Windows PowerShell 5.0 und höher</span><span class="sxs-lookup"><span data-stu-id="53d0a-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="53d0a-105">Die DSC-Ressource (Desired State Configuration) **WaitForSome** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](../../../configurations/configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="53d0a-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="53d0a-106">Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die durch die Eigenschaft **NodeName** definiert sind, im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="53d0a-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="53d0a-107">Die Ressource **WaitForSome** verwendet die Windows-Remoteverwaltung, um den Status anderer Knoten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="53d0a-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="53d0a-108">Weitere Informationen zu Anforderungen zur Portierung und Sicherheit für WinRM finden Sie unter [Sicherheitsaspekte von PowerShell-Remoting](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="53d0a-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="53d0a-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="53d0a-109">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="53d0a-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="53d0a-110">Properties</span></span>

|  <span data-ttu-id="53d0a-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="53d0a-111">Property</span></span>  |  <span data-ttu-id="53d0a-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="53d0a-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="53d0a-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="53d0a-113">NodeCount</span></span>| <span data-ttu-id="53d0a-114">Die Mindestanzahl von Knoten, die sich im gewünschten Zustand befinden muss, damit diese Ressource erfolgreich ist.</span><span class="sxs-lookup"><span data-stu-id="53d0a-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span>|
| <span data-ttu-id="53d0a-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="53d0a-115">NodeName</span></span>| <span data-ttu-id="53d0a-116">Die Zielknoten der Ressource für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="53d0a-116">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="53d0a-117">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="53d0a-117">ResourceName</span></span>| <span data-ttu-id="53d0a-118">Der Ressourcenname für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="53d0a-118">The resource name to depend on.</span></span> <span data-ttu-id="53d0a-119">Wenn diese Ressource zu einer anderen Konfiguration gehört, müssen Sie den Namen als „[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]“ formatieren.</span><span class="sxs-lookup"><span data-stu-id="53d0a-119">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="53d0a-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="53d0a-120">RetryIntervalSec</span></span>| <span data-ttu-id="53d0a-121">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="53d0a-121">The number of seconds before retrying.</span></span> <span data-ttu-id="53d0a-122">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="53d0a-122">Minimum is 1.</span></span>|
| <span data-ttu-id="53d0a-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="53d0a-123">RetryCount</span></span>| <span data-ttu-id="53d0a-124">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="53d0a-124">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="53d0a-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="53d0a-125">ThrottleLimit</span></span>| <span data-ttu-id="53d0a-126">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="53d0a-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="53d0a-127">Per Voreinstellung wird der new-cimsession-Standardwert verwendet.</span><span class="sxs-lookup"><span data-stu-id="53d0a-127">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="53d0a-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="53d0a-128">DependsOn</span></span> | <span data-ttu-id="53d0a-129">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="53d0a-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="53d0a-130">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="53d0a-130">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="53d0a-131">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="53d0a-131">PsDscRunAsCredential</span></span> | <span data-ttu-id="53d0a-132">Informationen finden Sie unter [Verwenden von DSC mit Benutzeranmeldeinformationen](https://docs.microsoft.com/powershell/dsc/runasuser).</span><span class="sxs-lookup"><span data-stu-id="53d0a-132">See [Using DSC with User Credentials](https://docs.microsoft.com/powershell/dsc/runasuser)</span></span> |

## <a name="example"></a><span data-ttu-id="53d0a-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="53d0a-133">Example</span></span>

<span data-ttu-id="53d0a-134">Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](../../../configurations/crossNodeDependencies.md).</span><span class="sxs-lookup"><span data-stu-id="53d0a-134">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
