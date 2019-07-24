---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: WaitForAny-Ressource in DSC
ms.openlocfilehash: d15acb3fb34d571eca56ed496eaa9a04b2551ff0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726858"
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="7bd66-103">WaitForAny-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="7bd66-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="7bd66-104">Gilt für: Windows PowerShell 5.1 und höher</span><span class="sxs-lookup"><span data-stu-id="7bd66-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="7bd66-105">Die DSC-Ressource (Desired State Configuration) **WaitForAny** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](../../../configurations/configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="7bd66-105">The **WaitForAny** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="7bd66-106">Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf einem beliebigen der in der Eigenschaft **NodeName** definierten Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="7bd66-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>

> [!NOTE]
> <span data-ttu-id="7bd66-107">Die Ressource **WaitForAny** verwendet die Windows-Remoteverwaltung, um den Status anderer Knoten zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="7bd66-107">**WaitForAny** resource uses Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="7bd66-108">Weitere Informationen zu Anforderungen zur Portierung und Sicherheit für WinRM finden Sie unter [Sicherheitsaspekte von PowerShell-Remoting](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="7bd66-108">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="syntax"></a><span data-ttu-id="7bd66-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="7bd66-109">Syntax</span></span>

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7bd66-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="7bd66-110">Properties</span></span>

|  <span data-ttu-id="7bd66-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="7bd66-111">Property</span></span>  |  <span data-ttu-id="7bd66-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7bd66-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="7bd66-113">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="7bd66-113">ResourceName</span></span>| <span data-ttu-id="7bd66-114">Der Ressourcenname für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="7bd66-114">The resource name to depend on.</span></span> <span data-ttu-id="7bd66-115">Wenn diese Ressource zu einer anderen Konfiguration gehört, müssen Sie den Namen als „[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]“ formatieren.</span><span class="sxs-lookup"><span data-stu-id="7bd66-115">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="7bd66-116">NodeName</span><span class="sxs-lookup"><span data-stu-id="7bd66-116">NodeName</span></span>| <span data-ttu-id="7bd66-117">Die Zielknoten der Ressource für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="7bd66-117">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="7bd66-118">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="7bd66-118">RetryIntervalSec</span></span>| <span data-ttu-id="7bd66-119">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="7bd66-119">The number of seconds before retrying.</span></span> <span data-ttu-id="7bd66-120">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="7bd66-120">Minimum is 1.</span></span>|
| <span data-ttu-id="7bd66-121">RetryCount</span><span class="sxs-lookup"><span data-stu-id="7bd66-121">RetryCount</span></span>| <span data-ttu-id="7bd66-122">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="7bd66-122">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="7bd66-123">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="7bd66-123">ThrottleLimit</span></span>| <span data-ttu-id="7bd66-124">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="7bd66-124">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="7bd66-125">Per Voreinstellung wird der new-cimsession-Standardwert verwendet.</span><span class="sxs-lookup"><span data-stu-id="7bd66-125">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="7bd66-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7bd66-126">DependsOn</span></span> | <span data-ttu-id="7bd66-127">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="7bd66-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7bd66-128">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7bd66-128">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="7bd66-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7bd66-129">Example</span></span>

<span data-ttu-id="7bd66-130">Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](../../../configurations/crossNodeDependencies.md).</span><span class="sxs-lookup"><span data-stu-id="7bd66-130">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
