---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: WaitForAny-Ressource in DSC
ms.openlocfilehash: 61fee456d2652e08ed9bdbe64457627ff5b2e145
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952997"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="df34b-103">WaitForAny-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="df34b-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="df34b-104">Gilt für: Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="df34b-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="df34b-105">Die DSC-Ressource (Desired State Configuration) **WaitForAny** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](../../../configurations/configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="df34b-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="df34b-106">Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf einem beliebigen der in der Eigenschaft **NodeName** definierten Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="df34b-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="df34b-107">Die Ressource **WaitForAny** verwendet die Windows-Remoteverwaltung, um den Status anderer Knoten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="df34b-107">**WaitForAny** resource uses Windows Remote Management to check the state of other Nodes.</span></span> <span data-ttu-id="df34b-108">Weitere Informationen zu Anforderungen zur Portierung und Sicherheit für WinRM finden Sie unter [Sicherheitsaspekte von PowerShell-Remoting](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="df34b-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="df34b-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="df34b-109">Syntax</span></span>

```Syntax
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string[]]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="df34b-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="df34b-110">Properties</span></span>

|<span data-ttu-id="df34b-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="df34b-111">Property</span></span> |<span data-ttu-id="df34b-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="df34b-112">Description</span></span> |
|---|---|
|<span data-ttu-id="df34b-113">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="df34b-113">ResourceName</span></span> |<span data-ttu-id="df34b-114">Der Ressourcenname für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="df34b-114">The resource name to depend on.</span></span> <span data-ttu-id="df34b-115">Wenn diese Ressource zu einer anderen Konfiguration gehört, formatieren Sie den Namen als `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span><span class="sxs-lookup"><span data-stu-id="df34b-115">If this resource belongs to a different configuration, format the name as `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`.</span></span> |
|<span data-ttu-id="df34b-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="df34b-116">NodeName</span></span> |<span data-ttu-id="df34b-117">Die Zielknoten der Ressource für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="df34b-117">The target nodes of the resource to depend on.</span></span> |
|<span data-ttu-id="df34b-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="df34b-118">RetryIntervalSec</span></span> |<span data-ttu-id="df34b-119">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="df34b-119">The number of seconds before retrying.</span></span> <span data-ttu-id="df34b-120">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="df34b-120">Minimum is 1.</span></span> |
|<span data-ttu-id="df34b-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="df34b-121">RetryCount</span></span> |<span data-ttu-id="df34b-122">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="df34b-122">The maximum number of times to retry.</span></span> |
|<span data-ttu-id="df34b-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="df34b-123">ThrottleLimit</span></span> |<span data-ttu-id="df34b-124">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="df34b-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="df34b-125">Die Standardeinstellung lautet `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="df34b-125">Default is `New-CimSession` default.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="df34b-126">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="df34b-126">Common properties</span></span>

|<span data-ttu-id="df34b-127">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="df34b-127">Property</span></span> |<span data-ttu-id="df34b-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="df34b-128">Description</span></span> |
|---|---|
|<span data-ttu-id="df34b-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="df34b-129">DependsOn</span></span> |<span data-ttu-id="df34b-130">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="df34b-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="df34b-131">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="df34b-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="df34b-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="df34b-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="df34b-133">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="df34b-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="df34b-134">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="df34b-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="df34b-135">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="df34b-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="df34b-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="df34b-136">Example</span></span>

<span data-ttu-id="df34b-137">Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](../../../configurations/crossNodeDependencies.md).</span><span class="sxs-lookup"><span data-stu-id="df34b-137">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>