---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Senden des Konfigurationsdokuments an den verwalteten Knoten und Verwenden des Konfigurations-Agents zum Anwenden der Konfiguration.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfigurationapply'
MSHAttr: 'PreferredLib:/library'
title: 'SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.

Syntax
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

Parameter
----------

*ConfigurationData* \[in\]  
Die Umgebungsdaten für die Konfiguration.

*force* \[in\]  
**true**, um das Beenden der Konfiguration zu erzwingen.

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


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->


