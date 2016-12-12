---
title: TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 0777467d37e2f5588f9c0ef368148e3bea963a5b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und überprüft die aktuelle Konfiguration anhand dieses Dokuments.

<a name="syntax"></a>Syntax
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Parameter
----------

*configurationData* \[in\]  
Umgebungsdaten für die Konfiguration.

*InDesiredState* \[out\]  
Gibt bei der Rückgabe an, ob sich der verwaltete Knoten im vom Konfigurationsdokument angegebenen Zustand befindet.

*ResourcesInDesiredState* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceInDesiredState**-Klasse, die Ressourcen angibt, die sich im gewünschten Zustand befinden.

*ResourcesNotInDesiredState* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceNotInDesiredState**-Klasse, die Ressourcen angibt, die sich nicht im gewünschten Zustand befinden.

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


 

 



