---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Aktiviert das Debuggen von DSC-Ressourcen.

<a id="syntax" class="xliff"></a>
Syntax
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a id="parameters" class="xliff"></a>
Parameter
----------

*BreakAll* \[in\]  
Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.

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
 

 



