---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Direktes Ausführen von „Set“ für einen Anbieter.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourceset'
MSHAttr: 'PreferredLib:/library'
title: 'ResourceSet-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# ResourceSet-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft direkt die **Set**-Methode einer DSC-Ressource auf.

Syntax
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
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

*RebootRequired* \[out\]  
Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn der Zielknoten neu gestartet werden muss.

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


