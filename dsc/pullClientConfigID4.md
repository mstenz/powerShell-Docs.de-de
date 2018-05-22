---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID in PowerShell 4.0
ms.openlocfilehash: f9bea92f1a2dce94792d72e03bef884d2729f3c0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a>Einrichten eines DSC-Pullclients mithilfe einer Konfigurations-ID in PowerShell 4.0

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Jeder Zielknoten muss angewiesen werden, den Pullmodus zu verwenden. Außerdem muss die URL angegeben werden, unter der der Pullserver zum Abrufen von Konfigurationen kontaktiert werden kann. Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren. Zum Konfigurieren des LCM müssen Sie einen besonderen Typ von Konfiguration erstellen, die als „Metakonfiguration“ bezeichnet wird. Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Windows PowerShell 4.0 DSC – Lokaler Konfigurations-Manager](metaConfig4.md).

Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „PullServer“:

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

Im Skript übergibt **DownloadManagerCustomData** die URL des Pullservers und lässt (bei diesem Beispiel) eine unsichere Verbindung zu.

Nachdem das Skript ausgeführt wurde, erstellt es einen neuen Ausgabeordner mit dem Namen **SimpleMetaConfigurationForPull**, der eine MOF-Datei mit der Metakonfiguration enthält.

Um die Konfiguration anzuwenden, verwenden Sie das Cmdlet **Set DscLocalConfigurationManager** mit Parametern für **ComputerName** (verwenden Sie „localhost“) und **Path** (der Pfad zum Speicherort der Datei „localhost.meta.mof“ für den Zielknoten). Beispiel:
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID
Das Skript legt die **ConfigurationID**-Eigenschaft des LCM auf eine GUID fest, die zuvor für diesen Zweck erstellt wurde (Sie können eine GUID mit dem Cmdlet **New-Guid** erstellen). Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver. Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist.

## <a name="pulling-from-an-smb-server"></a>Abrufen per Pull von einem SMB-Server

Wenn der Pullserver nicht als Webdienst, sondern als SMB-Dateifreigabe konfiguriert wurde, legen Sie **DscFileDownloadManager** anstelle von **WebDownLoadManager** fest.
**DscFileDownloadManager** verwendet eine **SourcePath**-Eigenschaft anstelle von **ServerUrl**. Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einer SMB-Freigabe namens „SmbDscShare“ auf einem Server namens „CONTOSO-SERVER“:

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a>Weitere Informationen

- [Einrichten eines DSC-Webpullservers](pullServer.md)
- [Einrichten eines DSC-SMB-Pullservers](pullServerSMB.md)