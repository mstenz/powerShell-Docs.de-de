---
title:  GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
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


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)
 

 





<!--HONumber=May16_HO3-->


