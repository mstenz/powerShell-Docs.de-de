---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186805"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.

<a name="syntax"></a>Syntax
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Parameter
----------

*jobId* \[in\] Die ID des Auftrags, für den Ausgabedaten abgerufen werden sollen.

*resumeOutputBookmark* \[in\] Gibt an, dass die Ausgabe eine Fortsetzung eines vorherigen Lesezeichens sein soll.

*output* \[out\] Die Ausgabe für den angegebenen Auftrag.

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