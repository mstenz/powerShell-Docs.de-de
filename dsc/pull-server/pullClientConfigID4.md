---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401757"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a>Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 4.0

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Vor dem Einrichten eines pullclients festlegen, sollten Sie eine Pull-Server einrichten. Obwohl diese Reihenfolge nicht erforderlich ist, hilft bei der Problembehandlung, und hilft Ihnen, stellen Sie sicher, dass die Registrierung erfolgreich war. Informationen zum Einrichten eines pullservers, können Sie die folgenden Handbüchern:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden. In den folgenden Abschnitten gezeigt, wie einen pullclient mit einem SMB-Freigabe oder ein HTTP-DSC-Pull-Server zu konfigurieren. Wenn des Knotens LCM aktualisiert, wird es an den konfigurierten Speicherort zugewiesene Konfigurationen herunterladen zugreifen. Wenn alle erforderlichen Ressourcen nicht auf dem Knoten vorhanden sind, werden sie automatisch aus dem konfigurierten Speicherort heruntergeladen. Wenn der Knoten mit konfiguriert ist ein [Berichtsserver](reportServer.md), er meldet klicken Sie dann den Status des Vorgangs.

## <a name="configure-the-pull-client-lcm"></a>Konfigurieren Sie den LCM-Pull-client

Ausführen von den folgenden Beispielen erstellt einen neuen Ausgabeordner mit dem Namen **PullClientConfigID** und fügt Sie einer MOF-metakonfigurationsdatei vorhanden. In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.

Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird. Beispiel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID

In den Beispielen unten Satz der **ConfigurationID** -Eigenschaft des LCM auf eine **Guid** , wurde zuvor für diesen Zweck erstellt. Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver. Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist. Weitere Informationen finden Sie unter [Konfigurationen veröffentlichen, um einen Pull-Server (v4/v5)](publishConfigs.md).

Sie können einen zufälligen erstellen **Guid** verwenden das folgende Beispiel.

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a>Ein Pull-Client zum Herunterladen von Konfigurationen einrichten

Jeder Client muss konfiguriert werden, **Pull** Modus und die Pull-Server-Url angegeben werden, in die Konfiguration gespeichert ist. Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren. Zum Konfigurieren des LCM müssen Sie eine besondere Art von Konfiguration erstellen, mit einem **"localconfigurationmanager"** Block. Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig4.md).

## <a name="http-dsc-pull-server"></a>HTTP-DSC-Pullserver

Wenn der Pull-Server als Webdienst eingerichtet ist, legen Sie die **DownloadManagerName** zu **WebDownloadManager**. Die **WebDownloadManager** erfordert die Angabe ein **ServerUrl** auf die **DownloadManagerCustomData** Schlüssel. Sie können auch angeben, einen Wert für **AllowUnsecureConnection**, wie im folgenden Beispiel. Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „PullServer“.

```powershell
Configuration PullClientConfigId
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
PullClientConfigId -Output "."
```

## <a name="smb-share"></a>SMB-Freigabe

Wenn der Pull-Server als SMB-Dateifreigabe, anstatt eines Webdiensts eingerichtet ist, legen Sie die **DownloadManagerName** zu **DscFileDownloadManager** anstelle der **WebDownLoadManager**. Die **DscFileDownloadManager** erfordert die Angabe einer **SourcePath** -Eigenschaft in der **DownloadManagerCustomData**. Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einer SMB-Freigabe namens „SmbDscShare“ auf einem Server namens „CONTOSO-SERVER“.

```powershell
Configuration PullClientConfigId
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
PullClientConfigId -Output "."
```

## <a name="next-steps"></a>Nächste Schritte

Nachdem der Pull-Client konfiguriert wurde, können Sie die folgenden Anleitungen, die nächsten Schritte ausführen:

- [Veröffentlichen von Konfigurationen auf einem Pullserver (v4/v5)](publishConfigs.md)
- [Verpacken und Hochladen von Ressourcen auf einen Pullserver (v4)](package-upload-resources.md)

## <a name="see-also"></a>Weitere Informationen

- [Einrichten eines DSC-webpullservers](pullServer.md)
- [Einrichten eines DSC-SMB-Pullservers](pullServerSMB.md)
