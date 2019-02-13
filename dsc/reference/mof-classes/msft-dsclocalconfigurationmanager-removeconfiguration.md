---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677621"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Entfernt die Konfigurationsdateien.

## <a name="syntax"></a>Syntax

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parameter

*Stage* \[in\] Gibt an, welches Konfigurationsdokument entfernt werden soll. Die folgenden Werte sind gültig:

|Wert |Beschreibung |
|:--- |:---|
|**1** | Das **aktuelle** (Current) Konfigurationsdokument (current.mof). |
|**2** | Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).  |
|**4** | Das **vorherige** (Previous) Konfigurationsdokument (previous.mof). |

*Force* \[in\] **true**, um das Entfernen der Konfiguration zu erzwingen.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## <a name="remarks"></a>Hinweise

Dies ist eine statische Methode.

## <a name="requirements"></a>Anforderungen

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Siehe auch

[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)