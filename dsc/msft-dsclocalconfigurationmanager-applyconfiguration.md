---
title: ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 6f9c6a8851732574ac72bc4f3a3db1a73fbbecf2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden. 

Wenn keine ausstehende Konfiguration vorhanden ist, wendet diese Methode die aktuelle Konfiguration erneut an.


## <a name="syntax"></a>Syntax
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameter
----------

*force* \[in\]  
Wenn dies **true** ist, wird die aktuelle Konfiguration erneut angewendet, auch wenn eine Konfiguration aussteht.

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

 

 



