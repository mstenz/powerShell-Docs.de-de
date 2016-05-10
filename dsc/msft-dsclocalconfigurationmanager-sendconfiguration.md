---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Senden des Konfigurationsdokuments an den verwalteten Knoten und Speichern des Dokuments als ausstehend.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.

Syntax
------

```mof
uint32 SendConfiguration(
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


