---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: vaibch
title: Fehler bei Cmdlets des Netzwerkswitch-Managers
ms.openlocfilehash: 626809513e7a8f1aa2c47a48c74e69ca4077f598
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
<span data-ttu-id="5f2ef-103">Die Cmdlets des Netzwerkswitch-Managers können zum Verwalten von Netzwerkswitches über WSMAN verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5f2ef-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="5f2ef-104">Einige Cmdlets dieses Moduls können Werte aus Pipelines akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="5f2ef-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="5f2ef-105">In WMF 5.1 Preview werden Cmdlets, die Werte aus Pipelines akzeptieren, nicht ausgeführt, wenn die Werte nicht über Pipelines übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="5f2ef-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="5f2ef-106">Wenn der Parameter „InputObject“ nicht verwendet wird, sollte das Cmdlet weiterhin ohne Fehler ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5f2ef-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="5f2ef-107">Nachfolgend finden Sie eine Liste der betroffenen Cmdlets, also der Cmdlets, die Werte für den Parameter „InputObject“ aus einer Pipeline akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="5f2ef-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="5f2ef-108">Wenn dieser Wert nicht über eine Pipeline übergeben wird, wird die Ausführung der Cmdlets mit einem Fehler beendet.</span><span class="sxs-lookup"><span data-stu-id="5f2ef-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="5f2ef-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5f2ef-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="5f2ef-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5f2ef-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="5f2ef-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5f2ef-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="5f2ef-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5f2ef-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="5f2ef-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="5f2ef-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="5f2ef-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="5f2ef-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="5f2ef-115">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5f2ef-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="5f2ef-116">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5f2ef-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="5f2ef-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="5f2ef-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="5f2ef-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="5f2ef-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="5f2ef-119">Lösung</span><span class="sxs-lookup"><span data-stu-id="5f2ef-119">Resolution</span></span>
<span data-ttu-id="5f2ef-120">Die Cmdlets werden ordnungsgemäß ausgeführt, wenn der Wert des Parameters „InputObject“ über eine Pipeline übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="5f2ef-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="5f2ef-121">Nachfolgend finden Sie Beispiele für die oben stehenden Cmdlets:</span><span class="sxs-lookup"><span data-stu-id="5f2ef-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="5f2ef-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5f2ef-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="5f2ef-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="5f2ef-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="5f2ef-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5f2ef-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="5f2ef-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="5f2ef-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="5f2ef-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="5f2ef-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="5f2ef-127">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5f2ef-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="5f2ef-128">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="5f2ef-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="5f2ef-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="5f2ef-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```