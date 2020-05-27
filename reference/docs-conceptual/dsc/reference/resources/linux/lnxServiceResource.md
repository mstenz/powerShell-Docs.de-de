---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für Linux-Resource „nxService“
ms.openlocfilehash: 30f3b15fccd1491fac2989832486ad15d062c1ad
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563984"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="ca955-103">DSC für Linux-Resource „nxService“</span><span class="sxs-lookup"><span data-stu-id="ca955-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="ca955-104">Die Ressource **nxService** in PowerShell DSC bietet einen Mechanismus zum Verwalten von Diensten auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="ca955-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca955-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca955-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="ca955-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ca955-106">Properties</span></span>

|<span data-ttu-id="ca955-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ca955-107">Property</span></span> |<span data-ttu-id="ca955-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="ca955-108">Description</span></span> |
|---|---|
|<span data-ttu-id="ca955-109">Name</span><span class="sxs-lookup"><span data-stu-id="ca955-109">Name</span></span> |<span data-ttu-id="ca955-110">Der Name des Diensts/Daemons, der konfiguriert werden soll.</span><span class="sxs-lookup"><span data-stu-id="ca955-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="ca955-111">Controller</span><span class="sxs-lookup"><span data-stu-id="ca955-111">Controller</span></span> |<span data-ttu-id="ca955-112">Der Typ des Dienstcontrollers, der beim Konfigurieren des Diensts verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ca955-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="ca955-113">Enabled</span><span class="sxs-lookup"><span data-stu-id="ca955-113">Enabled</span></span> |<span data-ttu-id="ca955-114">Gibt an, ob der Dienst beim Systemstart gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="ca955-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="ca955-115">State</span><span class="sxs-lookup"><span data-stu-id="ca955-115">State</span></span> |<span data-ttu-id="ca955-116">Überprüfen, ob der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ca955-116">Indicates whether the service is running.</span></span> <span data-ttu-id="ca955-117">Legen Sie diese Eigenschaft auf **Stopped** fest, um sicherzustellen, dass der Dienst nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ca955-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="ca955-118">Durch Festlegen auf **Running** wird sichergestellt, dass der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ca955-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ca955-119">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ca955-119">Common properties</span></span>

|<span data-ttu-id="ca955-120">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ca955-120">Property</span></span> |<span data-ttu-id="ca955-121">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="ca955-121">Description</span></span> |
|---|---|
|<span data-ttu-id="ca955-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ca955-122">DependsOn</span></span> |<span data-ttu-id="ca955-123">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="ca955-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ca955-124">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ca955-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="ca955-125">Zusätzliche Informationen</span><span class="sxs-lookup"><span data-stu-id="ca955-125">Additional Information</span></span>

<span data-ttu-id="ca955-126">Die Ressource **nxService** erstellt keine Dienstdefinition bzw. kein Skript für den Dienst, falls er nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ca955-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="ca955-127">Sie können die PowerShell DSC-Ressource **nxFile** verwenden, um das Vorhandensein oder den Inhalt der Dienstdefinitionsdatei oder des Skripts zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="ca955-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="ca955-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ca955-128">Example</span></span>

<span data-ttu-id="ca955-129">Das folgende Beispiel zeigt die Konfiguration des Diensts „httpd“ (für Apache HTTP Server), der mit dem Dienstcontroller **SystemD** registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="ca955-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
