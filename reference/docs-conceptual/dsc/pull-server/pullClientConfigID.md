---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Einrichten eines Pullclients mit Konfigurations-IDs in PowerShell 5.0 und höher
ms.openlocfilehash: a014e04fc5fbf2e813d9b0d79f39fe5aa3836f86
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500733"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Einrichten eines Pullclients mit Konfigurations-IDs in PowerShell 5.0 und höher

> Gilt für: Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Bevor Sie einen Pullclient einrichten, sollten Sie einen Pullserver einrichten. Diese Reihenfolge ist zwar nicht erforderlich, jedoch hilft sie bei der Problembehandlung und unterstützt Sie dabei, sicherzustellen, dass die Registrierung erfolgreich war. Sie können eine der folgenden Führungslinien zum Einrichten eines Pullservers verwenden:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden. In den folgenden Abschnitten wird veranschaulicht, wie Sie einen Pullclient mit einer SMB-Freigabe oder einem HTTP-DSC-Pullserver konfigurieren. Wenn der lokale Konfigurations-Manager des Knotens aktualisiert wird, wendet dieser sich an den konfigurierten Speicherort, um zugewiesene Konfigurationen herunterzuladen. Wenn erforderliche Ressourcen nicht auf dem Knoten vorhanden sind, werden diese automatisch vom konfigurierten Speicherort heruntergeladen. Wenn der Knoten mit einem [Berichtsserver](reportServer.md) konfiguriert wurde, wird anschließend der Status des Vorgangs gemeldet.

> [!NOTE]
> Dieser Artikel gilt nur für PowerShell 5.0. Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).

## <a name="configure-the-pull-client-lcm"></a>Konfigurieren des lokalen Konfigurations-Managers für den Pullclient

Durch Ausführen der folgenden Beispiele wird ein neuer Ausgabeordner namens **PullClientConfigID** erstellt, und in diesem wird eine MOF-Datei mit der Metakonfiguration platziert. In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.

Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird. Beispiel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID

In den folgenden Beispielen wird die Eigenschaft **ConfigurationID** des lokalen Konfigurations-Managers auf eine **GUID** festgelegt, die zuvor zu diesem Zweck erstellt wurde. Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver. Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der Eigenschaft **ConfigurationID** des LCM des Zielknotens ist. Weitere Informationen finden Sie unter [Publish Configurations to a Pull Server (v4/v5) (Veröffentlichen von Konfigurationen für einen Pullserver (PowerShell 4.0 und 5.0))](publishConfigs.md).

Sie können eine zufällige **GUID** mithilfe des folgenden Beispiels oder des Cmdlets [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) erstellen.

```powershell
[System.Guid]::NewGuid()
```

Weitere Informationen zur Verwendung von **GUIDs** in Ihrer Umgebung finden Sie unter [Plan for Guids (Planen von GUIDs)](secureserver.md#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Einrichten eines Pullclients zum Herunterladen von Konfigurationen

Jeder Client muss im Modus **Pull** konfiguriert werden und mit der Pullserver-URL zum Speicherort der Konfiguration versehen werden. Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren. Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs. Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).

### <a name="http-dsc-pull-server"></a>HTTP-DSC-Pullserver

Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver. **ServerUrl** gibt die URL für den DSC-Pull an.

### <a name="smb-share"></a>SMB-Freigabe

Mit dem folgenden Skript wird der lokale Konfigurations-Manager zum Pullen von Konfigurationen aus der SMB-Freigabe `\\SMBPullServer\Pull` konfiguriert.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

Der **ConfigurationRepositoryShare**-Block im Skript definiert den Pullserver, bei dem es sich in diesem Fall lediglich um eine SMB-Freigabe handelt.

## <a name="set-up-a-pull-client-to-download-resources"></a>Einrichten eines Pullclients zum Herunterladen von Ressourcen

Wenn Sie nur den **ConfigurationRepositoryWeb**- oder den **ConfigurationRepositoryShare**-Block in Ihrer Konfiguration für den lokalen Konfigurations-Manager angeben (wie in den vorherigen Beispielen), ruft der Pullclient die Ressourcen vom gleichen Speicherort wie die Konfigurationen per Pull ab. Sie können auch einen separaten Speicherort für Ressourcen festlegen. Verwenden Sie den **ResourceRepositoryWeb**-Block zum Festlegen eines Ressourcenspeicherorts als separater Server. Verwenden Sie den **ResourceRepositoryShare**-Block zum Festlegen eines Ressourcenspeicherorts als SMB-Freigabe.

> [!NOTE]
> Sie können **ConfigurationRepositoryWeb** mit **ResourceRepositoryShare** oder **ConfigurationRepositoryShare** mit **ResourceRepositoryWeb** kombinieren. Hierfür werden keine Beispiele gezeigt.

### <a name="http-dsc-pull-server"></a>HTTP-DSC-Pullserver

Mit der folgenden Metakonfiguration wird ein Pullclient zum Abrufen der Konfigurationen von **CONTOSO-PullSrv** und der Ressourcen von **CONTOSO-ResourceSrv** konfiguriert.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB-Freigabe

Im folgenden Beispiel wird eine Metakonfiguration gezeigt, die einen Client zum Pullen von Konfigurationen aus der SMB-Freigabe `\\SMBPullServer\Configurations` und Ressourcen aus der SMB-Freigabe `\\SMBPullServer\Resources` einrichtet.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a>Automatisches Herunterladen von Ressourcen im Pushmodus

Ab PowerShell 5.0 können Ihre Pullclients Module aus einer SMB-Freigabe auch dann herunterladen, wenn sie für den **Pushmodus** konfiguriert sind. Dies ist insbesondere in Szenarios hilfreich, in denen Sie keinen Pullserver einrichten möchten. Der **ResourceRepositoryShare**-Block kann ohne Festlegen von **ConfigurationRepositoryShare** verwendet werden. Im folgenden Beispiel wird eine Metakonfiguration gezeigt, die einen Client zum Pullen von Ressourcen aus der SMB-Freigabe `\\SMBPullServer\Resources` einrichtet. Wenn der Knoten eine Konfiguration per **PUSH** übertragen hat, lädt er automatisch alle erforderlichen Ressourcen von der angegebenen Freigabe herunter.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a>Einrichten eines Pullclients zum Berichten des Status

Knoten senden standardmäßig keine Berichte an einen konfigurierten Pullserver. Sie können für Konfigurationen, Ressourcen und Berichte einen einzigen Pullserver verwenden, allerdings müssen Sie einen **ReportRepositoryWeb**-Block erstellen, um die Berichterstattung einzurichten.

### <a name="http-dsc-pull-server"></a>HTTP-DSC-Pullserver

Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

Um einen Berichtsserver anzugeben, verwenden Sie einen **ReportRepositoryWeb**-Block. Ein Berichtsserver kann kein SMB-Server sein. Die folgende Metakonfiguration konfiguriert einen Pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von **CONTOSO-ResourceSrv** und zum Senden von Statusberichten an **CONTOSO-ReportSrv**:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a>SMB-Freigabe

Ein Berichtsserver kann keine SMB-Freigabe sein.

## <a name="next-steps"></a>Nächste Schritte

Sobald der Pullclient konfiguriert wurde, können Sie die folgenden Leitfäden zum Durchführen der nächsten Schritte verwenden:

- [Veröffentlichen von Konfigurationen auf einem Pullserver (v4/v5)](publishConfigs.md)
- [Verpacken und Hochladen von Ressourcen auf einen Pullserver (v4)](package-upload-resources.md)

## <a name="see-also"></a>Weitere Informationen

* [Einrichten eines Pullclients mit Konfigurationsnamen](pullClientConfigNames.md)
