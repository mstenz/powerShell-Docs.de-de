---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: PowerShell DSC – Teilkonfigurationen
ms.openlocfilehash: 842acad221d468ca5e4c9e660f0205c567bcc220
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500775"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell DSC – Teilkonfigurationen

_Gilt für: Windows PowerShell 5.0 und höher_

In PowerShell 5.0 ermöglicht DSC (Desired State Configuration, Konfiguration des gewünschten Zustands), dass Konfigurationen in Fragmenten und aus mehreren Quellen übermittelt werden. Der LCM (Local Configuration Manager, lokale Konfigurations-Manager) auf dem Zielknoten setzt die Fragmente zusammen, ehe sie als einzelne Konfiguration angewendet werden. Dies ermöglicht die gemeinsame Steuerung der Konfiguration durch Teams oder Einzelpersonen. Wenn z. B. zwei oder mehr Teams an der Entwicklung eines Diensts zusammenarbeiten, möchte ggf. jedes Team Konfigurationen für die Verwaltung seines Teils des Diensts erstellen. Jede dieser Konfigurationen kann von verschiedenen Pullservern abgerufen und in verschiedenen Phasen der Entwicklung hinzugefügt werden. Teilkonfigurationen ermöglichen außerdem verschiedenen Personen oder Teams das Steuern verschiedener Aspekte der Konfiguration von Knoten, ohne dass die Bearbeitung eines einzelnen Konfigurationsdokuments koordiniert werden muss. Ein Team kann z. B. für die Bereitstellung einer VM und eines Betriebssystems verantwortlich sein, während ein anderes Team andere Anwendungen und Dienste auf dieser VM bereitstellen kann. Bei Teilkonfigurationen kann jedes Team seine eigene Konfiguration erstellen, die dann nicht unnötig kompliziert sein muss.

Sie können Teilkonfigurationen im Pushmodus, Pullmodus oder einer Kombination aus beidem verwenden.

## <a name="partial-configurations-in-push-mode"></a>Teilkonfigurationen im Pushmodus

Um Teilkonfigurationen im Pushmodus zu verwenden, konfigurieren Sie den LCM auf dem Zielknoten für das Empfangen von Teilkonfigurationen. Jede Teilkonfiguration muss mithilfe von Push auf den Zielknoten übertragen werden, wozu das Cmdlet `Publish-DSCConfiguration` verwendet wird. Der Zielknoten kombiniert dann die Teilkonfigurationen zu einer einzelnen Konfiguration, und Sie können die Konfiguration durch Aufrufen des Cmdlets [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufrufen.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Konfigurieren des LCM für Teilkonfigurationen im Pushmodus

Zum Konfigurieren des LCM für Teilkonfigurationen im Pushmodus erstellen Sie eine **DSCLocalConfigurationManager**-Konfiguration mit einem **PartialConfiguration**-Block für jede Teilkonfiguration. Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md). Das folgende Beispiel zeigt eine LCM-Konfiguration, die zwei Teilkonfigurationen erwartet: eine, die das Betriebssystem bereitgestellt, und eine, die SharePoint bereitstellt und konfiguriert.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

**RefreshMode** für jede Teilkonfiguration ist auf „Push“ festgelegt. Die Namen der **PartialConfiguration**-Blöcke (in diesem Fall „ServiceAccountConfig“ und „SharePointConfig“) müssen genau mit den Namen der Konfigurationen übereinstimmen, die per Push an die Zielknoten übertragen werden.

> [!Note]
> Die benannten einzelnen **PartialConfiguration**-Blocks müssen mit dem tatsächlichen Namen der Konfiguration übereinstimmen, der im Konfigurationsskript angegeben ist, und nicht mit dem Namen der MOF-Datei, der der Name des Zielknotens oder `localhost` sein sollte.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Veröffentlichen und Starten von Teilkonfigurationen im Pushmodus

Rufen Sie dann [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) für jede Konfiguration auf, und übergeben Sie die Ordner mit den Konfigurationsdokumenten als **Path**-Parameter. `Publish-DSCConfiguration` positioniert die Konfigurations-MOF-Dateien auf die Zielknoten. Nach Veröffentlichen beider Konfigurationen können Sie `Start-DSCConfiguration –UseExisting` auf dem Zielknoten aufrufen.

Wenn Sie z.B. die folgenden Konfigurations-MOF-Dokumente auf dem Erstellungsknoten kompiliert haben:

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

Sie würden die Konfigurationen wie folgt veröffentlichen und ausführen:

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> Der Benutzer, der das Cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) ausführt, muss über Administratorrechte auf dem Zielknoten verfügen.

## <a name="partial-configurations-in-pull-mode"></a>Teilkonfigurationen im Pullmodus

Teilkonfigurationen können von einem oder mehreren Pullservern abgerufen werden (weitere Informationen zu Pullservern finden Sie unter [Windows PowerShell DSC – Pullserver](pullServer.md). Konfigurieren Sie hierzu den LCM so, dass die Teilkonfigurationen per Pull auf den Zielknoten abgerufen werden, und sorgen Sie dafür, dass die Konfigurationsdokumente auf den Pullservern ordnungsgemäß benannt und abgelegt werden.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Konfigurieren des LCM für Teilkonfigurationen im Pullmodus

Zum Konfigurieren des LCM zum Abrufen von Teilkonfigurationen per Pull von einem Pullserver müssen Sie den Pullserver entweder in einem **ConfigurationRepositoryWeb**-Block (für einen HTTP-Pullserver) oder einem **ConfigurationRepositoryShare**-Block (für einen SMB-Pullserver) definieren. Dann erstellen Sie **PartialConfiguration**-Blöcke, die unter Verwendung der **ConfigurationSource**-Eigenschaft auf den Pullserver verweisen. Sie müssen außerdem einen **Settings**-Block erstellen, um anzugeben, dass der LCM den Pullmodus verwendet, und um die **ConfigurationNames**- oder **ConfigurationID**-Werte anzugeben, die der Pullserver und Zielknoten zum Identifizieren der Konfigurationen verwenden. Die folgende Metakonfiguration definiert einen HTTP-Pullserver mit dem Namen „CONTOSO-PullSrv“ und zwei Teilkonfigurationen, die diesen Pullserver verwenden.

Weitere Informationen zum Konfigurieren des LCM unter Verwendung von **ConfigurationNames** finden Sie unter [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](pullClientConfigNames.md). Weitere Informationen zum Konfigurieren des LCM unter Verwendung von **ConfigurationID** finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Konfigurieren des LCM für Pullmoduskonfigurationen mithilfe von Konfigurationsnamen

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Konfigurieren des LCM für Pullmoduskonfigurationen mithilfe der Konfigurations-ID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

Sie können Teilkonfigurationen per Pull von mehreren Pullservern abrufen. Sie müssen dazu die einzelnen Pullserver definieren und dann im jeweiligen **PartialConfiguration**-Block auf den entsprechenden Pullserver verweisen.

Nach dem Erstellen der Metakonfiguration müssen Sie diese ausführen, um ein Konfigurationsdokument (eine MOF-Datei) zu erstellen. Rufen Sie anschließend [Set- DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) auf, um den LCM zu konfigurieren.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Benennen und Ablegen der Konfigurationsdokumente auf dem Pullserver (ConfigurationNames)

Die Teilkonfigurationsdokumente müssen in dem Ordner abgelegt werden, der als **ConfigurationPath** in der Datei `web.config` für den Pullserver angegeben ist (meist `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Benennen der Konfigurationsdokumente auf dem Pullserver in PowerShell 5.1

Wenn Sie nur eine partielle Konfiguration von einem einzelnen Pullserver abrufen, kann das Konfigurationsdokument beliebig benannt werden. Wenn Sie mehrere partielle Konfigurationen von einem Pullserver abrufen, kann das Konfigurationsdokument entweder `<ConfigurationName>.mof` genannt werden, wobei *ConfigurationName* der Name der partiellen Konfiguration ist, oder `<ConfigurationName>.<NodeName>.mof`, wobei *ConfigurationName* der Name der partiellen Konfiguration und *NodeName* der Name des Zielknotens ist. Dadurch können Sie Konfigurationen vom DSC-Pullserver für Azure Automation abrufen.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Benennen der Konfigurationsdokumente auf dem Pullserver in PowerShell 5.0

Konfigurationsdokumente müssen wie folgt benannt werden: `ConfigurationName.mof`, wobei *ConfigurationName* der Name der partiellen Konfiguration ist. In unserem Beispiel sollten die Konfigurationsdokumente wie folgt heißen:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Benennen und Ablegen der Konfigurationsdokumente auf dem Pullserver (ConfigurationID)

Die Teilkonfigurationsdokumente müssen in dem Ordner abgelegt werden, der als **ConfigurationPath** in der Datei `web.config` für den Pullserver angegeben ist (meist `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Die Konfigurationsdokumente müssen wie folgt genannt werden: `<ConfigurationName>.<ConfigurationID>.mof`, wobei _ConfigurationName_ der Name der partiellen Konfiguration und _ConfigurationID_ die Konfigurations-ID ist, die im LCM auf dem Zielknoten definiert ist. In unserem Beispiel sollten die Konfigurationsdokumente wie folgt heißen:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Ausführen von Teilkonfigurationen von einem Pullserver

Nachdem der LCM auf dem Zielknoten konfiguriert wurde und die Konfigurationsdokumente auf dem Pullserver erstellt und ordnungsgemäß benannt wurden, ruft der Zielknoten die Teilkonfigurationen ab, kombiniert sie und wendet die resultierende Konfiguration in regelmäßigen Abständen entsprechend der Angabe der **RefreshFrequencyMins**-Eigenschaft des LCM an. Wenn Sie eine Aktualisierung erzwingen möchten, können Sie das Cmdlet [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) aufrufen, um die Konfigurationen per Pull abzurufen, und dann `Start-DSCConfiguration –UseExisting` aufrufen, um sie anzuwenden.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Teilkonfigurationen im gemischten Push- und Pullmodus

Sie können Push- und Pullmodus für Teilkonfigurationen auch mischen. Es ist also möglich, dass eine Teilkonfiguration per Pull von einem Pullserver abgerufen wird, während eine andere per Push übertragen wird. Geben Sie den Aktualisierungsmodus für jede partielle Konfiguration an, wie in den vorherigen Abschnitten beschrieben. In der folgenden Metakonfiguration wird z. B. dasselbe Beispiel beschrieben – mit der partiellen Konfiguration für `ServiceAccountConfig` im Pullmodus und der partiellen Konfiguration für `SharePointConfig` im Pushmodus.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Gemischte Push- und Pullmodi unter Verwendung von „ConfigurationNames“

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Gemischte Push- und Pullmodi unter Verwendung von „ConfigurationID“

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Beachten Sie, dass der im „Settings“-Block angegebene **RefreshMode** auf „Pull“, aber der **RefreshMode** für die partielle Konfiguration `SharePointConfig` auf „Push“ festgelegt ist.

Benennen Sie die MOF-Konfigurationsdateien und legen Sie sie ab, wie oben für die entsprechenden Aktualisierungsmodi beschrieben.
Rufen Sie `Publish-DSCConfiguration` zum Veröffentlichen der `SharePointConfig`-Teilkonfiguration auf. Warten Sie dann entweder, bis die `ServiceAccountConfig`-Konfiguration vom Pullserver abgerufen wird, oder erzwingen Sie eine Aktualisierung durch das Aufrufen von [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Beispiel für eine ServiceAccountConfig-Teilkonfiguration

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>Beispiel für eine SharePointConfig-Teilkonfiguration

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell DSC (Desired State Configuration): Pullserver](pullServer.md)

[Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md)
