---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Direktes Ausführen von „Test“ für einen Anbieter.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourcetest'
MSHAttr: 'PreferredLib:/library'
title: 'ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft direkt die **Test**-Methode einer DSC-Ressource auf.

Syntax
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
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

*InDesiredState* \[out\]  
Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn sich der Zielknoten im gewünschten Zustand befindet.

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


