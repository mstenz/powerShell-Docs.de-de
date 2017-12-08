---
title: Fehler bei Cmdlets des Netzwerkswitch-Managers
contributor: vaibch
ms.openlocfilehash: 8495d79aec54d93f94e745e2efccb5116ad5d944
ms.sourcegitcommit: a3966253a165d193a42b43b9430a4dc76988f82f
ms.translationtype: HT
ms.contentlocale: de-DE
---
<span data-ttu-id="24c2c-102">Die Cmdlets des Netzwerkswitch-Managers können zum Verwalten von Netzwerkswitches über WSMAN verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="24c2c-102">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="24c2c-103">Einige Cmdlets dieses Moduls können Werte aus Pipelines akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="24c2c-103">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="24c2c-104">In WMF 5.1 Preview werden Cmdlets, die Werte aus Pipelines akzeptieren, nicht ausgeführt, wenn die Werte nicht über Pipelines übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="24c2c-104">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="24c2c-105">Wenn der Parameter „InputObject“ nicht verwendet wird, sollte das Cmdlet weiterhin ohne Fehler ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="24c2c-105">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="24c2c-106">Nachfolgend finden Sie eine Liste der betroffenen Cmdlets, also der Cmdlets, die Werte für den Parameter „InputObject“ aus einer Pipeline akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="24c2c-106">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="24c2c-107">Wenn dieser Wert nicht über eine Pipeline übergeben wird, wird die Ausführung der Cmdlets mit einem Fehler beendet.</span><span class="sxs-lookup"><span data-stu-id="24c2c-107">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="24c2c-108">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="24c2c-108">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="24c2c-109">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="24c2c-109">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="24c2c-110">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="24c2c-110">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="24c2c-111">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="24c2c-111">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="24c2c-112">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="24c2c-112">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="24c2c-113">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="24c2c-113">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="24c2c-114">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="24c2c-114">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="24c2c-115">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="24c2c-115">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="24c2c-116">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="24c2c-116">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="24c2c-117">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="24c2c-117">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="24c2c-118">Lösung</span><span class="sxs-lookup"><span data-stu-id="24c2c-118">Resolution</span></span>
<span data-ttu-id="24c2c-119">Die Cmdlets werden ordnungsgemäß ausgeführt, wenn der Wert des Parameters „InputObject“ über eine Pipeline übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="24c2c-119">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="24c2c-120">Nachfolgend finden Sie Beispiele für die oben stehenden Cmdlets:</span><span class="sxs-lookup"><span data-stu-id="24c2c-120">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="24c2c-121">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="24c2c-121">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="24c2c-122">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="24c2c-122">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="24c2c-123">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="24c2c-123">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="24c2c-124">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="24c2c-124">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="24c2c-125">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="24c2c-125">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="24c2c-126">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="24c2c-126">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="24c2c-127">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="24c2c-127">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="24c2c-128">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="24c2c-128">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
