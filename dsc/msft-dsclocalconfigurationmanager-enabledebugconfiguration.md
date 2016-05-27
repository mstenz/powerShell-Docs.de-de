---
title:  EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
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
 

 





<!--HONumber=May16_HO3-->


