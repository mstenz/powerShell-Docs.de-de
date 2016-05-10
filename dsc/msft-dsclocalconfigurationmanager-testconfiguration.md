---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Senden des Konfigurationsdokuments an den verwalteten Knoten und Testen des Dokuments anhand der aktuellen Konfiguration.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_testconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und überprüft die aktuelle Konfiguration anhand dieses Dokuments.

Syntax
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

Parameter
----------

*configurationData* \[in\]  
Umgebungsdaten für die Konfiguration.

*InDesiredState* \[out\]  
Gibt bei der Rückgabe an, ob sich der verwaltete Knoten im vom Konfigurationsdokument angegebenen Zustand befindet.

*ResourcesInDesiredState* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceInDesiredState**-Klasse, die Ressourcen angibt, die sich im gewünschten Zustand befinden.

*ResourcesNotInDesiredState* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceNotInDesiredState**-Klasse, die Ressourcen angibt, die sich nicht im gewünschten Zustand befinden.

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


