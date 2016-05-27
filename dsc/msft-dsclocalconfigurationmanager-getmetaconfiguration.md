---
title:  GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
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


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=May16_HO3-->


