---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: WaitForAny-Ressource in DSC
ms.openlocfilehash: 795c005c67c196ef9afb08af790fe2a1695392ec
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforany-resource"></a><span data-ttu-id="051b4-103">WaitForAny-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="051b4-103">DSC WaitForAny Resource</span></span>

> <span data-ttu-id="051b4-104">Gilt für: Windows PowerShell 5.1 und höher.</span><span class="sxs-lookup"><span data-stu-id="051b4-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="051b4-105">Die DSC-Ressource (Desired State Configuration) **WaitForSome** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="051b4-105">The **WaitForSome** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="051b4-106">Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf einem beliebigen der in der Eigenschaft **NodeName** definierten Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="051b4-106">This resource succeeds if if the resource specified by the **ResourceName** property is in the desired state on any target nodes defined in the **NodeName** property.</span></span>


## <a name="syntax"></a><span data-ttu-id="051b4-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="051b4-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="051b4-108">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="051b4-108">Properties</span></span>

|  <span data-ttu-id="051b4-109">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="051b4-109">Property</span></span>  |  <span data-ttu-id="051b4-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="051b4-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="051b4-111">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="051b4-111">ResourceName</span></span>| <span data-ttu-id="051b4-112">Der Ressourcenname für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="051b4-112">The resource name to depend on.</span></span>| 
| <span data-ttu-id="051b4-113">NodeName</span><span class="sxs-lookup"><span data-stu-id="051b4-113">NodeName</span></span>| <span data-ttu-id="051b4-114">Die Zielknoten der Ressource für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="051b4-114">The target nodes of the resource to depend on.</span></span>| 
| <span data-ttu-id="051b4-115">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="051b4-115">RetryIntervalSec</span></span>| <span data-ttu-id="051b4-116">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="051b4-116">The number of seconds before retrying.</span></span> <span data-ttu-id="051b4-117">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="051b4-117">Minimum is 1.</span></span>| 
| <span data-ttu-id="051b4-118">RetryCount</span><span class="sxs-lookup"><span data-stu-id="051b4-118">RetryCount</span></span>| <span data-ttu-id="051b4-119">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="051b4-119">The maximum number of times to retry.</span></span>| 
| <span data-ttu-id="051b4-120">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="051b4-120">ThrottleLimit</span></span>| <span data-ttu-id="051b4-121">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="051b4-121">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="051b4-122">Per Voreinstellung wird der new-cimsession-Standardwert verwendet.</span><span class="sxs-lookup"><span data-stu-id="051b4-122">Default is new-cimsession default.</span></span>| 
| <span data-ttu-id="051b4-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="051b4-123">DependsOn</span></span> | <span data-ttu-id="051b4-124">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="051b4-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="051b4-125">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="051b4-125">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="example"></a><span data-ttu-id="051b4-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="051b4-126">Example</span></span>

<span data-ttu-id="051b4-127">Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](crossNodeDependencies.md).</span><span class="sxs-lookup"><span data-stu-id="051b4-127">For an example of how to use this resource, see [Specifying cross-node dependencies](crossNodeDependencies.md)</span></span>

