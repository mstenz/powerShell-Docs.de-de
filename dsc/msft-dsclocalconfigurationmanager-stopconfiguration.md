---
title: StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 9721486cca6f94d6b156c6ee1992eced6652c123
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Beende die Konfigurationsänderung, die gerade ausgeführt wird.

<a name="syntax"></a>Syntax
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a>Parameter
----------

*force* \[in\]  
**true**, um das Beenden der Konfiguration zu erzwingen.

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


 

 



