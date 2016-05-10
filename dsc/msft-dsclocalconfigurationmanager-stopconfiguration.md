---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Beenden der in Ausführung befindlichen Konfiguration.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_stopconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Beende die Konfigurationsänderung, die gerade ausgeführt wird.

Syntax
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

Parameter
----------

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


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->


