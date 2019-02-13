---
ms.date: 1/17/2019
keywords: dsc,powershell,configuration,setup
title: Einen Knoten neu starten
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678354"
---
# <a name="reboot-a-node"></a>Einen Knoten neu starten

> [!NOTE]
> In diesem Thema erläutert, wie einen Knoten neu starten. In der Reihenfolge für den Neustart erfolgen die **ActionAfterReboot** und **RebootNodeIfNeeded** LCM-Einstellungen müssen ordnungsgemäß konfiguriert werden.
> Informationen zu den Einstellungen des lokalen Konfigurations-Managers finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md), oder [Konfigurieren des lokalen Konfigurations-Managers (v4)](../managing-nodes/metaConfig4.md).

Knoten können neu gestartet werden, von innerhalb einer Ressource, mit der `$global:DSCMachineStatus` Flag. Wenn dieses Flag auf `1` in die `Set-TargetResource` Funktion erzwingt, dass den LCM den Knoten direkt nach dem Neustart der **festgelegt** Methode die aktuelle Ressource. Verwenden dieses Flag die **xPendingReboot** Ressource wird erkannt, ob ein Neustart aussteht außerhalb von DSC.

Ihre [Konfigurationen](configurations.md) möglicherweise Schritte ausgeführt, die den Knoten neu starten zu müssen. Dies kann z. B. Aspekte umfassen:

- Windows-Updates
- Softwareinstallation
- Datei wird umbenannt.
- Benennen Sie Computer

Die **xPendingReboot** Ressource überprüft den bestimmten Computer-Standorte, um festzustellen, ob ein Neustart aussteht. Wenn der Knoten einen Neustart außerhalb von DSC, erfordert die **xPendingReboot** Ressourcensätzen der `$global:DSCMachineStatus` flag `1` einen Neustart erzwungen und das ausstehende Problem zu beheben.

> [!NOTE]
> Alle DSC-Ressourcen kann anweisen, die den LCM den Knoten neu gestartet, indem Sie dieses Flag festlegen, der `Set-TargetResource` Funktion. Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Syntax

```
xPendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Eigenschaften

| Eigenschaft | Beschreibung |
| --- | --- |
| Name| Erforderlicher Parameter, der jede Instanz der Ressource in einer Konfiguration eindeutig sein müssen.|
| SkipComponentBasedServicing | Skip-Neustarts, die von der komponentenbasierten Wartung-Komponente ausgelöst. |
| SkipWindowsUpdate | Skip-Neustarts durch Windows Update ausgelöst wird.|
| SkipPendingFileRename | Benennen Sie Skip ausstehende Neustarts aus. |
| SkipCcmClientSDK | Skip-Neustarts durch den ConfigMgr-Client ausgelöst wird. |
| SkipComputerRename | Skip wird veranschaulicht, wie die Computerrichtlinie durch Umbenennen der Computer neu gestartet. |
| PSDSCRunAsCredential | In v5 unterstützt. Führt die Ressource als den angegebenen Benutzer. |
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. Weitere Informationen finden Sie unter [mithilfe von "DependsOn"](resource-depends-on.md)|

## <a name="example"></a>Beispiel

Im folgende Beispiel wird installiert, Microsoft Exchange verwenden die [xExchange](https://github.com/PowerShell/xExchange) Ressource.
Während der Installation der **xPendingReboot** Ressource wird verwendet, um die Knoten neu starten.

> [!NOTE]
> Dieses Beispiel erfordert die Anmeldeinformationen eines Kontos, das über Rechte zum Hinzufügen von eines Exchange-Servers in der Gesamtstruktur verfügt. Weitere Informationen zur Verwendung von Anmeldeinformationen in DSC finden Sie unter [Behandeln von Anmeldeinformationen in DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module xPendingReboot

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        xPendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> In diesem Beispiel wird davon ausgegangen, dass Sie Ihre lokalen Konfigurations-Managers zum ermöglichen von Neustarts und die Konfiguration nach einem Neustart weiterhin konfiguriert haben.

## <a name="where-to-download"></a>Wo heruntergeladen

Sie können die Ressourcen verwendet, die in diesem Thema an folgenden Speicherorten oder mithilfe von PowerShell-Katalog herunterladen.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
