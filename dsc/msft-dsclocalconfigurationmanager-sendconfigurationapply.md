---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: c578f4f52d3ea70e7bcf683ac204d6e484d4630d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222155"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.

<a name="syntax"></a>Syntax
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Parameter
----------

*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.

*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.

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