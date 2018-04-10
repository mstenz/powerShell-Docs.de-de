---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxService“
ms.openlocfilehash: b02fb1153570f628682533cb57a7d429e5cc8762
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="f350e-103">DSC für Linux-Resource „nxService“</span><span class="sxs-lookup"><span data-stu-id="f350e-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="f350e-104">Die Ressource **nxService** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Diensten auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="f350e-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f350e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f350e-105">Syntax</span></span>

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="f350e-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="f350e-106">Properties</span></span>
|  <span data-ttu-id="f350e-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f350e-107">Property</span></span> |  <span data-ttu-id="f350e-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f350e-108">Description</span></span> |
|---|---|
| <span data-ttu-id="f350e-109">Name</span><span class="sxs-lookup"><span data-stu-id="f350e-109">Name</span></span>| <span data-ttu-id="f350e-110">Der Name des Diensts/Daemons, der konfiguriert werden soll.</span><span class="sxs-lookup"><span data-stu-id="f350e-110">The name of the service/daemon to configure.</span></span>|
| <span data-ttu-id="f350e-111">Controller</span><span class="sxs-lookup"><span data-stu-id="f350e-111">Controller</span></span>| <span data-ttu-id="f350e-112">Der Typ des Dienstcontrollers, der beim Konfigurieren des Diensts verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="f350e-112">The type of service controller to use when configuring the service.</span></span>|
| <span data-ttu-id="f350e-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="f350e-113">Enabled</span></span>| <span data-ttu-id="f350e-114">Gibt an, ob der Dienst beim Systemstart gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="f350e-114">Indicates whether the service starts on boot.</span></span>|
| <span data-ttu-id="f350e-115">State</span><span class="sxs-lookup"><span data-stu-id="f350e-115">State</span></span>| <span data-ttu-id="f350e-116">Überprüfen, ob der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f350e-116">Indicates whether the service is running.</span></span> <span data-ttu-id="f350e-117">Legen Sie diese Eigenschaft auf „Stopped“ fest, um sicherzustellen, dass der Dienst nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f350e-117">Set this property to "Stopped" to ensure that the service is not running.</span></span> <span data-ttu-id="f350e-118">Durch Festlegen auf „Running“ wird sichergestellt, dass der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f350e-118">Set it to "Running" to ensure that the service is not running.</span></span>|
| <span data-ttu-id="f350e-119">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f350e-119">DependsOn</span></span> | <span data-ttu-id="f350e-120">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="f350e-120">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f350e-121">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f350e-121">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|


## <a name="additional-information"></a><span data-ttu-id="f350e-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f350e-122">Additional Information</span></span>

<span data-ttu-id="f350e-123">Die Ressource **nxService** erstellt keine Dienstdefinition bzw. kein Skript für den Dienst, falls er nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="f350e-123">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="f350e-124">Sie können die PowerShell DSC-Ressource **nxFile** verwenden, um das Vorhandensein oder den Inhalt der Dienstdefinitionsdatei oder des Skripts zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="f350e-124">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="f350e-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f350e-125">Example</span></span>

<span data-ttu-id="f350e-126">Das folgende Beispiel zeigt die Konfiguration des Diensts „httpd“ (für Apache HTTP Server), der mit dem Dienstcontroller **SystemD** registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="f350e-126">The following example shows configuration of the “httpd” service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```
Import-DSCResource -Module nx

Node $node {
#Apache Service
nxService ApacheService
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```