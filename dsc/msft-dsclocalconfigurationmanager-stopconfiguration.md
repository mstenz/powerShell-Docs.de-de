---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Beende die Konfigurationsänderung, die gerade ausgeführt wird.

<a id="syntax" class="xliff"></a>
Syntax
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
Parameter
----------

*force* \[in\]  
**true**, um das Beenden der Konfiguration zu erzwingen.

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


 

 



