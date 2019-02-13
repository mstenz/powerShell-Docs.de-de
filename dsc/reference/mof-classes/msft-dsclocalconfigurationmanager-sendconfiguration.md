---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677636"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.

## <a name="syntax"></a>Syntax

```mof
uint32 SendConfiguration(
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