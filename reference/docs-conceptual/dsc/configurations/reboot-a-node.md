---
ms.date: 01/17/2019
keywords: dsc,powershell,configuration,setup
title: Neustart eines Knotens
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954027"
---
# <a name="reboot-a-node"></a>Neustart eines Knotens

> [!NOTE]
> In diesem Thema wird erläutert, wie ein Knoten neu gestartet wird. Damit der Neustart erfolgreich verläuft, müssen die LCM-Einstellungen **ActionAfterReboot** und **RebootNodeIfNeeded** ordnungsgemäß konfiguriert werden.
> Weitere Informationen zu Einstellungen des lokalen Konfigurations-Managers finden Sie unter [Configure the Local Configuration Manager (Konfigurieren des lokalen Konfigurations-Managers)](../managing-nodes/metaConfig.md) oder [Configure the Local Configuration Manager (v4) (Konfigurieren des lokalen Konfigurations-Managers (Version 4))](../managing-nodes/metaConfig4.md).

Knoten können mithilfe des `$global:DSCMachineStatus`-Flags innerhalb einer Ressource neu gestartet werden. Wenn dieses Flag in der Funktion `Set-TargetResource` auf `1` festgelegt wird, wird der LCM direkt nach der **Set**-Methode der aktuellen Ressource zum Neustart des Knotens gezwungen. Mithilfe dieses Flags erkennt die **PendingReboot**-Ressource im DSC-Ressourcenmodul [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc), ob ein Neustart außerhalb von DSC aussteht.

Ihre [Konfigurationen](configurations.md) führen möglicherweise Schritte aus, die für den Neustart des Knotens erforderlich sind. Dazu kann Folgendes gehören:

- Windows-Updates
- Softwareinstallation
- Umbenennen von Dateien
- Umbenennen von Computern

Die Ressource **PendingReboot** überprüft bestimmte Computerstandorte, um zu bestimmen, ob ein Neustart aussteht. Wenn der Knoten einen Neustart außerhalb der DSC erfordert, legt die Ressource **PendingReboot** das `$global:DSCMachineStatus`-Flag auf `1` fest, wodurch ein Neustart erzwungen und die ausstehende Bedingung aufgelöst wird.

> [!NOTE]
> Jede DSC-Ressource kann den LCM zum Neustart des Knotens anweisen, indem dieses Flag in der Funktion `Set-TargetResource` festgelegt wird. Weitere Informationen finden Sie unter [Writing a custom DSC resource with MOF (Schreiben einer benutzerdefinierten DSC-Ressource mit MOF)](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Syntax

```
PendingReboot [String] #ResourceName
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
| Name| Erforderlicher Parameter, der innerhalb einer Konfiguration pro Ressourceninstanz eindeutig sein muss.|
| SkipComponentBasedServicing | Überspringen von Neustarts, die von der komponentenbasierten Wartungskomponente ausgelöst wurden. |
| SkipWindowsUpdate | Überspringen von Neustarts, die von einem Windows-Update ausgelöst wurden.|
| SkipPendingFileRename | Überspringen von ausstehenden Neustarts aufgrund von Dateiumbenennungen. |
| SkipCcmClientSDK | Überspringen von Neustarts, die vom ConfigMgr-Client ausgelöst wurden. |
| SkipComputerRename | Überspringen von Neustarts, die von Umbenennungen eines Computers ausgelöst wurden. |
| PsDscRunAsCredential | Unterstützt in Version 5. Führt die Ressource als angegebener Benutzer aus. |
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. Weitere Informationen finden Sie unter [Using DependsOn (Verwenden von „DependsOn“)](resource-depends-on.md).|

## <a name="example"></a>Beispiel

Das folgende Beispiel installiert Microsoft Exchange mithilfe der [xExchange](https://github.com/PowerShell/xExchange)-Ressource.
Während der kompletten Installation wird die **PendingReboot**-Ressource verwendet, um den Knoten neu zu starten.

> [!NOTE]
> Für dieses Beispiel sind die Anmeldeinformationen eines Kontos erforderlich, das berechtigt ist, der Gesamtstruktur einen Exchange-Server hinzuzufügen. Weitere Informationen zur Verwendung von Anmeldeinformationen in DSC finden Sie unter [Handling Credentials in DSC (Verwendung von Anmeldeinformationen in DSC)](../configurations/configDataCredentials.md).

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
    Import-DscResource -Module ComputerManagementDsc

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
        PendingReboot BeforeExchangeInstall
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
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> In diesem Beispiel wird davon ausgegangen, dass Sie Ihren lokalen Konfigurations-Manager so konfiguriert haben, dass Neustarts erlaubt sind, und die Konfiguration nach einem Neustart fortgesetzt wird.

## <a name="where-to-download"></a>Speicherorte für Downloads

Sie können die in diesem Thema verwendeten Ressourcen an folgenden Speicherorten abspeichern, oder mithilfe des PowerShell-Katalogs.

- [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc)
- [xExchange](https://github.com/PowerShell/xExchange)
