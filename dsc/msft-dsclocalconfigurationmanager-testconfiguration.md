---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und überprüft die aktuelle Konfiguration anhand dieses Dokuments.

<a id="syntax" class="xliff"></a>
Syntax
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a id="parameters" class="xliff"></a>
Parameter
----------

*configurationData* \[in\]  
Umgebungsdaten für die Konfiguration.

*InDesiredState* \[out\]  
Gibt bei der Rückgabe an, ob sich der verwaltete Knoten im vom Konfigurationsdokument angegebenen Zustand befindet.

*ResourcesInDesiredState* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceInDesiredState**-Klasse, die Ressourcen angibt, die sich im gewünschten Zustand befinden.

*ResourcesNotInDesiredState* \[out\]  
Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceNotInDesiredState**-Klasse, die Ressourcen angibt, die sich nicht im gewünschten Zustand befinden.

<a id="return-value" class="xliff"></a>
## Rückgabewert
------------

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

<a id="remarks" class="xliff"></a>
## Hinweise

Dies ist eine statische Methode.

<a id="requirements" class="xliff"></a>
## Anforderungen
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## Siehe auch


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 



