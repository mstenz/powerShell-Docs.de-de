---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Abrufen des Konfigurationsstatusverlaufs.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationstatus'
MSHAttr: 'PreferredLib:/library'
title: 'GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Abrufen des Konfigurationsstatusverlaufs.

Syntax
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

Parameter
----------

*All* \[in\]  
**true**, wenn diese Methode Informationen zu allen Konfigurationsausführungen auf dem Computer zurückgeben soll, einschließlich
der Konfigurationsanwendung und der Konsistenzprüfung.

*configurationStatus* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCConfigurationStatus**-Klasse, die die Einstellungen definiert.

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


