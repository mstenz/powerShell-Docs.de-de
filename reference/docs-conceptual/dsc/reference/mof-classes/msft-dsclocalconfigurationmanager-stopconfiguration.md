---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953357"
---
# <a name="stopconfiguration-method"></a>StopConfiguration-Methode

Beende die Konfigurationsänderung, die gerade ausgeführt wird.

## <a name="syntax"></a>Syntax

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameter

*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## <a name="remarks"></a>Hinweise

Dies ist eine statische Methode.

## <a name="requirements"></a>Anforderungen

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Siehe auch

[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)