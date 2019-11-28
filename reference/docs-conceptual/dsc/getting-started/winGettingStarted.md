---
ms.date: 08/15/2019
keywords: dsc,powershell,configuration,setup
title: Erste Schritte mit Desired State Configuration (DSC) für Windows
ms.openlocfilehash: a9346b96693acdbad9bacbd4b6ca85971e17a3d1
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417769"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>Erste Schritte mit Desired State Configuration (DSC) für Windows

In diesem Thema werden die ersten Schritte mit PowerShell Desired State Configuration (DSC) für Windows erläutert.
Allgemeine Informationen zu DSC finden Sie unter [Erste Schritte mit Windows PowerShell DSC](../overview/overview.md).

## <a name="supported-windows-operation-system-versions"></a>Unterstützte Windows-Betriebssystemversionen

Die folgenden Versionen werden unterstützt:

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

Die eigenständige Produkt-SKU [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) umfasst keine Desired State Configuration-Implementierung und kann deshalb nicht mit PowerShell DSC oder Azure Automation State Configuration verwaltet werden.

## <a name="installing-dsc"></a>Installieren von DSC

PowerShell Desired State Configuration ist in Windows enthalten und wird über Windows Management Framework aktualisiert.
Die aktuelle Version ist [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

> [!NOTE]
> Es ist nicht erforderlich, das Windows Server-Feature „DSC-Service“ zu aktivieren, um einen Computer mithilfe von DSC zu verwalten.
> Dieses Feature wird nur benötigt, wenn Sie eine Windows Pull Server-Instanz erstellen.

## <a name="using-dsc-for-windows"></a>Verwenden von DSC für Windows

In den folgenden Abschnitten wird erläutert, wie DSC-Konfigurationen erstellt und auf Windows-Computern ausgeführt werden.

### <a name="creating-a-configuration-mof-document"></a>Erstellen eines MOF-Konfigurationsdokuments

Um eine Konfiguration zu erstellen, wird das Windows PowerShell-Schlüsselwort „Configuration“ verwendet.
Die folgenden Schritte beschreiben die Erstellung eines Konfigurationsdokuments mithilfe von Windows PowerShell.

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>Definieren Sie eine Konfiguration, und generieren Sie das Konfigurationsdokument:

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a>Installieren eines Moduls mit DSC-Ressourcen

Windows PowerShell Desired State Configuration umfasst integrierte Module, die DSC-Ressourcen enthalten.
Mithilfe der PowerShellGet-Cmdlets ist es außerdem möglich, Module aus externen Quellen wie z. B. dem PowerShell-Katalog zu laden.

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>Anwenden der Konfiguration auf den Computer

Konfigurationsdokumente (MOF-Dateien) können mit dem Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) auf den Computer angewendet werden.

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>Abrufen des aktuellen Status der Konfiguration

Mit dem Cmdlet [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) wird der aktuelle Status des Computers abgerufen, und es werden die aktuellen Werte für die Konfiguration zurückgegeben.

`Get-DscConfiguration`

Das Cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) gibt die aktuelle Metakonfiguration zurück, die auf den Computer angewendet wurde.

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>Entfernen der aktuellen Konfiguration von einem Computer

Cmdlet [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument):

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>Konfigurieren der Einstellungen im lokalen Konfigurations-Manager

Wenden Sie mit dem Cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) eine MOF-Metakonfigurationsdatei auf den Computer an.
Erfordert die Angabe des Pfads zur MOF-Metakonfigurationsdatei.

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Windows PowerShell DSC-Protokolldateien

Protokolle für Desired State Configuration werden in das Windows-Ereignisprotokoll im Pfad `Microsoft-Windows-Dsc/Operational` geschrieben.
Zusätzliche Protokolle zu Debuggingzwecken können mithilfe der unter [Wo befinden sich die DSC-Ereignisprotokolle?](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs) genannten Schritte aktiviert werden.
