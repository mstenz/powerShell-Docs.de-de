---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Senden des Konfigurationsdokuments an den verwalteten Knoten und Beginnen mit der Verwendung des Konfigurations-Agents zum Anwenden der Konfiguration. Verwenden Sie „GetConfigurationResultOutput“, um Ergebnisausgaben abzurufen.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfigurationapplyasync'
MSHAttr: 'PreferredLib:/library'
title: 'SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.

Syntax
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

Parameter
----------

*ConfigurationData* \[in\]  
Die Umgebungsdaten für die Konfiguration.

*force* \[in\]  
**true**, um das Beenden der Konfiguration zu erzwingen.

*jobId* \[in\]  
Die ID des Auftrags, für den die Konfiguration gesendet werden soll.

## Rückgabewert
------------

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## Hinweise

Dies ist eine statische Methode.

## Anforderungen
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## Siehe auch


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->


