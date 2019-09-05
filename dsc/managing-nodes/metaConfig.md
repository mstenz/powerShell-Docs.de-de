---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Konfigurieren des lokalen Konfigurations-Managers
ms.openlocfilehash: 42544036d87fcea3189fd6d2e55579fe87f137e1
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215389"
---
# <a name="configuring-the-local-configuration-manager"></a>Konfigurieren des lokalen Konfigurations-Managers

> Gilt für: Windows PowerShell 5.0

Der lokale Konfigurations-Manager (Local Configuration Manager, LCM) ist die Engine von DSC (Desired State Configuration, Konfiguration des gewünschten Zustands).
Der LCM wird auf allen Zielknoten ausgeführt und ist zuständig für das Analysieren und Anwenden von Konfigurationen, die zum Knoten gesendet werden.
Dieses Modul ist auch für verschiedene andere DSC-Aspekte zuständig, wie z. B. die folgenden.

- Bestimmen des Aktualisierungsmodus (Push- oder Pullmodus).
- Angeben, wie oft ein Knoten Konfigurationen abruft und anwendet.
- Verknüpfen des Knotens mit dem Pulldienst.
- Angeben von Teilkonfigurationen.

Sie verwenden eine spezielle Art von Konfiguration zum Konfigurieren des LCM, um jedes dieser Verhalten anzugeben.
In den folgenden Abschnitten wird beschrieben, wie der LCM konfiguriert wird.

Mit Windows PowerShell 5.0 wurden neue Einstellungen für das Verwalten von lokalen Konfigurations-Managern eingeführt.
Informationen zum Konfigurieren des LCMs in Windows PowerShell 4.0 finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers in früheren Versionen von Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Schreiben und Anwenden einer LCM-Konfiguration

Zum Konfigurieren des LCM müssen Sie einen besonderen Typ von Konfiguration zur Anwendung von LCM-Einstellungen erstellen und ausführen.
Zum Angeben der LCM-Konfiguration verwenden Sie das „DscLocalConfigurationManager“-Attribut.
Das folgende Beispiel zeigt eine einfache Konfiguration, die den LCM auf den Pushmodus festgelegt.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

Der Prozess zum Anwenden von Einstellungen auf LCM ähnelt dem Anwenden einer DSC-Konfiguration.
Sie erstellen eine LCM-Konfiguration, kompilieren sie in einer MOF-Datei und wenden sie auf den Knoten an.
Im Gegensatz zu DSC-Konfigurationen wird eine LCM-Konfiguration nicht durch Aufrufen des Cmdlets [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) angewendet.
Stattdessen rufen Sie [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) auf und geben dabei den Pfad zur MOF-Datei mit der LCM-Konfiguration als Parameter an.
Nach dem Anwenden der LCM-Konfiguration können Sie die Eigenschaften des LCM durch Aufrufen des Cmdlets [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) anzeigen.

Eine LCM-Konfiguration kann nur Blöcke für eine begrenzte Menge von Ressourcen enthalten.
Im vorherigen Beispiel ist **Settings** die einzige aufgerufene Ressource.
Es folgen die anderen verfügbaren Ressourcen:

* **ConfigurationRepositoryWeb**: Gibt einen HTTP-Pulldienst für Konfigurationen an.
* **ConfigurationRepositoryWeb**: Gibt eine SMB-Freigabe für Konfigurationen an.
* **ResourceRepositoryWeb**: Gibt einen HTTP-Pulldienst für Module an.
* **ResourceRepositoryWeb**: Gibt eine SMB-Freigabe für Module an.
* **ReportServerWeb**: Gibt einen HTTP-Pulldienst an, an den Berichte gesendet werden.
* **PartialConfiguration**: Stellt Daten für die Aktivierung von Teilkonfigurationen bereit.

## <a name="basic-settings"></a>Grundlegende Einstellungen

Außer der Angabe von Endpunkten/Pfaden und Teilkonfigurationen für Pulldienste werden alle Eigenschaften des LCM in einem **Settings**-Block konfiguriert.
Die folgenden Eigenschaften sind in einem **Settings**-Block verfügbar:

|  Eigenschaft  |  Type  |  Beschreibung   |
|----------- |------- |--------------- |
| ActionAfterReboot| string| Gibt an, was nach einem Neustart während der Anwendung einer Konfiguration passiert. Die möglichen Werte sind __ContinueConfiguration__ und __StopConfiguration__. <ul><li> __ContinueConfiguration__: Nach dem Neustart des Computers wird das Anwenden der aktuellen Konfiguration fortgesetzt. Dies ist der Standardwert.</li><li>__StopConfiguration__: Nach dem Neustart des Computers wird die aktuelle Konfiguration beendet.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__, wenn neue vom Pulldienst heruntergeladene Konfigurationen die alten Konfigurationen auf dem Zielknoten überschreiben dürfen. Andernfalls „$FALSE“.|
| CertificateId| string| Der Fingerabdruck eines Zertifikats zur Sicherung von Anmeldeinformationen, die in einer Konfiguration übergeben werden. Weitere Informationen finden Sie unter [Möchten Sie Anmeldeinformationen in Windows PowerShell zum Konfigurieren des gewünschten Zustands schützen?](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx). <br> __Hinweis:__ Dies wird bei Verwendung des Azure Automation DSC-Pulldiensts automatisch verwaltet.|
| ConfigurationDownloadManagers| CimInstance[]| Veraltet. Verwenden Sie die Blöcke __ConfigurationRepositoryWeb__ und __ConfigurationRepositoryShare__ zum Definieren von Pulldienstendpunkten für Konfigurationen.|
| ConfigurationID| string| Für die Abwärtskompatibilität mit älteren Pulldienstversionen. Eine GUID, die die Konfigurationsdatei identifiziert, die von einem Pulldienst abgerufen werden soll. Der Knoten ruft Konfigurationen vom Pulldienst ab, wenn der Name der MOF-Konfigurationsdatei „ConfigurationID.mof“ lautet.<br> __Hinweis:__ Wenn Sie diese Eigenschaft festlegen, kann der Knoten nicht mithilfe von __RegistrationKey__ bei einem Pulldienst registriert werden. Weitere Informationen finden Sie unter [Einrichten eines Pullclients mit Konfigurationsnamen](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| string | Gibt an, wie der LCM die Konfiguration tatsächlich auf die Zielknoten anwendet. Mögliche Werte sind __ApplyOnly__, __ApplyAndMonitor__ und __ApplyAndAutoCorrect__. <ul><li>__ApplyOnly__: DSC wendet die Konfiguration an und führt keine weiteren Schritte aus, es sei denn, eine neue Konfiguration wird per Push auf den Zielknoten übertragen oder per Pull von einem Dienst abgerufen. Nach der ersten Anwendung einer neuen Konfiguration überprüft DSC nicht auf Abweichungen von einem zuvor konfigurierten Status. Beachten Sie, dass DSC versucht, die Konfiguration anzuwenden, bis dies erfolgreich passiert ist, bevor __ApplyOnly__ wirksam wird. </li><li> __ApplyAndMonitor__: Dies ist der Standardwert. Der LCM wendet neue Konfigurationen an. Wenn der Zielknoten nach der ersten Anwendung einer neuen Konfiguration vom gewünschten Zustand abweicht, meldet DSC die Abweichung in Protokollen. Beachten Sie, dass DSC versucht, die Konfiguration anzuwenden, bis dies erfolgreich passiert ist, bevor __ApplyAndMonitor__ wirksam wird.</li><li>__ApplyAndAutoCorrect:__ DSC wendet neue Konfigurationen an. Wenn der Zielknoten nach der ersten Anwendung einer neuen Konfiguration vom gewünschten Zustand abweicht, meldet DSC die Abweichung in Protokollen und wendet dann die aktuelle Konfiguration an.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Gibt (in Minuten) an, wie oft die aktuelle Konfiguration überprüft und angewendet wird. Diese Eigenschaft wird ignoriert, wenn die „ConfigurationMode“-Eigenschaft auf „ApplyOnly“ festgelegt ist. Der Standardwert ist 15.|
| DebugMode| string| Mögliche Werte sind __None__, __ForceModuleImport__ und __All__. <ul><li>Bei Festlegung auf __None__ werden zwischengespeicherte Ressourcen verwendet. Dies ist die Standardeinstellung, die in Produktionsszenarien verwendet werden sollte.</li><li>Das Festlegen auf __ForceModuleImport__ bewirkt, dass der LCM DSC-Ressourcenmodule erneut lädt, auch wenn sie zuvor bereits geladen und zwischengespeichert wurden. Dies beeinträchtigt die Leistung von DSC-Vorgängen, da jedes Modul bei Verwendung neu geladen wird. In der Regel wird dieser Wert beim Debuggen einer Ressource verwendet.</li><li>In dieser Version ist __All__ identisch mit __ForceModuleImport__.</li></ul> |
| RebootNodeIfNeeded| bool| Legen Sie für diese Option `$true` fest, um Ressourcen das Neustarten des Knotens mithilfe des `$global:DSCMachineStatus`-Flags zu ermöglichen. Andernfalls müssen Sie den Knoten für jede Konfiguration manuell neu starten, die dies erfordert. Der Standardwert ist `$false`. Um diese Einstellung zu verwenden, wenn eine Neustartbedingung von einer anderen Komponente als von DSC in Kraft gesetzt wird (z.B. Windows Installer), kombinieren Sie diese Einstellung mit dem Modul [xPendingReboot](https://github.com/powershell/xpendingreboot).|
| RefreshMode| string| Gibt an, wie der LCM Konfigurationen abruft. Die möglichen Werte sind __Disabled__, __Push__ und __Pull__. <ul><li>__Disabled__: DSC-Konfigurationen werden für diesen Knoten deaktiviert.</li><li> __Push__: Konfigurationen werden gestartet, indem das Cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aufgerufen wird. Die Konfiguration wird sofort auf den Knoten angewendet. Dies ist der Standardwert.</li><li>__Pull:__ Der Knoten ist so konfiguriert, dass regelmäßig eine Überprüfung auf Konfigurationen von einem Pulldienst oder SMB-Pfad erfolgt. Wenn diese Eigenschaft auf __Pull__ festgelegt ist, müssen Sie in einem __ConfigurationRepositoryWeb__- oder __ConfigurationRepositoryShare__-Block einen HPPT-Pfad (Dienst) oder einen SMB-Pfad (Freigabe) angeben.</li></ul>|
| RefreshFrequencyMins| UInt32| Das Zeitintervall (in Minuten), in dem der LCM einen Pulldienst auf aktualisierte Konfigurationen abfragt. Dieser Wert wird ignoriert, wenn der LCM nicht im Pullmodus konfiguriert ist. Der Standardwert ist 30.|
| ReportManagers| CimInstance[]| Veraltet. Verwenden Sie __ReportServerWeb__-Blöcke, um einen Endpunkt zum Senden von Berichtsdaten an einen Pulldienst zu definieren.|
| ResourceModuleManagers| CimInstance[]| Veraltet. Verwenden Sie die Blöcke __ResourceRepositoryWeb__ und __ResourceRepositoryShare__ zum Definieren von HTTP-Endpunkten bzw. SMB-Pfaden für den Pulldienst.|
| PartialConfigurations| CimInstance| Nicht implementiert. Nicht verwenden.|
| StatusRetentionTimeInDays | UInt32| Anzahl der Tage, die der LCM den Status der aktuellen Konfiguration beibehält.|

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

## <a name="pull-service"></a>Pulldienst

Die LCM-Konfiguration unterstützt die folgenden Typen von Pulldienstendpunkten:

- **Konfigurationsserver**: Ein Repository für DSC-Konfigurationen. Definieren Sie Konfigurationsserver mithilfe der Blöcke **ConfigurationRepositoryWeb** (für webbasierte Server) und **ConfigurationRepositoryShare** (für SMB-basierte Server).
- **Ressourcenserver**: Ein Repository für DSC-Ressourcen, verpackt als PowerShell-Module. Definieren Sie Ressourcenserver mithilfe der Blöcke **ResourceRepositoryWeb** (für webbasierte Server) und **ResourceRepositoryShare** (für SMB-basierte Server).
- **Berichtsserver**: Dienst, an den DSC Berichtsdaten sendet. Definieren Sie Berichtsserver mithilfe von **ReportServerWeb**-Blöcken. Ein Berichtsserver muss ein Webdienst sein.

Weitere Informationen zu Pulldiensten finden Sie unter [Desired State Configuration – Pulldienst](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Konfigurationsserverblöcke

Zum Definieren eines webbasierten Konfigurationsservers erstellen Sie einen **ConfigurationRepositoryWeb**-Block.
Ein **ConfigurationRepositoryWeb**-Block definiert die folgenden Eigenschaften.

|Eigenschaft|Type|Beschreibung|
|---|---|---|
|AllowUnsecureConnection|bool|Legen Sie diese Einstellung auf **$TRUE** fest, um Verbindungen zwischen Knoten und Server ohne Authentifizierung zu erlauben. Bei Festlegung auf **$FALSE** ist eine Authentifizierung erforderlich.|
|CertificateId|string|Der Fingerabdruck eines Zertifikats zur Authentifizierung beim Server.|
|ConfigurationNames|String[]|Array der Namen von Konfigurationen, die per Pull vom Zielknoten abgerufen werden. Diese werden nur verwendet, wenn der Knoten über einen **RegistrationKey** beim Pulldienst registriert ist. Weitere Informationen finden Sie unter [Einrichten eines Pullclients mit Konfigurationsnamen](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|string|GUID, die den Knoten beim Pulldienst registriert. Weitere Informationen finden Sie unter [Einrichten eines Pullclients mit Konfigurationsnamen](../pull-server/pullClientConfigNames.md).|
|ServerURL|string|URL des Konfigurationsdiensts.|
|ProxyURL*|string|Die URL des HTTP-Proxys, der bei der Kommunikation mit dem Konfigurationsdienst verwendet werden soll.|
|ProxyCredential*|pscredential|Anmeldeinformation, die für den HTTP-Proxy verwendet werden soll.|

> [!NOTE]
> * Wird in den Windows-Versionen 1809 und höher unterstützt.

Ein Beispielskript, das die Konfiguration des Werts „ConfigurationRepositoryWeb“ für lokale Knoten vereinfacht, steht unter [Generieren von DSC-Metakonfigurationen](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) zur Verfügung.

Zum Definieren eines SMB-basierten Konfigurationsservers erstellen Sie einen **ConfigurationRepositoryShare**-Block.
Ein **ConfigurationRepositoryShare**-Block definiert die folgenden Eigenschaften.

|Eigenschaft|Type|Beschreibung|
|---|---|---|
|Credential|MSFT_Credential|Anmeldeinformationen zum Authentifizieren bei der SMB-Freigabe.|
|SourcePath|string|Pfad der SMB-Freigabe.|

## <a name="resource-server-blocks"></a>Ressourcenserverblöcke

Zum Definieren eines webbasierten Ressourcenservers erstellen Sie einen **ResourceRepositoryWeb**-Block.
Ein **ResourceRepositoryWeb**-Block definiert die folgenden Eigenschaften.

|Eigenschaft|Type|Beschreibung|
|---|---|---|
|AllowUnsecureConnection|bool|Legen Sie diese Einstellung auf **$TRUE** fest, um Verbindungen zwischen Knoten und Server ohne Authentifizierung zu erlauben. Bei Festlegung auf **$FALSE** ist eine Authentifizierung erforderlich.|
|CertificateId|string|Der Fingerabdruck eines Zertifikats zur Authentifizierung beim Server.|
|RegistrationKey|string|GUID, die den Knoten beim Pulldienst identifiziert.|
|ServerURL|string|URL des Konfigurationsservers.|
|ProxyURL*|string|Die URL des HTTP-Proxys, der bei der Kommunikation mit dem Konfigurationsdienst verwendet werden soll.|
|ProxyCredential*|pscredential|Anmeldeinformation, die für den HTTP-Proxy verwendet werden soll.|

> [!NOTE]
> * Wird in den Windows-Versionen 1809 und höher unterstützt.

Ein Beispielskript, das die Konfiguration des Werts „ResourceRepositoryWeb“ für lokale Knoten vereinfacht, steht unter [Generieren von DSC-Metakonfigurationen](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) zur Verfügung.

Zum Definieren eines SMB-basierten Ressourcenservers erstellen Sie einen **ResourceRepositoryShare**-Block.
Ein **ResourceRepositoryShare**-Block definiert die folgenden Eigenschaften.

|Eigenschaft|Type|Beschreibung|
|---|---|---|
|Credential|MSFT_Credential|Anmeldeinformationen zum Authentifizieren bei der SMB-Freigabe. Ein Beispiel für die Weitergabe von Anmeldeinformationen finden Sie unter [Einrichten eines DSC-SMB-Pullservers](../pull-server/pullServerSMB.md).|
|SourcePath|string|Pfad der SMB-Freigabe.|

## <a name="report-server-blocks"></a>Berichtsserverblöcke

Zum Definieren eines Berichtsservers erstellen Sie einen **ReportServerWeb**-Block.
Die Berichtsserverrolle ist nicht kompatibel mit dem SMB-basierten Pulldienst.
Ein **ReportServerWeb**-Block definiert die folgenden Eigenschaften.

|Eigenschaft|Type|Beschreibung|
|---|---|---|
|AllowUnsecureConnection|bool|Legen Sie diese Einstellung auf **$TRUE** fest, um Verbindungen zwischen Knoten und Server ohne Authentifizierung zu erlauben. Bei Festlegung auf **$FALSE** ist eine Authentifizierung erforderlich.|
|CertificateId|string|Der Fingerabdruck eines Zertifikats zur Authentifizierung beim Server.|
|RegistrationKey|string|GUID, die den Knoten beim Pulldienst identifiziert.|
|ServerURL|string|URL des Konfigurationsservers.|
|ProxyURL*|string|Die URL des HTTP-Proxys, der bei der Kommunikation mit dem Konfigurationsdienst verwendet werden soll.|
|ProxyCredential*|pscredential|Anmeldeinformation, die für den HTTP-Proxy verwendet werden soll.|

> [!NOTE]
> * Wird in den Windows-Versionen 1809 und höher unterstützt.

Ein Beispielskript, das die Konfiguration des Werts „ReportServerWeb“ für lokale Knoten vereinfacht, steht unter [Generieren von DSC-Metakonfigurationen](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations) zur Verfügung.

## <a name="partial-configurations"></a>Teilkonfigurationen

Zum Definieren von Teilkonfigurationen erstellen Sie einen **PartialConfiguration**-Block.
Weitere Informationen zu Teilkonfigurationen finden Sie unter [DSC-Teilkonfigurationen](../pull-server/partialConfigs.md).
Ein **PartialConfiguration**-Block definiert die folgenden Eigenschaften.

|Eigenschaft|Type|Beschreibung|
|---|---|---|
|ConfigurationSource|string[]|Ein Array mit Namen von Konfigurationsservern, die zuvor in den Blöcken **ConfigurationRepositoryWeb** und **ConfigurationRepositoryShare** definiert wurden, aus denen die Teilkonfiguration per Pull abgerufen wird.|
|DependsOn|string{}|Eine Liste der Namen anderer Konfigurationen, die abgeschlossen sein müssen, bevor diese Teilkonfiguration angewendet wird.|
|Beschreibung|string|Text zum Beschreiben der Teilkonfiguration.|
|ExclusiveResources|string[]|Array von Ressourcen, die ausschließlich für diese Teilkonfiguration gelten.|
|RefreshMode|string|Gibt an, wie der LCM diese Teilkonfiguration abruft. Die möglichen Werte sind __Disabled__, __Push__ und __Pull__. <ul><li>__Disabled__: Diese Teilkonfiguration ist deaktiviert.</li><li> __Push__: Die Teilkonfiguration wird per Push auf den Knoten übertragen, indem das Cmdlet [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) aufgerufen wird. Nachdem alle Teilkonfigurationen für den Knoten von einem Dienst per Push oder Pull abgerufen wurden, kann die Konfiguration durch Aufrufen von `Start-DscConfiguration –UseExisting` gestartet werden. Dies ist der Standardwert.</li><li>__Pull:__ Der Knoten ist so konfiguriert, dass regelmäßig eine Überprüfung auf Teilkonfigurationen von einem Pulldienst erfolgt. Wenn diese Eigenschaft auf __Pull__ festgelegt ist, müssen Sie einen Pulldienst in der __ConfigurationSource__-Eigenschaft festlegen. Weitere Informationen zum Azure Automation-Pulldienst finden Sie unter [Azure Automation DSC – Übersicht](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|Array der Namen von Ressourcenservern, von denen erforderliche Ressourcen für diese Teilkonfiguration heruntergeladen werden. Diese Namen müssen auf Dienstendpunkte verweisen, die zuvor in den Blöcken **ResourceRepositoryWeb** und **ResourceRepositoryShare** definiert wurden.|

__Hinweis:__ Teilkonfigurationen werden in Azure Automation DSC unterstützt, es kann jedoch nur eine Konfiguration aus jedem Automation-Konto pro Knoten abgerufen werden.

## <a name="see-also"></a>Weitere Informationen

### <a name="concepts"></a>Konzepte
[Windows PowerShell DSC – Übersicht](../overview/overview.md)

[Erste Schritte mit Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Weitere Ressourcen

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Einrichten eines Pullclients mit Konfigurationsnamen](../pull-server/pullClientConfigNames.md)
