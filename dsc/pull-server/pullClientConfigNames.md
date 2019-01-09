---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pull-Clients mithilfe von Konfigurationsnamen in PowerShell 5.0 und höher
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401787"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Einrichten eines Pull-Clients mithilfe von Konfigurationsnamen in PowerShell 5.0 und höher

> Gilt für: Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Vor dem Einrichten eines pullclients festlegen, sollten Sie eine Pull-Server einrichten. Obwohl diese Reihenfolge nicht erforderlich ist, hilft bei der Problembehandlung, und hilft Ihnen, stellen Sie sicher, dass die Registrierung erfolgreich war. Informationen zum Einrichten eines pullservers, können Sie die folgenden Handbüchern:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden. In den folgenden Abschnitten gezeigt, wie einen pullclient mit einem SMB-Freigabe oder ein HTTP-DSC-Pull-Server zu konfigurieren. Wenn des Knotens LCM aktualisiert, wird es an den konfigurierten Speicherort zugewiesene Konfigurationen herunterladen zugreifen. Wenn alle erforderlichen Ressourcen nicht auf dem Knoten vorhanden sind, werden sie automatisch aus dem konfigurierten Speicherort heruntergeladen. Wenn der Knoten mit konfiguriert ist ein [Berichtsserver](reportServer.md), er meldet klicken Sie dann den Status des Vorgangs.

> **Hinweis**: Dieses Thema gilt für PowerShell 5.0.
Informationen zum Einrichten eines pullclients in PowerShell 4.0 finden Sie unter [Einrichten eines pullclients mithilfe der Konfigurations-ID in PowerShell 4.0](pullClientConfigID4.md)

## <a name="configure-the-pull-client-lcm"></a>Konfigurieren Sie den LCM-Pull-client

Ausführen von den folgenden Beispielen erstellt einen neuen Ausgabeordner mit dem Namen **PullClientConfigName** und fügt Sie einer MOF-metakonfigurationsdatei vorhanden. In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.

Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird. Beispiel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Konfigurationsname

In den Beispielen unten legt der **ConfigurationName** -Eigenschaft des LCM auf den Namen einer zuvor kompilierte Konfiguration für diesen Zweck erstellt. Die **ConfigurationName** der LCM nutzt zum Auffinden der entsprechenden Konfiguration auf dem pullserver. MOF-Konfigurationsdatei auf dem pullserver muss den Namen `<ConfigurationName>.mof`, in diesem Fall "ClientConfig.mof". Weitere Informationen finden Sie unter [Konfigurationen veröffentlichen, um einen Pull-Server (v4/v5)](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Ein Pull-Client zum Herunterladen von Konfigurationen einrichten

Jeder Client muss konfiguriert werden, **Pull** Modus und die Pull-Server-Url angegeben werden, in die Konfiguration gespeichert ist. Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren. Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs. Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).

Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“.

- Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver. Die **ServerURL**-Eigenschaft gibt den Endpunkt für den Pullserver an.

- Die **RegistrationKey**-Eigenschaft ist ein freigegebener Schlüssel zwischen allen Clientknoten für einen Pullserver und dem jeweiligen Pullserver. Der gleiche Wert wird in einer Datei auf dem Pullserver gespeichert.
  > **Hinweis**: Registrierungsschlüssel funktionieren nur mit **Web** pullservern. Bei einem **SMB**-Pullserver müssen Sie **ConfigurationID** weiterhin verwenden.
  > Informationen zum Konfigurieren eines Pullservers unter Verwendung von **ConfigurationID** finden Sie unter [Einrichten eines Pullclients mithilfe der Konfigurations-ID](pullClientConfigId.md).

- Die **ConfigurationNames**-Eigenschaft ist ein Array, das die Namen der Konfigurationen angibt, die für den Clientknoten vorgesehen sind.
  >**Hinweis:** Bei Angabe mehrerer Werte unter **ConfigurationNames** müssen Sie auch **PartialConfiguration**-Blöcke in Ihrer Konfiguration angeben.
  >Informationen zu partiellen Konfigurationen finden Sie unter [PowerShell DSC – Teilkonfigurationen](partialConfigs.md).

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a>Richten Sie einen Pull-Client Ressourcen herunterladen

Wenn Sie nur angeben einer **ConfigurationRepositoryWeb** oder **ConfigurationRepositoryShare** -block in Ihrer LCM-Konfiguration (wie im vorherigen Beispiel), der pullclient Ressourcen aus derselben der Speicherort, in dem Ihre "MOF"-Dateien gespeichert werden. Sie können auch angeben, Speicherorte, in denen Clients die Ressourcen herunterladen können. Um einen Ressourcenserver anzugeben, verwenden Sie entweder einen **ResourceRepositoryWeb**-Block (für einen Webpullserver) oder einen **ResourceRepositoryShare**-Block (für einen SMB-Pullserver).

Das folgende Beispiel zeigt eine metakonfiguration, mit dem ein Client zum Herunterladen von Konfigurationen von einem Pull-Server und Ressourcen von einer SMB-Freigabe eingerichtet.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a>Richten Sie einen Pull-Client zum Melden von status

Sie können einen einzigen pullserver für Konfigurationen, Ressourcen und Berichte verwenden. Berichterstellung ist nicht für Clients standardmäßig konfiguriert. Um einen Client zur Berichtstatus konfigurieren zu können, müssen Sie erstellen eine **ReportRepositoryWeb** Block. Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.

> [!NOTE]
> Ein Berichtsserver eine SMB-Freigabe nicht möglich.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a>Weitere Informationen

* [Einrichten eines Pullclients mit Konfigurations-ID](PullClientConfigNames.md)
* [Einrichten eines DSC-Webpullservers](pullServer.md)
