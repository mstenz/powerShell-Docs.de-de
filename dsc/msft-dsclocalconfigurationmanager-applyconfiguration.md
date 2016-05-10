
# ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden. 

Wenn keine ausstehende Konfiguration vorhanden ist, wendet diese Methode die aktuelle Konfiguration erneut an.


## Syntax
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## Parameter
----------

*force* \[in\]  
Wenn dies **true** ist, wird die aktuelle Konfiguration erneut angewendet, auch wenn eine Konfiguration aussteht.

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


