---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
contributor: vaibch
title: Fehler bei Cmdlets des Netzwerkswitch-Managers
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893153"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="01e20-103">Fehler bei Cmdlets des Netzwerkswitch-Managers</span><span class="sxs-lookup"><span data-stu-id="01e20-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="01e20-104">Die Cmdlets des Netzwerkswitch-Managers können zum Verwalten von Netzwerkswitches über WSMAN verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="01e20-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="01e20-105">Einige Cmdlets dieses Moduls können Werte aus Pipelines akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="01e20-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="01e20-106">In WMF 5.1 Preview werden Cmdlets, die Werte aus Pipelines akzeptieren, nicht ausgeführt, wenn die Werte nicht über Pipelines übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="01e20-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="01e20-107">Wenn der Parameter „InputObject“ nicht verwendet wird, sollte das Cmdlet weiterhin ohne Fehler ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="01e20-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="01e20-108">Nachfolgend finden Sie eine Liste der betroffenen Cmdlets, also der Cmdlets, die Werte für den Parameter „InputObject“ aus einer Pipeline akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="01e20-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="01e20-109">Wenn dieser Wert nicht über eine Pipeline übergeben wird, wird die Ausführung der Cmdlets mit einem Fehler beendet.</span><span class="sxs-lookup"><span data-stu-id="01e20-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="01e20-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="01e20-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="01e20-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="01e20-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="01e20-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="01e20-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="01e20-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="01e20-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="01e20-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="01e20-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="01e20-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="01e20-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="01e20-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="01e20-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="01e20-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="01e20-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="01e20-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="01e20-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="01e20-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="01e20-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="01e20-120">Lösung</span><span class="sxs-lookup"><span data-stu-id="01e20-120">Resolution</span></span>

<span data-ttu-id="01e20-121">Die Cmdlets werden ordnungsgemäß ausgeführt, wenn der Wert des Parameters „InputObject“ über eine Pipeline übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="01e20-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="01e20-122">Nachfolgend finden Sie Beispiele für die oben stehenden Cmdlets:</span><span class="sxs-lookup"><span data-stu-id="01e20-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```