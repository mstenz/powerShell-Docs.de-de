---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 35f732698fcc58f7bd43945edd10c143ffb79af9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="msftdsclocalconfigurationmanager-class" class="xliff"></a>
# MSFT_DSCLocalConfigurationManager-Klasse

Der lokale Konfigurations-Manager, der die Zustände von Konfigurationsdateien steuert und den Konfigurations-Agent verwendet, um die Konfigurationen anzuwenden.

Die folgende Syntax wurde aus MOF-Code (Managed Object Format, verwaltetes Objektformat) vereinfacht und enthält alle geerbten Eigenschaften.

<a id="syntax" class="xliff"></a>
## Syntax
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

<a id="members" class="xliff"></a>
## Mitglieder
-------

Die **MSFT_DSCLocalConfigurationManager**-Klasse hat folgende Member:

-   [Methoden][]

<a id="methods" class="xliff"></a>
### Methoden

Die **MSFT_DSCLocalConfigurationManager**-Klasse enthält diese Methoden.

|Methode |Beschreibung |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden.| 
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Deaktiviert das Debuggen von DSC-Ressourcen.| 
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Aktiviert das Debuggen von DSC-Ressourcen.| 
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.| 
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.| 
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Abrufen des Konfigurationsstatusverlaufs.| 
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.| 
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Startet die Konsistenzprüfung.| 
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Entfernt die Konfigurationsdateien.| 
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Ruft direkt die **Get**-Methode einer DSC-Ressource auf.| 
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Ruft direkt die **Set**-Methode einer DSC-Ressource auf.| 
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Ruft direkt die **Test**-Methode einer DSC-Ressource auf.| 
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Führt einen Rollback zu einer vorherigen Konfiguration aus.| 
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.| 
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.| 
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Senden des Konfigurationsdokuments an den verwalteten Knoten und Beginnen mit der Verwendung des Konfigurations-Agents zum Anwenden der Konfiguration. Verwenden Sie „GetConfigurationResultOutput“, um Ergebnisausgaben abzurufen.| 
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.| 
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Beende die Konfiguration, die gerade ausgeführt wird.| 
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Sendet das Konfigurationsdokument an den verwalteten Knoten und überprüft die aktuelle Konfiguration anhand dieses Dokuments.| 



 

<a id="requirements" class="xliff"></a>
## Anforderungen
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration



 

 



