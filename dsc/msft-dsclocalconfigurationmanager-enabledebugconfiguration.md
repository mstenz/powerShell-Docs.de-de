---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Hilfe und Unterstützung bei der DSC-Konfiguration'
MS-HAID: 'cimwin32a.msft\_dsclocalconfigurationmanager\_enabledebugconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Aktiviert das Debuggen von DSC-Ressourcen.

Syntax
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

Parameter
----------

*BreakAll* \[in\]  
Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.

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


