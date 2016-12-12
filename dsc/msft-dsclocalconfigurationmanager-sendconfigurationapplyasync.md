---
title: SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 41177f2eb2bbcf2dddaf232141fb483efaaeeea5
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.

<a name="syntax"></a>Syntax
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a>Parameter
----------

*ConfigurationData* \[in\]  
Die Umgebungsdaten für die Konfiguration.

*force* \[in\]  
**true**, um das Beenden der Konfiguration zu erzwingen.

*jobId* \[in\]  
Die ID des Auftrags, für den die Konfiguration gesendet werden soll.

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


 

 



