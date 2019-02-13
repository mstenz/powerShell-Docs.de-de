---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679144"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.

## <a name="syntax"></a>Syntax

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parameter

*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.

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