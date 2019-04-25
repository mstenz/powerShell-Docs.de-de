---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: WaitForAll-Ressource in DSC
ms.openlocfilehash: 1e891f1aecbdbe641973669f71f22664ad8ea16c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076921"
---
# <a name="dsc-waitforall-resource"></a><span data-ttu-id="238da-103">WaitForAll-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="238da-103">DSC WaitForAll Resource</span></span>

> <span data-ttu-id="238da-104">Gilt für: Windows PowerShell 5.0 und höher</span><span class="sxs-lookup"><span data-stu-id="238da-104">Applies To: Windows PowerShell 5.0 and later</span></span>

<span data-ttu-id="238da-105">Die DSC-Ressource (Desired State Configuration) **WaitForAll** kann innerhalb eines Knotenblocks in einer [DSC-Konfiguration](../../../configurations/configurations.md) verwendet werden, um Abhängigkeiten von Konfigurationen auf anderen Knoten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="238da-105">The **WaitForAll** Desired State Configuration (DSC) resource can be used within a node block in a [DSC configuration](../../../configurations/configurations.md) to specify dependencies on configurations on other nodes.</span></span>

<span data-ttu-id="238da-106">Diese Ressource ist erfolgreich, wenn sich die mit der Eigenschaft **ResourceName** angegebene Ressource auf allen in der Eigenschaft **NodeName** definierten Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="238da-106">This resource succeeds if the resource specified by the **ResourceName** property is in the desired state on all target nodes defined in the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="238da-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="238da-107">Syntax</span></span>

```
WaitForAll [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ]
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="238da-108">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="238da-108">Properties</span></span>

|  <span data-ttu-id="238da-109">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="238da-109">Property</span></span>  |  <span data-ttu-id="238da-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="238da-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="238da-111">Ressourcenname</span><span class="sxs-lookup"><span data-stu-id="238da-111">ResourceName</span></span>| <span data-ttu-id="238da-112">Der Ressourcenname für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="238da-112">The resource name to depend on.</span></span> <span data-ttu-id="238da-113">Wenn diese Ressource zu einer anderen Konfiguration gehört, müssen Sie den Namen als „[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]“ formatieren.</span><span class="sxs-lookup"><span data-stu-id="238da-113">If this resource belongs to a different configuration, format the name as "[__ResourceType__]__ResourceName__::[__ConfigurationName__]::[__ConfigurationName__]"</span></span>|
| <span data-ttu-id="238da-114">NodeName</span><span class="sxs-lookup"><span data-stu-id="238da-114">NodeName</span></span>| <span data-ttu-id="238da-115">Die Zielknoten der Ressource für die Abhängigkeit.</span><span class="sxs-lookup"><span data-stu-id="238da-115">The target nodes of the resource to depend on.</span></span>|
| <span data-ttu-id="238da-116">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="238da-116">RetryIntervalSec</span></span>| <span data-ttu-id="238da-117">Die Anzahl von Sekunden bis zu einem Neuversuch.</span><span class="sxs-lookup"><span data-stu-id="238da-117">The number of seconds before retrying.</span></span> <span data-ttu-id="238da-118">Der Mindestwert lautet 1.</span><span class="sxs-lookup"><span data-stu-id="238da-118">Minimum is 1.</span></span>|
| <span data-ttu-id="238da-119">RetryCount</span><span class="sxs-lookup"><span data-stu-id="238da-119">RetryCount</span></span>| <span data-ttu-id="238da-120">Die maximal zulässige Anzahl von Neuversuchen.</span><span class="sxs-lookup"><span data-stu-id="238da-120">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="238da-121">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="238da-121">ThrottleLimit</span></span>| <span data-ttu-id="238da-122">Die Anzahl von Computern, die gleichzeitig eine Verbindung herstellen können.</span><span class="sxs-lookup"><span data-stu-id="238da-122">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="238da-123">Per Voreinstellung wird der new-cimsession-Standardwert verwendet.</span><span class="sxs-lookup"><span data-stu-id="238da-123">Default is new-cimsession default.</span></span>|
| <span data-ttu-id="238da-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="238da-124">DependsOn</span></span> | <span data-ttu-id="238da-125">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="238da-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="238da-126">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="238da-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="238da-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="238da-127">Example</span></span>

<span data-ttu-id="238da-128">Ein Beispiel zur Verwendung dieser Ressource finden Sie unter [Angeben knotenübergreifender Abhängigkeiten](../../../configurations/crossNodeDependencies.md).</span><span class="sxs-lookup"><span data-stu-id="238da-128">For an example of how to use this resource, see [Specifying cross-node dependencies](../../../configurations/crossNodeDependencies.md)</span></span>
