---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678603"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.

## <a name="syntax"></a>Syntax

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parameter

*jobId* \[in\] Die ID des Auftrags, für den Ausgabedaten abgerufen werden sollen.

*resumeOutputBookmark* \[in\] Gibt an, dass die Ausgabe eine Fortsetzung eines vorherigen Lesezeichens sein soll.

*output* \[out\] Die Ausgabe für den angegebenen Auftrag.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## <a name="remarks"></a>Hinweise

Dies ist eine statische Methode.

## <a name="requirements"></a>Anforderungen

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Siehe auch

[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)