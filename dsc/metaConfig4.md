---
ms.date: 2017-10-12
author: eslesar;mgreenegit
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Windows PowerShell 4.0 DSC – Lokaler Konfigurations-Manager (LCM)"
ms.openlocfilehash: d46862f9ea0f8e3206c596af7232160fc4a97939
ms.sourcegitcommit: 9a5da3f739b1eebb81ede58bd4fc8037bad87224
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2017
---
# <a name="windows-powershell-40-desired-state-configuration-local-configuration-manager-lcm"></a>Windows PowerShell 4.0 DSC – Lokaler Konfigurations-Manager (LCM)

>Gilt für: Windows PowerShell 4.0

Der lokale Konfigurations-Manager (Local Configuration Manager, LCM) ist das Windows PowerShell DSC-Modul (Desired State Configuration, Konfiguration des gewünschten Zustands).
Dieses Modul wird auf allen Zielknoten ausgeführt und ist zuständig für das Aufrufen der Konfigurationsressourcen, die in einem DSC-Konfigurationsskript enthalten sind.
In diesem Thema werden die Eigenschaften des lokalen Konfigurations-Managers (LCM) aufgelistet, und Sie erfahren, wie Sie die LCM-Einstellungen auf einem Zielknoten ändern können.

## <a name="local-configuration-manager-properties"></a>Eigenschaften des lokalen Konfigurations-Managers

Nachstehend sind die LCM-Eigenschaften aufgelistet, die Sie festlegen oder abrufen können.

- **AllowModuleOverwrite**: Steuert, ob neue vom Konfigurationsdienst heruntergeladene Konfigurationen die alten Konfigurationen auf dem Zielknoten überschreiben dürfen. Mögliche Werte sind „True“ und „False“.
- **CertificateID**: Der Fingerabdruck eines Zertifikats zur Sicherung von Anmeldeinformationen, die in einer Konfiguration weitergegeben werden. Weitere Informationen finden Sie unter [Möchten Sie Anmeldeinformationen in Windows PowerShell DSC schützen?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx).
- **ConfigurationID**: Eine GUID, die zum Abrufen einer bestimmten Konfigurationsdatei von einem Pulldienst dient. Die GUID stellt sicher, dass auf die richtige Konfigurationsdatei zugegriffen wird.
- **ConfigurationMode**: Gibt an, wie der lokale Konfigurations-Manager tatsächlich die Konfiguration auf die Zielknoten anwendet. Die folgenden Werte sind möglich:
  - **ApplyOnly**: Bei dieser Option wendet DSC die Konfiguration an und führt nur dann weitere Aktionen durch, wenn eine neue Konfiguration ermittelt wird – entweder indem Sie eine neue Konfiguration direkt an den Zielknoten senden oder indem Sie eine Verbindung mit einem Pulldienst herstellen und DSC bei der Abfrage des Pulldiensts eine neue Konfiguration ermittelt. Wenn die Konfiguration des Zielknotens abweicht, erfolgt keine Aktion.
  - **ApplyAndMonitor**: Bei dieser Standardoption wendet DSC neue Konfigurationen unabhängig davon an, ob diese von Ihnen direkt zum Zielknoten gesendet oder in einem Pulldienst ermittelt werden. Wenn sich im Anschluss die Konfiguration des Zielknotens von der Konfigurationsdatei unterscheidet, meldet DSC die Diskrepanz in Protokollen. Weitere Informationen zur DSC-Protokollierung finden Sie unter [Verwenden von Ereignisprotokollen zum Untersuchen von Fehlern in DSC](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect**: Bei dieser Option wendet DSC neue Konfigurationen unabhängig davon an, ob diese von Ihnen direkt zum Zielknoten gesendet oder in einem Pulldienst erkannt werden. Wenn sich im Anschluss die Konfiguration des Zielknotens von der Konfigurationsdatei unterscheidet, meldet DSC die Diskrepanz in Protokollen. Anschließend wird versucht, die Zielknotenkonfiguration in Übereinstimmung mit der Konfigurationsdatei zu bringen.
- **ConfigurationModeFrequencyMins**: Stellt die Häufigkeit (in Minuten) dar, mit der die Hintergrundanwendung von DSC versucht, die aktuelle Konfiguration auf dem Zielknoten zu implementieren. Der Standardwert ist 15. Dieser Wert kann in Verbindung mit „RefreshMode“ festgelegt werden. Wenn „RefreshMode“ auf PULL festgelegt ist, kontaktiert der Zielknoten den Konfigurationsdienst in einem von „RefreshFrequencyMins“ festgelegten Intervall und lädt die aktuelle Konfiguration herunter. Unabhängig vom Wert von „RefreshMode“ wendet das Konsistenzmodul im von „ConfigurationModeFrequencyMins“ festgelegten Intervall die neueste Konfiguration an, die auf den Zielknoten heruntergeladen wurde. „RefreshFrequencyMins“ muss auf ein Vielfaches in Form einer ganzen Zahl von „ConfigurationModeFrequencyMins“ festgelegt werden.
- **Credential**: Gibt (z.B. mit „Get-Credential“) erforderliche Anmeldeinformationen für den Zugriff auf Remoteressourcen an, um z.B. den Konfigurationsdienst zu kontaktieren.
- **DownloadManagerCustomData**: Stellt ein Array mit benutzerdefinierten Daten dar, die spezifisch für den Download-Manager sind.
- **DownloadManagerName**: Gibt den Namen der Konfiguration und des Moduls des Download-Managers an.
- **RebootNodeIfNeeded**: Bestimmte Konfigurationsänderungen auf einem Zielknoten erfordern ggf. einen Neustart, damit die Änderungen übernommen werden. Bei Festlegen auf **True** startet diese Eigenschaft den Knoten ohne vorherige Warnung neu, sobald die Konfiguration vollständig angewendet wurde. Falls **False** (Standardwert), wird die Konfiguration abgeschlossen, aber der Knoten muss manuell neu gestartet werden, damit die Änderungen wirksam werden.
- **RefreshFrequencyMins**: Wird verwendet, wenn Sie einen Pulldienst eingerichtet haben. Stellt die Häufigkeit (in Minuten) dar, mit der der lokale Konfigurations-Manager einen Pulldienst kontaktiert, um die aktuelle Konfiguration herunterzuladen. Dieser Wert kann in Verbindung mit „ConfigurationModeFrequencyMins“ festgelegt werden. Wenn „RefreshMode“ auf PULL festgelegt ist, kontaktiert der Zielknoten den Pulldienst in einem von „RefreshFrequencyMins“ festgelegten Intervall und lädt die aktuelle Konfiguration herunter. Das Konsistenzmodul wendet im von „ConfigurationModeFrequencyMins“ festgelegten Intervall die neueste Konfiguration an, die auf den Zielknoten heruntergeladen wurde. Wenn „RefreshFrequencyMins“ nicht in Form einer ganzen Zahl auf ein Vielfaches von „ConfigurationModeFrequencyMins“ festgelegt wurde, rundet das System den Wert auf. Der Standardwert ist 30.
- **RefreshMode**: Mögliche Werte sind **Push** (Standard) und **Pull**. Bei der Pushkonfiguration müssen Sie mithilfe eines beliebigen Clientcomputers eine Konfigurationsdatei auf jedem Zielknoten ablegen. Im Pullmodus müssen Sie einen Pulldienst für den lokalen Konfigurations-Manager einrichten, der für den Zugriff auf die Konfigurationsdateien kontaktiert werden muss.

### <a name="example-of-updating-local-configuration-manager-settings"></a>Beispiel der Aktualisierung der Einstellungen des lokalen Konfigurations-Managers

Sie können die Einstellungen des lokalen Konfigurations-Managers auf einem Zielknoten aktualisieren, indem Sie einen **LocalConfigurationManager**-Block dem „node“-Block in einem Konfigurationsskript hinzufügen (siehe das folgende Beispiel).

```powershell
Configuration ExampleConfig
{
    Node “Server001”
    {
        LocalConfigurationManager
        {
            ConfigurationID = "646e48cb-3082-4a12-9fd9-f71b9a562d4e"
            ConfigurationModeFrequencyMins = 45
            ConfigurationMode = "ApplyAndAutocorrect"
            RefreshMode = "Pull"
            RefreshFrequencyMins = 90
            DownloadManagerName = "WebDownloadManager"
            DownloadManagerCustomData = (@{ServerUrl="https://$PullService/psdscpullserver.svc"})
            CertificateID = "71AA68562316FE3F73536F1096B85D66289ED60E"
            Credential = $cred
            RebootNodeIfNeeded = $true
            AllowModuleOverwrite = $false
        }
# One or more resource blocks can be added here
    }
}

# The following line invokes the configuration and creates a file called Server001.meta.mof at the specified path
ExampleConfig -OutputPath "c:\users\public\dsc"
```

Bei Ausführen des Skripts im vorherigen Beispiel wird eine MOF-Datei generiert, die die gewünschten Einstellungen angibt und speichert.
Um die Einstellungen zu übernehmen, können Sie das Cmdlet **Set DscLocalConfigurationManager** verwenden (siehe das folgende Beispiel).

```powershell
Set-DscLocalConfigurationManager -Path "c:\users\public\dsc"
```

> **Hinweis**: Für den **Path**-Parameter müssen Sie den Pfad angeben, den Sie für den **OutputPath**-Parameter angegeben haben, als Sie die Konfiguration im vorherigen Beispiel aufgerufen haben.

Mit dem Cmdlet **Get-DscLocalConfigurationManager** können Sie die aktuellen Einstellungen des lokalen Konfigurations-Managers anzeigen.
Wenn Sie dieses Cmdlet ohne Parameter aufrufen, werden standardmäßig die Einstellungen des lokalen Konfigurations-Manager für den Knoten abgerufen, auf dem er ausgeführt wird.
Um einen anderen Knoten anzugeben, verwenden Sie mit diesem Cmdlet den **CimSession**-Parameter.
