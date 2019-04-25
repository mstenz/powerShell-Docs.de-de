---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Konfigurieren des lokalen Konfigurations-Managers in früheren Versionen von Windows PowerShell
ms.openlocfilehash: cea32c9aa8144bc52f3d44f2ad852f577f6a5e6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079607"
---
# <a name="configuring-the-local-configuration-manager-in-previous-versions-of-windows-powershell"></a>Konfigurieren des lokalen Konfigurations-Managers in früheren Versionen von Windows PowerShell

>Gilt für: Windows PowerShell 4.0

**Informationen, die sich auf Windows PowerShell 5.0 und höher beziehen, finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md).**

Der lokale Konfigurations-Manager (Local Configuration Manager, LCM) ist die Windows PowerShell DSC-Engine (Desired State Configuration, Konfiguration des gewünschten Zustands).
Dieses Modul wird auf allen Zielknoten ausgeführt und ist zuständig für das Aufrufen der Konfigurationsressourcen, die in einem DSC-Konfigurationsskript enthalten sind.
In diesem Thema werden die Eigenschaften des lokalen Konfigurations-Managers (LCM) aufgelistet, und Sie erfahren, wie Sie die LCM-Einstellungen auf einem Zielknoten ändern können.

## <a name="local-configuration-manager-properties"></a>Eigenschaften des lokalen Konfigurations-Managers

Nachstehend sind die LCM-Eigenschaften aufgelistet, die Sie festlegen oder abrufen können.

- **AllowModuleOverwrite:** Steuert, ob neue vom Konfigurationsdienst heruntergeladene Konfigurationen die alten Konfigurationen auf dem Zielknoten überschreiben dürfen. Mögliche Werte sind „True“ und „False“.
- **CertificateID**: Der Fingerabdruck eines Zertifikats zur Sicherung von Anmeldeinformationen, die in einer Konfiguration übergeben werden. Weitere Informationen finden Sie unter [Möchten Sie Anmeldeinformationen in Windows PowerShell DSC schützen?](https://blogs.msdn.microsoft.com/powershell/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/).
- **ConfigurationID:** Eine GUID, die zum Abrufen einer bestimmten Konfigurationsdatei von einem Pulldienst dient. Die GUID stellt sicher, dass auf die richtige Konfigurationsdatei zugegriffen wird.
- **ConfigurationMode:** Gibt an, wie der lokale Konfigurations-Manager tatsächlich die Konfiguration auf die Zielknoten anwendet. Die folgenden Werte sind möglich:
  - **ApplyOnly**: Bei dieser Option wendet DSC die Konfiguration an und führt nur dann weitere Aktionen durch, wenn eine neue Konfiguration ermittelt wird – entweder indem Sie eine neue Konfiguration direkt an den Zielknoten senden oder indem Sie eine Verbindung mit einem Pulldienst herstellen und DSC bei der Abfrage des Pulldiensts eine neue Konfiguration ermittelt. Wenn die Konfiguration des Zielknotens abweicht, erfolgt keine Aktion.
  - **ApplyAndMonitor**: Bei dieser Standardoption wendet DSC neue Konfigurationen unabhängig davon an, ob diese von Ihnen direkt zum Zielknoten gesendet oder in einem Pulldienst ermittelt werden. Wenn sich im Anschluss die Konfiguration des Zielknotens von der Konfigurationsdatei unterscheidet, meldet DSC die Diskrepanz in Protokollen. Weitere Informationen zur DSC-Protokollierung finden Sie unter [Verwenden von Ereignisprotokollen zum Untersuchen von Fehlern in DSC](http://blogs.msdn.com/b/powershell/archive/2014/01/03/using-event-logs-to-diagnose-errors-in-desired-state-configuration.aspx).
  - **ApplyAndAutoCorrect:** Bei dieser Option wendet DSC neue Konfigurationen unabhängig davon an, ob diese von Ihnen direkt zum Zielknoten gesendet oder in einem Pulldienst erkannt werden. Wenn sich im Anschluss die Konfiguration des Zielknotens von der Konfigurationsdatei unterscheidet, meldet DSC die Diskrepanz in Protokollen. Anschließend wird versucht, die Zielknotenkonfiguration in Übereinstimmung mit der Konfigurationsdatei zu bringen.
- **ConfigurationModeFrequencyMins:** Die Häufigkeit (in Minuten), mit der die DSC-Hintergrundanwendung versucht, die aktuelle Konfiguration auf dem Zielknoten anzuwenden. Der Standardwert ist 15. Dieser Wert kann in Verbindung mit „RefreshMode“ festgelegt werden. Wenn „RefreshMode“ auf PULL festgelegt ist, kontaktiert der Zielknoten den Konfigurationsdienst in einem von „RefreshFrequencyMins“ festgelegten Intervall und lädt die aktuelle Konfiguration herunter. Unabhängig vom Wert von „RefreshMode“ wendet die Konsistenz-Engine im von „ConfigurationModeFrequencyMins“ festgelegten Intervall die neueste Konfiguration an, die auf den Zielknoten heruntergeladen wurde. „RefreshFrequencyMins“ muss auf ein Vielfaches in Form einer ganzen Zahl von „ConfigurationModeFrequencyMins“ festgelegt werden.
- **Credential:** Gibt (z. B. mit „Get-Credential“) erforderliche Anmeldeinformationen für den Zugriff auf Remoteressourcen an, um z. B. den Konfigurationsdienst zu kontaktieren.
- **DownloadManagerCustomData:** Stellt ein Array mit benutzerdefinierten Daten dar, die spezifisch für den Download-Manager sind.
- **DownloadManagerName:** Gibt den Namen der Konfiguration und des Moduls des Download-Managers an.
- **RebootNodeIfNeeded:** Legen Sie für diese Option `$true` fest, um Ressourcen das Neustarten des Knotens mithilfe des `$global:DSCMachineStatus`-Flags zu ermöglichen. Andernfalls müssen Sie den Knoten für jede Konfiguration manuell neu starten, die dies erfordert. Der Standardwert ist `$false`. Um diese Einstellung zu verwenden, wenn eine Neustartbedingung von einer anderen Komponente als von DSC in Kraft gesetzt wird (z.B. Windows Installer), kombinieren Sie diese Einstellung mit dem Modul [xPendingReboot](https://github.com/powershell/xpendingreboot).
- **RefreshFrequencyMins:** Wird verwendet, wenn Sie einen Pulldienst eingerichtet haben. Stellt die Häufigkeit (in Minuten) dar, mit der der lokale Konfigurations-Manager einen Pulldienst kontaktiert, um die aktuelle Konfiguration herunterzuladen. Dieser Wert kann in Verbindung mit „ConfigurationModeFrequencyMins“ festgelegt werden. Wenn „RefreshMode“ auf PULL festgelegt ist, kontaktiert der Zielknoten den Pulldienst in einem von „RefreshFrequencyMins“ festgelegten Intervall und lädt die aktuelle Konfiguration herunter. Die Konsistenz-Engine wendet im von „ConfigurationModeFrequencyMins“ festgelegten Intervall die neueste Konfiguration an, die auf den Zielknoten heruntergeladen wurde. Wenn „RefreshFrequencyMins“ nicht in Form einer ganzen Zahl auf ein Vielfaches von „ConfigurationModeFrequencyMins“ festgelegt wurde, rundet das System den Wert auf. Der Standardwert ist 30.
- **RefreshMode:** Mögliche Werte sind **Push** (Standard) und **Pull**. Bei der Pushkonfiguration müssen Sie mithilfe eines beliebigen Clientcomputers eine Konfigurationsdatei auf jedem Zielknoten ablegen. Im Pullmodus müssen Sie einen Pulldienst für den lokalen Konfigurations-Manager einrichten, der für den Zugriff auf die Konfigurationsdateien kontaktiert werden muss.

> [!NOTE]
> Der LCM startet den **ConfigurationModeFrequencyMins**-Zyklus auf Grundlage folgender Ereignisse:
>
> - Mithilfe von `Set-DscLocalConfigurationManager` wird eine neue Metakonfiguration angewendet
> - Der Computer wird neu gestartet
>
> Bei Bedingungen, unter denen es beim Timerprozess zu einem Absturz kommt, der innerhalb von 30 Sekunden erkannt wird, wird der Zyklus neu gestartet.
> Ein gleichzeitiger Vorgang könnte den Start des Zyklus verzögern; wenn die Dauer dieses Vorgangs länger ist als die konfigurierte Zyklushäufigkeit, startet der nächste Timer nicht.
>
> Beispiel: Die Metakonfiguration ist auf eine Pullhäufigkeit von 15 Minuten konfiguriert, und ein Pull wird zum Zeitpunkt t1 ausgeführt.  Der Knoten kann seine Aufgaben 16 Minuten lang nicht beenden.  Der erste 15-Minuten-Zyklus wird ignoriert, und der nächste Pull wird zum Zeitpunkt t1+15+15 ausgeführt.

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

> [!NOTE]
> Für den **Path**-Parameter müssen Sie denselben Pfad angeben, den Sie für den **OutputPath**-Parameter angegeben haben, als Sie die Konfiguration im vorherigen Beispiel aufgerufen haben.

Mit dem Cmdlet **Get-DscLocalConfigurationManager** können Sie die aktuellen Einstellungen des lokalen Konfigurations-Managers anzeigen.
Wenn Sie dieses Cmdlet ohne Parameter aufrufen, werden standardmäßig die Einstellungen des lokalen Konfigurations-Manager für den Knoten abgerufen, auf dem er ausgeführt wird.
Um einen anderen Knoten anzugeben, verwenden Sie mit diesem Cmdlet den **CimSession**-Parameter.
