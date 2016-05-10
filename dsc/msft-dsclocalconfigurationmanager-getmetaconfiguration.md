---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Abrufen der Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getmetaconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.

Syntax
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

Parameter
----------

*MetaConfiguration* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCMetaConfiguration**-Klasse, die die Einstellungen definiert.

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


