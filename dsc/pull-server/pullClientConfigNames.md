---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Einrichten eines Pullclients mit Konfigurationsnamen in PowerShell 5.0 und höher
ms.openlocfilehash: d591e2a757130ccecaf4eaf9f363f607fca82b93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079386"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a>Einrichten eines Pullclients mit Konfigurationsnamen in PowerShell 5.0 und höher

> Gilt für: Windows PowerShell 5.0

> [!IMPORTANT]
> Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden. Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.

Bevor Sie einen Pullclient einrichten, sollten Sie einen Pullserver einrichten. Diese Reihenfolge ist zwar nicht erforderlich, jedoch hilft sie bei der Problembehandlung und unterstützt Sie dabei, sicherzustellen, dass die Registrierung erfolgreich war. Sie können eine der folgenden Führungslinien zum Einrichten eines Pullservers verwenden:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden. In den folgenden Abschnitten wird veranschaulicht, wie Sie einen Pullclient mit einer SMB-Freigabe oder einem HTTP-DSC-Pullserver konfigurieren. Wenn der lokale Konfigurations-Manager des Knotens aktualisiert wird, wendet dieser sich an den konfigurierten Speicherort, um zugewiesene Konfigurationen herunterzuladen. Wenn erforderliche Ressourcen nicht auf dem Knoten vorhanden sind, werden diese automatisch vom konfigurierten Speicherort heruntergeladen. Wenn der Knoten mit einem [Berichtsserver](reportServer.md) konfiguriert wurde, wird anschließend der Status des Vorgangs gemeldet.

> [!NOTE]
> Dieser Artikel gilt nur für PowerShell 5.0.
> Informationen zum Einrichten eines Pullclients in PowerShell 4.0 finden Sie unter [Set up a pull client using configuration ID in PowerShell 4.0 (Einrichten eines Pullclients mithilfe der Konfigurations-ID in PowerShell 4.0)](pullClientConfigID4.md).

## <a name="configure-the-pull-client-lcm"></a>Konfigurieren des lokalen Konfigurations-Managers für den Pullclient

Durch Ausführen der folgenden Beispiele wird ein neuer Ausgabeordner namens **PullClientConfigName** erstellt, und in diesem wird eine MOF-Datei mit der Metakonfiguration platziert. In diesem Fall heißt die MOF-Datei mit der Metakonfiguration `localhost.meta.mof`.

Rufen Sie zum Anwenden der Konfiguration das Cmdlet **Set DscLocalConfigurationManager** auf, wobei **Path** auf den Speicherort der MOF-Datei mit der Metakonfiguration festgelegt wird. Beispiel:

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a>Konfigurationsname

In den folgenden Beispielen wird die Eigenschaft **ConfigurationName** des lokalen Konfigurations-Managers auf den Namen einer zuvor kompilierten Konfiguration festgelegt, die zu diesem Zweck erstellt wurde. Der lokale Konfigurations-Manager verwenden die Eigenschaft **ConfigurationName**, um die entsprechende Konfiguration auf dem Pullserver zu finden. Die MOF-Datei für die Konfiguration auf dem Pullserver muss den Namen `<ConfigurationName>.mof` haben, in diesem Fall lautet er „ClientConfig.mof“. Weitere Informationen finden Sie unter [Publish Configurations to a Pull Server (v4/v5) (Veröffentlichen von Konfigurationen für einen Pullserver (PowerShell 4.0 und 5.0))](publishConfigs.md).

## <a name="set-up-a-pull-client-to-download-configurations"></a>Einrichten eines Pullclients zum Herunterladen von Konfigurationen

Jeder Client muss im Modus **Pull** konfiguriert werden und mit der Pullserver-URL zum Speicherort der Konfiguration versehen werden. Hierzu müssen Sie den lokalen Konfigurations-Manager (LCM) mit den benötigten Informationen konfigurieren. Zum Konfigurieren des LCM erstellten Sie eine besondere Art von Konfiguration unter Angabe des **DSCLocalConfigurationManager**-Attributs. Weitere Informationen zum Konfigurieren des LCM finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](../managing-nodes/metaConfig.md).

Das folgende Skript konfiguriert den LCM zum Abrufen von Konfigurationen von einem Pullserver namens „CONTOSO-PullSrv“.

- Im Skript definiert der **ConfigurationRepositoryWeb**-Block den Pullserver. Die **ServerURL**-Eigenschaft gibt den Endpunkt für den Pullserver an.

- Die **RegistrationKey**-Eigenschaft ist ein freigegebener Schlüssel zwischen allen Clientknoten für einen Pullserver und dem jeweiligen Pullserver. Der gleiche Wert wird in einer Datei auf dem Pullserver gespeichert.
  > [!NOTE]
  > Registrierungsschlüssel funktionieren nur mit **Webpullservern**. Bei einem **SMB**-Pullserver müssen Sie **ConfigurationID** weiterhin verwenden.
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

## <a name="set-up-a-pull-client-to-download-resources"></a>Einrichten eines Pullclients zum Herunterladen von Ressourcen

Wenn Sie nur den **ConfigurationRepositoryWeb**- oder den **ConfigurationRepositoryShare**-Block in Ihrer Konfiguration für den lokalen Konfigurations-Manager angeben (wie im vorherigen Beispiel), ruft der Pullclient die Ressourcen vom gleichen Speicherort per Pull ab, an dem Ihre MOF-Dateien gespeichert sind. Sie können auch andere Speicherorte angeben, von denen Clients Ressourcen herunterladen können. Um einen Ressourcenserver anzugeben, verwenden Sie entweder einen **ResourceRepositoryWeb**-Block (für einen Webpullserver) oder einen **ResourceRepositoryShare**-Block (für einen SMB-Pullserver).

Im folgenden Beispiel wird eine Metakonfiguration gezeigt, die einen Client zum Herunterladen von Konfigurationen von einem Pullserver und Ressourcen aus einer SMB-Freigabe einrichtet.

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

## <a name="set-up-a-pull-client-to-report-status"></a>Einrichten eines Pullclients zum Berichten des Status

Sie können einen einzelnen Pullserver für Konfigurationen, Ressourcen und Berichte verwenden. Die Berichterstellung ist standardmäßig nicht für Clients konfiguriert. Sie müssen einen **ReportRepositoryWeb**-Block erstellen, um einen Client zum Berichten des Status zu konfigurieren. Das folgenden Beispiel zeigt eine Metakonfiguration, mit der einen Client so eingerichtet wird, dass Konfigurationen und Ressourcen per Pull von einem Pullserver abgerufen und Berichtsdaten an denselben Pullserver gesendet werden.

> [!NOTE]
> Ein Berichtsserver kann keine SMB-Freigabe sein.

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
