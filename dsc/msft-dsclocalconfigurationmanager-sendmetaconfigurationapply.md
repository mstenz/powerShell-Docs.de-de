---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Legen Sie die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendmetaconfigurationapply'
MSHAttr: 'PreferredLib:/library'
title: 'SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.

Syntax
------

```mof
uint32 SendMetaConfigurationApply(
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


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->


