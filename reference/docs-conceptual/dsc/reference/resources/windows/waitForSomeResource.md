---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: WaitForSome-Ressource in DSC
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952977"
---
# <a name="dsc-waitforsome-resource"></a><span data-ttu-id="ba7ae-103">WaitForSome-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="ba7ae-103">DSC WaitForSome Resource</span></span>

> <span data-ttu-id="ba7ae-104">Gilt für: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ba7ae-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="ba7ae-105">Die DSC-Ressource (Desired State Configuration) **WaitForSome** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](../../../configurations/configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="ba7ae-106">Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf einer Mindestanzahl von Knoten (angegeben durch **NodeCount**), die durch die Eigenschaft **NodeName** definiert sind, im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="ba7ae-107">Die Ressource **WaitForSome** verwendet die Windows-Remoteverwaltung, um den Status anderer Knoten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-107">**WaitForSome** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="ba7ae-108">Weitere Informationen zu Anforderungen zur Portierung und Sicherheit für WinRM finden Sie unter [Sicherheitsaspekte von PowerShell-Remoting](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ba7ae-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="ba7ae-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba7ae-109">Syntax</span></span>

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ba7ae-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ba7ae-110">Properties</span></span>

|<span data-ttu-id="ba7ae-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ba7ae-111">Property</span></span> |<span data-ttu-id="ba7ae-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba7ae-112">Description</span></span> |
|---|---|
|<span data-ttu-id="ba7ae-113">NodeCount</span><span class="sxs-lookup"><span data-stu-id="ba7ae-113">NodeCount</span></span> |<span data-ttu-id="ba7ae-114">Die Mindestanzahl von Knoten, die sich im gewünschten Zustand befinden muss, damit diese Ressource erfolgreich ist.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-114">The minimum number of nodes that must be in the desired state for this resource to succeed.</span></span> |
|<span data-ttu-id="ba7ae-115">NodeName</span><span class="sxs-lookup"><span data-stu-id="ba7ae-115">NodeName</span></span> |<span data-ttu-id="ba7ae-116">Die Zielknoten der Ressource für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-116">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="ba7ae-117">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="ba7ae-117">ResourceName</span></span> |<span data-ttu-id="ba7ae-118">Der Ressourcenname für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-118">The resource name to depend on.</span></span> <span data-ttu-id="ba7ae-119">Wenn diese Ressource zu einer anderen Konfiguration gehört, formatieren Sie den Namen als `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-119">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="ba7ae-120">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="ba7ae-120">RetryIntervalSec</span></span> |<span data-ttu-id="ba7ae-121">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-121">The number of seconds before retrying.</span></span> <span data-ttu-id="ba7ae-122">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-122">Minimum is 1.</span></span> |
|<span data-ttu-id="ba7ae-123">RetryCount</span><span class="sxs-lookup"><span data-stu-id="ba7ae-123">RetryCount</span></span> |<span data-ttu-id="ba7ae-124">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-124">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="ba7ae-125">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="ba7ae-125">ThrottleLimit</span></span> |<span data-ttu-id="ba7ae-126">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-126">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="ba7ae-127">Die Standardeinstellung lautet `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-127">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ba7ae-128">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ba7ae-128">Common properties</span></span>

|<span data-ttu-id="ba7ae-129">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ba7ae-129">Property</span></span> |<span data-ttu-id="ba7ae-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba7ae-130">Description</span></span> |
|---|---|
|<span data-ttu-id="ba7ae-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ba7ae-131">DependsOn</span></span> |<span data-ttu-id="ba7ae-132">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ba7ae-133">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-133">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ba7ae-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ba7ae-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="ba7ae-135">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ba7ae-136">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ba7ae-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ba7ae-137">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="ba7ae-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="ba7ae-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ba7ae-138">Example</span></span>

<span data-ttu-id="ba7ae-139">Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](../../../configurations/crossNodeDependencies.md).</span><span class="sxs-lookup"><span data-stu-id="ba7ae-139">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>