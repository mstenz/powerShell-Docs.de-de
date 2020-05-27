---
title: Kompatibilität von PowerShell 7-Modulen
ms.date: 02/03/2020
ms.openlocfilehash: 273e25e3b7cd48e09b63e50c34ed0b98a4e766f0
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565062"
---
# <a name="powershell-7-module-compatibility"></a>Kompatibilität von PowerShell 7-Modulen

Dieser Artikel enthält eine Liste mit von Microsoft veröffentlichten PowerShell-Modulen. Diese Module ermöglichen die Verwaltung und Unterstützung verschiedener Microsoft-Produkte und -Dienste. Diese Module wurden so aktualisiert, dass sie nativ mit PowerShell 7 funktionieren, oder auf Kompatibilität mit PowerShell 7 getestet. Diese Liste wird mit neuen Informationen aktualisiert, sobald weitere Module ermittelt und getestet wurden.

Wenn Sie Informationen zu bestimmten Modulen teilen möchten oder Probleme mit bestimmten Modulen haben, melden Sie im [Repository WindowsCompatibility](https://github.com/PowerShell/WindowsCompatibility) ein Issue.

## <a name="windows-management-modules"></a>Windows-Verwaltungsmodule

Das Windows-Verwaltungsmodul wird je nach Edition von Windows und der Art und Weise, wie das Modul für diese Edition gepackt wurde, auf unterschiedliche Weise installiert.

Verwenden Sie unter Windows Server als Administrator das Cmdlet [Install-WindowsFeature](/powershell/module/servermanager/install-windowsfeature) mit dem Featurenamen. Beispiel:

```powershell
Install-WindowsFeature -Name ActiveDirectory
```

Unter Windows 10 werden die Windows-Verwaltungsmodule als **Optionale Windows-Features** oder **Windows-Funktionen** zur Verfügung gestellt. Die folgenden Befehle müssen in einer Sitzung mit erhöhten Rechten unter Verwendung von **Als Administrator ausführen** ausgeführt werden.

- Für optionale Windows-Features

  Um eine Liste optionaler Features zu erhalten, führen Sie den folgenden Befehl aus:

  ```powershell
  Get-WindowsOptionalFeature -Online
  ```

  So installieren Sie das Feature

  ```powershell
  Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-Management-PowerShell
  ```

  Weitere Informationen finden Sie unter:

  - [Get-WindowsOptionalFeature](/powershell/module/dism/get-windowsoptionalfeature)
  - [Enable-WindowsOptionalFeature](/powershell/module/dism/enable-windowsoptionalfeature)

- Für Windows-Funktionen

  Um eine Liste der Windows-Funktionen zu erhalten, führen Sie den folgenden Befehl aus:

  ```powershell
  Get-WindowsCapability -online
  ```

  Beachten Sie, dass der Name des Funktionspakets mit `~~~~0.0.1.0` endet. Sie müssen den vollständigen Namen verwenden, um die Funktion zu installieren:

  ```powershell
  Add-WindowsCapability -Online -Name Rsat.ServerManager.Tools~~~~0.0.1.0
  ```

  Weitere Informationen finden Sie unter:

  - [Get-WindowsCapability](/powershell/module/dism/get-windowscapability)
  - [Add-WindowsCapability](/powershell/module/dism/add-windowscapability)

### <a name="module-list"></a>Modulliste

| Modulname                        | Status                               | Unterstütztes Betriebssystem                       |
| ---------------------------------- | ------------------------------------ | ---------------------------------- |
| ActiveDirectory                    | Nativ kompatibel                  | Windows Server 1809 und höher mit RSAT-AD-PowerShell<br>Windows 10 1809 und höher mit Rsat.ActiveDirectory.DS-LDS.Tools |
| ADFS                               | Nicht mit Kompatibilitätsebene getestet    |                                    |
| AppBackgroundTask                  | Nativ kompatibel                  | Windows 10 1903 und höher                   |
| AppLocker                          | Nicht mit Kompatibilitätsebene getestet    |                                    |
| AppvClient                         | Nicht mit Kompatibilitätsebene getestet    |                                    |
| Appx                               | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher |
| AssignedAccess                     | Nativ kompatibel                  | Windows 10 1809 und höher                   |
| BestPractices                      | Nicht mit Kompatibilitätsebene getestet    |                                    |
| BitLocker                          | Nativ kompatibel                  | Windows Server 1809 und höher mit BitLocker<br>Windows 10 1809 und höher |
| BitsTransfer                       | Nativ kompatibel                  | Windows Server 20H1<br>Windows 10 20H1 |
| BootEventCollector                 | Nicht mit Kompatibilitätsebene getestet    |                                        |
| BranchCache                        | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher |
| CimCmdlets                         | Nativ kompatibel                  | In PowerShell 7 integriert |
| ClusterAwareUpdating               | Nicht mit Kompatibilitätsebene getestet    |                         |
| ConfigCI                           | Nicht mit Kompatibilitätsebene getestet    |                         |
| Defender                           | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher  |
| DeliveryOptimization               | Nativ kompatibel                  | Windows Server 1903 und höher<br>Windows 10 1903 und höher  |
| DFSN                               | Nativ kompatibel                  | Windows Server 1809 und höher mit FS-DFS-Namespace<br>Windows 10 1809 und höher mit Rsat.FailoverCluster.Management.Tools |
| DFSR                               | Nicht mit Kompatibilitätsebene getestet    |                                   |
| DhcpServer                         | Nicht mit Kompatibilitätsebene getestet    |                                   |
| DirectAccessClientComponents       | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher  |
| Dism                               | Nativ kompatibel                  | Windows Server 1903 und höher<br>Windows 10 1903 und höher  |
| DnsClient                          | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher  |
| DnsServer                          | Nativ kompatibel                  | Windows Server 1809 und höher mit DNS- oder RSAT-DNS-Server<br>Windows 10 1809 und höher mit Rsat.Dns.Tools |
| EventTracingManagement             | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher  |
| FailoverClusters                   | Nicht mit Kompatibilitätsebene getestet    |                                  |
| FailoverClusterSet                 | Nicht mit Kompatibilitätsebene getestet    |                                  |
| FileServerResourceManager          | Nativ kompatibel                  | Windows Server 1809 und höher mit FS-Resource-Manager |
| GroupPolicy                        | Nicht mit Kompatibilitätsebene getestet    |                                               |
| HgsClient                          | Nativ kompatibel                  | Windows Server 1903 und höher mit Hyper-V oder RSAT-Shielded-VM-Tools<br>Windows 10 1903 und höher mit Rsat.Shielded.VM.Tools |
| HgsDiagnostics                     | Nativ kompatibel                  | Windows Server 1809 und höher mit Hyper-V oder RSAT-Shielded-VM-Tools<br>Windows 10 1809 und höher mit Rsat.Shielded.VM.Tools |
| Hyper-V                            | Nativ kompatibel                  | Windows Server 1809 und höher mit Hyper-V-PowerShell<br>Windows 10 1809 und höher mit Microsoft-Hyper-V-Management-PowerShell |
| IISAdministration                  | Nicht mit Kompatibilitätsebene getestet    |                                               |
| International                      | Nativ kompatibel                  | Windows Server 1903 und höher<br>Windows 10 1903 und höher      |
| IpamServer                         | Nicht mit Kompatibilitätsebene getestet    |                                               |
| iSCSI                              | Nicht mit Kompatibilitätsebene getestet    |                                               |
| IscsiTarget                        | Nicht mit Kompatibilitätsebene getestet    |                                               |
| ISE                                | Nicht mit Kompatibilitätsebene getestet    |                                               |
| Kds                                | Nativ kompatibel                  | Windows Server 20H1<br>Windows 10 20H1        |
| Microsoft.PowerShell.Archive       | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| Microsoft.PowerShell.Diagnostics   | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| Microsoft.PowerShell.Host          | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| Microsoft.PowerShell.LocalAccounts | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| Microsoft.PowerShell.Management    | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| Microsoft.PowerShell.ODataUtils    | Nicht mit Kompatibilitätsebene getestet    |                                               |
| Microsoft.PowerShell.Security      | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| Microsoft.PowerShell.Utility       | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| Microsoft.WSMan.Management         | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| MMAgent                            | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| MPIO                               | Nativ kompatibel                  | Windows Server 1809 und höher mit Multipath-IO        |
| MsDtc                              | Nicht mit Kompatibilitätsebene getestet    |                                               |
| NetAdapter                         | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetConnection                      | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetEventPacketCapture              | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetLbfo                            | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetLldpAgent                       | Nicht mit Kompatibilitätsebene getestet    |                                               |
| NetNat                             | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetQos                             | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetSecurity                        | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetSwitchTeam                      | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetTCPIP                           | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetWNV                             | Nicht mit Kompatibilitätsebene getestet    |                                               |
| NetworkConnectivityStatus          | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetworkController                  | Nicht mit Kompatibilitätsebene getestet    |                                               |
| NetworkControllerDiagnostics       | Nicht mit Kompatibilitätsebene getestet    |                                               |
| NetworkLoadBalancingClusters       | Nicht mit Kompatibilitätsebene getestet    |                                               |
| NetworkSwitchManager               | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NetworkTransition                  | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| NFS                                | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher mit Rsat.ServerManager.Tools |
| PackageManagement                  | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| PcsvDevice                         | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| PersistentMemory                   | Nicht mit Kompatibilitätsebene getestet    |                                               |
| PKI                                | Nicht mit Kompatibilitätsebene getestet    |                                               |
| PnpDevice                          | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| PowerShellGet                      | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| PrintManagement                    | Nativ kompatibel                  | Windows Server 1903 und höher mit Print-Services<br>Windows 10 1903 und höher  |
| ProcessMitigations                 | Nativ kompatibel                  | Windows Server 1903 und höher<br>Windows 10 1903 und höher      |
| Bereitstellung                       | Nicht mit Kompatibilitätsebene getestet    |                                               |
| PSDesiredStateConfiguration        | Teilweise                            | In PowerShell 7 integriert                       |
| PSDiagnostics                      | Nativ kompatibel                  | In PowerShell 7 integriert                       |
| PSScheduledJob                     | Funktioniert nicht mit Kompatibilitätsebene | In PowerShell 5.1 integriert                     |
| PSWorkflow                         | Nicht mit Kompatibilitätsebene getestet    |                                               |
| PSWorkflowUtility                  | Nicht mit Kompatibilitätsebene getestet    |                                               |
| RemoteAccess                       | Nicht mit Kompatibilitätsebene getestet    |                                               |
| RemoteDesktop                      | Nicht mit Kompatibilitätsebene getestet    |                                               |
| ScheduledTasks                     | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| SecureBoot                         | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| ServerCore                         | Nicht mit Kompatibilitätsebene getestet    |                                               |
| ServerManager                      | Nicht mit Kompatibilitätsebene getestet    |                                               |
| ServerManagerTasks                 | Nicht mit Kompatibilitätsebene getestet    |                                               |
| ShieldedVMDataFile                 | Nativ kompatibel                  | Windows Server 1903 und höher mit RSAT-Shielded-VM-Tools<br>Windows 10 1903 und höher mit Rsat.Shielded.VM.Tools |
| ShieldedVMProvisioning             | Nativ kompatibel                  | Windows Server 1809 und höher mit HostGuardian<br>Windows 10 1809 und höher mit HostGuardian  |
| ShieldedVMTemplate                 | Nativ kompatibel                  | Windows Server 1809 und höher mit RSAT-Shielded-VM-Tools<br>Windows 10 1809 und höher mit Rsat.Shielded.VM.Tools |
| SmbShare                           | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| SmbWitness                         | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| SMISConfig                         | Nativ kompatibel                  | Windows Server 1903 und höher mit WindowsStorageManagementService |
| sms                                | Nicht mit Kompatibilitätsebene getestet    |                                               |
| SoftwareInventoryLogging           | Nativ kompatibel                  | Windows Server 1809 und höher                          |
| StartLayout                        | Nativ kompatibel                  | Windows Server 1809 und höher mit Desktopoberfläche<br>Windows 10 1809 und höher |
| Storage                            | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| StorageBusCache                    | Nicht mit Kompatibilitätsebene getestet    |                                               |
| StorageMigrationService            | Nicht mit Kompatibilitätsebene getestet    |                                               |
| StorageQOS                         | Nativ kompatibel                  | Windows Server 1809 und höher mit RSAT-Clustering-PowerShell<br>Windows 10 1809 und höher mit Rsat.FailoverCluster.Management.Tools |
| StorageReplica                     | Nicht mit Kompatibilitätsebene getestet    |                                               |
| SyncShare                          | Nativ kompatibel                  | Windows Server 1809 und höher mit FS-SyncShareService |
| SystemInsights                     | Nicht mit Kompatibilitätsebene getestet    |                                               |
| TLS                                | Nicht mit Kompatibilitätsebene getestet    |                                               |
| TroubleshootingPack                | Nativ kompatibel                  | Windows 10 1903 und höher                              |
| TrustedPlatformModule              | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| UEV                                | Nativ kompatibel                  | Windows Server ??Künftige Version von Server mit Desktopoberfläche??<br>Windows 10 1903 und höher |
| UpdateServices                     | Funktioniert nicht mit Kompatibilitätsebene |                                               |
| VpnClient                          | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| Wdac                               | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| WebAdministration                  | Nicht mit Kompatibilitätsebene getestet    |                                               |
| WHEA                               | Nativ kompatibel                  | Windows Server 1903 und höher<br>Windows 10 1903 und höher      |
| WindowsDeveloperLicense            | Nativ kompatibel                  | Windows Server 1809 und höher mit Desktopoberfläche<br>Windows 10 1809 und höher |
| WindowsErrorReporting              | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher      |
| WindowsSearch                      | Nativ kompatibel                  | Windows 10 1903 und höher                              |
| WindowsServerBackup                | Nativ kompatibel                  | Windows Server 19H2 mit Windows-Server-Backup |
| WindowsUpdate                      | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher       |
| WindowsUpdate              | Nativ kompatibel                  | Windows Server 1809 und höher<br>Windows 10 1809 und höher       |
