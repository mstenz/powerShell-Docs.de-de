---
title: Fehler bei Cmdlets des Netzwerkswitch-Managers
contributor: vaibch
ms.openlocfilehash: e32e31762b665a7e2c6f6938fe494cb6127d4264
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
Die Cmdlets des Netzwerkswitch-Managers können zum Verwalten von Netzwerkswitches über WSMAN verwendet werden. Einige Cmdlets dieses Moduls können Werte aus Pipelines akzeptieren. In WMF 5.1 Preview werden Cmdlets, die Werte aus Pipelines akzeptieren, nicht ausgeführt, wenn die Werte nicht über Pipelines übergeben werden.

Wenn der Parameter „InputObject“ nicht verwendet wird, sollte das Cmdlet weiterhin ohne Fehler ausgeführt werden.

Nachfolgend finden Sie eine Liste der betroffenen Cmdlets, also der Cmdlets, die Werte für den Parameter „InputObject“ aus einer Pipeline akzeptieren. Wenn dieser Wert nicht über eine Pipeline übergeben wird, wird die Ausführung der Cmdlets mit einem Fehler beendet.

- Disable-NetworkSwitchEthernetPort
- Enable-NetworkSwitchEthernetPort
- Remove-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchPortMode
- Set-NetworkSwitchPortProperty
- Disable-NetworkSwitchFeature
- Enable-NetworkSwitchFeature
- Remove-NetworkSwitchVlan
- Set-NetworkSwitchVlanProperty

### <a name="resolution"></a>Lösung
Die Cmdlets werden ordnungsgemäß ausgeführt, wenn der Wert des Parameters „InputObject“ über eine Pipeline übergeben wird. Nachfolgend finden Sie Beispiele für die oben stehenden Cmdlets:

- Disable-NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```
- Enable-NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Remove-NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- Set-NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- Set-NetworkSwitchPortProperty
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- Disable-NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- Enable-NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- Set-NetworkSwitchVlanProperty
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
