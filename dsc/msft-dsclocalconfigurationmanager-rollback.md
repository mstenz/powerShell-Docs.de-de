---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Rollback zur vorherigen Konfiguration.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_rollback'
MSHAttr: 'PreferredLib:/library'
title: 'RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Führt einen Rollback der Konfiguration zu einer früheren Version durch.

Syntax
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

Parameter
----------

*configurationNumber* \[in\]  
Gibt die angeforderte Konfiguration an. 

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


