---
ms.date: 02/03/2020
keywords: powershell,core
title: Releaseverlauf von Modulen und Cmdlets
ms.openlocfilehash: e0fe9b263bdd0a5e1bedd0762b7613a4bbe02a58
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706127"
---
# <a name="release-history-of-modules-and-cmdlets"></a>Releaseverlauf von Modulen und Cmdlets

In diesem Artikel werden die Module und Cmdlets aufgelistet, die mit verschiedenen Versionen von PowerShell ausgeliefert werden. Dies ist eine Zusammenfassung der Informationen, die in den Versionshinweisen enthalten sind. Ausführliche Informationen finden Sie in den Versionshinweisen:

- [Neuigkeiten in PowerShell Core 6.2](what-s-new-in-powershell-core-62.md)
- [Neuigkeiten in PowerShell Core 6.1](what-s-new-in-powershell-core-61.md)
- [Neuigkeiten in PowerShell Core 6.0](what-s-new-in-powershell-core-60.md)
- [Wichtige Änderungen in PowerShell Core 6.0](breaking-changes-ps6.md)
- [Bekannte Probleme in PowerShell Core 6.0](known-issues-ps6.md)

Dies ist in Bearbeitung. Helfen Sie uns dabei, diese Informationen auf dem neuesten Stand zu halten.

## <a name="module-release-history"></a>Modulreleaseverlauf

|         Modulname/PS-Version          |   5,1   |   6.x   |   7.0   |   7.1   |     Hinweis     |
| ----------------------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| CimCmdlets                                | &check; | &check; | &check; | &check; | Nur Windows |
| ISE (eingeführt in 2.0)                   | &check; |         |         |         | Nur Windows |
| Microsoft.PowerShell.Archive              | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Core                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Diagnostics          | &check; | &check; | &check; | &check; | Nur Windows |
| Microsoft.PowerShell.Host                 | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.LocalAccounts        | &check; |         |         |         | Nur Windows |
| Microsoft.PowerShell.Management           | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.ODataUtils           | &check; |         |         |         | Nur Windows |
| Microsoft.PowerShell.Operation.Validation | &check; |         |         |         | Nur Windows |
| Microsoft.PowerShell.Security             | &check; | &check; | &check; | &check; |              |
| Microsoft.PowerShell.Utility              | &check; | &check; | &check; | &check; |              |
| Microsoft.WSMan.Management                | &check; | &check; | &check; | &check; | Nur Windows |
| PackageManagement                         | &check; | &check; | &check; | &check; |              |
| PowershellGet                             | &check; | &check; | &check; | &check; |              |
| PSDesiredStateConfiguration               | &check; | &check; | &check; | &check; |              |
| PSDiagnostics                             | &check; | &check; | &check; | &check; | Nur Windows |
| PSReadline 1.x                            | &check; |         |         |         | Nur Windows |
| PSReadline 2.x                            |         | &check; | &check; | &check; |              |
| PSScheduledJob                            | &check; |         |         |         | Nur Windows |
| PSWorkflow                                | &check; |         |         |         | Nur Windows |
| PSWorkflowUtility                         | &check; |         |         |         | Nur Windows |
| ThreadJob                                 |         | &check; | &check; | &check; | Installation in PowerShell 5.1 möglich |

## <a name="cmdlet-release-history"></a>Cmdlet-Releaseverlauf

### <a name="cimcmdlets"></a>CimCmdlets

|         Cmdlet-Name         |   5,1   |   6.x   |   7.0   |   7.1   |     Hinweis     |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-BinaryMiLog          | &check; | &check; | &check; | &check; | Nur Windows |
| Get-CimAssociatedInstance   | &check; | &check; | &check; | &check; | Nur Windows |
| Get-CimClass                | &check; | &check; | &check; | &check; | Nur Windows |
| Get-CimInstance             | &check; | &check; | &check; | &check; | Nur Windows |
| Get-CimSession              | &check; | &check; | &check; | &check; | Nur Windows |
| Import-BinaryMiLog          | &check; | &check; | &check; | &check; | Nur Windows |
| Invoke-CimMethod            | &check; | &check; | &check; | &check; | Nur Windows |
| New-CimInstance             | &check; | &check; | &check; | &check; | Nur Windows |
| New-CimSession              | &check; | &check; | &check; | &check; | Nur Windows |
| New-CimSessionOption        | &check; | &check; | &check; | &check; | Nur Windows |
| Register-CimIndicationEvent | &check; | &check; | &check; | &check; | Nur Windows |
| Remove-CimInstance          | &check; | &check; | &check; | &check; | Nur Windows |
| Remove-CimSession           | &check; | &check; | &check; | &check; | Nur Windows |
| Set-CimInstance             | &check; | &check; | &check; | &check; | Nur Windows |

### <a name="ise-introduced-in-20"></a>ISE (eingeführt in 2.0)

|    Cmdlet-Name    |   5,1   | 6.x  |  7.0  |  7.1  |     Hinweis     |
| ----------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-IseSnippet    | &check; |      |       |       | Nur Windows |
| Import-IseSnippet | &check; |      |       |       | Nur Windows |
| New-IseSnippet    | &check; |      |       |       | Nur Windows |


### <a name="microsoftpowershellarchive"></a>Microsoft.PowerShell.Archive

|   Cmdlet-Name    |   5,1   |   6.x   |   7.0   |   7.1   | Hinweis |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Compress-Archive | &check; | &check; | &check; | &check; |      |
| Expand-Archive   | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershellcore"></a>Microsoft.PowerShell.Core

|            Cmdlet-Name            |   5,1   |   6.x   |   7.0   |   7.1   |            Hinweis            |
| --------------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------- |
| Add-History                       | &check; | &check; | &check; | &check; |                            |
| Add-PSSnapin                      | &check; |         |         |         | Nur Windows               |
| Clear-History                     | &check; | &check; | &check; | &check; |                            |
| Clear-Host                        | &check; | &check; | &check; | &check; |                            |
| Connect-PSSession                 | &check; | &check; | &check; | &check; | Nur Windows               |
| Debug-Job                         | &check; | &check; | &check; | &check; |                            |
| Disable-ExperimentalFeature       |         |   6.2   | &check; | &check; |                            |
| Disable-PSRemoting                | &check; | &check; | &check; | &check; | Nur Windows               |
| Disable-PSSessionConfiguration    | &check; | &check; | &check; | &check; | Nur Windows               |
| Disconnect-PSSession              | &check; | &check; | &check; | &check; | Nur Windows               |
| Enable-ExperimentalFeature        |         |   6.2   | &check; | &check; |                            |
| Enable-PSRemoting                 | &check; | &check; | &check; | &check; | Nur Windows               |
| Enable-PSSessionConfiguration     | &check; | &check; | &check; | &check; | Nur Windows               |
| Enter-PSHostProcess               | &check; | &check; | &check; | &check; | Linux-Unterstützung in 6.2 hinzugefügt |
| Enter-PSSession                   | &check; | &check; | &check; | &check; |                            |
| Exit-PSHostProcess                | &check; | &check; | &check; | &check; | Linux-Unterstützung in 6.2 hinzugefügt |
| Exit-PSSession                    | &check; | &check; | &check; | &check; |                            |
| Export-Console                    | &check; |         |         |         | Nur Windows               |
| Export-ModuleMember               | &check; | &check; | &check; | &check; |                            |
| ForEach-Object                    | &check; | &check; | &check; | &check; |                            |
| Get-Command                       | &check; | &check; | &check; | &check; |                            |
| Get-ExperimentalFeature           |         |   6.2   | &check; | &check; |                            |
| Get-Help                          | &check; | &check; | &check; | &check; |                            |
| Get-History                       | &check; | &check; | &check; | &check; |                            |
| Get-Job                           | &check; | &check; | &check; | &check; |                            |
| Get-Module                        | &check; | &check; | &check; | &check; |                            |
| Get-PSHostProcessInfo             | &check; | &check; | &check; | &check; | Linux-Unterstützung in 6.2 hinzugefügt |
| Get-PSSession                     | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionCapability           | &check; | &check; | &check; | &check; |                            |
| Get-PSSessionConfiguration        | &check; | &check; | &check; | &check; |                            |
| Get-PSSnapin                      | &check; |         |         |         | Nur Windows               |
| Get-Verb                          | &check; |         |         |         | Verschoben nach Microsoft.PowerShell.Utility 6.0 und höher |
| Import-Module                     | &check; | &check; | &check; | &check; |                            |
| Invoke-Command                    | &check; | &check; | &check; | &check; |                            |
| Invoke-History                    | &check; | &check; | &check; | &check; |                            |
| New-Module                        | &check; | &check; | &check; | &check; |                            |
| New-ModuleManifest                | &check; | &check; | &check; | &check; |                            |
| New-PSRoleCapabilityFile          | &check; | &check; | &check; | &check; |                            |
| New-PSSession                     | &check; | &check; | &check; | &check; |                            |
| New-PSSessionConfigurationFile    | &check; | &check; | &check; | &check; | Nur Windows               |
| New-PSSessionOption               | &check; | &check; | &check; | &check; |                            |
| New-PSTransportOption             | &check; | &check; | &check; | &check; |                            |
| Out-Default                       | &check; | &check; | &check; | &check; |                            |
| Out-Host                          | &check; | &check; | &check; | &check; |                            |
| Out-Null                          | &check; | &check; | &check; | &check; |                            |
| Receive-Job                       | &check; | &check; | &check; | &check; |                            |
| Receive-PSSession                 | &check; | &check; | &check; | &check; | Nur Windows               |
| Register-ArgumentCompleter        | &check; | &check; | &check; | &check; |                            |
| Register-PSSessionConfiguration   | &check; | &check; | &check; | &check; | Nur Windows               |
| Remove-Job                        | &check; | &check; | &check; | &check; |                            |
| Remove-Module                     | &check; | &check; | &check; | &check; |                            |
| Remove-PSSession                  | &check; | &check; | &check; | &check; |                            |
| Remove-PSSnapin                   | &check; |         |         |         | Nur Windows               |
| Resume-Job                        | &check; |         |         |         |                            |
| Save-Help                         | &check; | &check; | &check; | &check; |                            |
| Set-PSDebug                       | &check; | &check; | &check; | &check; |                            |
| Set-PSSessionConfiguration        | &check; | &check; | &check; | &check; | Nur Windows               |
| Set-StrictMode                    | &check; | &check; | &check; | &check; |                            |
| Start-Job                         | &check; | &check; | &check; | &check; |                            |
| Stop-Job                          | &check; | &check; | &check; | &check; |                            |
| Suspend-Job                       | &check; |         |         |         | Nur Windows               |
| Test-ModuleManifest               | &check; | &check; | &check; | &check; |                            |
| Test-PSSessionConfigurationFile   | &check; | &check; | &check; | &check; | Nur Windows               |
| Unregister-PSSessionConfiguration | &check; | &check; | &check; | &check; | Nur Windows               |
| Update-Help                       | &check; | &check; | &check; | &check; |                            |
| Wait-Job                          | &check; | &check; | &check; | &check; |                            |
| Where-Object                      | &check; | &check; | &check; | &check; |                            |

### <a name="microsoftpowershelldiagnostics"></a>Microsoft.PowerShell.Diagnostics

|  Cmdlet-Name   |   5,1   |   6.x   |   7.0   |   7.1   |     Hinweis     |
| -------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Export-Counter | &check; |         |         |         | Nur Windows |
| Get-Counter    | &check; |         | &check; | &check; | Nur Windows |
| Get-WinEvent   | &check; | &check; | &check; | &check; | Nur Windows |
| Import-Counter | &check; |         |         |         | Nur Windows |
| New-WinEvent   | &check; | &check; | &check; | &check; | Nur Windows |

### <a name="microsoftpowershellhost"></a>Microsoft.PowerShell.Host

|   Cmdlet-Name    |   5,1   |   6.x   |   7.0   |   7.1   | Hinweis |
| ---------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Start-Transcript | &check; | &check; | &check; | &check; |      |
| Stop-Transcript  | &check; | &check; | &check; | &check; |      |

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

|       Cmdlet-Name       |   5,1   | 6.x  |  7.0  |  7.1  |     Hinweis     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-LocalGroupMember    | &check; |      |       |       | Nur Windows |
| Disable-LocalUser       | &check; |      |       |       | Nur Windows |
| Enable-LocalUser        | &check; |      |       |       | Nur Windows |
| Get-LocalGroup          | &check; |      |       |       | Nur Windows |
| Get-LocalGroupMember    | &check; |      |       |       | Nur Windows |
| Get-LocalUser           | &check; |      |       |       | Nur Windows |
| New-LocalGroup          | &check; |      |       |       | Nur Windows |
| New-LocalUser           | &check; |      |       |       | Nur Windows |
| Remove-LocalGroup       | &check; |      |       |       | Nur Windows |
| Remove-LocalGroupMember | &check; |      |       |       | Nur Windows |
| Remove-LocalUser        | &check; |      |       |       | Nur Windows |
| Rename-LocalGroup       | &check; |      |       |       | Nur Windows |
| Rename-LocalUser        | &check; |      |       |       | Nur Windows |
| Set-LocalGroup          | &check; |      |       |       | Nur Windows |
| Set-LocalUser           | &check; |      |       |       | Nur Windows |

### <a name="microsoftpowershellmanagement"></a>Microsoft.PowerShell.Management

|          Cmdlet-Name          |   5,1   |   6.x   |   7.0   |   7.1   |               Hinweis               |
| ----------------------------- | :-----: | :-----: | :-----: | :-----: | -------------------------------- |
| Add-Computer                  | &check; |         |         |         | Nur Windows                     |
| Add-Content                   | &check; | &check; | &check; | &check; |                                  |
| Checkpoint-Computer           | &check; |         |         |         | Nur Windows                     |
| Clear-Content                 | &check; | &check; | &check; | &check; |                                  |
| Clear-EventLog                | &check; |         |         |         | Nur Windows                     |
| Clear-Item                    | &check; | &check; | &check; | &check; |                                  |
| Clear-ItemProperty            | &check; | &check; | &check; | &check; |                                  |
| Clear-RecycleBin              | &check; |         | &check; | &check; | Nur Windows                     |
| Complete-Transaction          | &check; |         |         |         | Nur Windows                     |
| Convert-Path                  | &check; | &check; | &check; | &check; |                                  |
| Copy-Item                     | &check; | &check; | &check; | &check; |                                  |
| Copy-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| Debug-Process                 | &check; | &check; | &check; | &check; |                                  |
| Disable-ComputerRestore       | &check; |         |         |         | Nur Windows                     |
| Enable-ComputerRestore        | &check; |         |         |         | Nur Windows                     |
| Get-ChildItem                 | &check; | &check; | &check; | &check; |                                  |
| Get-Clipboard                 | &check; |         | &check; | &check; | Unter macOS nicht unterstützt           |
| Get-ComputerInfo              | &check; | &check; | &check; | &check; |                                  |
| Get-ComputerRestorePoint      | &check; |         |         |         | Nur Windows                     |
| Get-Content                   | &check; | &check; | &check; | &check; |                                  |
| Get-ControlPanelItem          | &check; |         |         |         | Nur Windows                     |
| Get-EventLog                  | &check; |         |         |         | Nur Windows                     |
| Get-HotFix                    | &check; |         | &check; | &check; | Nur Windows                     |
| Get-Item                      | &check; | &check; | &check; | &check; |                                  |
| Get-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Get-ItemPropertyValue         | &check; | &check; | &check; | &check; |                                  |
| Get-Location                  | &check; | &check; | &check; | &check; |                                  |
| Get-Process                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| Get-PSProvider                | &check; | &check; | &check; | &check; |                                  |
| Get-Service                   | &check; | &check; | &check; | &check; | Nur Windows                     |
| Get-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Get-Transaction               | &check; |         |         |         | Nur Windows                     |
| Get-WmiObject                 | &check; |         |         |         | Nur Windows                     |
| Invoke-Item                   | &check; | &check; | &check; | &check; |                                  |
| Invoke-WmiMethod              | &check; |         |         |         | Nur Windows                     |
| Join-Path                     | &check; | &check; | &check; | &check; |                                  |
| Limit-EventLog                | &check; |         |         |         | Nur Windows                     |
| Move-Item                     | &check; | &check; | &check; | &check; |                                  |
| Move-ItemProperty             | &check; | &check; | &check; | &check; |                                  |
| New-EventLog                  | &check; |         |         |         | Nur Windows                     |
| New-Item                      | &check; | &check; | &check; | &check; |                                  |
| New-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| New-PSDrive                   | &check; | &check; | &check; | &check; |                                  |
| New-Service                   | &check; | &check; | &check; | &check; | Nur Windows                     |
| New-WebServiceProxy           | &check; |         |         |         | Nur Windows                     |
| Pop-Location                  | &check; | &check; | &check; | &check; |                                  |
| Push-Location                 | &check; | &check; | &check; | &check; |                                  |
| Register-WmiEvent             | &check; |         |         |         | Nur Windows                     |
| Remove-Computer               | &check; |         |         |         | Nur Windows                     |
| Remove-EventLog               | &check; |         |         |         | Nur Windows                     |
| Remove-Item                   | &check; | &check; | &check; | &check; |                                  |
| Remove-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Remove-PSDrive                | &check; | &check; | &check; | &check; |                                  |
| Remove-Service                |         | &check; | &check; | &check; | Nur Windows                     |
| Remove-WmiObject              | &check; |         |         |         | Nur Windows                     |
| Rename-Computer               | &check; | &check; | &check; | &check; |                                  |
| Rename-Item                   | &check; | &check; | &check; | &check; |                                  |
| Rename-ItemProperty           | &check; | &check; | &check; | &check; |                                  |
| Reset-ComputerMachinePassword | &check; |         |         |         | Nur Windows                     |
| Resolve-Path                  | &check; | &check; | &check; | &check; |                                  |
| Restart-Computer              | &check; | &check; | &check; | &check; |                                  |
| Restart-Service               | &check; | &check; | &check; | &check; | Nur Windows                     |
| Restore-Computer              | &check; |         |         |         | Nur Windows                     |
| Resume-Service                | &check; | &check; | &check; | &check; | Nur Windows                     |
| Set-Clipboard                 | &check; |         | &check; | &check; |                                  |
| Set-Content                   | &check; | &check; | &check; | &check; |                                  |
| Set-Item                      | &check; | &check; | &check; | &check; |                                  |
| Set-ItemProperty              | &check; | &check; | &check; | &check; |                                  |
| Set-Location                  | &check; | &check; | &check; | &check; |                                  |
| Set-Service                   | &check; | &check; | &check; | &check; | Nur Windows                     |
| Set-TimeZone                  | &check; | &check; | &check; | &check; |                                  |
| Set-WmiInstance               | &check; |         |         |         | Nur Windows                     |
| Show-ControlPanelItem         | &check; |         |         |         | Nur Windows                     |
| Show-EventLog                 | &check; |         |         |         | Nur Windows                     |
| Split-Path                    | &check; | &check; | &check; | &check; |                                  |
| Start-Process                 | &check; | &check; | &check; | &check; |                                  |
| Start-Service                 | &check; | &check; | &check; | &check; | Nur Windows                     |
| Start-Transaction             | &check; |         |         |         | Nur Windows                     |
| Stop-Computer                 | &check; | &check; | &check; | &check; | Linux-/macOS-Unterstützung in 7.0 hinzugefügt |
| Stop-Process                  | &check; | &check; | &check; | &check; |                                  |
| Stop-Service                  | &check; | &check; | &check; | &check; | Nur Windows                     |
| Suspend-Service               | &check; | &check; | &check; | &check; | Nur Windows                     |
| Test-ComputerSecureChannel    | &check; |         |         |         | Nur Windows                     |
| Test-Connection               | &check; | &check; | &check; | &check; |                                  |
| Test-Path                     | &check; | &check; | &check; | &check; |                                  |
| Undo-Transaction              | &check; |         |         |         | Nur Windows                     |
| Use-Transaction               | &check; |         |         |         | Nur Windows                     |
| Wait-Process                  | &check; | &check; | &check; | &check; | Funktioniert nicht unter Linux/macOS     |
| Write-EventLog                | &check; |         |         |         | Nur Windows                     |

### <a name="microsoftpowershellodatautils"></a>Microsoft.PowerShell.ODataUtils

|        Cmdlet-Name        |   5,1   | 6.x  |  7.0  |  7.1  |     Hinweis     |
| ------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Export-ODataEndpointProxy | &check; |      |       |       | Nur Windows |

### <a name="microsoftpowershelloperationvalidation"></a>Microsoft.PowerShell.Operation.Validation

|        Cmdlet-Name         |   5,1   | 6.x  |  7.0  |  7.1  |     Hinweis     |
| -------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Get-OperationValidation    | &check; |      |       |       | Nur Windows |
| Invoke-OperationValidation | &check; |      |       |       | Nur Windows |

### <a name="microsoftpowershellsecurity"></a>Microsoft.PowerShell.Security

|        Cmdlet-Name        |   5,1   |   6.x   |   7.0   |   7.1   |                  Hinweis                   |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | --------------------------------------- |
| ConvertFrom-SecureString  | &check; | &check; | &check; | &check; |                                         |
| ConvertTo-SecureString    | &check; | &check; | &check; | &check; |                                         |
| Get-Acl                   | &check; | &check; | &check; | &check; | Nur Windows                            |
| Get-AuthenticodeSignature | &check; | &check; | &check; | &check; | Nur Windows                            |
| Get-CmsMessage            | &check; | &check; | &check; | &check; | Nur Windows                            |
| Get-Credential            | &check; | &check; | &check; | &check; |                                         |
| Get-ExecutionPolicy       | &check; | &check; | &check; | &check; | Gibt unter Linux/macOS **Uneingeschränkt** zurück |
| Get-PfxCertificate        | &check; | &check; | &check; | &check; |                                         |
| New-FileCatalog           | &check; | &check; | &check; | &check; | Nur Windows                            |
| Protect-CmsMessage        | &check; | &check; | &check; | &check; | Nur Windows                            |
| Set-Acl                   | &check; | &check; | &check; | &check; | Nur Windows                            |
| Set-AuthenticodeSignature | &check; | &check; | &check; | &check; | Nur Windows                            |
| Set-ExecutionPolicy       | &check; | &check; | &check; | &check; | Funktioniert nicht unter Linux/macOS             |
| Test-FileCatalog          | &check; | &check; | &check; | &check; | Nur Windows                            |
| Unprotect-CmsMessage      | &check; | &check; | &check; | &check; | Nur Windows                            |

### <a name="microsoftpowershellutility"></a>Microsoft.PowerShell.Utility

|        Cmdlet-Name        |   5,1   |   6.x   |   7.0   |   7.1   |                   Hinweis                    |
| ------------------------- | :-----: | :-----: | :-----: | :-----: | ----------------------------------------- |
| Add-Member                | &check; | &check; | &check; | &check; |                                           |
| Add-Type                  | &check; | &check; | &check; | &check; |                                           |
| Clear-Variable            | &check; | &check; | &check; | &check; |                                           |
| Compare-Object            | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Csv           | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Json          | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-Markdown      |         |   6.1   | &check; | &check; |                                           |
| ConvertFrom-SddlString    | &check; | &check; | &check; | &check; |                                           |
| ConvertFrom-String        | &check; |         |         |         |                                           |
| ConvertFrom-StringData    | &check; | &check; | &check; | &check; |                                           |
| Convert-String            | &check; |         |         |         |                                           |
| ConvertTo-Csv             | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Html            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Json            | &check; | &check; | &check; | &check; |                                           |
| ConvertTo-Xml             | &check; | &check; | &check; | &check; |                                           |
| Debug-Runspace            | &check; | &check; | &check; | &check; |                                           |
| Disable-PSBreakpoint      | &check; | &check; | &check; | &check; |                                           |
| Disable-RunspaceDebug     | &check; | &check; | &check; | &check; |                                           |
| Enable-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Enable-RunspaceDebug      | &check; | &check; | &check; | &check; |                                           |
| Export-Alias              | &check; | &check; | &check; | &check; |                                           |
| Export-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Export-Csv                | &check; | &check; | &check; | &check; |                                           |
| Export-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Export-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Format-Custom             | &check; | &check; | &check; | &check; |                                           |
| Format-Hex                | &check; | &check; | &check; | &check; |                                           |
| Format-List               | &check; | &check; | &check; | &check; |                                           |
| Format-Table              | &check; | &check; | &check; | &check; |                                           |
| Format-Wide               | &check; | &check; | &check; | &check; |                                           |
| Get-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Get-Culture               | &check; | &check; | &check; | &check; |                                           |
| Get-Date                  | &check; | &check; | &check; | &check; |                                           |
| Get-Error                 |         |         | &check; | &check; |                                           |
| Get-Event                 | &check; | &check; | &check; | &check; | Keine Ereignisquellen unter Linux/macOS verfügbar |
| Get-EventSubscriber       | &check; | &check; | &check; | &check; |                                           |
| Get-FileHash              | &check; | &check; | &check; | &check; |                                           |
| Get-FormatData            | &check; | &check; | &check; | &check; |                                           |
| Get-Host                  | &check; | &check; | &check; | &check; |                                           |
| Get-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Get-Member                | &check; | &check; | &check; | &check; |                                           |
| Get-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Get-PSCallStack           | &check; | &check; | &check; | &check; |                                           |
| Get-Random                | &check; | &check; | &check; | &check; |                                           |
| Get-Runspace              | &check; | &check; | &check; | &check; |                                           |
| Get-RunspaceDebug         | &check; | &check; | &check; | &check; |                                           |
| Get-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Get-TypeData              | &check; | &check; | &check; | &check; |                                           |
| Get-UICulture             | &check; | &check; | &check; | &check; |                                           |
| Get-Unique                | &check; | &check; | &check; | &check; |                                           |
| Get-Uptime                |         | &check; | &check; | &check; |                                           |
| Get-Variable              | &check; | &check; | &check; | &check; |                                           |
| Get-Verb                  |         | &check; | &check; | &check; |                                           |
| Group-Object              | &check; | &check; | &check; | &check; |                                           |
| Import-Alias              | &check; | &check; | &check; | &check; |                                           |
| Import-Clixml             | &check; | &check; | &check; | &check; |                                           |
| Import-Csv                | &check; | &check; | &check; | &check; |                                           |
| Import-LocalizedData      | &check; | &check; | &check; | &check; |                                           |
| Import-PowerShellDataFile | &check; | &check; | &check; | &check; |                                           |
| Import-PSSession          | &check; | &check; | &check; | &check; |                                           |
| Invoke-Expression         | &check; | &check; | &check; | &check; |                                           |
| Invoke-RestMethod         | &check; | &check; | &check; | &check; |                                           |
| Invoke-WebRequest         | &check; | &check; | &check; | &check; |                                           |
| Join-String               |         | &check; | &check; | &check; |                                           |
| Measure-Command           | &check; | &check; | &check; | &check; |                                           |
| Measure-Object            | &check; | &check; | &check; | &check; |                                           |
| New-Alias                 | &check; | &check; | &check; | &check; |                                           |
| New-Event                 | &check; | &check; | &check; | &check; | Keine Ereignisquellen unter Linux/macOS verfügbar |
| New-Guid                  | &check; | &check; | &check; | &check; |                                           |
| New-Object                | &check; | &check; | &check; | &check; |                                           |
| New-TemporaryFile         | &check; | &check; | &check; | &check; |                                           |
| New-TimeSpan              | &check; | &check; | &check; | &check; |                                           |
| New-Variable              | &check; | &check; | &check; | &check; |                                           |
| Out-File                  | &check; | &check; | &check; | &check; |                                           |
| Out-GridView              | &check; |         | &check; | &check; |                                           |
| Out-Printer               | &check; |         | &check; | &check; |                                           |
| Out-String                | &check; | &check; | &check; | &check; |                                           |
| Read-Host                 | &check; | &check; | &check; | &check; |                                           |
| Register-EngineEvent      | &check; | &check; | &check; | &check; | Keine Ereignisquellen unter Linux/macOS verfügbar |
| Register-ObjectEvent      | &check; | &check; | &check; | &check; |                                           |
| Remove-Alias              |         | &check; | &check; | &check; |                                           |
| Remove-Event              | &check; | &check; | &check; | &check; | Keine Ereignisquellen unter Linux/macOS verfügbar |
| Remove-PSBreakpoint       | &check; | &check; | &check; | &check; |                                           |
| Remove-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Remove-Variable           | &check; | &check; | &check; | &check; |                                           |
| Select-Object             | &check; | &check; | &check; | &check; |                                           |
| Select-String             | &check; | &check; | &check; | &check; |                                           |
| Select-Xml                | &check; | &check; | &check; | &check; |                                           |
| Send-MailMessage          | &check; | &check; | &check; | &check; |                                           |
| Set-Alias                 | &check; | &check; | &check; | &check; |                                           |
| Set-Date                  | &check; | &check; | &check; | &check; |                                           |
| Set-MarkdownOption        |         |   6.1   | &check; | &check; |                                           |
| Set-PSBreakpoint          | &check; | &check; | &check; | &check; |                                           |
| Set-TraceSource           | &check; | &check; | &check; | &check; |                                           |
| Set-Variable              | &check; | &check; | &check; | &check; |                                           |
| Show-Command              | &check; |         | &check; | &check; |                                           |
| Show-Markdown             |         |   6.1   | &check; | &check; |                                           |
| Sort-Object               | &check; | &check; | &check; | &check; |                                           |
| Start-Sleep               | &check; | &check; | &check; | &check; |                                           |
| Tee-Object                | &check; | &check; | &check; | &check; |                                           |
| Test-Json                 |         | &check; | &check; | &check; |                                           |
| Trace-Command             | &check; | &check; | &check; | &check; |                                           |
| Unblock-File              | &check; | &check; | &check; | &check; | Unterstützung für macOS in 7.0 hinzugefügt            |
| Unregister-Event          | &check; | &check; | &check; | &check; | Keine Ereignisquellen unter Linux/macOS verfügbar |
| Update-FormatData         | &check; | &check; | &check; | &check; |                                           |
| Update-List               | &check; |         | &check; | &check; |                                           |
| Update-TypeData           | &check; | &check; | &check; | &check; |                                           |
| Wait-Debugger             | &check; | &check; | &check; | &check; |                                           |
| Wait-Event                | &check; | &check; | &check; | &check; |                                           |
| Write-Debug               | &check; | &check; | &check; | &check; |                                           |
| Write-Error               | &check; | &check; | &check; | &check; |                                           |
| Write-Host                | &check; | &check; | &check; | &check; |                                           |
| Write-Information         | &check; | &check; | &check; | &check; |                                           |
| Write-Output              | &check; | &check; | &check; | &check; |                                           |
| Write-Progress            | &check; | &check; | &check; | &check; |                                           |
| Write-Verbose             | &check; | &check; | &check; | &check; |                                           |
| Write-Warning             | &check; | &check; | &check; | &check; |                                           |

### <a name="microsoftwsmanmanagement"></a>Microsoft.WSMan.Management

|      Cmdlet-Name       |   5,1   |   6.x   |   7.0   |   7.1   |     Hinweis     |
| ---------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Connect-WSMan          | &check; | &check; | &check; | &check; | Nur Windows |
| Disable-WSManCredSSP   | &check; | &check; | &check; | &check; | Nur Windows |
| Disconnect-WSMan       | &check; | &check; | &check; | &check; | Nur Windows |
| Enable-WSManCredSSP    | &check; | &check; | &check; | &check; | Nur Windows |
| Get-WSManCredSSP       | &check; | &check; | &check; | &check; | Nur Windows |
| Get-WSManInstance      | &check; | &check; | &check; | &check; | Nur Windows |
| Invoke-WSManAction     | &check; | &check; | &check; | &check; | Nur Windows |
| New-WSManInstance      | &check; | &check; | &check; | &check; | Nur Windows |
| New-WSManSessionOption | &check; | &check; | &check; | &check; | Nur Windows |
| Remove-WSManInstance   | &check; | &check; | &check; | &check; | Nur Windows |
| Set-WSManInstance      | &check; | &check; | &check; | &check; | Nur Windows |
| Set-WSManQuickConfig   | &check; | &check; | &check; | &check; | Nur Windows |
| Test-WSMan             | &check; | &check; | &check; | &check; | Nur Windows |

### <a name="packagemanagement"></a>PackageManagement

|       Cmdlet-Name        |   5,1   |   6.x   |   7.0   |   7.1   | Hinweis |
| ------------------------ | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Package             | &check; | &check; | &check; | &check; |      |
| Find-PackageProvider     | &check; | &check; | &check; | &check; |      |
| Get-Package              | &check; | &check; | &check; | &check; |      |
| Get-PackageProvider      | &check; | &check; | &check; | &check; |      |
| Get-PackageSource        | &check; | &check; | &check; | &check; |      |
| Import-PackageProvider   | &check; | &check; | &check; | &check; |      |
| Install-Package          | &check; | &check; | &check; | &check; |      |
| Install-PackageProvider  | &check; | &check; | &check; | &check; |      |
| Register-PackageSource   | &check; | &check; | &check; | &check; |      |
| Save-Package             | &check; | &check; | &check; | &check; |      |
| Set-PackageSource        | &check; | &check; | &check; | &check; |      |
| Uninstall-Package        | &check; | &check; | &check; | &check; |      |
| Unregister-PackageSource | &check; | &check; | &check; | &check; |      |

### <a name="powershellget"></a>PowershellGet

|           Cmdlet-Name           |   5,1   |   6.x   |   7.0   |   7.1   | Hinweis |
| ------------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Find-Command                    | &check; | &check; | &check; | &check; |      |
| Find-DscResource                | &check; | &check; | &check; | &check; |      |
| Find-Module                     | &check; | &check; | &check; | &check; |      |
| Find-RoleCapability             | &check; | &check; | &check; | &check; |      |
| Find-Script                     | &check; | &check; | &check; | &check; |      |
| Get-CredsFromCredentialProvider |         | &check; | &check; | &check; |      |
| Get-InstalledModule             | &check; | &check; | &check; | &check; |      |
| Get-InstalledScript             | &check; | &check; | &check; | &check; |      |
| Get-PSRepository                | &check; | &check; | &check; | &check; |      |
| Install-Module                  | &check; | &check; | &check; | &check; |      |
| Install-Script                  | &check; | &check; | &check; | &check; |      |
| New-ScriptFileInfo              | &check; | &check; | &check; | &check; |      |
| Publish-Module                  | &check; | &check; | &check; | &check; |      |
| Publish-Script                  | &check; | &check; | &check; | &check; |      |
| Register-PSRepository           | &check; | &check; | &check; | &check; |      |
| Save-Module                     | &check; | &check; | &check; | &check; |      |
| Save-Script                     | &check; | &check; | &check; | &check; |      |
| Set-PSRepository                | &check; | &check; | &check; | &check; |      |
| Test-ScriptFileInfo             | &check; | &check; | &check; | &check; |      |
| Uninstall-Module                | &check; | &check; | &check; | &check; |      |
| Uninstall-Script                | &check; | &check; | &check; | &check; |      |
| Unregister-PSRepository         | &check; | &check; | &check; | &check; |      |
| Update-Module                   | &check; | &check; | &check; | &check; |      |
| Update-ModuleManifest           | &check; | &check; | &check; | &check; |      |
| Update-Script                   | &check; | &check; | &check; | &check; |      |
| Update-ScriptFileInfo           | &check; | &check; | &check; | &check; |      |

### <a name="psdesiredstateconfiguration"></a>PSDesiredStateConfiguration

|                Cmdlet-Name                 |   5,1   |   6.x   |   7.0   |   7.1   |     Hinweis     |
| ------------------------------------------ | :-----: | :-----: | :-----: | :-----: | ------------ |
| Add-NodeKeys                               |         | &check; |         |         |              |
| ConvertTo-MOFInstance                      |         | &check; |         |         |              |
| Disable-DscDebug                           | &check; |         |         |         | Nur Windows |
| Enable-DscDebug                            | &check; |         |         |         | Nur Windows |
| Generate-VersionInfo                       |         | &check; |         |         |              |
| Get-CompatibleVersionAddtionaPropertiesStr |         | &check; |         |         |              |
| Get-ComplexResourceQualifier               |         | &check; |         |         |              |
| Get-ConfigurationErrorCount                |         | &check; |         |         |              |
| Get-DscConfiguration                       | &check; |         |         |         | Nur Windows |
| Get-DscConfigurationStatus                 | &check; |         |         |         | Nur Windows |
| Get-DscLocalConfigurationManager           | &check; |         |         |         | Nur Windows |
| Get-DscResource                            | &check; | &check; | &check; | &check; |              |
| Get-DSCResourceModules                     |         | &check; |         |         |              |
| Get-EncryptedPassword                      |         | &check; |         |         |              |
| Get-InnerMostErrorRecord                   |         | &check; |         |         |              |
| Get-MofInstanceName                        |         | &check; |         |         |              |
| Get-MofInstanceText                        |         | &check; |         |         |              |
| Get-PositionInfo                           |         | &check; |         |         |              |
| Get-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Get-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Get-PSMetaConfigDocumentInstVersionInfo    |         | &check; |         |         |              |
| Get-PSMetaConfigurationProcessed           |         | &check; |         |         |              |
| Get-PSTopConfigurationName                 |         | &check; |         |         |              |
| Get-PublicKeyFromFile                      |         | &check; |         |         |              |
| Get-PublicKeyFromStore                     |         | &check; |         |         |              |
| Initialize-ConfigurationRuntimeState       |         | &check; |         |         |              |
| Invoke-DscResource                         | &check; |         | &check; | &check; |              |
| New-DSCCheckSum                            | &check; | &check; | &check; | &check; |              |
| Publish-DscConfiguration                   | &check; |         |         |         | Nur Windows |
| Remove-DscConfigurationDocument            | &check; |         |         |         | Nur Windows |
| Restore-DscConfiguration                   | &check; |         |         |         | Nur Windows |
| Set-DscLocalConfigurationManager           | &check; |         |         |         | Nur Windows |
| Set-NodeExclusiveResources                 |         | &check; |         |         |              |
| Set-NodeManager                            |         | &check; |         |         |              |
| Set-NodeResources                          |         | &check; |         |         |              |
| Set-NodeResourceSource                     |         | &check; |         |         |              |
| Set-PSCurrentConfigurationNode             |         | &check; |         |         |              |
| Set-PSDefaultConfigurationDocument         |         | &check; |         |         |              |
| Set-PSMetaConfigDocInsProcessedBeforeMeta  |         | &check; |         |         |              |
| Set-PSMetaConfigVersionInfoV2              |         | &check; |         |         |              |
| Set-PSTopConfigurationName                 |         | &check; |         |         |              |
| Start-DscConfiguration                     | &check; |         |         |         | Nur Windows |
| Stop-DscConfiguration                      | &check; |         |         |         | Nur Windows |
| Test-ConflictingResources                  |         | &check; |         |         |              |
| Test-DscConfiguration                      | &check; |         |         |         | Nur Windows |
| Test-ModuleReloadRequired                  |         | &check; |         |         |              |
| Test-MofInstanceText                       |         | &check; |         |         |              |
| Test-NodeManager                           |         | &check; |         |         |              |
| Test-NodeResources                         |         | &check; |         |         |              |
| Test-NodeResourceSource                    |         | &check; |         |         |              |
| Update-ConfigurationDocumentRef            |         | &check; |         |         |              |
| Update-ConfigurationErrorCount             |         | &check; |         |         |              |
| Update-DependsOn                           |         | &check; |         |         |              |
| Update-DscConfiguration                    | &check; |         |         |         | Nur Windows |
| Update-LocalConfigManager                  |         | &check; |         |         |              |
| Update-ModuleVersion                       |         | &check; |         |         |              |
| ValidateUpdate-ConfigurationData           |         | &check; |         |         |              |
| Write-Log                                  |         | &check; |         |         |              |
| Write-MetaConfigFile                       |         | &check; |         |         |              |
| Write-NodeMOFFile                          |         | &check; |         |         |              |

### <a name="psdiagnostics"></a>PSDiagnostics

|         Cmdlet-Name          |   5,1   |   6.x   |   7.0   |   7.1   |     Hinweis     |
| ---------------------------- | :-----: | :-----: | :-----: | :-----: | ------------ |
| Disable-PSTrace              | &check; |   6.2   | &check; | &check; | Nur Windows |
| Disable-PSWSManCombinedTrace | &check; |   6.2   | &check; | &check; | Nur Windows |
| Disable-WSManTrace           | &check; | &check; | &check; | &check; | Nur Windows |
| Enable-PSTrace               | &check; | &check; | &check; | &check; | Nur Windows |
| Enable-PSWSManCombinedTrace  | &check; | &check; | &check; | &check; | Nur Windows |
| Enable-WSManTrace            | &check; |   6.2   | &check; | &check; | Nur Windows |
| Get-LogProperties            | &check; |   6.2   | &check; | &check; | Nur Windows |
| Set-LogProperties            | &check; |   6.2   | &check; | &check; | Nur Windows |
| Start-Trace                  | &check; |   6.2   | &check; | &check; | Nur Windows |
| Stop-Trace                   | &check; |   6.2   | &check; | &check; | Nur Windows |

### <a name="psreadline"></a>PSReadline

|         Cmdlet-Name         |   5,1   |   6.x   |   7.0   |   7.1   | Hinweis |
| --------------------------- | :-----: | :-----: | :-----: | :-----: | ---- |
| Get-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Get-PSReadlineOption        | &check; | &check; | &check; | &check; |      |
| PSConsoleHostReadline       | &check; | &check; | &check; | &check; |      |
| Remove-PSReadlineKeyHandler | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineKeyHandler    | &check; | &check; | &check; | &check; |      |
| Set-PSReadlineOption        | &check; | &check; | &check; | &check; |      |

### <a name="psscheduledjob"></a>PSScheduledJob

|       Cmdlet-Name       |   5,1   | 6.x  |  7.0  |  7.1  |     Hinweis     |
| ----------------------- | :-----: | :--- | :---: | :---: | ------------ |
| Add-JobTrigger          | &check; |      |       |       | Nur Windows |
| Disable-JobTrigger      | &check; |      |       |       | Nur Windows |
| Disable-ScheduledJob    | &check; |      |       |       | Nur Windows |
| Enable-JobTrigger       | &check; |      |       |       | Nur Windows |
| Enable-ScheduledJob     | &check; |      |       |       | Nur Windows |
| Get-JobTrigger          | &check; |      |       |       | Nur Windows |
| Get-ScheduledJob        | &check; |      |       |       | Nur Windows |
| Get-ScheduledJobOption  | &check; |      |       |       | Nur Windows |
| New-JobTrigger          | &check; |      |       |       | Nur Windows |
| New-ScheduledJobOption  | &check; |      |       |       | Nur Windows |
| Register-ScheduledJob   | &check; |      |       |       | Nur Windows |
| Remove-JobTrigger       | &check; |      |       |       | Nur Windows |
| Set-JobTrigger          | &check; |      |       |       | Nur Windows |
| Set-ScheduledJob        | &check; |      |       |       | Nur Windows |
| Set-ScheduledJobOption  | &check; |      |       |       | Nur Windows |
| Unregister-ScheduledJob | &check; |      |       |       | Nur Windows |

### <a name="psworkflow--psworkflowutility"></a>PSWorkflow und PSWorkflowUtility

|          Cmdlet-Name          |   5,1   | 6.x  |  7.0  |  7.1  |     Hinweis     |
| ----------------------------- | :-----: | :--- | :---: | :---: | ------------ |
| New-PSWorkflowExecutionOption | &check; |      |       |       | Nur Windows |
| New-PSWorkflowSession         | &check; |      |       |       | Nur Windows |
| Invoke-AsWorkflow             | &check; |      |       |       | Nur Windows |

### <a name="threadjob"></a>ThreadJob

|   Cmdlet-Name   |  5,1  |   6.x   |   7.0   |   7.1   | Hinweis |
| --------------- | :---: | :-----: | :-----: | :-----: | ---- |
| Start-ThreadJob |       | &check; | &check; | &check; | Installation in PowerShell 5.1 möglich |
