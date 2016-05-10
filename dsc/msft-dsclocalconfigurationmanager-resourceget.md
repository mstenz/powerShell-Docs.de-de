---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Direktes Ausführen von „Get“ für einen Anbieter.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourceget'
MSHAttr: 'PreferredLib:/library'
title: 'ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft direkt die **Get**-Methode einer DSC-Ressource auf.

Syntax
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

Parameter
----------

*ResourceType* \[in\]  
Der Name der aufzurufenden Ressource.

*ModuleName* \[in\]  
Der Name des Moduls, das die aufzurufende Ressource enthält.

*resourceProperty* \[in\]  
Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an. Verwenden Sie das
[Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)-Cmdlet zum Ermitteln von Ressourceneigenschaften und deren Typen.

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


