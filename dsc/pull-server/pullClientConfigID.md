---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 5.0 und höher
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401601"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a>Einrichten eines Pull-Clients mithilfe des Konfigurations-ID in PowerShell 5.0 und höher

> Gilt für: Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Vor dem Einrichten eines pullclients festlegen, sollten Sie eine Pull-Server einrichten. Obwohl diese Reihenfolge nicht erforderlich ist, hilft bei der Problembehandlung, und hilft Ihnen, stellen Sie sicher, dass die Registrierung erfolgreich war. Informationen zum Einrichten eines pullservers, können Sie die folgenden Handbüchern:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden. In den folgenden Abschnitten gezeigt, wie einen pullclient mit einem SMB-Freigabe oder ein HTTP-DSC-Pull-Server zu konfigurieren. Wenn des Knotens LCM aktualisiert, wird es an den konfigurierten Speicherort zugewiesene Konfigurationen herunterladen zugreifen. Wenn alle erforderlichen Ressourcen nicht auf dem Knoten vorhanden sind, werden sie automatisch aus dem konfigurierten Speicherort heruntergeladen. Wenn der Knoten mit konfiguriert ist ein [Berichtsserver](reportServer.md), er meldet klicken Sie dann den Status des Vorgangs.

> **Hinweis**: Dieses Thema gilt für PowerShell 5.0. Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md).

## <a name="configure-the-pull-client-lcm"></a>Konfigurieren Sie den LCM-Pull-client

Ausführen von den folgenden Beispielen erstellt einen neuen Ausgabeordner mit dem Namen **PullClientConfigID** und fügt Sie einer MOF-metakonfigurationsdatei vorhanden. In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.

Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird. Beispiel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a>Konfigurations-ID

In den Beispielen unten legt der **ConfigurationID** -Eigenschaft des LCM auf eine **Guid** , wurde zuvor für diesen Zweck erstellt. Der LCM nutzt die **ConfigurationID** zum Auffinden der entsprechenden Konfiguration auf dem Pullserver. Die MOF-Konfigurationsdatei auf dem Pullserver muss den Namen `ConfigurationID.mof` haben, wobei *ConfigurationID* der Wert der **ConfigurationID**-Eigenschaft des LCM des Zielknotens ist. Weitere Informationen finden Sie unter [Konfigurationen veröffentlichen, um einen Pull-Server (v4/v5)](publishConfigs.md).

Sie können einen zufälligen erstellen **Guid** verwenden Sie das Beispiel unten oder mithilfe der [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Weitere Informationen zur Verwendung von **Guids** in Ihrer Umgebung finden Sie unter [Guids planen](/powershell/dsc/secureserver#guids).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Ein Pull-Client zum Herunterladen von Konfigurationen einrichten

Jeder Client muss konfiguriert werden, **Pull** Modus und die Pull-Server-Url angegeben werden, in die Konfiguration gespeichert ist. Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren. Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs. Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).

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

Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver. Die **ServerUrl** gibt die Url der DSC-Pull

### <a name="smb-share"></a>SMB-Freigabe

Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen aus der SMB-Freigabe `\\SMBPullServer\Pull`.

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

Im Skript die **ConfigurationRepositoryShare** -Block definiert die Pull-Server, die in diesem Fall nur eine SMB-Freigabe ist.

## <a name="set-up-a-pull-client-to-download-resources"></a>Richten Sie einen Pull-Client Ressourcen herunterladen

Wenn Sie nur angeben, die **ConfigurationRepositoryWeb** oder **ConfigurationRepositoryShare** -block in Ihrer LCM-Konfiguration (wie im vorherigen Beispiel), der pullclient Ressourcen aus der gleichen der Speicherort abgerufen, die Konfigurationen. Sie können auch separate Standorte für Ressourcen angeben. Um einen Ressourcenspeicherort als separater Server anzugeben, verwenden die **ResourceRepositoryWeb** Block. Verwenden Sie zum Angeben eines Speicherorts für die Ressource als eine SMB-Freigabe der **ResourceRepositoryShare** Block.

> [!NOTE]
> Sie können kombinieren **ConfigurationRepositoryWeb** mit **ResourceRepositoryShare** oder **ConfigurationRepositoryShare** mit **ResourceRepositoryWeb** . Beispiele hierfür sind unten nicht angezeigt.

### <a name="http-dsc-pull-server"></a>HTTP-DSC-Pullserver

Die folgende metakonfiguration konfiguriert einen pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von **CONTOSO-ResourceSrv**.

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

Das folgende Beispiel zeigt eine metakonfiguration, mit dem ein Client zum Abrufen von Konfigurationen aus der SMB-Freigabe eingerichtet `\\SMBPullServer\Configurations`, und Ressourcen aus der SMB-Freigabe `\\SMBPullServer\Resources`.

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

#### <a name="automatically-download-resources-in-push-mode"></a>Herunterladen Sie automatisch, Ressourcen im Modus mithilfe von Push übertragen

Ab PowerShell 5.0 können Ihre pullclients können-Module herunterladen von einer SMB-Freigabe, selbst wenn sie für konfiguriert sind **Push** Modus. Dies ist besonders nützlich in Szenarien, in denen Sie nicht, um eine Pull-Server einzurichten möchten. Die **ResourceRepositoryShare** Block kann verwendet werden, ohne Angabe einer **ConfigurationRepositoryShare**. Das folgende Beispiel zeigt eine metakonfiguration, mit dem ein Client zum Abrufen von Ressourcen aus einer SMB-Dateifreigabe eingerichtet `\\SMBPullServer\Resources`. Wenn der Knoten ist **PUSHED** eine Konfiguration, es werden automatisch herunterladen, alle erforderlichen Ressourcen, aus der angegebenen Freigabe.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Richten Sie einen Pull-Client zum Melden von status

Standardmäßig werden der Knoten Berichte nicht mit einem konfigurierten Pull-Server senden. Sie können für Konfigurationen, Ressourcen und Berichte einen einzigen Pullserver verwenden, allerdings müssen Sie einen **ReportRepositoryWeb**-Block erstellen, um die Berichterstattung einzurichten.

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

Um einen Berichtsserver anzugeben, verwenden Sie einen **ReportRepositoryWeb**-Block. Ein Berichtsserver kann kein SMB-Server sein.
Die folgende Metakonfiguration konfiguriert einen Pullclient zum Abrufen seiner Konfigurationen von **CONTOSO-PullSrv** und seiner Ressourcen von**CONTOSO-ResourceSrv** und Senden von Statusberichten an **CONTOSO-ReportSrv**.

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

Ein Berichtsserver eine SMB-Freigabe nicht möglich.

## <a name="next-steps"></a>Nächste Schritte

Nachdem der Pull-Client konfiguriert wurde, können Sie die folgenden Anleitungen, die nächsten Schritte ausführen:

- [Veröffentlichen von Konfigurationen auf einem Pullserver (v4/v5)](publishConfigs.md)
- [Verpacken und Hochladen von Ressourcen auf einen Pullserver (v4)](package-upload-resources.md)

## <a name="see-also"></a>Weitere Informationen

* [Einrichten eines Pullclients mit Konfigurationsnamen](pullClientConfigNames.md)
