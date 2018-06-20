---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218194"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Aktiviert das Debuggen von DSC-Ressourcen.

<a name="syntax"></a>Syntax
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a>Parameter
----------

*BreakAll* \[in\] Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.

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