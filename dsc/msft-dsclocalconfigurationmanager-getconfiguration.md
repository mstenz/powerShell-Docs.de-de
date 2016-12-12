---
title: GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 19d4790f22491e0bb11de1e315d1ee3b07929d55
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.

<a name="syntax"></a>Syntax
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a>Parameter
----------

*configurationData* \[in\]  
Gibt die zu sendenden Konfigurationsdaten an.

*configurations* \[out\]  
Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.

## <a name="return-value"></a>Rückgabewert
------------

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## <a name="remarks"></a>Hinweise

Dies ist eine statische Methode.

## <a name="requirements"></a>Anforderungen
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Siehe auch


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)
 

 



