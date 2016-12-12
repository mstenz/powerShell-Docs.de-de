---
title: SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 95b141472d9428cee71b6970fc1f496704211c0b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.

<a name="syntax"></a>Syntax
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Parameter
----------

*ConfigurationData* \[in\]  
Die Umgebungsdaten für die Konfiguration.

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


 

 



