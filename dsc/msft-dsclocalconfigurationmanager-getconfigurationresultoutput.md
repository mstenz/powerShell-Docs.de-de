---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.

<a id="syntax" class="xliff"></a>
Syntax
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a id="parameters" class="xliff"></a>
Parameter
----------

*jobId* \[in\]  
Die ID des Auftrags, für den Ausgabedaten abgerufen werden sollen.

*resumeOutputBookmark* \[in\]  
Gibt an, dass die Ausgabe eine Fortsetzung eines vorherigen Lesezeichens sein soll.

*output* \[out\]  
Die Ausgabe für den angegebenen Auftrag.

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

 

 



