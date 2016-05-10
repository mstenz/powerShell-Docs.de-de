---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Senden des Konfigurationsdokuments an den verwalteten Knoten und Verwenden des Konfigurations-Agents zum Anwenden der Konfiguration mithilfe der Get-Methode.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.

Syntax
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

Parameter
----------

*configurationData* \[in\]  
Gibt die zu sendenden Konfigurationsdaten an.

*configurations* \[out\]  
Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.

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


