---
title: RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: c915ebd021ed20209bc491505d45cff2ac89f21d
ms.openlocfilehash: 771a9c7b50aba26f89dbf6b24eb3df67bafeac0a

---


# RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Führt einen Rollback der Konfiguration zu einer früheren Version durch.

Syntax
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

Parameter
----------

*configurationNumber* \[in\]  
Gibt die angeforderte Konfiguration an. 

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


 

 






<!--HONumber=Aug16_HO3-->


